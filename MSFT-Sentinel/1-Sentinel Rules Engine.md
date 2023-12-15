## References 
- https://learn.microsoft.com/en-us/azure/sentinel/detect-threats-custom


## Ingestion Delay
- https://learn.microsoft.com/en-us/azure/sentinel/ingestion-delay

## Limits 
**The size limit for an entire alert is _64 KB_**.
- Alerts that grow larger than 64 KB will be truncated. As entities are identified, they are added to the alert one by one until the alert size reaches 64 KB, and any remaining entities are dropped from the alert.


- Set **Run query every** to control how often the query is run—as frequently as every 5 minutes or as infrequently as once every 14 days.
    
- Set **Lookup data from the last** to determine the time period of the data covered by the query—for example, it can query the past 10 minutes of data, or the past 6 hours of data. The maximum is 14 days.

## Entities 
- https://learn.microsoft.com/en-us/azure/sentinel/map-data-fields-to-entities

## Customization
- https://learn.microsoft.com/en-us/azure/sentinel/surface-custom-details-in-alerts
- https://learn.microsoft.com/en-us/azure/sentinel/customize-alert-details