## Name: Aathi sakthi
## Ref: 24900323
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
### client
~~~
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
~~~
### output
~~~
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
~~~
## OUPUT - ARP
### Client.py
![ARP Client-output](https://github.com/user-attachments/assets/b5fca322-4c98-49bd-84a2-ccd5c70752a2)
### Server.py
![ARP Server-output](https://github.com/user-attachments/assets/8119cc62-ac3c-4f3b-8182-0b9671ac0920)

## PROGRAM - RARP
### Client.py
~~~
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
~~~
### Server.py
~~~
import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
 ip=input("Enter MAC Address : ")
 s.send(ip.encode())
 print("Logical Address",s.recv(1024).decode())
~~~
## OUPUT -RARP
### Client
![Client outup](https://github.com/user-attachments/assets/5f51edcd-1ba5-479e-8556-51893aafb700)
### Server
![Server-output](https://github.com/user-attachments/assets/1f60166b-7559-442b-97ae-72cc2199a04f)
## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
