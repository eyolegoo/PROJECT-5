# PROJECT-5
CLIENT SERVER ARCHITECTURE


## IMPLEMENT A CLIENT SERVER ARCHITECTURE USING MYSQL DATABASE MANAGEMENT SYSTEM (DBMS).

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

- By default, both ***EC2 virtual servers*** are located in the same ***local virtual network***, so they can communicate to each other using local IP addresses. I used mysql server's local IP address to connect from mysql client. MySQL server uses TCP port 3306 by default, so I opened it by creating a new entry in ‘Inbound rules’ in ‘mysql server’ Security Groups. For extra security, I didn't allow all IP addresses to reach my ‘mysql server’ – allow access only to the specific local IP address of my ‘mysql client’.

- <img width="815" alt="Inbound rules" src="https://user-images.githubusercontent.com/115954100/215882239-e8ffb22d-0e1a-457f-b43e-1104e8277561.png">

- In the MySQL Server, I created the user's **username, password and a database**.

- I logged in to MySQL console using `sudo mysql`. This connected to the MySQL server as the administrative database user root, which is inferred by the use of sudo when running this command.

- I ran a security script that comes pre-installed with MySQL. This script removed some insecure default settings and lock down access to my database system. Before running the script I set a password for the **root user**, using mysql_native_password as default authentication method. We’re defining this user’s password as **PassWord.1**.

- Using `ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'PassWord.1';`

- Then I exited the console using `exit`.

- I installed the security using the security script `sudo mysql_secure_installation`. I didn't validate password component since this is not for deployment purpose but just a simple setup.

- I went back to MySQL console using `sudo mysql`

- This time, I created the user with **root_Godwin** as the username.

- `CREATE USER 'root_Godwin'@'%' IDENTIFIED WITH mysql_native_password BY 'PassWord.1';`. Note, the ***%*** sign allows the user to connect using any IP address.

- Next is the database call it **testwork**

- `CREATE DATABASE testwork;`

- I granted privileges on **testwork** to the user **root_Godwin** using `GRANT ALL ON testwork.* TO 'root_Godwin'@'%' WITH GRANT OPTION;`

- I flushed using `FLUSH PRIVILEGES` and then exited with `exit`.

- I configured MySQL server to allow connections from remote hosts using `sudo vi /etc/mysql/mysql.conf.d/mysqld.cnf` and 

- Replace ‘127.0.0.1’ to ‘0.0.0.0’ like this:

- ![image](https://user-images.githubusercontent.com/115954100/215881697-e41f9f34-1171-4734-a243-fc3c14b27761.png)

- I restarted the MySQL Server using `sudo systemctl restart mysql`

- From mysql client Linux Server I connected remotely to mysql server Database Engine without using SSH. I used the mysql utility to perform this action.

- `sudo mysql -u root_Godwin -h private IP address -p` ***Note***, the private IP address is the server's Linux private IP address and the ***-p*** will prompt for password.

- with the command `Show databases;` I checked that I have successfully connected to a remote MySQL server and can perform SQL queries:

- <img width="620" alt="Final output" src="https://user-images.githubusercontent.com/115954100/215885093-d79d6713-f965-406d-83cf-3868c5c590ee.png">

- With this, the implementation was successful
