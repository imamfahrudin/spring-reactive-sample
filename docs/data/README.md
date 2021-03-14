# Reactive Data Operations

Spring Data also added Reactive Streams support into the existing projects.

NoSQL support, such as Redis, MongoDB, Couchbase and Cassandra are the first-class citizen in the WebFlux world.

RDBMS support, such as JDBC and JPA are designated for blocking access will not work under the new WebFlux applications. 

To resolve the problem, Spring team leads a new reactive specification [R2dbc](https://R2dbc.io) to access RDBMS. Similar to the JDBC specification, it provides a collection of standardized APIs and allow you to implement your own database drivers through `r2dbc-spi`.  Check the [R2dbc website](https://r2dbc.io/) for more info. 

Currently, MySQL(and MariaDB), MSSQL, Oracle, H2, PostgresSQL have got support.

## Reactive Repository

Similar to the existing `Repository` and it derived interfaces for blocking cases such as `PagingAndSortingRepository` and `CurdRepository`. Spring Data Commons add variants for reactive cases, such as `ReactiveSortingRepository` and `ReactiveCurdRepository`.

> Note: There is no `Paging` variant for reactive interfaces.

The Spring Data subprojects could have its specific top-level `Repository`, such as Spring Data Mongo provides `ReactiveMongoRepository`.

```java
@NoRepositoryBean
public interface ReactiveMongoRepository<T,ID>
extends ReactiveSortingRepository<T,ID>, ReactiveQueryByExampleExecutor<T>{...}
```

