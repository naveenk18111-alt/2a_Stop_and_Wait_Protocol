# 2a_Stop_and_Wait_Protocol

## AIM 
To write a python program to perform stop and wait protocol

## ALGORITHM
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program

## PROGRAM:
### client.py
```py
import socket

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(1)

print("Waiting for connection...")
conn, addr = s.accept()
print("Connected to", addr)

while True:
    data = conn.recv(1024).decode()
    if not data:
        break

    print("Frame received:", data)
    conn.send("ACK".encode())

conn.close()
```
### server.py
```py
import socket

s = socket.socket()
s.connect(('localhost', 8000))

n = int(input("Enter number of frames: "))

for i in range(n):
    msg = input("Enter frame: ")
    s.send(msg.encode())

    ack = s.recv(1024).decode()
    print("Received:", ack)

s.close()
```
## OUTPUT:
### Client
<img width="480" height="165" alt="image" src="https://github.com/user-attachments/assets/41263920-d5cf-4793-83c3-96b2cb8e78bc" />

### Server
<img width="460" height="208" alt="image" src="https://github.com/user-attachments/assets/183429d0-439c-4209-99d8-20e842d15921" />

## RESULT:
Thus, python program to perform stop and wait protocol was successfully executed.
