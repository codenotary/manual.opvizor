# Snapshots

Snapshots are the snapshots you have taken of your VMware installation.

When you create a snapshot on a virtual machine, a certain point in time
is recorded, meaning as of the time of the snapshot, the original files
of the VM remain as they are, and all modifications are recorded in new
files. This may take place during ongoing operation of the virtual
machines. It is also possible to merge the current data with the data of
the snapshot, which also does not cause downtime. Only if you want to
delete the data accumulated since the snapshot, the virtual machine is
stopped, reset to the old status, and activated again.

Theoretically you can create a large number number of VM snapshots,
however, this is hardly beneficial due to the lacking transparency in
snapshot administration and the elaborate management.

As soon as a snapshot is created, the newly produced Delta files grow
dynamically with the activity in the guest, and every modification on
the hard drive thus leads to an increase of the Delta-hard drive file.
This relates to every modification, from copying a file via secure
formatting of the hard drive with zeros all the way to deleting files.
The drive space need is never reduced. However, a Delta file can never
become larger than its original file, as all memory blocks were copied
1:1. If the same block is overwritten a hundred times, this does not
change the size of the Delta file. As soon as a new block is written,
the Delta file grows along with it in steps of at least 15 MB.

Thus it is important to understand that after creating the snapshot, the
additional memory requirement may be doubled at most, but this is
applicable to every snapshot; meaning if the Delta file is 5 GB in size
after the first snapshot and a second snapshot is created, the Delta
files add up on the datastore. This is why you need to watch the number
of snapshots as well as their size.

  - [Monitoring Snapshots](Monitoring_Snapshots)
  - [Calculation of Snapshot Space](Calculation_of_Snapshot_Space)

<div class="pageSectionHeader">

## Attachments:

</div>

<div class="greybox" data-align="left">

![](images/icons/bullet_blue.gif)
[image2017-7-2\_0-11-3.png](attachments/84037398/84038214.png)
(image/png)  

</div>
