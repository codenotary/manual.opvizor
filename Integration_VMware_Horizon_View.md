# Integration VMware Horizon View

To enable VMware Horizon View, please install the telegraf service on
each VMware View VM you want to monitor (*after the eval, it makes sense
to integrate it into the master image and change the collection interval
(when monitoring more than 200 VMs) to 60seconds instead of the 10second
default*) using the following archive:

<https://storage.googleapis.com/opvizor/latest/telegraf_view.zip>

  

Please make sure to unblock the downloaded file before extracting into
%programfiles%

![](attachments/810450945/810418204.png?height=250)

Change the following line within %programfiles%\\telegraf\\telegraf.conf
to match your Performance Analyzer appliance IP or FQDN:

\[\[outputs.influxdb\]\]

urls =
\["[https://**pa\_appliance\_ip**:8086](http://pa_appliance_ip:8086)"\]

  

**Open a administrative command line and run:**

*%programfiles%\\telegraf\\telegraf\_installservice.cmd*

*net start telegraf*

**Add a new datasource to Performance Analyzer**

![](attachments/810450945/959119361.png?height=400)

![](attachments/810450945/959053832.png?height=150)

![](attachments/810450945/959053837.png?height=250)

![](attachments/810450945/959119369.png)

Please select vmwareview as a datasource when importing:

[VMware Horizon Desktop VM](attachments/810450945/810614792.json)

[Highlights: VMware Horizon View](attachments/810450945/1289060353.json)

<div class="pageSectionHeader">

## Attachments:

</div>

<div class="greybox" data-align="left">

![](images/icons/bullet_blue.gif)
[netapp-dashboards.png](attachments/810450945/810450948.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[netapp-add.png](attachments/810450945/810450951.png) (image/png)  
![](images/icons/bullet_blue.gif)
[veeam\_patch.png](attachments/810450945/810450954.png) (image/png)  
![](images/icons/bullet_blue.gif)
[veeam\_admin.png](attachments/810450945/810450957.png) (image/png)  
![](images/icons/bullet_blue.gif)
[veeam\_dashboard.png](attachments/810450945/810450960.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[veeam\_admin2.png](attachments/810450945/810450963.png) (image/png)  
![](images/icons/bullet_blue.gif)
[image2018-10-3\_11-33-0.png](attachments/810450945/810418204.png)
(image/png)  
![](images/icons/bullet_blue.gif) [Highlights\_ VMware View Horizon
VMs-1530601910290.json](attachments/810450945/810647553.json)
(application/json)  
![](images/icons/bullet_blue.gif) [VMware Horizon\_ Desktop
VM-1530598496743.json](attachments/810450945/810614792.json)
(application/json)  
![](images/icons/bullet_blue.gif)
[create\_vmview\_datasource.png](attachments/810450945/811466754.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[image2018-10-4\_10-46-26.png](attachments/810450945/811565057.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[image2020-1-8\_13-37-36.png](attachments/810450945/959119361.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[image2020-1-8\_13-38-52.png](attachments/810450945/959053832.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[image2020-1-8\_13-39-15.png](attachments/810450945/959053837.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[image2020-1-8\_13-39-43.png](attachments/810450945/959119369.png)
(image/png)  
![](images/icons/bullet_blue.gif) [Highlights\_ VMware View Horizon
VMs-1590394661070.json](attachments/810450945/1289060353.json)
(application/octet-stream)  

</div>
