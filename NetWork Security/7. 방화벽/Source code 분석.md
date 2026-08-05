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