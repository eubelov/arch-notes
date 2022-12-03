# CQRS

CQRS is a pattern for separating data modification operations (writes, updates, deletes) from read. Separate services backing their own data stores handle the two concerns. The data stores are kept up-to-date by means of data propagation events or event sourcing.

## Problems with API Aggregation Pattern

1. Joining large set of data in memory is inefficient
2. Service's data store is not always optimized for the required query (i.e. geospatial)
3. Service does not (an cannot) support the required query at all (the service implements a different business concern or is not optimized for potentially high throughput)

## CQRS Implementation 

With CQRS, two data stores are used - one for writes, deletes and updates, and a separate store (or stores) for reads.
The command side publishes event (data propagation) whenever data in its store changes; the query side has a handler that subscribes to these events thus keeping the read data store in sync.

The query side should be optimized for the types of queries it handles. It usually handles complex queries, while simple primary key bases queries can still be handled by the command side.

## Query-only Services

The sole purpose of this flavour of service is to implement efficient query operations. It can subscribe to events from multiple services and maintain _materialized views_ that the queries are executed against. This kind of service does not belong to any service so it always makes sense to implement is as a standalone service.

> CQRS is an event-based generalization of the popular approach of using RDBMS as the system of record and a text search engine, such as Elasticsearch, to handle text queries.

## Idempotent Updates

Since the same event may be delivered more than once, updates should be idempotent.

If non-idempotent handlers are required (e.g. increment of the account balance), data store must store IDs of processed events and discard duplicated events.
Data store must be updated atomically! In RDBMS, transactions must be used. In NoSQL with limited transactional capability, event IDs should be save in the record that is being updated.

## Benefits

- Allows for efficient querying of data that is owned by multiple services
- Allows for using multiple data sources for different types of queries
- Makes queries possible in event-sourcing applications as event stores only support PK-based queries
- Improves separation on concerns

## Drawbacks

- More complex architecture (different types of data store, messaging infrastructure)
- Data inconsistency due to the replication lag

> 💡 The API Aggregation pattern should be used whenever possible and use CQRS only when you must. 