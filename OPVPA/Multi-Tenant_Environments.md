# Multi-Tenant Environments

Performance Analyzer supports different architectures to monitor and
separate multi-tenant environments. Typically, a customer wants to check
the real performance of their own systems in an individual dashboard. As
the responsible system administrator, you typically want all the
details, while the customer should see the most important data – to not
raise more questions than answered.

A tenant dashboard

![Tenant View - one
month](http://www.opvizor.com/wp-content/uploads/2017/06/monthsview.png)

## Typical Multi-Tenant Setups

Depending on the goals you want to achieve, there are different kinds of
multi-tenant setups. Sometimes, the customer owns the whole environment
including his own [VMware
vCenter](http://www.opvizor.com/opvizor-performance-analyzer-part-10-performance-in-real-time-for-vmware-vcenter-server-appliance-vcsa/) but
outsourced the management; sometimes the vCenter is centralized and all
tenants just use their part of the resources. Another important factor
is the isolation of data and what data should be seen in what
environments and by whom.

### Many Tenants, Each Tenant Owns a VMware vCenter

In this case, each tenant runs a complete environment, including a
VMware vCenter. The setup can look as follows.

![Multi-tenant environments - all
vCenter](http://www.opvizor.com/wp-content/uploads/2017/06/multi-tenant.png)

#### **Performance Analyzer Appliance 1 – Central Location**

In the central location, the largest Performance Analyzer appliance will
be deployed. All data of the central location as well as *Tenant 1* and
*Tenant 2* location will be collected here.

This appliance is only configured to collect data from the central
vCenter system. There is also a receiver listening for the data coming
from the tenant appliances.

The dashboard that is accessible in the central location can be used to
view all locations at once or separately, depending on the selection.

![vCenter
selection](http://www.opvizor.com/wp-content/uploads/2017/06/vcenter_selection.png)

#### **Performance Analyzer Appliance 2 – Tenant 1 Location**

This appliance is configured to collect data of the local tenants VMware
vCenter system, but sends the data to the local receiver as well as the
central Performance Appliance receiver. Only one TCP port is used for
communication and can be configured to the network needs.

#### **Performance Analyzer Appliance 2 – Tenant 2 Location**

Similar setup as *Tenant 2*. If there are different [storage
systems](http://www.opvizor.com/traditional-data-center-storage-systems-are-moved-to-the-cloud/) at
the different locations or different applications running, the appliance
configuration can differ. That is, *Tenant 2* should also gather NetApp
filer data as well as MS SQL data.

### Many Tenants, One VMware vCenter Manages All Tenant Environments

One very common setup is, to have only central VMware vCenter server
that manage the environments of different tenants and locations. The
separation is done either by vCloud Director or simply by using roles
and permissions.

![multi-tenant environment with one
vCenter](http://www.opvizor.com/wp-content/uploads/2017/06/multi-tenant_singlevcenter.png)

  

In this case, our Performance Analyzer appliance can be configured in 3
different ways:

1\) Use different Performance Analyzer appliances for each tenant using
the same permissions as the tenant itself. That is the simplest possible
setup and it ensures that the tenant user only sees its own data. The
downside is, to run multiple Performance Analyzer appliances. This setup
makes also sense, when no merged data should be accessible by the master
operator.

2\) Performance Analyzer as a multi-tenant appliance. Multiple data
collectors are configured to collect data using different credentials
(permissions) and send the data into different time series databases.
Every tenant has its own user and organization. That ensure that the
data is separated but can also be merged if needed (master operator).

3\) Data is completely collected by one data collector, but the
dashboards are configured to show separate data by tenant or user. This
setup is pretty straightforward, but the data separation is only
protected by the dashboards configuration and not by the time series
database.

## Different Performance Analyzer Components

Before we dig into details, it’s important to know that Performance
Analyzer consists of different services (components) that can be
completely separated, based on the architecture. All components can be
separated to run on different appliances. That enables us to scale as
well as to build efficient multi-tenant scenarios. We currently focus on
time series data, but we can handle unstructured and configuration data
as well. Just ask us, if you´re interested in learning more.

The **data collector** connects to the data source, for example, VMware
vCenter API, NetApp API or MS SQL Systemdb, to gather all performance
and statistical data in the configured crawling interval.

The **data receiver** listens to data and decides where to write the
data

The **Time Series Database** gets feeded by the data receiver and
handles the data retention as well as the possible queries on the data
itself.

The **Query Engine** allows to query the time series data using simple
and complex functions (math, transform, aso.)

The** Graphical front-end**, in our
case [Grafana](http://www.grafana.org/), allows us to visualize the
data based on the query engine that sits on top of the
data. 

![Architecture](http://www.opvizor.com/wp-content/uploads/2017/06/architecture_opvizor_1.png)

All components need to work hand in hand and know about the data stream,
metrics format and collected interval to make the visualization as great
as you´ll like it.
