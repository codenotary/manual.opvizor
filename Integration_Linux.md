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

<div class="pageSectionHeader">

## Attachments:

</div>

<div class="greybox" data-align="left">

![](images/icons/bullet_blue.gif)
[netapp-dashboards.png](attachments/375259143/375259146.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[netapp-add.png](attachments/375259143/375259149.png) (image/png)  
![](images/icons/bullet_blue.gif)
[veeam\_patch.png](attachments/375259143/375259152.png) (image/png)  
![](images/icons/bullet_blue.gif)
[veeam\_admin.png](attachments/375259143/375259155.png) (image/png)  
![](images/icons/bullet_blue.gif)
[veeam\_dashboard.png](attachments/375259143/375259158.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[veeam\_admin2.png](attachments/375259143/375259161.png) (image/png)  
![](images/icons/bullet_blue.gif)
[image2017-12-18\_16-29-19.png](attachments/375259143/374669341.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[image2017-12-18\_16-44-5.png](attachments/375259143/375357453.png)
(image/png)  

</div>
