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
	
	// 4. Accept a connection requese
	
}
```