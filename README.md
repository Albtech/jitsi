## How To: Install Jitsi Server on Ubuntu

Jitsi is a video conferencing application that is fully open source, and allows you to easily build and deploy your own video conferencing server. This guide will show you how to set up a secure Vultr hosted virtual server that runs Jitsi – you can be video conferencing in less than an hour!



### Step 1: Log into your new server.
At this point, you should have your Vultr username (root) and password from the server details.  Copy the password to your clipboard and then open up PuTTY.

Enter in the IP address or hostname of your server and then click ‘Open.’
![](https://crosstalksolutions.com/wp-content/uploads/2020/04/image-5.png)

PuTTY will open up a terminal window and first ask you if you want to accept the new host (click ‘YES’).  Then you will be given a login prompt.  Use the information from the Vultr server properties:
User:  root
Password:  (the password from the Vultr server properties – you can do SHIFT+INS or right-click to paste it in)
The very first thing that you should do is change your root password.
```markdown
sudo passwd root
```

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/Albtech/asad/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
