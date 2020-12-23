# Integration Microsoft Windows

There are 3 steps to follow after selecting Infrastructure / Windows in
your admin
interface:

<div class="intercom-container">

<https://downloads.intercomcdn.com/i/o/41550233/63b873f9e2460b3cbbf2cfbe/image.png>

</div>

  
Download the telegraf archive (1) from our admin page as well as the
telegraf.conf (2), follow the installation instruction for telegraf
(extract, install service, start) and make sure to overwrite the
telegraf.conf. 

  - Extract telegraf to %programfiles%/telegraf
  - Overwrite the telegraf.conf
  - Open an administrative PowerShell session, change to
    the %programfiles%/telegraf directory and type **telegraf.exe
    --service install** to install the Windows service and **net start
    telegraf**

Then click load/reset Windows Dashboards (3) that automatically imports
the Microsoft: Windows Host Overview
Dashboard:  
  

<div class="intercom-container">

<https://downloads.intercomcdn.com/i/o/41550435/d91f780f5328c9510cd1dae4/image.png>

</div>

  
That's it

