Funny thing is that I realised today, with a standard hibernate - PG stack you have the cached data 4 times in memory:
Hibernate entity manager
Hibernate 1st level cache for dirty checking.
Postgres Buffer Pool for page cacheing.
OS Page cache for file system operations.
 
You can cut it to half by:
@Transactional(readonly = true) disables the hibernate cache for dirty checking.
Choosing a database that uses direct IO, therefore skipping the OS Page cache.  
 