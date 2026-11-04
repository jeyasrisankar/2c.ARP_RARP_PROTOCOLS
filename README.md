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

<img width="1280" height="131" alt="Screenshot 2026-11-04 104616" src="https://github.com/user-attachments/assets/085950eb-d919-4e09-9e1d-8ada7ef444a5" />

<img width="1272" height="200" alt="Screenshot 2026-11-04 104558" src="https://github.com/user-attachments/assets/cc34f41c-0cf4-4917-a214-8ccdf6fe30ea" />





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

<img width="1530" height="950" alt="image" src="https://github.com/user-attachments/assets/de673b33-646f-4a13-8db6-c4d0186acc73" />

<img width="1535" height="940" alt="Screenshot 2026-11-04 105714" src="https://github.com/user-attachments/assets/7fbd7624-91fb-4b26-87d1-ac0c7c04c867" />


## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
