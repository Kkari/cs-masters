---
title: "Value Proposition of Hibernate and the journey to learn it"
date: 2024-12-09
---

I spent a fair amount of time to learn Hibernate in the past 2 months. I went from the generic concepts to the source code and the construction of an ORM system. 

In the meanwhile I have come to appreciate the elegance of good old Hibernate. There is just 20 years of engineering in it. It made me reflect why people hate on Hibernate so much. I think they misunderstand the value proposition of an ORM. 

People think that you don't have to understand SQL or the RDBMS if you use an ORM. This is false, ohhh boy this is false. Especially with Hibernate you have to understand it because another layer of software complexity is added to the stack, adding some funky twists on top of isolation and fetching behaviour. Like the way the PersistenceContext makes already loaded entity behave as REPEATABLE_READ in the session even if the isolation is actually READ_COMMITTED.

I believe the actual value proposition of hibernate is:

---
#### Hibernate makes the team significatly faster, given that there is at least one person on the team who understands both Hibernate and the RDBMS on a good level. God save you if that person is not present though.
---

That is because Hibernate takes care of many sensible optimisations for enterprise software, for example maintaining an identity map, or flushing in the right order. But on the other hand, all these sensible optimisations have their limits and edge cases that the team has to be aware of to safely operate Hibernate, or probably any ORM for that matter.

### How to learn Hibernate?
I think the best way to learn Hibernate is to: 
1. Understand the basic concepts.
2. Learn to use it efficiently.
3. Learn how an ORM works internally. (And the JDBC driver for that matter.)

* I found for the basic concepts the "Architecture" part of the documentation pretty good.
* A very good resource to learn Hibernate on an advanced user level was the "High-Performance JPA" Course from Vlad Michalcea: https://vladmihalcea.com/courses/high-performance-java-persistence/
* There are no good resources to directly learn the Hibernate architecture, but there is one for SqlAlchemy in Python and it was inspired by Hibernate! I advise reading that amazing chapter, going through the Hibernate source and thinking about how concepts releate to each other in both frameworks. It really helped me to solidify my understanding of ORMs: https://aosabook.org/en/v2/sqlalchemy.html

That's it for now :)