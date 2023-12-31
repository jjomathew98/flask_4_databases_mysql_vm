# flask_4_databases_mysql_vm

## VM and MySQL Setup Process
1. Login into Azure Portal and go to Virtual Machines. Click on create a new Azure virtual machine.
2. Select existing resource group or create a new one. Change the default configuraton options as needed. Make sure to create a password for the VM. And select the inbound ports HTTP(80) and HTTPS(443). Click on Review + create and then Create.
3. Once the VM is created, click on the VM and go to Networking. Click on Add inbound port rule and add MySQL port 3306 and Flask port 5000. Click on Add.
4. Open up the Cloud Shell environement and SSH into the VM using the command ssh <username>@<public-ip-address>. Enter the password when prompted.
5. Update the UBUNTU (OS) SERVER by entering sudo apt-get update. Install MySQL by entering sudo apt-get install mysql-server. Enter Y when prompted.
6. Enter sudo mysql to log into MySQL. Enter the following commands to create a new user and grant privileges to the user: CREATE USER ‘user'@'%' IDENTIFIED BY ‘password’; and GRANT ALL PRIVILEGES ON *.* TO ‘user'@'%’ WITH GRANT OPTION;. Enter exit to exit MySQL.
7. Enter sudo nano /etc/mysql/mysql.conf.d/mysqld.cnf to edit the MySQL configuration file. Change the bind-address to 0.0.0.0. Save the file and exit.
8. Enter sudo service mysql restart to restart MySQL.
9. Open up MySQL Workbench and create a new connection. Enter the VM's public IP address, username, and password. Click on Test Connection and then OK. The IP address can be found on the VM's overview page in Azure Portal. And the username and password are the ones created in step 6.

## MySQL Setup Process
1. In google shell ssh joel4vm@20.127.217.77
2. Continue connecting- yes
    ssh sh joel4vm@20.127.217.77
    password
3. Google shell shows that the local computer is connected to virtual machine CheviMySQLhw4b
4. sudo apt install mysql-client mysql-server
5. sudo mysql
5. in mysql create user 'joel4vm'@'%' identified by 'jm4vm1998';
6. grant all privileges on . to 'joel4vm'@'%' with grant option;
7. Go back to azure and add import inbound security rule, choose MySQL service for port 3306, Add.
8. Go back to shell to change bind address to 0.0.0.0.
9. Save changes in nano with Control O
10. Connect to MySQL workbench

## MySQL Workbench Database

### In MySQL workbench, create a database:

          CREATE DATABASE lung;
          USE lung;
          
          CREATE TABLE patients (
              patient_id INT PRIMARY KEY AUTO_INCREMENT,
              first_name VARCHAR(50) NOT NULL,
              last_name VARCHAR(50) NOT NULL,
              date_of_birth DATE
          );
          
          CREATE TABLE medications (
              medication_id INT PRIMARY KEY AUTO_INCREMENT,
              medication_name VARCHAR(100) NOT NULL
          );

### Create fake data:
INSERT INTO patients (first_name, last_name, date_of_birth) VALUES 
('Sam', 'Mathew', '1921-10-15'),
('John', 'Hann', '1911-10-17'),
('aaron', 'jojo', '1931-10-20');

INSERT INTO medications (medication_name) VALUES
('ibuprofen'), 
('tylenol'), 
('Flonase');
