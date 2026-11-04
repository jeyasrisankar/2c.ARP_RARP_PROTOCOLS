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
Server program 
```
import socket
s = socket.socket()
s.bind(('localhost', 8000))
s.listen(5)
c, addr = s.accept()
address = {
    "165.165.80.80": "6A:08:AA:C2",
    "165.165.79.1": "8A:BC:E3:FA"
}
while True:
    ip = c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())
```
Client program
```
import socket
s = socket.socket()
s.connect(('localhost', 8000))
while True:
    ip = input("Enter logical Address: ")
    s.send(ip.encode())
    print("MAC Address", s.recv(1024).decode())
```


## OUPUT - ARP
<img width="1272" height="200" alt="Screenshot 2026-11-04 104558" src="https://github.com/user-attachments/assets/766bca82-7b4c-486c-8d20-4fc355c2dab7" />

<img width="1280" height="131" alt="Screenshot 2026-11-04 104616" src="https://github.com/user-attachments/assets/09c50c59-3f3e-4f20-8c71-3a579fc11b80" />



## PROGRAM - RARP

Server program 
```
import socket
s = socket.socket()
s.bind(('localhost', 9000))
s.listen(5)
c, addr = s.accept()
address = {
    "6A:08:AA:C2": "192.168.1.100",
    "8A:BC:E3:FA": "192.168.1.99"
}
while True:
    ip = c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())
```
Client program
```
import socket
s = socket.socket()
s.connect(('localhost', 9000))
while True:
    ip = input("Enter MAC Address: ")
    s.send(ip.encode())
    print("Logical Address", s.recv(1024).decode())
```


## OUPUT -RARP
<img width="1530" height="950" alt="image" src="https://github.com/user-attachments/assets/3f6f4e73-e168-4286-b668-d6d7a8ca2c9b" />


<img width="1527" height="907" alt="image" src="https://github.com/user-attachments/assets/cc36fecb-dab4-4459-8203-c39ab0112d49" />

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
