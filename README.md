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

<img width="937" height="278" alt="Screenshot 2025-08-14 081659" src="https://github.com/user-attachments/assets/f642ae4a-13c9-4f20-9f29-bcc2e09bb700" />


### SERVER OUTPUT:
<img width="756" height="220" alt="Screenshot 2025-08-14 081708" src="https://github.com/user-attachments/assets/f1eec2c3-3eb0-425f-bf69-9dd38bbf633f" />


## RESULT:
The program is executed succesfully
