# Microservices Architecture Challenges

Since microservices is a distributed architecture, one of the biggest challenges is how to implement transactions that span multiple databases and/or message brokers.
While local transactions can be ACID, transactions between multiple services cannot.

One possible solution is Two-phase commits (2PC), however they have several significant drawbacks:
- 2PCs are not supported by many modern databases and message brokers
- 2PCs reduce the overall availability of the system due to their synchronous nature
