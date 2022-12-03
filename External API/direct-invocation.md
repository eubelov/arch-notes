# Direct Invocation

Clients have knowledge about all services and which portion of  data they hold, and invoke the services that provide data necessary for the current operation.

## Benefits
- Easy to implement
- Can be used by client in LAN

## Drawbacks
- Poor user experience for clients on slow networks
- Lack of encapsulation may result in lock-step releases of frontend and backend
- Services might use client-unfriendly protocols (e.g. gRPC)
- Third-party consumers may be unwilling to update their existing integration when the contracts of a service changes