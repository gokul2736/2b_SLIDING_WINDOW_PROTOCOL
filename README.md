# 2B IMPLEMENTATION OF SLIDING WINDOW PROTOCOL

## Developed By: Markandeyan Gokul
## Reg No: 212224240086
## AIM
To implement a program to illustrate the mechanism of sliding window protocol

## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM

## Client
```python
import socket
s = socket.socket()
s.bind(('localhost',8002))
s.listen(5)
c, addr = s.accept()
ListSize = int(input("Enter the number of frames to send : "))
List = list(range(ListSize))
WindowSize = int(input("Enter Window Size : "))
st, i = 0, 0
while True:
    while(i < ListSize):
        st += WindowSize
        c.send(str(List[i:st]).encode())
        Acknowledgment = c.recv(1024).decode()
        if Acknowledgment:
            print(Acknowledgment)
            i+=st

```

## Server
```python
import socket
s = socket.socket()
s.connect(('localhost', 8002))
while True:
    print(s.recv(1024).decode())
    s.send("Acknowledgement received from the server".encode())
```

## OUPUT
<img width="1855" height="367" alt="image" src="https://github.com/user-attachments/assets/49ac92f0-76d8-43b3-a5d9-28a29b73cd06" />


## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
