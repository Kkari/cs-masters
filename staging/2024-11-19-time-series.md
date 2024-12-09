You wondered at one point, what is the advantage of time series databases like Timescale over vanilla Postgres? 
 
The biggest I learned is:
They automatically handle partitioning based on timestamps, which becomes an important point above 100GB data.
They implement a nice continuous aggregation and compression algorithms on top of those time partitioned tables.
They have special autovacuum, index and background worker tuning for the append-only timescale use case. 
For example method I learned for managing old data is:
You have an ingest table with multiple partitions.
You rotate the partitions.
You aggregate the inactive partitions to a new partition or a new table.
You truncate the processed partition. It is much faster than deletion because no vacuum is needed. The index can be dropped as well because it is partition-based.