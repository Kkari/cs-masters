---
title: "Indexing in Postgres"
date: 2024-12-10
---

I loved the pg.fm episodes about indexing. ([Over Indexing](https://postgres.fm/episodes/over-indexing), [Under Indexing](https://postgres.fm/episodes/under-indexing), [JSON](https://postgres.fm/episodes/json))
I feel that indexing is a topic that has to be better understood by application developers to develop performant software.

I loved the older talks of Thompson about [Mechanical Sympathy](https://youtu.be/MC1EKLQ2Wmg?si=kYdH6Mkw5R8vn0lH), where he talks about understanding the processor to develop performant code and the [numbers everyone should know](https://colin-scott.github.io/personal_website/research/interactive_latency.html) by Jeff Dean. 

I feel it is similar with the database and indexing. Application developers should know:
1. How index types.
2. Time and space trade-offs.
3. Behaviour around inserts, updates, HOT updates, WAL, etc. 

Might sound a lot, but it is important to know these to be able to develop good applications. 

What I found the most important were the Multi-column index behaviour and the neccessity random_page_cost setting, especially in DB providers running on SSD.

Some readings I still have to dvelve into on the topic:
* Flexible queries with a lot of indexes: https://www.heap.io/blog/running-10-million-postgresql-indexes-in-production
* Indexing for E-commerce: https://www.cybertec-postgresql.com/en/faceting-large-result-sets/
* Indexing in the Postgres Pro book
* https://www.postgresql.org/docs/current/indexes.html
* https://www.postgresql.org/docs/current/textsearch.html
* FP_LOCK_SLOTS_PER_BACKEND in Postgres 
* LWLock:lock_manager (Amazon RDS docs) https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/wait-event.lw-lock-manager.html 
