## How To: Install Jitsi Server on Ubuntu

Jitsi is a video conferencing application that is fully open source, and allows you to easily build and deploy your own video conferencing server. This guide will show you how to set up a secure Vultr hosted virtual server that runs Jitsi – you can be video conferencing in less than an hour!



### Step 1: Log into your new server.
At this point, you should have your Vultr username (root) and password from the server details.  Copy the password to your clipboard and then open up PuTTY.

Enter in the IP address or hostname of your server and then click ‘Open.’
![](https://crosstalksolutions.com/wp-content/uploads/2020/04/image-5.png)

PuTTY will open up a terminal window and first ask you if you want to accept the new host (click ‘YES’).  Then you will be given a login prompt.  Use the information from the Vultr server properties:
User:  root

To change your root password type 
```markdown
sudo passwd root
```
### Step 2: Setring up ports.
Let’s open up access to the ports that Jitsi needs.  We’re going to allow connections to this server on HTTP, HTTPS, and UDP 10,000-20,000.
```markdown
sudo ufw allow http
sudo ufw allow https
sudo ufw allow in 10000:20000/udp
```
Let’s take a look at our rules:
```markdown
sudo ufw status
```
You should see something similar to this:
![](https://crosstalksolutions.com/wp-content/uploads/2020/04/image-6.png)

### Step 3: Upadet your server.
```markdown
sudo apt update
sudo apt upgrade -y
sudo apt dist-upgrade -y
```
### Step 3: Seeting up your domian.

The first thing you’ll need to do to add an A Record is to make sure that you are using Name.com's default nameservers (which point computers looking for your DNS records to where they need to go.). Once you are on our nameservers, follow the steps below:
```markdown
1.Log into your Name.com account.
2.Click on the My Domains button, located on the top right-hand corner.
3.Click on the domain name you wish to create an A record for.
4.Click Manage DNS Records.
5.Here, you will add the desired A record, typically supplied by your website provider or host. If you were provided an IP address then you would typically create two A records:
```
First A record Leave the drop-down menu Type as A, leave the Host field blank, and then copy and paste the IP address into the answer field. Then click the blue Add Record button. 

![](https://cs.name.com/hc/article_attachments/360000490668/2018-02-12_1102.png)


### Step 4: Install Jitsi.

Finally it’s time to install Jitsi! First, we will add the Jitsi package repository and GPG key with these two commands:
```markdown
sudo wget -qO - https://download.jitsi.org/jitsi-key.gpg.key | sudo apt-key add -
```
```markdown
sudo sh -c "echo 'deb https://download.jitsi.org stable/' > /etc/apt/sources.list.d/jitsi-stable.list"
```
Next update your package list:
```markdown
sudo apt update
```
And finally install the full Jitsi package (I say full Jitsi package because it is possible to install various Jitsi components separately – however, that is beyond the scope of this guide):
```markdown
sudo apt install jitsi-meet -y
```
During installation, you will be asked for the hostname of the server – enter in your hostname (ie. yourdomainname.com).

You will also be asked if you want to generate a new self-signed certificate, or if you want to use your own certificate. Choose option 1 since we will be installing Let’s Encrypt in the next step.

Installation should only take about 1 minute or so. Once complete, run this command to install Let’s Encrypt:
```markdown
sudo /usr/share/jitsi-meet/scripts/install-letsencrypt-cert.sh
```
You will be prompted for your email address – enter it and press ENTER.

You have now successfully installed Jitsi! Let’s test it out. Open your browser and navigate to https://yourdomainname.com – you should see a screen like this:
![](https://crosstalksolutions.com/wp-content/uploads/2020/04/image-7-1024x517.png)

