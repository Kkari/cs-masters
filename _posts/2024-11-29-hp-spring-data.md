---
title: "High Performance Spring Data Workshop"
date: 2024-11-28
---
## Intro
Recently I have taken part in a high-performance Spring Data JPA workshop with Vlad Mihalcea, it was amazing!
At first I was a bit worried that it will be too basic, but it actually assumed the basics, 
over 4 hours I learned a lot about optimising fetching logic in Hibernate and Spring Data JPA.

I can only recommend it to anyone who is interested in the topic. :) 

Link: https://hypersistence.teachable.com/p/high-performance-spring-persistence-online-workshop

## Notes
Fetching:
    - Postgres fetches everything at once by default, Oracle needs tuning, but it is usually not suchan interesting problem.
    - FindAll is evil. 
    - OSIV is evil.
    - Interface based projections are good to save adata. Records can be used as well.
    - Interface based projections are good to save data both at fetching time and at query processing. The less attributes are present the more optimised the query can be.
    - Pagination is not working with JOIN FETCH, Hibernate  siletnly queries all items and filters in memory. Use hibernate.query.fail_on_pagination_over_collection_fetch to catch it. Use inner subquery to prevent it.
    

ResultStreams:
    - JPA 2.2 getResultStream can avoid prefetching everything. You have to set the statement fetch size here to avoid prefetching everything. Use @QueryHints to set it.
    - The problem with ResultStreams is that they hold the cursor open, constatly pulling DB resources, if possible, then paging is usually a better idea. Preferably keyset based.


Q&A:
    - Does that break java collections if people used the default hashcode and equals methods?
        ○ Yes, if you have an unmanaged collection and you call saved on a managed entity that has the default eqhc implementation, then it can data corruption in memory.
    - Does Spring Data issues a real merge when entities are already managed by Hibernate? 
        ○ Yes, calling save on a managed entity really executes a full merge of the entity unecessarily. It took 11ms on Vlads computer. 
    - Do you know a good talk or resource about Hibernate internals? 
        ○ No. :(
    - Does the OneToOne and ManyToOne only becomese Lazy if optional = false?
        ○ Only for 1:1 and mappedBy on the parent side. 
    

Further Study:
    - ORM Architecture https://aosabook.org/en/v2/sqlalchemy.html
    - Different Spring Data repositories: https://www.baeldung.com/spring-data-repositories
    - Does keyset pagination work with both composite and separate indexes? Like: BT(createdAt,Id) and BT(createdAt), BT(id)
    - How does that impact the performance of keyset pagination if the ID is UUIDv4 instead of SERIAL?
    - How does index merging work?
    - For interface based projections look at the Hypersistence utils and creating records in the HQL.
    - What is a stateless session in Spring?
    
