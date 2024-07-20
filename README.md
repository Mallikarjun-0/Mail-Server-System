# MAIL SERVER SYSTEM

### Overview

In this project, I designed and implemented a simple mail server and client using the SMTP and POP3 protocols. The SMTP protocol is used for sending emails between user and server or server and server, while the POP3 protocol is used for retrieving emails from a mail server.

### Objectives
1. **Implement an SMTP server program referring RFC 5321:** To send and receive emails using the SMTP protocol.
2. **Implement a POP3 server program referring RFC 1939:** To retrieve and manage emails using the POP3 protocol.
3. **Handle multiple users and concurrent connections:** The server should handle multiple users accessing their mailboxes simultaneously.
4. **Implement a client program:** The client program can connect to SMTP server and send mails, can connect to POP3 server to retrieve inbox mails

### Components

#### Mail Server Machine (MailServer)
1. **SMTP Server (smtpmail.c):** Receives and stores emails.
2. **POP3 Server (popserver.c):** Allows clients to access and manage their mailboxes.

#### Client Machine
1. **Mail Client (mailclient.c):** Implements both sending and receiving of emails.

### Setup Instructions

1. **Create User Directory and File:**
    - In the directory where the programs will run, create a file named `user.txt`. Each line should contain a username and password separated by spaces.
    - Create a subdirectory for each user specified in `user.txt`.

2. **SMTP Server (smtpmail.c):**
    - Takes a command-line argument `my_port` to specify the port number.
    - Listens on `my_port` for incoming connections.
    - Receives emails and stores them in the respective user's subdirectory in a file named `mymailbox`.

3. **POP3 Server (popserver.c):**
    - Takes a command-line argument `pop3_port` to specify the port number.
    - Handles client connections, allowing users to access and manage their mailboxes.

### Mail Client (mailclient.c)

1. **Command-line Arguments:**
    - `server_IP`: IP address of the MailServer machine.
    - `smtp_port`: Port number of the SMTP server.
    - `pop3_port`: Port number of the POP3 server.

2. **User Options:**
    - **Manage Mail:** View stored emails.
    - **Send Mail:** Compose and send an email.
    - **Quit:** Exit the program.

### Email Format

#### For Sending:
From: <username>@<domain_name>\
To: <username>@<domain_name>\
Subject: <subject string, max 50 characters>\
<Message body, terminated by a line with only a fullstop>



#### For Storing in the server:
From: <username>@<domain_name>\
To: <username>@<domain_name>\
Subject: <subject string, max 100 characters>\
Received: "<time in date : hour : minute>"
<Message body same as recieved to the server>



### Protocol Details

#### SMTP Commands:
- HELO
- MAIL
- RCPT
- DATA
- QUIT

#### SMTP Replies:
- 220 `<domain name>` Service Ready
- 221 `<domain name>` Service closing transmission channel
- 250 OK `<message>`
- 354 Start mail input; end with `<CRLF>.<CRLF>`
- 550 No such user

#### POP3 Commands:
- STAT
- LIST
- RETR
- DELE
- RSET
- QUIT

### References
- SMTP: [RFC 5321](https://tools.ietf.org/html/rfc5321)
- POP3: [RFC 1939](https://tools.ietf.org/html/rfc1939)
