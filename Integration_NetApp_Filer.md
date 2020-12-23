# Integration NetApp Filer

## Patch Performance Analyzer

**Please contact <sales@opvizor.com> to receive information about the
Performance Analyzer NetApp Feature Pack. You will receive a feature
patch that needs to be applied.  
**

# Add your NetApp Filer

![](attachments/84219590/84219630.png?height=250)

You can use whatever Poller name you want, with one exception: if you
intend to use OCUM too (for Capacity information), the Poller name must
match the filer name in OCUM.

  - Poller =if you intend to use OCUM please make sure to use the same
    Filer or Cluster names that are also visible in your OCUM console -
    often this is not the FQDN but only the hostname of your
    NetApp filer head (i. e. filer1)
  - Site = descriptive Site name (i. e. datacenter\_1, no whitespace)
  - Host = IP or DNS name of the NetApp Filer (i. e. 192.168.80.200)
  - Host Type = Filer (for NetApp Filer Head), OCUM (for OnCommand
    Unified Manager Server)
  - User = user name to poll the data from the filer
  - PW = password of the user to poll data from the filer

  

**Important**: For NetApp, you need to enable TLS on each node: options
tls.enable on

# NetApp data collecter account

**NetApp account to be used (please always use a read only user with
limited
rights)**



**NetApp User Integration**

``` bash
# NetApp 7-Mode
useradmin role add opvizor-pacollect-role -c "Role for performance monitoring by Opvizor PA collect" -a login-http-admin,api-system-get-version,api-system-get-info,api-perf-object-*,api-emsautosupport-log
useradmin group add opvizor-pacollect-group -c "Group for performance monitoring by Opvizor PA collect" -r opvizor-pacollect-role
useradmin user add opvizor-pacollect -c "User account for performance monitoring by Opvizor PA collect" -n "Opvizor PA collect" -g opvizor-pacollect-group 


# NetApp cMode 8.x
# NetApp create role
security login role create -role opvizor-pacollect-role -access readonly -cmddirname "version"
security login role create -role opvizor-pacollect-role -access readonly -cmddirname "clusteridentity show"
security login role create -role opvizor-pacollect-role -access readonly -cmddirname "clustershow"
security login role create -role opvizor-pacollect-role -access readonly -cmddirname "system node show"
security login role create -role opvizor-pacollect-role -access readonly -cmddirname "statistics"
security login role create -role opvizor-pacollect-role -access readonly -cmddirname "lun show"
security login role create -role opvizor-pacollect-role -access readonly -cmddirname "network interface show"
security login role create -role opvizor-pacollect-role -access readonly -cmddirname "qos workload show"

# NetApp create role
# Data ONTAP 8.2 or earlier
security login create -username opvizor-pacollect -application ontapi -role opvizor-pacollect-role -authmethod password

# Data ONTAP 8.3 or later
security login create -user-or-group-name opvizor-pacollect -application ontapi -role
opvizor-pacollect-role -authmethod password

# NetApp cMode 9.x, vServer example
security login role create -vserver <cluster_svm> -role opvizor-pacollect-role -access readonly -cmddirname "version" 
security login role create -vserver <cluster_svm> -role opvizor-pacollect-role -access readonly -cmddirname "cluster"
security login role create -vserver <cluster_svm> -role opvizor-pacollect-role -access readonly -cmddirname "system node"
security login role create -vserver <cluster_svm> -role opvizor-pacollect-role -access readonly -cmddirname "statistics"
security login role create -vserver <cluster_svm> -role opvizor-pacollect-role -access readonly -cmddirname "lun"
security login role create -vserver <cluster_svm> -role opvizor-pacollect-role -access readonly -cmddirname "network interface"
security login role create -vserver <cluster_svm> -role opvizor-pacollect-role -access readonly -cmddirname "qos workload"
#Create account
security login create -vserver <cluster_svm> -user-or-group-name opvizor-pacollect -application http -authmethod password -role opvizor-pacollect-role
# Type in a password twice
security login create -vserver <cluster_svm> -user-or-group-name opvizor-pacollect -application ontapi -authmethod password -role opvizor-pacollect-role
```

  

## Dashboards

 ![](attachments/84219590/84219655.png?height=250)

  

After adding the NetApp Systems you should find NetApp Dashboards.

We automatically add both, Dashboards for 7Mode and Cluster Mode. You
can safely delete the dashboards you don´t want.

  
