# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
```
DEVELOPED BY: ASWINI D     REG NO: 212225240015
client side:

import socket 
s = socket.socket() 
s.connect(('localhost',9000))
while True: 
    data = s.recv(1024).decode()
    if not data:
        break
    print(data) 
    s.send("acknowledgement received from the client".encode())

server side:

import socket 
s = socket.socket() 
s.bind(('localhost',9000)) 
s.listen(5) 
c,addr = s.accept() 
size = int(input("Enter number of frames to send : "))
l = list(range(size)) 
w = int(input("Enter Window Size : "))   
st = 0 
i = 0 
while True: 
    if(i < len(l)):   
        st = i + w    
        c.send(str(l[i:st]).encode()) 
        ack = c.recv(1024).decode() 
        if ack: 
            print(ack) 
            i += w 
    else:
        break
```
## OUPUT
<img width="746" height="257" alt="image" src="https://github.com/user-attachments/assets/e385ca28-32d8-43bd-8d66-fcdd8f8cea04" />
<img width="789" height="352" alt="image" src="https://github.com/user-attachments/assets/a6ededd0-0ea9-468c-92ee-2ed7927bad1b" />

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
