# API Gateway

API Gateway provides a single entry point into the system. 

## Capabilities

- Routes request to downstream services
- _Protocol translation_
- Provides edge services like authentication, authorization, monitoring, audit, logging, caching etc.
- Performs API composition

## Variations

A separate API Gateway can be created per client since different client have different demands. This pattern is called _Backends for frontends (BFF)_.
This also enabled separate teams to work on the specific API gateway thus making team independent and more scalable.

## Benefits

- Greater encapsulation of internal services
- Simpler client code
- BFF breaks dependencies between team thus increasing delivery speed

## Drawbacks

- Must be highly available, performant and scalable
- May become a development bottleneck

### Reading List

- Reactive programming for API composition