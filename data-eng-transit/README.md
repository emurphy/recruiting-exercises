## Carrier transit times

When shipping a package, we need to know whether a ground shipping method can reliably deliver from one zip code to another within 1 or 2 days. 
The file [tracking-data.csv](tracking-data.csv) includes a sample of FedEx package tracking data where all packages originate from zip3 752. Our task is to code (as far as possible) a function that will predict whether FedEx Ground can reliably ship from zip3 752 and reach each destination zip3 (in the `zip_group_to` column) within delivery days 1, 2 or 3 respectively. The target rate for on-time delivery (OTD) is 95%.

### Sample transit corridor

For example the following table extracts the tracking data for destination zip3 358.

| trackingcode | shippingmethod | fromzip | tozip | acceptedat | deliveredat | zip_group_to | transit_time | day_of_week |
| ------------ | -------------- | ------- | ----- | ---------- | ----------- | ------------ | ------------ | ----------- |
| 390470684941 | FEDEX.GROUND | 75211 | 35801 | 2020-02-18T16:16:00-06:00 | 2020-02-20T10:43:39-06:00 | 358 | 2 | Tuesday |
| 390099979099 | FEDEX.GROUND | 75211 | 35806 | 2020-02-03T17:12:00-06:00 | 2020-02-05T12:39:46-06:00 | 358 | 2 | Monday |
| 390101490575 | FEDEX.GROUND | 75211 | 35810 | 2020-02-03T16:10:00-06:00 | 2020-02-05T08:35:21-06:00 | 358 | 2 | Monday |
| 390101489321 | FEDEX.GROUND | 75211 | 35810 | 2020-02-03T16:10:00-06:00 | 2020-02-05T08:35:21-06:00 | 358 | 2 | Monday |
| 390101490255 | FEDEX.GROUND | 75211 | 35810 | 2020-02-03T16:10:00-06:00 | 2020-02-05T08:35:21-06:00 | 358 | 2 | Monday |
| 390101489398 | FEDEX.GROUND | 75211 | 35810 | 2020-02-03T16:10:00-06:00 | 2020-02-05T08:35:21-06:00 | 358 | 2 | Monday |

When we send a package on FedEx Ground from 752 to 358, can we expect it to arrive within 1, 2 or 3 days? The `transit_time` column lists the number of days that each package actually spent in transit.

### Sample output

There is sample output in [transit-time-decisions.csv](transit-time-decisions.csv), though it may or may not be helpful.
It goes farther than needed for this simplified problem, in a few respects:

  - The decision is made on two levels: By day of week vs. aggregate
  - Includes the confidence level that led to the decision
  - The OTD target rate has been varied according to unspecified logic
  
The output file is included in case it is helpful for clarifying the requirements, but it is expected that your own 
output will be simpler.