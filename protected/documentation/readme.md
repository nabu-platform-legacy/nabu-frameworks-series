# Sources

Data can be obtained in a number of ways, the passive data collection overlaps with the process engine:

- service hooks where we trigger on service calls
- events
- signals

Apart from that we can do active data collection as well:

- push data explicitly to the series engine
- use a gauge to periodically check and generate data

You can also create derivative series where the output of one series feeds another.

## Named

All of these sources can be identified by two things:

- type: specifies which type it is
- name: within that type a unique name that identifies it, for example a data type, a service id,...



# Targets

Without additional configuration all data pushed to the series engine is ignored entirely.
It requires active subscriptions from series to actually do something with said data.

If you create a series, you can add multiple subscriptions.
If you configure nothing else, the data will be stored "raw" in the series.

# Series

Every data type is automatically a series you can subscribe to

Additionally you have named series

# Usecases



## Counting service calls

We want to count how often a service is called (e.g. to create contracts) so we can conclude how many contracts exist.
When counting, we might want to "group by" a field (e.g. location) to count how many per location. This means if we move from A to B, we should do A-- and B++. However, in the move service we likely have only B...

## Gauge

A gauge is where we periodically call a service that outputs particular data which is then pushed to a series for further processing.