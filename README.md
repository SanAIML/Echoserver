# Echoserver
Echo server and client using python socket
# AIM:

To develop a simple webserver to serve html programming pages.

## DESIGN STEPS:

### Step 1:

HTML content creation is done

### Step 2:

Design of webserver workflow

### Step 3:

Implementation using Python code

### Step 4:

Serving the HTML pages.

### Step 5:

Testing the webserver

## PROGRAM:
SERVER CODE
```
echo-server.py

import socket

HOST = "127.0.0.1"  
PORT = 65432       

with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as s:
    s.bind((HOST, PORT))      
    s.listen()                
    print(f"Server listening on {HOST}:{PORT} ...")
    conn, addr = s.accept()   
    with conn:
        print(f"Connected by {addr}")
        while True:
            data = conn.recv(1024)  
            if not data:        
                break
            conn.sendall(data)      
```
CLIENT CODE
```
echo-client.py

import socket

HOST = "127.0.0.1"  
PORT = 65432

with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as s:
    s.connect((HOST, PORT))         
    s.sendall(b"Hello, world")      
    data = s.recv(1024)            

print(f"Received {data!r}")

```


##  Architecture Diagram

```bash
+--------------------------+
|  User's Web Browser      |
|  (Client: Chrome/Firefox)|
+-----------+--------------+
            |
            |  HTTP Request (GET /)
            v
+-----------+--------------+
|   Python Web Server      |
| (http.server + Handler)  |
| - Listens on Port 8000   |
| - Handles GET Requests   |
| - Sends HTML Response    |
+-----------+--------------+
            |
            |  HTML Response
            v
+--------------------------+
|  User Sees Rendered Page |
|  <h1>Hello Web Server</h1>|
+--------------------------+
```


## OUTPUT:
### CLIENT OUTPUT:
<img width="802" height="182" alt="image" src="https://github.com/user-attachments/assets/7163cfb2-9281-47b4-98a0-d45f16c0a0fe" />

### SERVER OUTPUT:
<img width="802" height="187" alt="image" src="https://github.com/user-attachments/assets/ae40d726-5f82-42f4-8f4d-b7c86b7a15d2" />

## RESULT:
The program is executed succesfully
