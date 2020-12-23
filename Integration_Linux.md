# Integration Linux

There are 3 steps to follow after selecting Infrastructure / Linux in
your admin interface:

![](attachments/375259143/374669341.png?height=250)

  
Download the telegraf package for linux distribution (1) from our admin
page as well as the telegraf.conf (2), follow the installation
instruction for telegraf of your linux distribition and make sure to
overwrite the telegraf.conf (/etc/telegraf/telegraf.conf) before
restarting the service (*service telegraf restart*). 

**Debian/Ubuntu**

*sudo dpkg -i telegraf.deb*

**RedHat/CentOS**

*sudo yum localinstall telegraf.rpm*

**Linux x64 - in case you want to use your own package installation**

*tar xf telegraf.tar.gz*  
`  `Then click load/reset Linux Dashboards (3) that automatically
imports the Linux: Host Overview Dashboard:  
![](attachments/375259143/375357453.png?height=250)

  
That's it

