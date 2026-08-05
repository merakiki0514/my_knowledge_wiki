# 1. Netfiler
## (1) UDP 차단 - seedFilter.c
```c
// skb => 실제 패킷
unsinged int blockUDP(void *priv, struct sk_buff *skb, const struct nf_hook_state *state)
{
	struct iphdr *iph;
	struct udphdr *udph;
	u32 ip_addr;
	char ip[16] = "8.8.8.8";
	
	// Convert the IPv4 addres from dotted decimal to a 32-bit number
	in4_pton(ip, -1, (u8 *)&ip_addr, '\0', NULL);
	// 커널 내부에서 10 진수 형식의 IP주소를 32비트 2진수로 변환
	
	iph = ip_hdr(skb);
	if (iph->protocol == IPPROTO_UDP) {
		udph = udp_hdr(skb);
		if(iph->daddr == ip_addr && ntohs(udph->dest) == 53) {
			printk(KERN_DEBUG "****Droping %pI4 (UDP), port %d\n", &(iph->daddr), port);
			return NF_DROP;  // 패킷 폐기
		}
	}
	return NF_ACCEPT; // 패킷이 이동을 계속하도록 함
}
```
## (2) 기타 응용
- netfilter는 차단하는 대신 패킷을 수정할 수 있음 -> LOCAL_IN hook를 사용함으로 써
-  (ex) 패킷이 hook를 통과하면 IP 헤더에 있는 TTL 필드가 99로 설정 
```c
// Hook this function to NF_INET_LOCAL_IN
unsigned int increaseTTL(void *priv, struct sk_buff *skb, const struct nf_hook_state *state)
{
	struct iphdr *iph;
	
	if (!skb) return NF_ACCEPT;
	iph = ip_hdr(skb);
	if (!iph) return NF_ACCEPT;
	
}
```