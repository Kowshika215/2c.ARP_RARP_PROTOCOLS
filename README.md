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
CLIENT-ARP
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
SERVER-ARP
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
 ip=input("Enter logical Address : ")
 s.send(ip.encode())
 print("MAC Address",s.recv(1024).decode()
```
CLIENT-RARP
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
SERVER-RARP
```
import socket 
s=socket.socket() 
s.connect(('localhost',9000)) 
while True: 
 ip=input("Enter MAC Address : ") 
 s.send(ip.encode()) 
 print("Logical Address",s.recv(1024).decode())
```
## OUPUT
CLIENT-ARP
![Screenshot 2025-04-07 104029](https://github.com/user-attachments/assets/6b15362c-4f2b-49ee-9751-ecbdddd25d27)

SERVER-ARP
![Screenshot 2025-04-07 104005](https://github.com/user-attachments/assets/0b3cc1e8-7bf1-4f3f-9518-9f551fc52e61)

CLIENT-RARP
![Screenshot 2025-04-29 130924](https://github.com/user-attachments/assets/b96a9578-daee-42c7-ad4f-0ae738532aa5)

SERVER-RARP
![Screenshot 2025-04-29 130937](https://github.com/user-attachments/assets/ee9bb84c-057a-4ecb-bc3b-dc0843461fab)

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
