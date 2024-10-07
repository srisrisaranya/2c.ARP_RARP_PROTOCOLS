# 2c.SIMULATING ARP /RARP PROTOCOLS
## AIM
To write a python program for simulating ARP protocols using TCP.
## ALGORITHM:
## Client:
1. Start the program
2. Using socket connection is established between client and server.
3. Get the IP address to be converted into MAC address.
4. Send this IP address to server.
5. Server returns the MAC address to client.
## Server:
1. Start the program
2. Accept the socket which is created by the client.
3. Server maintains the table in which IP and corresponding MAC addresses are
stored.
4. Read the IP address which is send by the client.
5. Map the IP address with its MAC address and return the MAC address to client.
P
## PROGRAM 
# CLIENT
```
import socket
from datetime import datetime
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
print("client address:",addr)
now=datetime.now()
c.send(now.strftime("%d/%m/%Y %H:%M:%S").encode())
ack=c.recv(1024).decode()
if ack:
    print(ack)
    c.close()
```
## OUPUT 
![image](https://github.com/user-attachments/assets/f6044c0c-8a0c-4ce4-b97e-4e9db201e4f5)


# SERVER
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
print(s.getsockname())
print(s.recv(1024).decode())
s.send("acknowledgement received from the server".encode())
```
## OUPUT 
![image](https://github.com/user-attachments/assets/84628318-3782-42ff-87c5-6f50a65c594b)

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
