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

printf "REGISTER sip:192.168.1.10 SIP/2.0\r\n\
Via: SIP/2.0/UDP 192.168.1.20:5062;branch=z9hG4bK123456\r\n\
Max-Forwards: 70\r\n\
From: <sip:1001@192.168.1.10>;tag=1234\r\n\
To: <sip:1001@192.168.1.10>\r\n\
Call-ID: 123456@192.168.1.20\r\n\
CSeq: 1 REGISTER\r\n\
Contact: <sip:1001@192.168.1.20:5062>\r\n\
Expires: 3600\r\n\
Content-Length: 0\r\n\r\n" | nc -u 192.168.1.10 5060



printf "INVITE sip:1002@192.168.1.10 SIP/2.0\r\n\
Via: SIP/2.0/UDP 192.168.1.20:5062;branch=z9hG4bK98765\r\n\
Max-Forwards: 70\r\n\
From: <sip:1001@192.168.1.10>;tag=1111\r\n\
To: <sip:1002@192.168.1.10>\r\n\
Call-ID: 987654@192.168.1.20\r\n\
CSeq: 1 INVITE\r\n\
Contact: <sip:1001@192.168.1.20:5062>\r\n\
Content-Type: application/sdp\r\n\
Content-Length: 129\r\n\r\n\
v=0\r\n\
o=user1 53655765 2353687637 IN IP4 192.168.1.20\r\n\
s=-\r\n\
c=IN IP4 192.168.1.20\r\n\
t=0 0\r\n\
m=audio 4000 RTP/AVP 0\r\n\
a=rtpmap:0 PCMU/8000\r\n" | nc -u 192.168.1.10 5060
