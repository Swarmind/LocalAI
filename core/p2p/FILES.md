# core/p2p/federated.go  
Package: p2p  
  
Imports:  
- "fmt"  
- "math/rand/v2"  
- "sync"  
- "github.com/rs/zerolog/log"  
  
External data, input sources:  
- The code uses the `GetAvailableNodes` function, which is assumed to be defined elsewhere, to retrieve a list of available nodes for a given service.  
  
TODOs:  
- There are no TODO comments in the provided code.  
  
Summary:  
- The `FederatedServer` struct represents a server that handles requests for a federated service. It maintains a table of request counts for each node in the service and uses this information to select the least used server for a given request.  
- The `NetworkID` function takes a network ID and a service ID as input and returns a combined ID string.  
- The `RandomServer` method selects a random online server from the list of available nodes.  
- The `syncTableStatus` method updates the request table to reflect the current status of available nodes.  
- The `SelectLeastUsedServer` method selects the least used server from the request table.  
- The `RecordRequest` method increments the request count for a given node ID.  
- The `ensureRecordExist` method ensures that a record exists for a given node ID in the request table.  
  
  
  
# core/p2p/federated_server.go  
Package/Component name: p2p  
  
Imports:  
- context  
- errors  
- fmt  
- io  
- net  
- github.com/mudler/edgevpn/pkg/node  
- github.com/rs/zerolog/log  
  
External data, input sources:  
- p2ptoken: A token used for authentication and authorization in the p2p network.  
- service: The name of the service being proxied.  
- listenAddr: The address to listen on for incoming connections.  
- workerTarget: A specific worker node to target for connections.  
- loadBalanced: A flag indicating whether to use load balancing.  
  
TODOs:  
- Add support for TLS encryption.  
- Implement a mechanism for node discovery and registration.  
  
Summary:  
- The p2p package provides a p2p server implementation for the edgevpn project.  
- The FederatedServer struct is responsible for starting the p2p server and handling incoming connections.  
- The Start method initializes a new node, starts it, and then discovers other nodes in the network.  
- The proxy method listens for incoming connections and forwards them to the appropriate p2p node.  
- The sendHTMLResponse method sends a basic HTML response with a status code and a message.  
- The getHTTPStatusText method returns a textual representation of HTTP status codes.  
  
  
  
# core/p2p/node.go  
Package: p2p  
  
Imports:  
sync  
time  
  
External data, input sources:  
- The code uses a global map called 'nodes' to store information about available nodes. This map is accessed and modified by the functions in the package.  
  
TODOs:  
- There are no TODO comments in the provided code.  
  
Summary of major code parts:  
- The code defines a NodeData struct to store information about a node, including its name, ID, tunnel address, service ID, and last seen time.  
- It provides functions to get available nodes, get a specific node, and add a new node to the system.  
- The GetAvailableNodes function returns a list of available nodes for a given service ID. If no service ID is provided, it defaults to "services".  
- The GetNode function returns a specific node for a given service ID and node ID. If the node is not found, it returns an empty NodeData struct and false.  
- The AddNode function adds a new node to the system for a given service ID. If the service ID is not provided, it defaults to "services".  
  
  
  
# core/p2p/p2p.go  
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
  
# core/p2p/p2p_common.go  
Package name: p2p  
Imports:  
os  
strings  
  
External data, input sources:  
- Environment variable LOCALAI_P2P_LOGLEVEL is used to set the log level.  
  
TODOs:  
- There are no TODO comments in the provided code.  
  
Summary of major code parts:  
- The code defines a package-level variable logLevel, which is initialized to the value of the environment variable LOCALAI_P2P_LOGLEVEL. If the environment variable is not set, the log level defaults to "info".  
- The code defines two constants, logLevelDebug and logLevelInfo, which represent the possible values for the log level.  
- The init function is used to set the default log level if the environment variable is not set.  
  
  
  
# core/p2p/p2p_disabled.go  
Package name: p2p  
  
Imports:  
- context  
- fmt  
- github.com/mudler/edgevpn/pkg/node  
  
External data, input sources:  
- DHTInterval: An integer representing the interval for DHT updates.  
- OTPInterval: An integer representing the interval for OTP updates.  
- token: A string representing the authentication token.  
- servicesID: A string representing the ID of the services.  
- host: A string representing the host address.  
- port: A string representing the port number.  
  
TODOs:  
- Implement GenerateToken function.  
- Implement Start function.  
- Implement ServiceDiscoverer function.  
- Implement ExposeService function.  
- Implement NewNode function.  
  
Summary:  
The p2p package provides functionalities for peer-to-peer networking and service discovery. It includes functions for generating tokens, starting the federated server, discovering services, exposing services, and creating new nodes.  
  
- GenerateToken: This function generates a token for authentication and authorization.  
- Start: This function starts the federated server, which is responsible for managing the peer-to-peer network.  
- ServiceDiscoverer: This function discovers services on the network and provides their details to the caller.  
- ExposeService: This function exposes a service on the network, making it discoverable by other nodes.  
- IsP2PEnabled: This function checks if peer-to-peer networking is enabled.  
- NewNode: This function creates a new node in the peer-to-peer network.  
  
The p2p package is designed to work in conjunction with the node package, which provides the necessary data structures and functions for representing nodes in the network.  
  
  
  
