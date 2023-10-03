**Step 1: Launch an EC2 Instance**

Log in to your AWS Management Console.
Go to the EC2 dashboard and click "Launch Instance."
Choose an Amazon Machine Image (AMI), typically a Linux distribution.
Select an instance type, configure instance details, and add storage as needed.
Configure security groups to allow HTTP (port 80) and SSH (port 22) access.
Launch the instance, selecting or creating a key pair for SSH access.

**Step 2: Connect to Your EC2 Instance**

Use SSH to connect to your EC2 instance using the key pair:

ssh -i YourKeyPair.pem ec2-user@YourEC2PublicIP

**Step 3: Update and Install LAMP Stack**

Update the server's package list and upgrade installed packages:
arduino

sudo yum update -y  # for Amazon Linux
sudo apt update && sudo apt upgrade -y  # for Ubuntu
Install the LAMP stack components (Linux, Apache, MySQL, PHP) on your EC2 instance:

sudo yum install httpd mysql-server php php-mysql -y  # for Amazon Linux
sudo apt install apache2 mysql-server php php-mysql -y  # for Ubuntu

**Step 4: Secure MySQL**

Run the MySQL security script to set a root password and secure your MySQL installation:

sudo mysql_secure_installation

**Step 5: Download and Install phpMyAdmin**

Download phpMyAdmin to your EC2 instance:

sudo yum install phpmyadmin -y  # for Amazon Linux
sudo apt install phpmyadmin -y  # for Ubuntu

During installation, choose Apache2 as the web server to configure phpMyAdmin to work with Apache.

**Step 6: Configure Apache for phpMyAdmin**

Create a symbolic link to the phpMyAdmin configuration file in the Apache configuration directory:

sudo ln -s /etc/phpmyadmin/apache.conf /etc/apache2/conf-available/phpmyadmin.conf

Enable the phpMyAdmin configuration:

sudo a2enconf phpmyadmin

Restart Apache to apply the changes:

sudo systemctl restart apache2  # for Ubuntu
sudo service httpd restart  # for Amazon Linux

**Step 7: Access phpMyAdmin**

Open a web browser and navigate to your EC2 instance's public IP or domain name followed by /phpmyadmin:

http://EC2PublicIP/phpmyadmin

**Step 8: Log in to phpMyAdmin**

Log in to phpMyAdmin using the MySQL root credentials
