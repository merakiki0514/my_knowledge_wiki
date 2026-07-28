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
#include <unistd.h>
#include <stdio.h>
#include <sys/socket.h>
#include <linux/if_packet.h>
#include <net/ethernet.h>
#include <arpa/inet.h>
int main() {
	int PACKET_LEN = 512;
	char buffer[PACKET_LEN];
	struct sockaddr saddr;
	struct packet_mreq mr;
	
	// Create the raw socket
	int sock = socket(AF_PACKET, SOCK_RAW, htons(ETH_P_ALL));
	/* 일반 소켓과 원시 소켓의 차이
	일반 소켓 : 커널이 패킷을 수신하면 네트워크 프로토콜을 통해 패킷을 전달하고 결국 소켓을 통해 응용 프로그램에 페이로드를 전달
	원시 소켓 : 패킷을 프로토콜 스택에 전달하느 것외에도 커널은 링크 계층 헤더를 포함한 패킷 복사본을 원시 소켓에 전달 => 패킷을 가로채는 것이 아닌, 사본을 얻음
	*/
	// 세번째 인수 htons(ETH_P_ALL) => 프로토콜 인수 => IP 패킷만 원시 소켓으로 전달
	
	// Turn on the promiscuous mode
	mr.mr_type = PACKET_MR_PROMISC;
	setsockopt(sock, SOL_PACKET, PACKET_ADD_MEMBERSHIP, &mr, sizeof(mr));
	
	// Getting captured packets
	while (1) {
		int data_size=recvfrom(sock, buffer, PACKET_LEN, 0, &saddr, (socklen_t*)sizeof(saddr)); // recvfrom()를 통해 패킷을 기다림 -> 패킷이 도착하면 원시 소켓은 이 API를 통해 패킷의 복사본을 받음
		if(data_size) printf("Got one packet\n");
	}
	close(sock);
	return 0;
}
```
## pcap API를 이용한 패킷 스니핑 - libpcap(sniff.c)(유닉스)
```c
#include <stdlib.h>
#include <stdio.h>
#include <pcap.h>

void got_packet (u_char *args, const struct pcap_pkthdr *header, const u_char *packet)
{
	printf("Got a packet\n");
}
int main()
{
	pcap_t *handle;
	char errbuf[PCAP_ERRBUF_SIZE];
	struct bpf_program fp;
	char filter_exp[] = "icmp";
	bpf_u_int32 net;
	
// Open live pcap session on NIC with name enp0s3
handle = pcap_open_live("enp0s3", BUFSIZ, 1, 1000, errbuf);

// Compile filter_exp into BPF psuedo-code
pcap_compile(handle, &fp, filter_exp, 0, net);
if (pcap_setfilter(handle, &fp) ! = 0)
}
```
