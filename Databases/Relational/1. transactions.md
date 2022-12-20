# Isolation levels

## Dirty Read

Read uncommitted changes of the other transaction.

> Does not happen in PostgreSQL on any isolation level

## Lost Update

The first transaction reads data into its local memory, and the second transaction changes this data and commits its change.
After this, the first transaction updates the same data. In this cases, the updated performed by the second transaction is a lost update.

## Non-Repeatable Read

One of the rows you've queried at different stage of transaction may be updated by other transactions.

