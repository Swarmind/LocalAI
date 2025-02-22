## Package: cli

This package provides command-line interface functionality for the LocalAI application.

### External Data and Input Sources

The code interacts with the following external data sources and input sources:

1. Configuration files: The application reads configuration files to set various parameters and options.
2. Environment variables: The application uses environment variables to override default settings and customize behavior.
3. Command-line arguments: The application accepts command-line arguments to control its operation.
4. Network connections: The application establishes network connections to communicate with other instances of LocalAI and external services.

### TODOs

There are no TODO comments in the provided code.

### Major Code Parts

1. RunCMD struct: This struct defines the command-line options and parameters for the LocalAI application. It includes options for configuring the application, such as setting the model path, enabling P2P mode, and specifying API keys.

2. Run method: This method is responsible for starting the LocalAI application and handling the command-line options. It initializes the application, sets up the P2P stack, and starts the HTTP server.

3. Configuration options: The code includes a number of configuration options that can be set through command-line arguments, environment variables, or configuration files. These options control various aspects of the application, such as the model path, P2P settings, and API keys.

4. P2P stack: The code includes functionality for starting and managing the P2P stack, which allows LocalAI instances to communicate with each other. This includes generating and managing P2P tokens, setting up the DHT, and handling incoming and outgoing connections.

5. HTTP server: The code includes functionality for starting and managing the HTTP server, which provides the API for interacting with the LocalAI application. This includes handling API requests, managing sessions, and serving static content.

6. Watchdog: The code includes functionality for monitoring the health of backends and taking action if they become unresponsive. This includes setting timeouts for idle and busy backends, and restarting them if necessary.

7. External backends: The code includes functionality for interacting with external backends, such as those provided by third-party services. This includes configuring the connection to the external backend and handling communication with it.

8. Galleries: The code includes functionality for managing galleries of images and other content. This includes loading galleries from configuration files, enabling galleries to be auto-loaded, and providing an API for accessing and manipulating galleries.

9. API keys: The code includes functionality for managing API keys, which can be used to authenticate requests to the LocalAI API. This includes setting up API keys, checking for valid API keys, and handling API key-related errors.

10. Parallel requests: The code includes functionality for enabling parallel requests to backends, which can improve performance by allowing multiple requests to be processed simultaneously.

11. Single active backend: The code includes functionality for enabling a single active backend, which can be useful for testing and debugging purposes.

12. Load to memory: The code includes functionality for loading models into memory at startup, which can improve performance by reducing the time it takes to load models on demand.

13. Machine tag: The code includes functionality for adding a machine tag header to each response, which can be useful for tracking the machine in the P2P network.

14. Disable metrics endpoint: The code includes functionality for disabling the metrics endpoint, which can be useful for security purposes.

15. Disable gallery endpoint: The code includes functionality for disabling the gallery endpoint, which can be useful for security purposes.

16. Disable API key requirement for HTTP GET: The code includes functionality for disabling the API key requirement for HTTP GET requests, which can be useful for testing purposes.

17. HTTP GET exempted endpoints: The code includes functionality for specifying a list of endpoints that are exempt from the API key requirement for HTTP GET requests.

18. Disable predownload scan: The code includes functionality for disabling the predownload scan, which can be useful for performance purposes.

19. Opaque errors: The code includes functionality for enabling opaque errors, which can be useful for hardening against information leaks.

20. Subtle key comparison: The code includes functionality for enabling subtle key comparison, which can be useful for hardening against timing attacks.

21. Disable API key requirement for HTTP GET: The code includes functionality for disabling the API key requirement for HTTP GET requests, which can be useful for testing purposes.

22. HTTP GET exempted endpoints: The code includes functionality for specifying a list of endpoints that are exempt from the API key requirement for HTTP GET requests.

23. Disable