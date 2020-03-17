# Carrier transit times

We need to know whether ground shipping methods can be sent from one zip code to another within 1 or 2 days. 
With input from [tracking-data.csv](tracking-data.csv), outline a process and code (as far as possible) a function that 
will decide whether FedEx Ground can reliably ship from zip3 752 and reach the destination 
zip3 (in the `zip_group_to` column). The target rate for on-time delivery (OTD) is 95%.

There is sample output in [transit-time-decisions.csv](transit-time-decisions.csv), though it may or may not be helpful.
It goes farther than needed for this simplified problem, in a few respects:

  - The decision is made on two levels: By day of week vs. aggregate
  - Includes the confidence level that led to the decision
  - The OTD target rate has been varied according to unspecified logic
  
The output file is included in case it is helpful for clarifying the requirements, but it is expected that your own 
output will be simpler.