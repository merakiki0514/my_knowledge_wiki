# 1. 스니핑 Source Code
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
// 콜백 함수
int main()
{
	pcap_t *handle;
	char errbuf[PCAP_ERRBUF_SIZE];
	struct bpf_program fp;
	char filter_exp[] = "icmp";
	bpf_u_int32 net;
	
// Open live pcap session on NIC with name enp0s3
handle = pcap_open_live("enp0s3", BUFSIZ, 1, 1000, errbuf);
// 원시 소켓을 초기화하고 enp0s3 네트워크 장치를 무차별 모드로 설정(3번째 매개변수의 값 1은 무차별모드를 킴)
// 만약 모든 인터페이스에서 패킷을 캡처하기 위해 첫번째 인수에 "any"를 지정할 수 있지만 이 값을 사용하면 promisuous인수가 무시됨

// Compile filter_exp into BPF psuedo-code
pcap_compile(handle, &fp, filter_exp, 0, net);
if (pcap_setfilter(handle, &fp) ! = 0){
	pcap_perror(handle, "Error:");
	exit(EXIT_FAILURE);
}
// pcap_setfilter() -> 소켓에 BPF필터를 설정
// 만약 지정된 필터 표현식에 구문 오류가 있는 경우, pcap_setfilter()는 실패하고 0이 아닌 값을 반환

// Capture packets
pcap_loop(handle, -1, got_packet, NULL);
// pcap_loop() -> 패킷이 캡처되는 pcap세션의 기본 실행 루프에 돌입
// 두번째 매개변수 : 루프가 종료되기전에 캡처하려는 패킷 수를 지정할 수 있음 / -1 => 루프가 끝나지않음
// 세번째 인수 -> 콜백 함수로, 패킷이 pcap에 의해 캡처될 때마다 콜백 함수 가 호출되어 캡처된 패킷에 대해 추가 분석을 수행할 수 있음

pcap_close(handle); // Close handle
return 0;
}
```
-> 스니핑을 위한 C코드를 만들었으면 컴파일 필요
```bash
gcc -o <파일명> <컴파일될 파일명> -lpcap
# gcc를 사용시에는 pcap를 사용하는 코드를 컴파일시 -lpcap 인수를 추가해야 함
```
## 캡처된 패킷 가져오기 - sniff_improved.c
```c
#include <stdlib.h>
#include <stdio.h>
#include <pcap.h>
#include <arpa/inet.h>

/* IP Header*/
struct ipheader {
	unsigned char iph_ihl:4, // IP header length
				  iph_ver:4; // IP version
	unsigned char iph_tos; // Type of service
	unsigned short int iph_len; // IP Packet Length (data + header)
	unsigned short int iph_ident; // Identification
	unsigned short int iph_flag:3, // Fragmentation flags
					   iph_offset:13; // Flags offset
	unsigned char iph_ttl; // Time to Live
	unsigned char iph_protocol; // Protocol type
	unsigned short int iph_checksum; // IP datagram checksum
	struct in_addr iph_sourceip; // Source IP address
	struct in_addr iph_destip; // Destination IP address
};

void got_packet(u_char *args, const struct pcap_pkthdr *header, const u_char *packet)
{
	Struct ethheader *eth = (struct ethheader *)packet;
	// (struct ethheader *)를 사용하여 char버퍼에 대한 포인터를 이더넷 헤더 구조에 대한 포인터로 유형 변환
	if (ntohs(eth->ether_type) == 0x0800) { // 0x0800 is IP type / 다음 offset을 계산하는 대신, eth-> ether_type 필드 이름을 사용하여 유형 필드를 참조 가능
		struct ipheader *ip = (struct ipheader *)
							   (packet + sizeof(struct ethheader)); 
		// IP 헤더에서 일부 정보를 출력하고 싶음 => 포인터를 IP 시작 부분으로 이동 => 이동할 거리 = 이더넷 헤더의 크기(packet + sizeof(struct ethheader))로 IP 패킷의 시작 부분으로 이동
		// 아래와 같이 필드 이름을 사용해 '->'(유형 캐스팅 수행) => 발신지/목적지 IP 주소와 프로토콜 필드에 접근할 수 있음
		printf("From: %s\n", inet_ntoa(ip->iph_sourceip));
		printf("To :%s\n", inet_ntoa(ip->iph_destip));
		
		/* determine protocol */
		switch(ip->iph_protocol) {
			case IPPROTO_TCP:
				printf("Protocol:TCP\n");
				return;
			case IPPROTO_UDP:
				printf("Protocol:UDP\n");
				return;
			case IPPROTO_ICMP:
				printf("Protocol:ICMP\n");
				return;
			default:
				printf("Protocol: others\n");
				return;
		}
	}
}
```
- 패킷을 추가로 처리하려는 경우, 유사하게 사용가능
	-> 포인터를 다음 헤더의 시작 부분으로 이동하고, 해당 헤더로 유형-캐스트
	- 이때, 일부 패킷 의 헤더에는 추가 IP 옵션 필드가 포함될 수 있으므로, IP 헤더의 크기는 고정 X
		=> sizeof(struct ipheader) 사용 불가
	==> IP헤더의 길이를 계산해야 됨 -> IP 헤더의 헤더 길이 필드(ip -> iph ihl)를 사용하여 IP 헤더의 실제 크기를 계산(4를 곱한 값)한 다음 그에 따라 포인터를 이동해야함
	```
	int ip_header_len = ip->iph_ihl * 4;
	u_char *icmp = (struct icmpheader *)
	               (packet + sizeof(struct ethheader) + ip_header_len);
	```

## Scapy를 이용한 스니핑
```python
#!/usr/bin/python3
from scapy.all import *
# 모든 Scapy의 모듈을 가져옴 ------- 1
def print_pkt(pkt) :
	print(pkt.summary())
# 캡쳐된 각 패킷에 대해 callback 함수인 print_pkt()가 호출됨 => 정의된 일부 정보를 출력

pkt = sniff(iface='eth0', filter='icmp', prn= print_pkt)
# 프로그램은 sniff()를 호출하여 eth0 인터페이스에서 패킷 캡처를 시작 / 이때, count를 이용해 패킷의 개수를 지정할 수 있음 => 지정한 패킷을 캡처후 sniff()는 해제  ---------- 2
```
# 2. 스푸핑 Source Code
## 소켓을 이용한 정상적인 일반 패킷 전송
```c
#include <unistd.h>
#include <stdio.h>
#include <string.h>
#include <sys/socket.h>
#include <netinet/ip.h>
#include <arpa/inet.h>
void main()
{
	struct sockaddr_in dest_info;
	char *data = "UDP message\n";
	
	// Create a network socket
	int sock - socket(AF_INET, SOCK_DGRAM, IPPROTO_UDP);
	
	// Provide information about destination.
	memset((char *) &dest_info, 0, sizeof(dest_info));
	dest_info.sin_family = AF_INET;
	dest_info.sin_add.s_add = inet_addr("10.9.0.5");
	dest_info.sin_port = htons(9090);
	
	// Send out the packet
	sendto(sock, data, strlen(data), 0, (struct sockaddr*) &dest_info, sizeof(dest_info));
	close(sock);
}
```

## 윈시 소켓을 이용한 스푸핑된 패킷 보내기 - send_raw_ip_packet()
```c
/* IP Header*/
struct ipheader {
	unsigned char iph_ihl:4, // IP header length
				  iph_ver:4; // IP version
	unsigned char iph_tos; // Type of service
	unsigned short int iph_len; // IP Packet Length (data + header)
	unsigned short int iph_ident; // Identification
	unsigned short int iph_flag:3, // Fragmentation flags
					   iph_offset:13; // Flags offset
	unsigned char iph_ttl; // Time to Live
	unsigned char iph_protocol; // Protocol type
	unsigned short int iph_checksum; // IP datagram checksum
	struct in_addr iph_sourceip; // Source IP address
	struct in_addr iph_destip; // Destination IP address
};

void send_raw_ip_packet(struct ipheader* ip)
{
	struct sockaddr_in dest_info;
	int enable = 1;
	
	// Create a raw network socket.
	int sock = socket (AF_INET, SOCK_RAW, IPPROTO_RAW);
	// AF_INET : IPv4용
	// IPPROTO_RAW : IP 헤더를 제공할 것임을 의미 -> 활성화된 IP_HDRINCL을 의미
	
	// Set socket option.
	setsockopt(sock, IPPROTO_IP, IP_HDRINCL, &enable, sizeof(enable));
	// setsockopt를 이용해 IP_HDRINCL을 활성화
	
	// Provide needed information about destination
	dest_info.sin_family = AF_INET;
	dest_infor.sin_addr = ip->iph_destip
	// 원시 소켓 프로그래밍의 경우, 제공된 IP 헤더에 목적지 정보가 이미 포함 => 계열 정보 및 목적지 IP 주소 설정을 제외하고, sockaddr_in 구조체의 모든 필드를 채울 필요없음
	// 목적지 IP 주소를 설정 -> 목적지가 동일한 네트워크에 있는 경우, 커널이 목적지에 해당하는 올바른 MAC 주소를 얻는데 도움이 됨
	
	// Send the packet out.
	sendto(sock, ip, ntohs(ip->iph_len), 0, (struct sockaddr *) &dest_info, sizeof(dest_info));
	// 패킷을 보낼때 사용 -> sendto()
	// 2번째 인수 : 전체 IP 패킷을 포함하는 버퍼에 대한 포인터
	// 3번째 인수 : 패킷의 길이 필드에서 얻을 수 있는 패킷의 크기
	// 4번째 인수 : 함수 동작에 영향을 미치는 플래그를 설정
	// 다음 두 인수 : 목적지 Sockaddr_in 구조체에 대한 포인터와 크기
	// => 원시 소켓이므로, 호출받으면 자동으로 계산되는 검사합 필드를 제외하고는 IP 패킷을 있는 그대로 보냄
	close(sock);
}
```
## 원시 ICMP 에코 요청 패킷 구성 - spoof_icmp.c
```c
#include <stdio.h>
#include <string.h>
#include <sys/socket.h>
#include <netinet/ip.h>

/* ICMP Header */
struct icmpheader {
	unsigned char icmp_type; // ICMP message type
	unsigned char icmp_code; // Error code
	unsigned short int icmp_chksum; // Checksum for ICMP Header and data
	unsigned short int icmp_id; // Used for identifying request
	unsigned short int icmp_seq; // Sequence number
};

/* IP Header*/
struct ipheader {
	unsigned char iph_ihl:4, // IP header length
				  iph_ver:4; // IP version
	unsigned char iph_tos; // Type of service
	unsigned short int iph_len; // IP Packet Length (data + header)
	unsigned short int iph_ident; // Identification
	unsigned short int iph_flag:3, // Fragmentation flags
					   iph_offset:13; // Flags offset
	unsigned char iph_ttl; // Time to Live
	unsigned char iph_protocol; // Protocol type
	unsigned short int iph_checksum; // IP datagram checksum
	struct in_addr iph_sourceip; // Source IP address
	struct in_addr iph_destip; // Destination IP address
};

unsigned short in_cksum (unsigned short *buf, int length);
void send_raw_ip_packet (struct ipheader* ip);

/***************************************************************
Spoof an ICMP echo request using an arbitrary sorce IP Address
****************************************************************/
int main() {
	char buffer[1500];
	memset(buffer, 0, 1500);
	// 1500 크기의 버퍼를 만들고 0으로 채움
	/************************************************************************
	Fill in the ICMP echo request Header -> 유형과 검사합을 채우면됨
	*************************************************************************/
	struct icmpheader *icmp = (struct icmpheader *)
							  (buffer + sizeof(struct ipheader));
	icmp->ipcmp_type = 8; // ICMP Type: 8 is request, 0 is reply.
	
	// Calculate the checksum for integrity
	icmp->icmp_chksum = 0;
	icmp->icmp_chksum = in_cksum((unsigned short *)icmp, sizeof(struct icmpheader));
	
	/***********************************************************************
	Fill in the IP header
	***********************************************************************/
	struct ipheader *ip = (struct ipheader *) buffer;
	ip->iph_ver = 4;
	ip->iph_ihl = 5;
	ip->iph_ttl = 20;
	ip->iph_sourceip.s_addr = inet_addr("1.2.3.4");
	ip->iph_destip.s_addr = inet_addr("10.9.0.5");
	ip->iph_protocol = IPPROTO_ICMP
	ip->iph_len = htons(sizeof(struct ipheader) + sizeof(struct icmpheader));
	
	/*************************************************************************
	Finally, send the spoofed packet
	*************************************************************************/
	send_raw_ip_packet (ip); 
	return 0;
}

void send_raw_ip_packet(struct ipheader* ip)
{
	struct sockaddr_in dest_info;
	int enable = 1;
	
	// Create a raw network socket.
	int sock = socket (AF_INET, SOCK_RAW, IPPROTO_RAW);
	
	// Set socket option.
	setsockopt(sock, IPPROTO_IP, IP_HDRINCL, &enable, sizeof(enable));
	
	// Provide needed information about destination
	dest_info.sin_family = AF_INET;
	dest_info.sin_addr = ip->iph_destip
	
	// Send the packet out.
	sendto(sock, ip, ntohs(ip->iph_len), 0, (struct sockaddr *)&dest_info, sizeof(dest_info));
	close(sock);
}


```
## 스푸핑 UDP 패킷 구성 - spoof_udp.c
```c
#include <unistd.h>
#include <stdio.h>
#include <string.h>
#include <sys/socket.h>
#include <netinet/ip.h>
#include <arpa/inet.h>

/* UDP Header */
struct udpheader
{
	u_int16_t udp_sport; // source port 
	u_int16_t udp_dport; // destination port
	u_int16_t udp_ulen; // udp length
	u_int16_t udp_sum; // udp checksum
}

/* IP Header*/
struct ipheader {
	unsigned char iph_ihl:4, // IP header length
				  iph_ver:4; // IP version
	unsigned char iph_tos; // Type of service
	unsigned short int iph_len; // IP Packet Length (data + header)
	unsigned short int iph_ident; // Identification
	unsigned short int iph_flag:3, // Fragmentation flags
					   iph_offset:13; // Flags offset
	unsigned char iph_ttl; // Time to Live
	unsigned char iph_protocol; // Protocol type
	unsigned short int iph_checksum; // IP datagram checksum
	struct in_addr iph_sourceip; // Source IP address
	struct in_addr iph_destip; // Destination IP address
};
void send_raw_ip_packet(struct upheader* ip);
// Spoof a UDP packet using an arbitrary source IP Address and port
int main() {
	char buffer[1500];
	memset(buffer, 0, 1500);
	struct ipheader *ip = (struct ipheader *) buffer;
	struct udpheader *udp = (struct udpheader *) (buffer + sizeof(struct ipheader));
	
	// Fill in the UDP data field
	char *data = buffer + sizeof(struct upheader) + sizeof(struct udpheader);
	const char *msg = "Hello Server!\n";
	int data_len - strlen(msg);
	strncpy (data, msg, data_len);
	
	// Fill in the UDP header
	udp->udp_sport = htons(12345);
	udp->udp_dport = htons(9090);
	udp->udp_ulen = htons(sizeof(struct udpheader) + data_len);
	udp->udp_sum = 0; // Many OSes ignore this field, so we do not calculate it.
	
	// Fill in the IP header
	struct ipheader *ip = (struct ipheader *) buffer;
	ip->iph_ver = 4;
	ip->iph_ihl = 5;
	ip->iph_ttl = 20;
	ip->iph_sourceip.s_addr = inet_addr("1.2.3.4");
	ip->iph_destip.s_addr = inet_addr("10.9.0.5");
	ip->iph_protocol = IPPROTO_UDP // The value is 17
	ip->iph_len = htons(sizeof(struct ipheader) + sizeof(struct udpheader) + data_len);
	
	// Send the spoofed packet
	send_raw_ip_packet (ip);
	return 0;
}

void send_raw_ip_packet(struct ipheader* ip)
{
	struct sockaddr_in dest_info;
	int enable = 1;
	
	// Create a raw network socket.
	int sock = socket (AF_INET, SOCK_RAW, IPPROTO_RAW);
	
	// Set socket option.
	setsockopt(sock, IPPROTO_IP, IP_HDRINCL, &enable, sizeof(enable));
	
	// Provide needed information about destination
	dest_info.sin_family = AF_INET;
	dest_info.sin_addr = ip->iph_destip
	
	// Send the packet out.
	sendto(sock, ip, ntohs(ip->iph_len), 0, (struct sockaddr *)&dest_info, sizeof(dest_info));
	close(sock);
}

```
# 3. 스니핑 후 스푸핑
## C코드로 구현 - sniff_spoof_udp.c
- 스푸핑할 목적인 패킷을 캡처한 후 조건에 따라 스푸핑을 진행하는 코드
-> 모든 UDP 패킷을 캡처 => 캡처된 각 UDP 패킷에 대해 목적지 포트가 9999이면 스푸핑된 응답이 전송
```c
#include <stdlib.h>
#include <stdio.h>
#include <pcap.h>
#include <string.h>
#include <sys/socket.h>
#include <netinet/ip.h>
#include <arpa/inet.h>

/* UDP Header */
struct udpheader
{
	u_int16_t udp_sport; // source port 
	u_int16_t udp_dport; // destination port
	u_int16_t udp_ulen; // udp length
	u_int16_t udp_sum; // udp checksum
}

/* IP Header*/
struct ipheader {
	unsigned char iph_ihl:4, // IP header length
				  iph_ver:4; // IP version
	unsigned char iph_tos; // Type of service
	unsigned short int iph_len; // IP Packet Length (data + header)
	unsigned short int iph_ident; // Identification
	unsigned short int iph_flag:3, // Fragmentation flags
					   iph_offset:13; // Flags offset
	unsigned char iph_ttl; // Time to Live
	unsigned char iph_protocol; // Protocol type
	unsigned short int iph_checksum; // IP datagram checksum
	struct in_addr iph_sourceip; // Source IP address
	struct in_addr iph_destip; // Destination IP address
};

// 서로 참조하무르 미리 프로토타입 선언
void got_packet (u_char *args, const struct pcap_pkthdr *header, const u_char *packet);
void send_raw_ip_packet(struct ipheader *ip);
void spoof_reply_udp(struct ipheader *ip);


int main()
{
	pcap_t *handle;
	char errbuf[PCAP_ERRBUF_SIZE];
	struct bpf_program fp;
	char filter_exp[] = "udp";
	bpf_u_int32 net = 0;  // netmask (모르면 0)
	
	// Open live pcap session on NIC with name enp0s3
	handle = pcap_open_live("enp0s3", BUFSIZ, 1, 1000, errbuf);

	// Compile filter_exp into BPF psuedo-code
	pcap_compile(handle, &fp, filter_exp, 0, net);
	if (handle == NULL) {
		fprintf(stderr, "Couldn't open device: %s\n", errbuf);
		exit(EXIT_FAILURE);
	}

	if (pcap_complie(handle, &fp, filter_exp, 0 net) == -1) {
		pcap_perror(handle, "Error:");
		exit(EXIT_FAILURE);
	}
	
	if (pcap_setfilter(handle, &fp) ! = 0){
		pcap_perror(handle, "Error:");
		exit(EXIT_FAILURE);
	}

// Capture packets
pcap_loop(handle, -1, got_packet, NULL);
pcap_close(handle); 
return 0;
}

void got_packet (u_char *args, const struct pcap_pkthdr *header, const u_char *packet)
{
	printf("Got a packet\n");
	
	// 이더넷 헤더(14바이트) 다음이 IP 헤더
	struct ipheader *ip = (struct ipheader *)(packet + 14);
	spoof_reply_udp(ip);
}

void spoof_reply_udp(struct upheader* ip)
{
	const char buffer[1500];
	int ip_header_len = ip->iph_ihl * 4;
	
	struct udpheader *udp = (struct udpheader *) ((u_char *)ip + ip_header_len);
	
	if (ntohs(udp->udp_dport) != 9999) {
		// Only spoof UDP packet with destination port 9999
		return;
	}
	
	// Make a copy from the original packet
	memset((char*)buffer, 0, 1500);
	memcpy((char*)buffer, ip, ntohs(ip->iph_len));
	
	struct ipheader *newip = (struct ipheader *) buffer;
	struct udpheader *newudp = (struct udpheader *) (buffer + ip_header_len);
	char *data = (char *)newudp + sizeof(struct udpheader);
	
	// Construct the UDP payload, keep track of payload size 
	const char *msg = "This is a spoofed reply\n";
	int data_len = strlen(msg);
	strncpy (data, msg, data_len);
	
	// Construct the UDP Header
	newudp->udp_sport = udp->udp_dport;
	newudp->udp_dport = udp->udp_sport;
	newudp->udp_ulen = htons(sizeof(struct udpheader) + data_len);
	newudp->udp_sum = 0;
	
	// Construct the IP header (no change for other fields)
	newip->iph_sourceip = ip->iph_destip;
	newip->iph_destip = ip->iph_sourceip;
	newip->iph_ttl = 50;
	newip->iph_len = htons(sizeof(struct ipheader) + sizeof(struct udpheader) + data_len)
	
	// Send out the spoofed Ip packet
	send_raw_ip_packet(newip); 
}

void send_raw_ip_packet(struct ipheader* ip)
{
	struct sockaddr_in dest_info;
	int enable = 1;
	
	// Create a raw network socket.
	int sock = socket (AF_INET, SOCK_RAW, IPPROTO_RAW);
	if (sock < 0) {
		perror("socket() error");
		return;
	}
	// Set socket option.
	setsockopt(sock, IPPROTO_IP, IP_HDRINCL, &enable, sizeof(enable));
	
	// Provide needed information about destination
	dest_info.sin_family = AF_INET;
	dest_info.sin_addr = ip->iph_destip
	
	// Send the packet out.
	sendto(sock, ip, ntohs(ip->iph_len), 0, (struct sockaddr *)&dest_info, sizeof(dest_info));
	close(sock);
}
```
## 하이브리드 방식 (Scapy와 C를 이용)
### 1. Scapy를 이용한 패킷 템플릿 구성 - generate_udp.c
- UDP 패킷을 구성하고 파일에 저장
```c
#!/usr/bin/python3
from scapy.all import *

IPpkt = IP(dst='10.9.0.5', chksum=0) 
// IP 헤더의 검사합은 패킷이 전송될 때, 다시 계산되므로 설정하지 않거나,잘못된 값이라도 괜찮음
UDPpkt = UDP (dport=53, chksum=0)
// UDP 검사합은 0으로 설정 안되면, Scapy가 검사합을 계산하고 이 필드를 설정
// UDP일 경우 검사합 필드가 0이면, 누락된 검사합으로 간주하여 패킷을 수락
// 단, TCP, ICMP 패킷의 경우, 검사합 필드가 엄격히 확인(0 or 잘못된 값이면 폐기)
pkt = IPpkt/UDPpkt

# Save the packet data to a file
with open('ip.bin', 'wb') as f:
 f.write(bytes(pkt))
```
### 2. C를 이용한 패킷 수정과 전송 - send_premade_udp.c
- 1에서 미리 만들어진 UDP 패킷을 C 프로그램에 로드
- 이 템플릿을 이용해 각각 임의의 발신지 IP 주소와 임의의 발신지 포트 번호를 가진 많은 스푸핑 UDP 패킷 전송
```c
#include <unistd.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/socket.h>
#include <arpa/inet.h>
#include <time.h>

#define MAX_FILE_SIZE 2000
#define TARGET_IP "10.9.0.5"
int send_packet_raw (int sock, char *ip, int n);

int main()
{
	// Create raw socket
	int enable = 1;
	int sock = socket (AF_INET, SOCK_RAW, IPPROTO_RAW);
	setsockopt(sock, IPPROTO_IP, IP_HDRINCL, &enable, sizeof(enable));
	
	// Read the UDP packet from file
	FILE *f = fopen("ip.bin", "rb");
	if (!f) {
		perror("Can't3021174626101)
	}
}
```