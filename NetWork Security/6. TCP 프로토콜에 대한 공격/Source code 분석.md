# (1) Python으로 작성한 TCP
## TCP 클라이언트 프로그램
- 요청을 받는 서버는 9090으로 기다리고 있다는 전제(nc -lnv 9090)
```python
#!/bin/env python3
import socket

tcp = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
tcp.connect(('10.0.2.69', 9090))

tcp.sendall(b"Hello Server!\n")
tcp
```