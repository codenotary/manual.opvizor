# Maintaining Time

Opvizor Performance Analyzer utilizes serveral time series databases.
For correct function, it is important to have the correct time
configured on both Opvizor Performance Analyzer, the vCenter and ideally
all ESXi hosts.

# How is the clock of Performance Analyzer set?

From Version 5.0.5 on, Performance Analyzer tries to use NTP for time
synchronization with the servers from pool.ntp.org.

When Performance Analyzer can't connect or reach the NTP servers, it
will fall back to the clock of the host on which the appliance is
running using VMware tools time sync. You always need to make sure to
have NTP up and running.

Versions before 5.0.5 only use the host clock.

# Admin UI says "Too big time offset"

When you test the connection with the vCenter, Performance Analyzer
compares the clocks of both the vCenter and the Performance Analyzer
appliance. When these clocks differ more than a few seconds, there is
likely a misconfiguration in your infrastructure and NTP not configured
well.

The most common issues are:

  - ESXi host clocks drift and are not in sync with any external time
    service. ESXi is always configured to use UTC since version 6.x.
    ESXi host clocks should always be ynchronized with NTP. Have a look
    at [Configuring Network Time Protocol (NTP) on an ESXi host using
    the vSphere Web
    Client](https://kb.vmware.com/s/article/57147?lang=en_US) for
    configuration.
  - Even when NTP is configured, there can be firewalling issues in your
    network making time synchronization impossible. To make sure NTP
    functions properly, have a look at [Troubleshooting NTP on ESX and
    ESXi 4.x / 5.x
    / 6.x](https://kb.vmware.com/s/article/1005092?lang=en_US) .

# How can I monitor correct time in my network?

From Version 5.0.5 on, Performance Analyzer ships with a Dashboard
"VMware Config: Clocks and Timedrift". It is designed to help you to
find time synchronization issues.
