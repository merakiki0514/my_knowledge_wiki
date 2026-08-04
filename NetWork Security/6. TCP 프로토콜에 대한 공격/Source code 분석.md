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
```c
#include <unistd.h>
#include <stdio.h>
#include <string.h>
#include <sys/socket.h>
#include <netinet/ip.h>
#include <arpa/inet.h>

int main() {
	// 1. Create a socket
	int sockfd = socket(AF_INET, SOCK_STREAM, 0);

	// 2. Set the destination information
	struct sockaddr_in dest;
	memset(&dest, 0, sizeof(struct sockaddr_in));
	dest.sin_family = AF_INET;
	dest.sin_addr.s_addr = inet_addr("10.0.2.69");
	dest.sin_port = htons(9090);
	
	// 3. Connect to the server
	connect(sockfd, (struct sockaddr *)&dest, sizeof(struct socka))
}
```