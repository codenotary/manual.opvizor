# Data Retention

Performance Analyzer uses disk space based on the number of entities and
the configured retention. You need to keep in mind, that we
automatically inflate the time series data base based on all possible
metrics that can be received by an entity over the configured retention.

That means that storing data over 30 days instead of 7 days
automatically consumes disk space from day 1.

If you want to change the data retention, you can use our web
administration interface.

**Some important tips:**

  - Data retention should always be a multiple of the retention before,
    so 20sec:2h, 60sec:6h, 4min:24h aso. Never use 20sec:2h, 30sec:6h,
    50sec:25h\!
  - Data retention should never be duplicated: like 20sec:2h, 20sec:6h,
    20sec:24h
  - Data retention should never be lower than the retention before:
    20sec:4h, 6min:8h, 2min:24h

  

The following video shows the use of our data retention section to
customize the data granularity and duration. Please keep in mind that
high granularity (i. e. 20 seconds over 7 day, 1minute over 2 years)
require disk space and can slow down dashboard performance on slower
storage.

![](attachments/83990959/778108929.gif?height=250)

Despite the fact, that all retention can be changed, we provide a
default setting out-of-the box. Please contact <support@opvizor.com> if
you have questions about retention settings.

## VMware

<div class="table-wrap">

<table>
<colgroup>
<col style="width: 44%" />
<col style="width: 31%" />
<col style="width: 23%" />
</colgroup>
<thead>
<tr class="header">
<th>Data Type</th>
<th>Data Interval</th>
<th>Duration</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>VMware Configuration</td>
<td>10 minutes</td>
<td>1 day</td>
</tr>
<tr class="even">
<td>VMware Configuration</td>
<td>90 minutes</td>
<td>7 days</td>
</tr>
<tr class="odd">
<td>VMware Configuration</td>
<td>180 minutes</td>
<td>45 days</td>
</tr>
<tr class="even">
<td>VMware Performance</td>
<td>20 seconds</td>
<td>2 hours</td>
</tr>
<tr class="odd">
<td>VMware Performance</td>
<td>2 minutes</td>
<td>8 hours</td>
</tr>
<tr class="even">
<td>VMware Performance</td>
<td>4 minutes</td>
<td>12 hours</td>
</tr>
<tr class="odd">
<td>VMware Performance</td>
<td>12 minutes</td>
<td>24 hours</td>
</tr>
<tr class="even">
<td>VMware Performance</td>
<td>24 minutes</td>
<td>2 days</td>
</tr>
<tr class="odd">
<td>VMware Performance</td>
<td>96 minutes</td>
<td>7 days</td>
</tr>
<tr class="even">
<td>VMware Performance</td>
<td>192 minutes</td>
<td>45 days</td>
</tr>
<tr class="odd">
<td><br />
</td>
<td><br />
</td>
<td><br />
</td>
</tr>
</tbody>
</table>

</div>

## VMware vSAN

<div class="table-wrap">

| Data Type   | Data Interval | Duration |
| ----------- | ------------- | -------- |
| VMware vSAN | 1 minute      | 1 hour   |
| VMware vSAN | 2 minutes     | 2 hours  |
| VMware vSAN | 4 minutes     | 3 hours  |
| VMware vSAN | 12 minutes    | 12 hours |
| VMware vSAN | 24 minutes    | 2 days   |
| VMware vSAN | 96 minutes    | 7 days   |
| VMware vSAN | 192 minutes   | 30 days  |
| VMware vSAN | 960 minutes   | 180 days |

</div>

## NetApp

<div class="table-wrap">

<table>
<colgroup>
<col style="width: 43%" />
<col style="width: 32%" />
<col style="width: 24%" />
</colgroup>
<thead>
<tr class="header">
<th>Data Type</th>
<th>Data Interval</th>
<th>Duration</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>NetApp Capacity</td>
<td>15 minutes</td>
<td>100 days</td>
</tr>
<tr class="even">
<td>NetApp Capacity</td>
<td>1 day</td>
<td>5 year</td>
</tr>
<tr class="odd">
<td>NetApp Performance</td>
<td>30 seconds</td>
<td>35 days</td>
</tr>
<tr class="even">
<td>NetApp Performance</td>
<td>5 minutes</td>
<td>100 days</td>
</tr>
<tr class="odd">
<td>NetApp Performance</td>
<td>15 minutes</td>
<td>395 days</td>
</tr>
<tr class="even">
<td>NetApp Performance</td>
<td>1 hours</td>
<td>5 years</td>
</tr>
<tr class="odd">
<td><br />
</td>
<td><br />
</td>
<td><br />
</td>
</tr>
</tbody>
</table>

</div>

  

## DataCore

<div class="table-wrap">

<table style="width:100%;">
<colgroup>
<col style="width: 29%" />
<col style="width: 40%" />
<col style="width: 29%" />
</colgroup>
<thead>
<tr class="header">
<th>Data Type</th>
<th>Data Interval</th>
<th>Duration</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>DataCore</td>
<td>60 seconds</td>
<td>35 days</td>
</tr>
<tr class="even">
<td>DataCore</td>
<td>5 minutes</td>
<td>100 days</td>
</tr>
<tr class="odd">
<td>DataCore</td>
<td>15 minutes</td>
<td>395 days</td>
</tr>
<tr class="even">
<td>DataCore</td>
<td>5 minutes</td>
<td>100 days</td>
</tr>
<tr class="odd">
<td>DataCore</td>
<td>15 minutes</td>
<td>395 days</td>
</tr>
<tr class="even">
<td>DataCore</td>
<td>1 hours</td>
<td>5 years</td>
</tr>
<tr class="odd">
<td><br />
</td>
<td><br />
</td>
<td><br />
</td>
</tr>
</tbody>
</table>

</div>

<div class="pageSectionHeader">

## Attachments:

</div>

<div class="greybox" data-align="left">

![](images/icons/bullet_blue.gif)
[change\_retention.gif](attachments/83990959/778108929.gif)
(image/gif)  

</div>
