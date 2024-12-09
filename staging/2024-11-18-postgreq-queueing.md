Yesterday by the way while cooking I was listening to the Queuing episode on PG.fm, it was really interesting! 
 
Some key points:
You can easily use PG as Queue implementation, it only gets hairy at multiple thousand TPS.
The important point if you use it for queuing is bloat management, so Vacuum tuning. That is because of the update behaviour with delete and insert we discussed today. PG does not deal well with short lived objects on default settings.
If the queue gets large then there is a standard approach with table partitioning to manage bloat.
Most cases 1 processor is enough, then you don't need to worry about SKIP Locked behaviour.
Other goodies:
A bigger sized node PG can handle multiple tens of thousands of OLTP requests per second on a reasonably sized amazon machine.
If a table gets above 100 GB then consider table partitioning, above 1TB consider sharding.

To connect the dots, I just considered: 
A queue based workload is something where you definitely do not want a UUIDv4 as a primary key. The load has usually a high temporal locality, meaning you touch the latest added elements the most often. 
If you use a UUDv4, then those will be distributed in random index pages, so you cannot rely on the visibility map that well to optimise index only scans and your disk will be more stressed because of the increased WAL workload you will have if you have something like a indexed status column and you change it as a message gets updated because the WAL cannot localise the changes to the few of the latest pages.
So here I would definitely use an big serial autoincrement key. 