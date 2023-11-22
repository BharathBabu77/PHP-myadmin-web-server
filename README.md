Project Title: Setting Up LAMP Stack with phpMyAdmin on AWS EC2

Services Used:

Amazon EC2
Ubuntu or Amazon Linux AMI
Apache HTTP Server
MySQL
PHP
phpMyAdmin

Steps of execution 

Launch an EC2 Instance:

Log in to your AWS Management Console.
Go to the EC2 dashboard and click "Launch Instance."
Choose an Amazon Machine Image (AMI), such as Ubuntu or Amazon Linux.
Select an instance type, configure instance details, and add storage as needed.
Configure security groups to allow HTTP (port 80) and SSH (port 22) access.
Launch the instance, selecting or creating a key pair for SSH access.
Connect to Your EC2 Instance:

Use SSH to connect to your EC2 instance using the key pair:
 
ssh -i KeyPair.pem ec2-user@EC2PublicIP
 
Update and Install LAMP Stack:

Update the server's package list and upgrade installed packages:

For Amazon Linux:
 
sudo yum update -y
 
For Ubuntu:
 
sudo apt update && sudo apt upgrade -y
 
Install the LAMP stack components (Linux, Apache, MySQL, PHP) on your EC2 instance:

For Amazon Linux:
 
sudo yum install httpd mysql-server php php-mysql -y
 
For Ubuntu:
 
sudo apt install apache2 mysql-server php php-mysql -y
 
Secure MySQL:

Run the MySQL security script to set a root password and secure your MySQL installation:
 
sudo mysql_secure_installation
 
Download and Install phpMyAdmin:

Download phpMyAdmin to your EC2 instance:

For Amazon Linux:
 
sudo yum install phpmyadmin -y
 
For Ubuntu:
 
sudo apt install phpmyadmin -y
 
During installation, choose Apache2 as the web server to configure phpMyAdmin to work with Apache.
Configure Apache for phpMyAdmin:

Create a symbolic link to the phpMyAdmin configuration file in the Apache configuration directory:

 
sudo ln -s /etc/phpmyadmin/apache.conf /etc/apache2/conf-available/phpmyadmin.conf
 
Enable the phpMyAdmin configuration:

 
sudo a2enconf phpmyadmin
 
Restart Apache to apply the changes:

For Ubuntu:
 
sudo systemctl restart apache2
 
For Amazon Linux:
 
sudo service httpd restart
 
Access phpMyAdmin:

Open a web browser and navigate to your EC2 instance's public IP or domain name followed by /phpmyadmin:
 
http://EC2PublicIP/phpmyadmin
 
Log in to phpMyAdmin:

Log in to phpMyAdmin using the MySQL root credentials.
