# Carrier transit times

We need to know whether ground shipping methods can be sent from one zip code to another within 1 or 2 days. 
With input from [tracking-data.csv](tracking-data.csv), outline a process and code (as far as possible) a function that 
will decide whether FedEx Ground can reliably ship from zip3 752 and reach the destination 
zip3 (in the `zip_group_to` column). The target rate for on-time delivery (OTD) is 95%.

## Sample transit corridor

For example the following table reproduces the tracking data for destination zip3 358.

| trackingcode | shippingmethod | fromzip | tozip | acceptedat | deliveredat | zip_group_to | transit_time | day_of_week |
| ------------ | -------------- | ------- | ----- | ---------- | ----------- | ------------ | ------------ | ----------- |
| 390470684941 | FEDEX.GROUND | 75211 | 35801 | 2020-02-18T16:16:00-06:00 | 2020-02-20T10:43:39-06:00 | 358 | 2 | Tuesday |
| 390099979099 | FEDEX.GROUND | 75211 | 35806 | 2020-02-03T17:12:00-06:00 | 2020-02-05T12:39:46-06:00 | 358 | 2 | Monday |
| 390101490575 | FEDEX.GROUND | 75211 | 35810 | 2020-02-03T16:10:00-06:00 | 2020-02-05T08:35:21-06:00 | 358 | 2 | Monday |
| 390101489321 | FEDEX.GROUND | 75211 | 35810 | 2020-02-03T16:10:00-06:00 | 2020-02-05T08:35:21-06:00 | 358 | 2 | Monday |
| 390101490255 | FEDEX.GROUND | 75211 | 35810 | 2020-02-03T16:10:00-06:00 | 2020-02-05T08:35:21-06:00 | 358 | 2 | Monday |
| 390101489398 | FEDEX.GROUND | 75211 | 35810 | 2020-02-03T16:10:00-06:00 | 2020-02-05T08:35:21-06:00 | 358 | 2 | Monday |

Can we send a package on FedEx Ground from 752 to 358 and expect it to arrive within 2 days?

## Sample output

There is sample output in [transit-time-decisions.csv](transit-time-decisions.csv), though it may or may not be helpful.
It goes farther than needed for this simplified problem, in a few respects:

  - The decision is made on two levels: By day of week vs. aggregate
  - Includes the confidence level that led to the decision
  - The OTD target rate has been varied according to unspecified logic
  
The output file is included in case it is helpful for clarifying the requirements, but it is expected that your own 
output will be simpler.