# Installing the Virtual Appliance

<div class="toc-macro rbtoc1606556333373">

  - [Provisioning - step by
    step](#InstallingtheVirtualAppliance-_Toc457289564Provisioning-stepbystep)
  - [Enable HTTPS](#InstallingtheVirtualAppliance-EnableHTTPS)
  - [VMware vSphere
    Settings](#InstallingtheVirtualAppliance-VMwarevSphereSettings)
  - [Active Directory
    Authentification](#InstallingtheVirtualAppliance-ActiveDirectoryAuthentification)
  - [Increasing disk
    space:](#InstallingtheVirtualAppliance-Increasingdiskspace:)
  - [Used Network Ports Opvizor Performance Analyzer
    Appliance](#InstallingtheVirtualAppliance-UsedNetworkPortsOpvizorPerformanceAnalyzerAppliance)

</div>

  
**General information**

  

To simplify the installation, we decided to deliver the PerfAnalyzer as
a prepackaged virtual appliance. So there are just a few steps to do to
get PerfAnalyzer up and running.

  

# **Provisioning - step by step**

  

The opvizor PerfAnalyzer is supplied as a VMware OVF template. To
install:

1.  Download the opvizor PerfAnalyzer ZIP file
    from <http://try.opvizor.com/opvizor-perfanalyzer-product-page/>
2.  Extract the ZIP file, e.g. with Windows Explorer.
3.  Import the appliance using your VMware vCenter. Use the function
    "Deploy OVF Template" or "Deploy OVF template". 
    1.  If you use the vSphere Web client, it can happen that this
        function is not available until you install the Client
        package. Then you can access the vSphere client (aka
        Fat-Client). During the deployment, you can set the storage for
        the appliance. 
    2.  If your infrastructure has more than 1000 virtual machines the
        use of SSD storage is recommended as continuously storing
        performance in real-time is very IO-intensive. 
    3.  If you are running 1000 VMs or more, you should also consider
        doubling the amount of memory of the appliance.  
        ![](attachments/82023843/898662401.png?height=250)
4.  Start the appliance. 
5.  Open the console. 
6.  When the startup has completed, you will see the following screen
    and log in with the following credentials: **Login**: *admin*
    **Password**: *VMware123*  
    ![](attachments/82023843/898498562.png?height=250)
7.  After login the configuration main menu shows up: Choose the menu
    item 6, if you use a German keyboard (for confirmation "z" for "y").
8.  Variant a): If you are using DHCP, just open the appliance ip in a
    browser   
    Variant b): If you want to use a static address, you have to use
    menu item 5. When completing this menu, a demo license creates
    automatically and the appliance restarts.
9.  After about one minute, the appliance should be back up. To collect
    and represent data from your VMware infrastructure the appliance has
    to connect to a VMware vCenter. 
10. Open the appliance configuration page under
    http://ip\_or\_systemname\_appliance/admin in your browser.  
    ![](attachments/82023843/898465802.png?height=250)
11. To login, use the following data: **User name**:
    *admin ***Password**: *VMware123* and press the login button.   
    The **Overview** page of the administration area appears.   
    ![](attachments/82023843/898465807.png?height=400)
12. Click on **Infrastructure \>VMware \>Add new vCenter **to indicate
    the vCenter and access data.  
      
    ![](attachments/82023843/898531338.png?height=400)
13. Enter the credentials and click **Add**.  
    As a user you can use a less privileged VMware user that has only
    read access and the Global - Service Manager permission (to enable
    NUMA data gathering)  
    ![](attachments/82023843/749731844.png?height=250)
14. The credentials are automatically tested.  
    ![](attachments/82023843/898695169.png?height=400)  
    If the test was successful, the message "Connection successfully
    tested" shows up.   
      
15. The opvizor PerfAnalyzer is now successfully configured and begins
    collecting data. Depending on the size of your infrastructure, it
    may take approximately 5 to 15 minutes until you see results.
16. Now press the **Log-out** in the left menu.

# Enable HTTPS

We made it pretty straightforward to enable HTTPS (SSL) to access the
appliance. Within the Admin interface / Overview click the Open Button
under SSL settings:

![](attachments/82023843/423231492.png?height=250)

Then either use the integrated SSL Certificate or upload your own PEM
formatted certificate. [Detailed information to create your own
CSR](SSL_Details_CSR_generation_)

![](attachments/82023843/423198724.png?height=250)

You can save the SSL Settings and decide to redirect all HTTP
connections to HTTPS as well.

  

# VMware vSphere Settings

Please make sure that you have a 5 minute statistics level of 2
configured for your VMware vCenter systems:

 ![](attachments/82023843/84050016.png?height=250)

Otherwise some virtual machine metrics can't be collected and the some
charts will be empty.

IMPORTANT NOTE: Changing these statistics level result in a higher
amount of data collected on the vCSA appliance. Also only change the
first interval (5minute, 1 day), not the others.

**Please make sure to check the estimated space required in the
statistics section and your local partition free space:**

Increase disk space: <https://kb.vmware.com/s/article/2126276>

What to do when a root partition is
full: <https://www.opvizor.com/vcenter-appliance-vcsa-root-partition-full>

Some more blog posts about full
vCSA: <https://thevirtualist.org/vcsa-filesystem-is-out-of-disk-space/>

# Active Directory Authentification

Important: To enable the Active Directory authentication, the network
settings of the appliance must configured to reach the AD server and the
domain (AD Name Server, Domain Name).

Choose Auth in the main menu:

![](attachments/82023843/562003978.png?height=250)

Enable the AD Authentication and select one of the Active Directory
Controller shown.

Enter username and password of the AD user to search for the AD access
groups and click Check AD connection.

If all goes well, select the Admin, Editor and Viewer group for the
dashboards. You can type parts of the group name and search. The drop
down selection box shows all found groups.

When everything is correctly configured AD user of the related group can
log on. **Please type only the username and password to login, not the
domain\!**

# Increasing disk space:

To increase the disk space you can just change the disk capacity of the
second disk and our system will automatically resize the data partition
within 5 minutes.

Hint: If you can´t change the capacity, please delete existing VM
snapshots.

![](attachments/82023843/667844610.png?height=250)

Next Topic: [Using Performance
Analyzer](https://opvizor.atlassian.net/wiki/display/OPVPA/Using+opvizor+PerfAnalyzer)

# Used Network Ports Opvizor Performance Analyzer Appliance

  

  - Client \> Opvizor Dashboard - TCP Ports **80,443**
  - Client \> Opvizor SSH - TCP Port **22**
  - Opvizor \> Mailserver - TCP Port **25**
  - Opvizor \> DNS - UDP/TCP Port **53**
  - Opvizor \> vCenter - TCP Port **443**
  - Opvizor \> NetApp Filer - TCP Port **443**
  - Opvizor \> NetApp HyperFlex - TCP Port **443**
  - Opvizor \> Cisco UCS - TCP Port **443**
  - Opvizor \> Active Directory - TCP **Port 389**
  - Opvizor \> Microsoft SQL  - TCP Port **1433**
  - Opvizor \> Oracle - TCP Port **1521**
  - when using telegraf - Windows/Linux system \> Opvizor TCP
    Port **8086**

  

  

<div class="pageSectionHeader">

## Attachments:

</div>

<div class="greybox" data-align="left">

![](images/icons/bullet_blue.gif)
[worddav61904dbc25a6cd35000b7cb7469627a1.png](attachments/82023843/82023842.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[worddavaa104f22ba852b4270fb90ccac8d4dee.png](attachments/82023843/82023850.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[worddaveee8413b8437fab67605dadd0faa34c0.png](attachments/82023843/82023856.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[worddav3f2d004ecccb300e075f3a1676fc60ab.png](attachments/82023843/82023862.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[worddav62fdac44032e5cc95b6320955873116c.png](attachments/82023843/82023868.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[worddav080aa4baa5f37f458a02ec468b813744.png](attachments/82023843/82023875.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[worddav18b203bd4133ce3a6bedf43320bb0d24.png](attachments/82023843/82023882.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[worddavac0142df730012f5f4afb8f014e9c2fe.png](attachments/82023843/82023888.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[worddav638a05df1dbcdee1ddba6139af48bd39.png](attachments/82023843/82023894.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[worddavc2d3573add9776304d9bed5bc58a9064.png](attachments/82023843/82023900.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[worddav54449f81ca6fd53d57b7cbf87cd26366.png](attachments/82023843/82023906.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[worddav98988c63e221df9f9ddb93988e378246.png](attachments/82023843/82023912.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[worddav092530424e35250521b7bda65c12d8b5.png](attachments/82023843/82023918.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[worddav27122057d65ad1c538ca7ad517e64f95.png](attachments/82023843/82023924.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[worddave52c19dbcac1b26312a64327f40f3d06.png](attachments/82023843/82023930.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[worddav69edf648f8ac183a0d6f9a7f661a0121.png](attachments/82023843/82023936.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[worddav06dbff2300c14185a21435067a9e145e.png](attachments/82023843/82023942.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[worddav5be4bf5119573609c4923f11cbbbc51e.png](attachments/82023843/82023948.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[worddavb3763aa4a64e94e607ca19d533ae443d.png](attachments/82023843/82023954.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[worddav1f04558543a7ec0ca05486a1f0e696a6.png](attachments/82023843/82023962.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[worddav07481bb2ca03400983bd638b67b60558.png](attachments/82023843/82023969.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[image2017-6-21\_23-3-31.png](attachments/82023843/83856449.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[image2017-6-21\_23-4-24.png](attachments/82023843/83856477.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[image2017-6-21\_23-5-32.png](attachments/82023843/83856500.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[image2017-6-28\_21-35-2.png](attachments/82023843/83984996.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[vcenter\_level.png](attachments/82023843/84050016.png) (image/png)  
![](images/icons/bullet_blue.gif)
[image2017-7-5\_23-3-7.png](attachments/82023843/84124913.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[image2017-7-5\_23-4-58.png](attachments/82023843/84124947.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[image2017-7-5\_23-10-30.png](attachments/82023843/84125002.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[image2018-1-4\_16-9-10.png](attachments/82023843/423231492.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[image2018-1-4\_16-10-37.png](attachments/82023843/423198724.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[image2018-3-2\_20-12-27.png](attachments/82023843/562003978.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[image2018-4-16\_15-20-39.png](attachments/82023843/667844610.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[image2018-6-18\_17-1-44.png](attachments/82023843/749731844.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[image2018-7-17\_9-20-42.png](attachments/82023843/767328269.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[image2019-5-7\_14-31-45.png](attachments/82023843/898531329.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[image2019-5-7\_14-32-27.png](attachments/82023843/898498562.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[image2019-5-7\_14-33-1.png](attachments/82023843/898662401.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[image2019-5-7\_14-35-54.png](attachments/82023843/898465802.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[image2019-5-7\_14-37-29.png](attachments/82023843/898465807.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[image2019-5-7\_14-38-6.png](attachments/82023843/898531338.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[image2019-5-7\_14-39-36.png](attachments/82023843/898695169.png)
(image/png)  

</div>
