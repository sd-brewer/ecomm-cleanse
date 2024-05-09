# Data Quality Issues
- note down all data quality issues, grouped by table


## all_sessions
- update records where `productprice` = 0, these should be changed to null, as it is clearly missing data (or maybe its not a product page)
- `totaltransactionrevenue`, `productprice`, and all other currency columns should be divided by 1,000,000
- null columns
    - columns `productrefundamount`, `itemquantity`, `itemrevenue`, `searchkeyword` contain entirely null values, and can be safely dropped
- duplicate records
    - before cleaning, `all_sessions` contained no duplicate rows, all 15134 rows are unique
- `productprice` doesn't correlate with the `unitprice` found in `analytics` where revenue values are recorded
- `totaltransactionrevenue` is not always equal to the sum of `revenue` recorded in `analytics` for a given `visitid`
- there are `totaltransactionrevenue`s that are null, where there is `revenue` value recorded in `analytics`
    - this represents missing/incomplete data
    - there are also `visitid`s missing from `all_sessions` entirely that have `revenue` values recorded in `analytics`
    - clearly data is not being aggregated effectively, some transactions might be slipping through the cracks
- missing `transactionid`: `transactionid` is only recorded for 9 / 81 records where a non-null `totaltransactionrevenue` is present


## analytics
- `revenue`, `unitprice` should be divided by 1,000,000
- `visitid` seems to be assigned based on `visitstarttime` (unix timestamp, seconds from 1970-01-01 00:00)
    - there are only 38610 / 4.3 million records where this is not the case
    - `visitid` then wont be unique, and must be paired with `fullvisitorid` as a composite key, since visitors can visit the site at the same second, and get assigned the same `visitid`
- null columns
    - `unitprice` contained entirely null values, and can be safely dropped 
- duplicate records
    - before any column alterations, `analytics` contained 4301122 total rows, of which 1739307 are unique
        - its unclear if these duplicates are created from technical glitches, or issues with data collection
            - for example, if these duplicates represent actual user behavior (clicking on a link/page multiple times), this information might have some value for keeping, and therefore keeping a count of how many of each duplicate appears would be better than simply removing the duplicate rows
                - even if the duplicate count has no analytical value, it may be useful for sourcing the technical glitches that created them (linking to specific users, visits, geographic locations)
- `timeonesite`
    - `bounces` are correlated with null `timeonsite` values, however there are many null `timeonsite` values that are not labelled as `bounces` (this could be due to a user opening the page in a seperate browser tab, and closing it before visiting, not necessarily an issue with bounce labeling or timeonsite collection)
        - where there is more obviously an issue, is where there is recorded `revenue` (indicating a transaction), yet null values for `timeonsite`. This occurs in 7 records, representing 5 unique visitors.
- `revenue`
    - there are `visitid`s in `all_sessions` that have a recorded `totaltransactionrevenue` that have null `revenue` in the corresponding `analytics` record