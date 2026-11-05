# 2c.SIMULATING ARP /RARP PROTOCOLS
## AIM:
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

## PROGRAM - ARP:
### Server Program:
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
### Client Program:
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("Enter logical Address : ")
    s.send(ip.encode())
    print("MAC Address",s.recv(1024).decode())
```

## OUPUT - ARP:
### Server Output:

<img width="1920" height="1080" alt="Screenshot (205)" src="https://github.com/user-attachments/assets/d6914b86-e52c-4a67-b277-20311523064f" />

### Client Output:

<img width="1920" height="1080" alt="Screenshot (206)" src="https://github.com/user-attachments/assets/c325202a-a9a2-4e75-9317-327992912b37" />

## PROGRAM - RARP:
### Server Program:
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
### Client Program:
```
import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
    ip=input("Enter MAC Address : ")
    s.send(ip.encode())
    print("Logical Address",s.recv(1024).decode())
```

## OUPUT -RARP:
### Server Output:

<img width="1920" height="1080" alt="Screenshot (207)" src="https://github.com/user-attachments/assets/14e60ecc-a99d-4bcb-84df-150b1452e331" />

### Client Output:

<img width="1920" height="1080" alt="Screenshot (208)" src="https://github.com/user-attachments/assets/6530d273-0e53-4357-a3f4-84df604cfa69" />

## RESULT:
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
