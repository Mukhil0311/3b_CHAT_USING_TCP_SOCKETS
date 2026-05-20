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

SERVER SIDE:

```py
import socket

host = "localhost"
port = 8000

# Create TCP socket
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# Bind socket
s.bind((host, port))

# Start listening
s.listen(5)

print("Server Started...")
print("Waiting for client connection...")

conn, addr = s.accept()

print("Client Connected :", addr)

while True:
    message = conn.recv(1024).decode()

    if not message:
        break

    print("Client >", message)

    response = input("Server > ")

    conn.sendall(response.encode())

    if response.lower() == "bye":
        break

conn.close()
s.close()

print("Server Stopped")
```

CLIENT SIDE

```py
import socket

client = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

host = "localhost"
port = 8000

client.connect((host, port))

print("Connected to Server")

while True:
    text = input("Client : ")

    if text == "exit":
        break

    client.sendall(text.encode())

    reply = client.recv(1024).decode()
    print("Server :", reply)

client.close()
print("Connection Closed")
```
## OUPUT

![image](https://github.com/Mukhil0311/3b_CHAT_USING_TCP_SOCKETS/blob/main/Screenshot%202026-05-20%20104008.png)


## RESULT
Thus, the python program for creating Chat using TCP Sockets Links was successfully 
created and executed.
