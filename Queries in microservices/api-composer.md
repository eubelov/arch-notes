# API Composition Pattern

The API Composer stitches together responses from multiple _data providers_ and return an aggregated response to the client.

The pattern can be implemented in different places, for example:
- The web client itself invokes downstream services and aggregates the responses. This is acceptable if the client runs inside the firewall where LAN is fast.
- API Gateway
- Standalone service

## Benefits:
- Easy to understand and implement

## Drawbacks:
- Increased overhead
- Risk of reduced availability
- Lack of transactional data consistency
- Potentially large memory usage when joining large datasets in memory

## Considerations:
- The Reactive Programming paradigm can be used to fetch data from _data providers_ 
- Use caching where applicable
- Return *partial* responses if one of the _data providers_ fails