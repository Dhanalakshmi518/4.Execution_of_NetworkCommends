# 4.Execution_of_NetworkCommands
## AIM :Use of Network commands in Real Time environment
## Software : Command Prompt And Network Protocol Analyzer
## Procedure: To do this EXPERIMENT- follows these steps:
<BR>
In this EXPERIMENT- students have to understand basic networking commands e.g cpdump, netstat, ifconfig, nslookup ,traceroute and also Capture ping and traceroute PDUs using a network protocol analyzer 
<BR>
All commands related to Network configuration which includes how to switch to privilege mode
<BR>
and normal mode and how to configure router interface and how to save this configuration to
<BR>
flash memory or permanent memory.
<BR>
This commands includes
<BR>
• Configuring the Router commands
<BR>
• General Commands to configure network
<BR>
• Privileged Mode commands of a router 
<BR>
• Router Processes & Statistics
<BR>
• IP Commands
<BR>
• Other IP Commands e.g. show ip route etc.
<BR>
## PROGRAM:
SERVER.PY:

```
import socket
import subprocess

s = socket.socket()

s.bind(('localhost', 8000))
s.listen(5)

print("Ping Server started...")
print("Waiting for connection...")

c, addr = s.accept()

print("Connected to:", addr)

while True:
    hostname = c.recv(1024).decode()

    if not hostname:
        break

    if hostname.lower() == "exit":
        break

    result = subprocess.run(
        ["ping", hostname],
        capture_output=True,
        text=True
    )

    c.send(result.stdout.encode())

c.close()
s.close()
```
CLIENT.PY:

```
import socket

s = socket.socket()

s.connect(('localhost', 8000))

while True:
    website = input("Enter the website you want to ping: ")

    if website.lower() == "exit":
        break

    s.send(website.encode())

    result = s.recv(4096).decode()

    print("\nPing Result:\n")
    print(result)

s.close()

```

## Output
1) ping :
<img width="716" height="371" alt="Screenshot 2026-08-17 145546" src="https://github.com/user-attachments/assets/3ae1cfd5-30da-4221-bfe4-b8189add7913" />
2) tracert :
<img width="814" height="530" alt="Screenshot 2026-08-17 184700" src="https://github.com/user-attachments/assets/7f4fd373-e54e-4498-83f1-6864a0cf45eb" />
3) ipconfig :
<img width="900" height="911" alt="Screenshot 2026-08-17 183410" src="https://github.com/user-attachments/assets/4dc5e118-7500-4862-9018-12e34d7da8d2" />
4) netstat: 
<img width="796" height="893" alt="Screenshot 2026-08-17 183530" src="https://github.com/user-attachments/assets/387f4449-6ffd-45b0-85b1-cfa2cc9d3439" />
5) nslookup :
<img width="605" height="573" alt="Screenshot 2026-08-17 183636" src="https://github.com/user-attachments/assets/e0319140-966e-47ea-82d9-b7d3d2afc5fb" />
6) getmac :
<img width="712" height="182" alt="Screenshot 2026-08-17 183705" src="https://github.com/user-attachments/assets/480d4974-95fc-4552-b9a9-15dd7c23044f" />
7) nbtstat :
  <img width="886" height="565" alt="Screenshot 2026-08-17 183728" src="https://github.com/user-attachments/assets/f6685844-ae07-444f-8c4c-cdad38db4201" />
8) arp
 <img width="876" height="740" alt="Screenshot 2026-08-17 183752" src="https://github.com/user-attachments/assets/5a6649ba-e848-4f23-a518-e188e25b5590" />
9) systeminfo :
<img width="813" height="827" alt="Screenshot 2026-08-17 183908" src="https://github.com/user-attachments/assets/cef79d5e-ee60-4c18-b977-65ec0af35795" />


## Result
Thus Execution of Network commands Performed 
