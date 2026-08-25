# 3c.CREATION FOR FILE TRANSFER USING TCP SOCKETS
## AIM
To write a python program for creating File Transfer using TCP Sockets Links
## ALGORITHM:
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.
## PROGRAM

## server.py

```py
import socket

# Create socket
server = socket.socket()

# Bind IP and port
server.bind(("127.0.0.1", 5555))

# Listen for client
server.listen(1)

print("Server waiting for connection...")

# Accept client
client, addr = server.accept()

print("Connected to:", addr)

# Ask filename
filename = input("Enter file name to send: ")

# Open and send file
with open(filename, "rb") as file:
    data = file.read()

client.send(data)

print("File sent successfully")

# Close connections
client.close()
server.close()

print("Connection closed.") 
```

## client.py

```py
import socket

# Create socket
client = socket.socket()

# Connect to server
client.connect(("127.0.0.1", 5555))

# Save file name
save_name = input("Enter name to save file: ")

# Receive data
data = client.recv(1000000)

# Save file
with open(save_name, "wb") as file:
    file.write(data)    

print("File received successfully")

# Close connection
client.close()

print("Connection closed.")
```
## OUPUT

server.py

<img width="1480" height="193" alt="image" src="https://github.com/user-attachments/assets/c3754d10-3047-41cc-9488-5dbcb0cecbfe" />

client.py

<img width="1066" height="172" alt="image" src="https://github.com/user-attachments/assets/1dc77ec8-0096-4019-9b6c-e491023846af" />

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
