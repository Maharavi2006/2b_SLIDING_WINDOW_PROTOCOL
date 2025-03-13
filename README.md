# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM
 write a python program to perform sliding window protocol
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
```
SERVER.PY

import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
size=int(input("Enter number of frames to send : "))
l=list(range(size))
s=int(input("Enter Window Size : "))
st=0
i=0
while True:
    while(i<len(l)):
        st+=s
        c.send(str(l[i:st]).encode())
        ack=c.recv(1024).decode()
        if ack:
            print(ack)
            i+=s
```
```
CLIENT.PY

import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    print(s.recv(1024).decode())
    s.send("acknowledgement recived from the server".encode())
```
## OUTPUT

![image](https://github.com/user-attachments/assets/e4d916e6-79fc-45e1-907c-8d2e42c9f740)

![image](https://github.com/user-attachments/assets/2af7f082-feb0-4de3-8da4-725d66e022e2)



## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
