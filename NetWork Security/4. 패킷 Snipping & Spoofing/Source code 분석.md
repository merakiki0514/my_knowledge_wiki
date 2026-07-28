## udp server.c (소켓을 이용한 패킷 수신)
```
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
	
	// 프로그램이 수신하는 UDP 포트와 서버 프로그램이 사용하는 IP 주소와 같은 서버에 대한 정보를 제공
	memset((char *) &server, 0, sizeof(server));
	server.sin_family = AF_INET;
	server.sin_addr.s_addr = htonl(INADDR_ANY); # INADDR_ANY를 지정 -> thzptdmf tkdyd
	server.sin_port = htons(9090);
	
	if (bind(sock, (struct sockaddr *) &server, sizeof(server)) < 0)
		perror("ERROR on binding");
}
```