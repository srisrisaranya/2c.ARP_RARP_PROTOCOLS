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
## PROGRAM - ARP
# CLIENT
```
import socket 
s=socket.socket() 
s.bind(('localhost',8000)) 
s.listen(5) 
c,addr=s.accept() 
address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"8A:BC:E3:FA"}; 
while True: 
            ip=c.recv(1024).decode() 
            try: 
                c.send(address[ip].encode()) 
            except KeyError: 
                c.send("Not Found".encode())   
```
## OUPUT 
![image](https://github.com/user-attachments/assets/9d714534-b872-4703-94bf-ab94bd6758c7)

# SERVER
```
 
import socket 
s=socket.socket() 
s.connect(('localhost',8000)) 
while True: 
 
 
    ip=input("Enter logical Address : ") 
    s.send(ip.encode()) 
    print("MAC Address",s.recv(1024).decode())
```
## OUPUT 
![image](https://github.com/user-attachments/assets/da65ab83-9f58-4966-ba04-de5c542351ad)

# PROGRAM - RARP
# CLIENT
``` 
import socket 
s=socket.socket() 
s.bind(('localhost',9000)) 
s.listen(5) 
c,addr=s.accept() 
address={"6A:08:AA:C2":"192.168.1.100","8A:BC:E3:FA":"192.168.1.99"}; 
while True: 
            ip=c.recv(1024).decode() 
            try: 
                c.send(address[ip].encode()) 
            except KeyError: 
                c.send("Not Found".encode())
```       
# OUTPUT:
![image](https://github.com/user-attachments/assets/4d837687-342c-473f-9820-43a00b918da4)

# SERVER
``` 
import socket 
s=socket.socket() 
s.connect(('localhost',9000)) 
while True: 
    ip=input("Enter MAC Address : ") 
 
 
    s.send(ip.encode()) 
    print("Logical Address",s.recv(1024).decode())
```
# OUTPUT
![image](https://github.com/user-attachments/assets/6a1e06ef-2c5f-42af-8745-7e1f78c99b89)

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
