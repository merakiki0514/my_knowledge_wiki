## UDP 클라이언트 프로그램
```python
#!/bin/env python3
import socket

udp = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)

data = b"Hellow, Server 1 \n"
udp.sendto(data, ("10.9.0.5", 9090))

data = b"Hellow, Server 2 \n"
udp.sendto(data, ("10.9.0.6", 9010))
```