---
title: "Explaining Postgres"
date: 2024-11-05
---

I had the idea to approach the databases topic from multiple angles to get a deeper understanding of what is happening inside the system: 
1. Analyze queries and workloads running on Postgres.
2. Be able to write high-performance SQL.
3. Understand the inner workings of the database. 
4. Get an overview of advanced database internals.
5. Understand how Hibernate and other ORM softwares are built and how they interoperate with the database.

I believe all of these will provide me a deep understanding to optimise enterprise applications for databases.

Analysing queries is very much a DBA topic, but I was always fascinated by the query plan and I wanted to understand it deeply. I believe it is also a good entry point into the topic. 

Thankfully, I found an amazing series of 6 entries from depesz.com about explaining the unexplainable, so the [Postgres query plan.](https://www.depesz.com/2013/04/16/explaining-the-unexplainable/)

I can only recommend this series to anyone who wants to go through a similar journey and be able to understand what are the different operations Postgres executes under the hood. It takes a few hours to read through them and try them out. 

In that you will learn:
1. Cost calculations for a query and glean the amount of data planned for processing.
2. It is a good conversation entry for different operations, like HashAggregate or Seq Scan or BitMaps.
3. Undestanding the [stats](https://www.depesz.com/2013/05/30/explaining-the-unexplainable-part-5/) and buffers Postgres uses under the hood for different queries.

It they make the database feel closer than just a logical interface to execute SQL queries against.

A good extension was [this](https://www.depesz.com/2011/07/03/understanding-postgresql-conf-work_mem/) article about understanding the postgres work_mem. Generally the entire blog is a goldmine of information on Posgres.