# Integration Microsoft SQL Server (agentless)

There are 2 steps to follow after selecting Infrastructure / MS SQL in
your admin interface:

![](attachments/423723009/423854081.png?height=250)  
  

1.  add your MS SQL server - please check the listener port if non
    default or dynamic (no support for dynamic ports). More information
    can be found
    here: <https://docs.microsoft.com/en-us/sql/database-engine/configure-windows/configure-a-server-to-listen-on-a-specific-tcp-port>
2.  click Load/Reset MS SQL Dashboard to automatically import the
    Microsoft: Windows Host Overview Dashboard

When adding the SQL Server using the embedded connector of the
Performance Analyzer appliance (agentless MS SQL monitoring), make sure
to leave the default YES in the top line.

![](attachments/423723009/423854093.png?height=250)

Make sure to create a MS SQL user having sufficient permissions:

USE master;  
GO  
CREATE LOGIN pamsql WITH PASSWORD = N'mystrongpassword';  
GO  
GRANT VIEW SERVER STATE TO pamsql;  
GO  
GRANT VIEW ANY DEFINITION TO pamsql;  
GO

  

![](attachments/423723009/423886853.png?height=250)

  
That's
    it

## collected metrics

## Wait stats

  - ## Wait time (ms) | I/O, Latch, Lock, Network, Service broker, Memory, Buffer, CLR, XEvent, Other, Total

  - ## Wait tasks | I/O, Latch, Lock, Network, Service broker, Memory, Buffer, CLR, XEvent, Other, Total

## Memory clerk

  - ## Memory breakdown (%) | Buffer pool, Cache (objects), Cache (sql plans), Other

  - ## Memory breakdown (bytes) | Buffer pool, Cache (objects), Cache (sql plans), Other

## Database size

  - ## Log size (bytes) | databases (included sysdb)

  - ## Rows size (bytes) | databases (included sysdb)

## Database IO

  - ## Log writes (bytes/sec) | databases (included sysdb)

  - ## Rows writes (bytes/sec) | databases (included sysdb)

  - ## Log reads (bytes/sec) | databases (included sysdb)

  - ## Rows reads (bytes/sec) | databases (included sysdb)

  - ## Log (writes/sec) | databases (included sysdb)

  - ## Rows (writes/sec) | databases (included sysdb)

  - ## Log (reads/sec) | databases (included sysdb)

  - ## Rows (reads/sec) | databases (included sysdb)

## Database latency

  - ## Log read latency (ms) | databases (included sysdb)

  - ## Log write latency (ms) | databases (included sysdb)

  - ## Rows read latency (ms) | databases (included sysdb)

  - ## Rows write latency (ms) | databases (included sysdb)

  - ## Log (average bytes/read) | databases (included sysdb)

  - ## Log (average bytes/write) | databases (included sysdb)

  - ## Rows (average bytes/read) | databases (included sysdb)

  - ## Rows (average bytes/write) | databases (included sysdb)

## Database properties

  - ## Recovery Model FULL | databases (included sysdb)

  - ## Recovery Model BULK\_LOGGED | databases (included sysdb)

  - ## Recovery Model SIMPLE | databases (included sysdb)

  - ## State ONLINE | databases (included sysdb)

  - ## State RESTORING | databases (included sysdb)

  - ## State RECOVERING | databases (included sysdb)

  - ## State RECOVERY\_PENDING | databases (included sysdb)

  - ## State SUSPECT | databases (included sysdb)

  - ## State EMERGENCY | databases (included sysdb)

  - ## State OFFLINE | databases (included sysdb)

## OS Volume

  - ## Volume total space (bytes) | logical volumes

  - ## Volume available space (bytes) | logical volumes

  - ## Volume used space (bytes) | logical volumes

  - ## Volume used space (%) | logical volumes

## CPU

  - ## CPU (%) | SQL process, External process, SystemIdle

## Performance metrics

  - ## Performance metrics | Point In Time Recovery, Available physical memory (bytes), Average pending disk IO, Average runnable tasks, Average tasks, Buffer pool rate (bytes/sec), Connection memory per connection (bytes), Memory grant pending, Page File Usage (%), Page lookup per batch request, Page split per batch request, Readahead per page read, Signal wait (%), Sql compilation per batch request, Sql recompilation per batch request, Total target memory ratio

 

<div class="pageSectionHeader">

## Attachments:

</div>

<div class="greybox" data-align="left">

![](images/icons/bullet_blue.gif)
[netapp-dashboards.png](attachments/423723009/423723012.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[netapp-add.png](attachments/423723009/423723015.png) (image/png)  
![](images/icons/bullet_blue.gif)
[veeam\_patch.png](attachments/423723009/423723018.png) (image/png)  
![](images/icons/bullet_blue.gif)
[veeam\_admin.png](attachments/423723009/423723021.png) (image/png)  
![](images/icons/bullet_blue.gif)
[veeam\_dashboard.png](attachments/423723009/423723024.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[veeam\_admin2.png](attachments/423723009/423723027.png) (image/png)  
![](images/icons/bullet_blue.gif)
[image2018-1-5\_19-10-11.png](attachments/423723009/423854081.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[image2018-1-5\_19-14-11.png](attachments/423723009/423886853.png)
(image/png)  
![](images/icons/bullet_blue.gif)
[image2018-1-5\_19-16-49.png](attachments/423723009/423854093.png)
(image/png)  

</div>
