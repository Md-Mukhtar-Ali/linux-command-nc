# linux-command-nc
1️⃣ Basic Purpose of nc
nc is mainly used to:
Test TCP/UDP connectivity
Open raw network connections
Send or receive data over sockets
Debug network services
Create simple client/server communication
Port scanning

**1.Check if a Port is Open**
nc -zv 192.168.1.10 5060
Explanation:
-z → scan mode (no data sent)
-v → verbose output

**sngrep port 5060**


Create a Simple TCP Server

You can make a listening server.

nc -l 9000

Now it waits for connections on port 9000.

4️⃣ Connect to a Server (Client)

From another terminal or machine:

nc 192.168.1.10 9000

Now whatever you type will appear on the server side.

Example:

Server sees:

Hello
How are you?
5️⃣ Send a File

Send file from one machine to another.

Receiver:

nc -l 9000 > file.txt

Sender:

nc 192.168.1.10 9000 < file.txt
6️⃣ Test HTTP Server

You can manually send HTTP request.

nc google.com 80
