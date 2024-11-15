#Setting Up a Web Server with Apache on AWS EC2


#Steps
#1. Launch an EC2 Instance
Log in to the AWS Management Console.
Navigate to EC2 and click Launch Instances.
Configure the instance as follows:
Name: Give any name
AMI (Operating System): Ubuntu 22.04 (or Amazon Linux/Red Hat).
Instance Type: t2.micro (to stay within the free tier).
Key Pair: Create or use an existing key pair.
Security Group Rules:
SSH (Port 22): To connect to the instance.
HTTP (Port 80): For website access.
HTTPS (Port 443): For secure website access.
Launch the instance and wait until its status changes to "Running".

#2. Connect to the EC2 Instance
Navigate to the EC2 dashboard, select your instance, and copy the Public IP Address.

Use one of the following methods to connect:

Instance Connect: Open a browser-based SSH session from the AWS console.

SSH Client: Run the following command in your terminal (replace <key.pem> and <ip-address> with your key file and instance IP):
ssh -i <key.pem> ubuntu@<ip-address>

#3. Install Apache Web Server
Update and upgrade the instance:

sudo apt update
sudo apt upgrade -y
Install Apache:

sudo apt install apache2 -y
Verify Apache installation:

apache2 -v
Start Apache and check its status:

sudo service apache2 start
sudo service apache2 status
Test by accessing the public IP address in your browser. You should see the Apache default test page.

#4. Deploy Your Website
Navigate to the Apache document root:

cd /var/www/html
Replace the default index.html with your content:

Remove the default file:
sudo rm index.html

Create a new index.html:
sudo nano index.html

Add your custom HTML:
Save and exit (Ctrl+O, Enter, Ctrl+X).

Restart Apache:
sudo service apache2 restart
Refresh your browser. Your custom website should now be visible.

#Resources
AWS EC2 Documentation
Apache HTTP Server Documentation
