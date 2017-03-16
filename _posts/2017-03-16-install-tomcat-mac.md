---
layout: post
title: Install Apache Tomcat on Mac OS X
categories: [tomcat]
tags: [tomcat, programming, apache]
fullview: false
comments: true
---

# Install Apache Tomcat on Mac OS X

The easiest way to install and configure an Apache Tomcat server on a mac is using the open-source homebrew package management suite. If you’re not already using homebrew, check out its popularity on GitHub. It makes open-source package management on mac 100 times cleaner than doing it manually (everything is stored in one place, packages are easy to remove, upgrade and find configs for).

There is a good tutorial here on installing homebrew if you do not already have it.

1)  –  Install Tomcat Server

Install tomcat with the brew install in terminal (as a normal user, not root):

$ brew install tomcat
This will take care of the downloading, installation and configuration of Tomcat and manage its dependencies as well. Take note of the output, brew commands are typically really good at displaying concise but useful info, error messages and help.

Homebrew keeps packages (known as kegs) in the Cellar, where you can check config and data files. It is a directory located at:

$ ls /usr/local/Cellar/
Verify the Tomcat installation using homebrew’s handy “services” utility:

$ brew services list
Tomcat should now be listed here. brew services are really useful for managing system services, type $ brew services --help for more info.

2)  –  Run Tomcat Server

We are going to start the server by executing Tomcat’s Catalina command with the “run” parameter as such:

$ ls /usr/local/Cellar/tomcat/

$ /usr/local/Cellar/tomcat/8.5.3/bin/catalina run
or more generally:

$ /usr/local/Cellar/tomcat/[version]/bin/catalina run
With [version] replaced with your installed version.

The version number and installation directory will have been listed by homebrew at the end of the installation output (typically the last line with a beer symbol in front). Catalina can also be set to start on system launch – although for security reasons we prefer to only run when needed (either using this command or more commonly via an IDE plugin).

Once the server is running you can navigate to the host page at:

http://localhost:8080/
 

3)  –  Configure Tomcat Server

To add and manage applications running on the server you will also need to edit a configuration file:

$ vim /usr/local/Cellar/tomcat/[version]/libexec/conf/tomcat-users.xml
With [version] again replaced with your installed version.

Towards the bottom of this short config file you will see a selection of users – all commented out by default. You need to uncomment one of these and give it the extra role “manager-gui” (preferably also changing the username and password for security). The resultant user entry should look something like this:

<user username="admin" password="password" roles="tomcat,manager-gui" />
After this you can navigate to the page (or click the “Manager App” link on the main Tomcat Server page):

http://localhost:8080/manager/html
Here you can view or delete the included sample application and deploy your own. Usually, it’s easiest to deploy applications in a dev / testing environment using an IDE like PHPStorm or NetBeans however, Tomcat’s web interface is useful also. For reference, deployed applications are usually then located under the directory:

/usr/local/Cellar/tomcat/[version]/libexec/webapps/
