# 3b.CREATION FOR CHAT USING TCP SOCKETS
## AIM
To write a python program for creating Chat using TCP Sockets Links.
## ALGORITHM:
1. Import the necessary modules in python
2. Create a socket connection to using the socket module.
3. Send message to the client and receive the message from the client using the Socket module in
 server
4. Send and receive the message using the send function in socket.
## PROGRAM
server
```
import socket

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

s.bind(('localhost', 8000))

s.listen(5)

print("Server is waiting for connection...")

c, addr = s.accept()

print("Connected to:", addr)

while True:
    ClientMessage = c.recv(1024).decode()

    if not ClientMessage:
        break

    print("Client >", ClientMessage)

    if ClientMessage.lower() == 'exit':
        break

    msg = input("Server > ")

    c.send(msg.encode())

    if msg.lower() == 'exit':
        break

c.close()
s.close()
```
client
```
import socket

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

s.connect(('localhost', 8000))

while True:
    msg = input("Client > ")

    s.send(msg.encode())

    if msg.lower() == 'exit':
        break

    reply = s.recv(1024).decode()
    print("Server >", reply)

    if reply.lower() == 'exit':
        break

s.close()
```

## OUPUT
<img width="822" height="319" alt="image" src="https://github.com/user-attachments/assets/da6e8108-97f7-4f76-874d-396d59c3ef76" />

## RESULT
Thus, the python program for creating Chat using TCP Sockets Links was successfully 
created and executed.
