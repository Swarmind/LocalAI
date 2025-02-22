## Package: p2p

This package provides functionality for peer-to-peer (P2P) communication and service discovery. It includes functions for generating connection data, managing nodes, and handling P2P connections.

### External Data and Input Sources:

- Environment variables: The package reads environment variables to configure its behavior, such as the network token, listen addresses, and bootstrap peers.
- Ledger: The package interacts with a distributed ledger to store and retrieve information about nodes and services.

### TODOs:

- Ensure that the discoveryTunnels function returns all the nodes and addresses associated with it.
- Add a function to check if workers are online and cancel the context of allocateLocalService if they are not.
- Implement a mechanism to keep track of the last seen time for each node.

### Major Code Parts:

1. Connection Data Generation:
   - The `generateNewConnectionData` function generates a new connection configuration with random keys and intervals for the DHT and OTP protocols.
   - The `GenerateToken` function generates a token based on the provided DHT and OTP intervals.

2. Node Management:
   - The `NewNode` function creates a new node with the given token and configuration options.
   - The `newNodeOpts` function prepares the node options based on the provided token and environment variables.

3. Service Discovery:
   - The `ServiceDiscoverer` function starts a goroutine that keeps the LLAMACPP_GRPC_SERVERS environment variable updated with the discovered services.
   - The `discoveryTunnels` function retrieves new services from the ledger and allocates them if necessary.
   - The `ensureService` function ensures that a service is running and updates its status in the ledger.

4. P2P Connection Handling:
   - The `proxyP2PConnection` function handles incoming connections and redirects them to the appropriate service.
   - The `allocateLocalService` function allocates a local service and listens for incoming connections.

5. Utility Functions:
   - The `nodeID` function generates a unique ID for a node based on its hostname and a given string.
   - The `nodeAnnounce` function announces the node's presence on the network.
   - The `copyStream` function copies data between two streams.

6. Main Function:
   - The `ExposeService` function exposes a service on the given host and port, registers it with the ledger, and starts the node.

This package provides a comprehensive set of tools for managing P2P connections and service discovery. It is designed to be flexible and configurable, allowing users to tailor its behavior to their specific needs.

### File Structure:

- core/p2p/federated.go
- core/p2p/federated_server.go
- core/p2p/node.go
- core/p2p/p2p.go
- core/p2p/p2p_common.go
- core/p2p/p2p_disabled.go

### Relations between Code Entities:

The code entities in this package are closely related and work together to provide a complete P2P solution. The `FederatedServer` struct and its associated functions handle the management of nodes and services, while the `ServiceDiscoverer` and `ExposeService` functions enable the discovery and registration of services on the network. The `NewNode` function creates new nodes, and the `proxyP2PConnection` function handles incoming connections.

### Unclear Places:

- The purpose of the `p2p_disabled.go` file is not entirely clear, as it contains functions that seem to be related to the P2P functionality but are marked as disabled. It is possible that this file is intended for testing or debugging purposes, or that it contains code that is not yet implemented.

### Dead Code:

- The `p2p_disabled.go` file contains several functions that are marked as disabled, which may indicate that they are no longer in use or are considered experimental.

### Edge Cases:

- If the environment variables required by the package are not set, the package may not function correctly.
- If the ledger is unavailable, the package may be unable to discover or register services.