## udp server.c (소켓을 이용한 패킷 수신)
```c
#include <unistd.h>
#include <stdio.h>
#include <string.h>
#include <sys/socket.h>
#include <netinet/ip.h>
void main()
{
	struct sockaddr_in server;
	struct sockaddr_in client;
	int clientlen;
	char buf[1500];
	
	// Creat Socket
	int sock = socket(AF_INET, SOCK_DGRAM, IPPROTO_UDP);
	
	// 프로그램이 수신하는 UDP 포트와 서버 프로그램이 사용하는 IP 주소와 같은 서버에 대한 정보를 제공 => 소켓 설정
	memset((char *) &server, 0, sizeof(server));
	server.sin_family = AF_INET;
	server.sin_addr.s_addr = htonl(INADDR_ANY); // INADDR_ANY를 지정 -> 소켓을 사용가능한 모든 IP 주소에 바인딩할 수 있도록
	server.sin_port = htons(9090);
	
	if (bind(sock, (struct sockaddr *) &server, sizeof(server)) < 0)
		perror("ERROR on binding");
	// 소켓은 bind()시스템 호출을 통해 제공된 정보로 구성 => 제공된 목적지 IP 주소와 포트번호를 가진 UDP 패킷이 소켓을 통해 서버 프로그램에 제공
	
	while (1) {
		bzero(buf, 1500);
		recvfrom(sock, buf, 1500-1, 0, (struct sockaddr *) &client, &clientlen);
		printf("%s\n", buf);
	} 
	// 서버는 recvfrom()을 사용하여 UDP 패킷을 수신할 수 있음
	close(sock);
}
```

## 윈시 소켓을 이용 - sniff_raw.c
```c

```