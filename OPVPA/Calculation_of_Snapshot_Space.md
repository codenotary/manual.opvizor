# Calculation of Snapshot Space

Snapshots are almost always used by backup products to secure active
virtual machines from the outside (not via agent in the guest, but VCB).
This is due to the hard drive files of a VM having exclusive read/write
access through the VMkernel until a VM snapshot is created. At this
point in time, the original hard drive files are readable, and the last
Delta file has exclusive write/read access through the VMkernel.

This table illustrates the technical process of a snapshot.

![VM snapshot growth
calculation](http://www.opvizor.com/wp-content/uploads/2017/06/snapshotcalc.png)
