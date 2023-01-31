# PROJECT-5
CLIENT SERVER ARCHITECTURE


##IMPLEMENT A CLIENT SERVER ARCHITECTURE USING MYSQL DATABASE MANAGEMENT SYSTEM (DBMS).

- To demonstrate a basic client-server using MySQL Relational Database Management System (RDBMS), the following steps were taken.

- i created and configured two Linux-based virtual servers (EC2 instances in AWS).

```
Server A name - `mysql server`
Server B name - `mysql client`
```

- With this project, two windows terminals were opened simultaneously. One for the server and one for the client.

- On mysql server Linux Server install MySQL Server software.

- I updated the server using `sudo apt update -y` and the installed the MySQL software using `sudo apt installed mysql-server -y`.

- I enabled the service after installation using `sudo systemctl enable mysql`

- I moved to the Client terminal.

- Using `sudo apt update -y`, I updated the server.

- I then installed MySQL Client software using `sudo apt install mysql-client -y`.

- Back
