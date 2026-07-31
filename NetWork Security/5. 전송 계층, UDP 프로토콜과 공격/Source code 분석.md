## UDP 클라이언트 프로그램
```python
#!/bin/env python3
import socket

udp = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)

data = b"Hellow, Server 1 \n"
udp.sendto(data, ("10.9.0.5", 9090))

data = b"Hellow, Server 2 \n"
udp.sendto(data, ("10.9.0.6", 9091))
```
-> UDP 패킷에는 발신지 Port와 목적지 Port가 포함되지만, 소켓이 포트 번호에 바인딩 되지 않는 경우, 운영체제는 무작위 포트 번호를 생성하고 소켓이 처음 사용될 때, 할당 
	- 이때, 첫번째 sendto()는 포트 번호 생성을 트리거하고, 두 번째 sendto()는 발신지 포트가 바인딩
- 만약, 특정 발신지 포트를  선택하려는 경우, bind()를 사용해 바인등 가능 -> 이는 첫번째 sendto()전에 수행
	```python
	udp.bind(("0.0.0.0", 9090))
	```
- 확인하기 위해 서버에서 nc -luk 9090 을 통해 서버를 열고, 수행 가능
---
## UDP 서버 프로그램
- 서버는 특정 포트 번호를 선택하고 소켓을 이 번호에 바인딩해야 서버가 이 포트를 수신하고 있음을 나타냄
```python
#!/bin/env python3
import socket

udp = socket.socket(socket.AF_INET, socket, SOCK_DGRAM)
udp.bind(("0.0.0.0", 9090)) # 첫 번째 인수 : 서버가 데이터를 가져올 수 있는 인터페이스

while Ture:
	data, addr = udp.recvfrom(1024) 
	# 서버가 설정되면 recvfrom()을 사용하여 데이터를 가져올 수 있음
	# 이때, 소켓이 차단되지 않는 경우가 아니면 호출은 UDP 패킷이 도착할 때까지 기다림
	# 호출의 인수 : UDP 패킷에서 검색해야 하는 최대 바이트 수를 지정 => 초과 데이터는 삭제
	print ("From {}: {}".format(addr, data))
```
- 이 서버를 테스트하기 위해선, UDP 클라이언트 프로그램을 사용하여 UDP 패킷을 보내거나, ""