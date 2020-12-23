# Integration Oracle Database

**Please contact <sales@opvizor.com> to receive information about the
Performance Analyzer Oracle Feature Pack. You will receive a feature
patch that needs to be applied.  
**

  

# Add your Oracle Databases

**![](attachments/861470723/861569025.png?height=250)**

  - The SID is used to connect to the database server. It is commonly of
    the format **hostname/servicename**, using the hostname where the
    database is running, and the service name of the Oracle Database
    instance. The dsn (data source name) is the TNS entry (from the
    Oracle names server or tnsnames.ora file). So Performance Analyzer
    connects to the host with the name (or ip) **hostname,** this host
    serves the database with the name **servicename**.

  - You can specify a custom TCP port for the connection with the syntax
    **hostname:port/servicename**

  - The User needs Select-Privileges for the following dynamic Views: 
    
    gv$instance , gv$containers, gv$database , gv$sysstat ,
    gv$con\_sysstat , gv$waitclassmetric , gv$system\_wait\_class ,
    gv$sysmetric , gv$parameter , gv$con\_sysmetric , gv$eventmetric
    , gv$event\_name, gv$sql 

