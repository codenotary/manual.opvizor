# vscsiStats

vscsiStats is a tool running on the ESXi host. It allows in depth
analysis of VM, host and datastores, with data not available in vCenter.

Since vscsiStats consumes some host resources itself, it is not
recommended to have it running all the time. But it is very helpful, if
you have to troubleshoot storage performance.

Opvizor created an on demand invocation for vscsiStats. Just add a
custom attribute "opvizor.vscsistats" to the host(s) you want to
monitor, and set it to 1 to start data collection. Set it to 0 to stop
data collection.

![](attachments/860160001/898236423.png)

![](attachments/860160001/898203653.png)

  

![](attachments/860160001/860192780.png?height=250)

  

The dashboard uses incremental rendering. To view best, click the
Refresh-Icon in the upper left corner once the dashboard is loaded.

  

<div class="pageSectionHeader">

## Attachments:

</div>

<div class="greybox" data-align="left">

![](images/icons/bullet_blue.gif)
[image2018-12-11\_15-30-30.png](attachments/860160001/860192780.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[image2019-5-6\_10-56-0.png](attachments/860160001/898236417.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[image2019-5-6\_10-57-20.png](attachments/860160001/898236423.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[image2019-5-6\_10-58-4.png](attachments/860160001/898203653.png)
(image/png)  

</div>
