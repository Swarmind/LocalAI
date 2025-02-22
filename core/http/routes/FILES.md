# core/http/routes/elevenlabs.go  
Package: routes  
  
Imports:  
- "github.com/gofiber/fiber/v2"  
- "github.com/mudler/LocalAI/core/config"  
- "github.com/mudler/LocalAI/core/http/endpoints/elevenlabs"  
- "github.com/mudler/LocalAI/core/http/middleware"  
- "github.com/mudler/LocalAI/core/schema"  
- "github.com/mudler/LocalAI/pkg/model"  
  
External data, input sources:  
- The code uses the `config.BackendConfigLoader` to load backend configuration.  
- It uses the `model.ModelLoader` to load models.  
- It uses the `config.ApplicationConfig` to access application-wide configuration.  
  
TODOs:  
- There are no TODO comments in the code.  
  
Summary:  
- The `RegisterElevenLabsRoutes` function registers routes for ElevenLabs endpoints.  
- It sets up two endpoints: one for text-to-speech and one for sound generation.  
- For each endpoint, it uses middleware to filter and select the appropriate model based on the use case.  
- It then calls the corresponding endpoint handler function from the `elevenlabs` package.  
  
  
  
# core/http/routes/explorer.go  
Package/Component name: routes  
  
Imports:  
- "github.com/gofiber/fiber/v2"  
- "github.com/mudler/LocalAI/core/explorer"  
- "github.com/mudler/LocalAI/core/http/endpoints/explorer"  
  
External data, input sources:  
- The code interacts with a database instance of type coreExplorer.Database, which is passed as an argument to the RegisterExplorerRoutes function.  
  
TODOs:  
- There are no TODO comments in the provided code.  
  
Summary of major code parts:  
- The RegisterExplorerRoutes function registers routes for the explorer component. It takes an instance of a fiber.App and a coreExplorer.Database as input.  
- The function registers three routes:  
    - A GET route at "/" that returns the explorer dashboard.  
    - A POST route at "/network/add" that adds a new network to the database.  
    - A GET route at "/networks" that shows a list of networks in the database.  
  
  
  
# core/http/routes/health.go  
Package/Component name: routes  
  
Imports:  
github.com/gofiber/fiber/v2  
  
External data, input sources:  
None  
  
TODOs:  
None  
  
Summary:  
The `HealthRoutes` function in the `routes` package is responsible for setting up health check endpoints for a service. It defines two endpoints, `/healthz` and `/readyz`, which return a 200 OK status code when accessed. These endpoints can be used by monitoring systems to check the health and readiness of the service.  
  
The function takes an instance of the Fiber web framework's `App` struct as input, which represents the application's router. It then registers two GET routes, one for each health check endpoint, using the `app.Get` method. The `ok` function is used as the handler for both endpoints, which simply returns a 200 OK status code to the client.  
  
By providing these health check endpoints, the `HealthRoutes` function enables monitoring systems to easily determine the status of the service and ensure that it is functioning correctly.  
  
  
  
# core/http/routes/jina.go  
Package: routes  
  
Imports:  
- "github.com/mudler/LocalAI/core/config"  
- "github.com/mudler/LocalAI/core/http/endpoints/jina"  
- "github.com/mudler/LocalAI/core/http/middleware"  
- "github.com/mudler/LocalAI/core/schema"  
- "github.com/gofiber/fiber/v2"  
- "github.com/mudler/LocalAI/pkg/model"  
  
External data, input sources:  
- The code uses the `config.BackendConfigLoader` to load backend configuration.  
- It uses the `model.ModelLoader` to load models.  
- It uses the `config.ApplicationConfig` to access application-wide configuration.  
  
TODOs:  
- There are no TODO comments in the code.  
  
Summary:  
The `RegisterJINARoutes` function registers a POST endpoint for reranking requests. It uses the provided `RequestExtractor`, `BackendConfigLoader`, `ModelLoader`, and `ApplicationConfig` to handle the request and perform the reranking operation. The endpoint is designed to mimic the behavior of the JINA framework.  
  
  
  
# core/http/routes/localai.go  
Package/Component name: routes  
  
Imports:  
- "github.com/gofiber/fiber/v2"  
- "github.com/gofiber/swagger"  
- "github.com/mudler/LocalAI/core/config"  
- "github.com/mudler/LocalAI/core/http/endpoints/localai"  
- "github.com/mudler/LocalAI/core/http/middleware"  
- "github.com/mudler/LocalAI/core/p2p"  
- "github.com/mudler/LocalAI/core/schema"  
- "github.com/mudler/LocalAI/core/services"  
- "github.com/mudler/LocalAI/internal"  
- "github.com/mudler/LocalAI/pkg/model"  
  
External data, input sources:  
- The code uses the following external data sources:  
    - Configuration settings from the config package  
    - Model information from the model package  
    - Application configuration from the applicationConfig object  
    - Gallery information from the galleryService object  
  
TODOs:  
- TODO: Should these use standard middlewares? Refactor later, they are extremely simple.  
  
Summary:  
- The RegisterLocalAIRoutes function registers various API endpoints for the LocalAI application.  
- It handles endpoints related to model galleries, text-to-speech, voice activity detection, stores, backend statistics, p2p, version, system information, and tokenization.  
- The function uses middleware to extract request information and set model and configuration details.  
- It also leverages services and endpoints from other packages to provide functionality for the LocalAI application.  
- The code includes a TODO comment suggesting that certain endpoints might benefit from using standard middlewares for improved maintainability.  
  
  
  
# core/http/routes/openai.go  
## Package/Component: routes  
  
This file is part of the `routes` package, which handles the registration of API routes for the application.  
  
### External Data and Input Sources  
  
The code relies on several external data sources and input sources, including:  
  
1. The `application.ApplicationConfig()` function, which provides configuration settings for the application.  
2. The `application.BackendLoader()`, `application.ModelLoader()`, and `application.TemplatesEvaluator()` functions, which interact with the backend, model, and template systems, respectively.  
3. The `config.FLAG_CHAT`, `config.FLAG_EDIT`, `config.FLAG_COMPLETION`, and `config.FLAG_EMBEDDINGS` constants, which define the use cases for the models.  
  
### TODOs  
  
There are no TODO comments in the code.  
  
### Summary of Major Code Parts  
  
1. **OpenAI API Endpoint Registration:** The `RegisterOpenAIRoutes` function registers API endpoints for the openAI compatible API. This includes endpoints for chat, edit, completion, assistant, files, embeddings, audio, and images.  
  
2. **Request Handling:** The code uses middleware to handle incoming requests, such as filtering models based on use case, setting default model names, and setting the openAI request object.  
  
3. **Endpoint Implementation:** Each endpoint is implemented using functions from the `openai` and `localai` packages, which interact with the backend, model, and template systems to process the request and return the response.  
  
4. **Static File Serving:** The code serves static files for generated images and audio, if the corresponding directories are configured.  
  
5. **Model Listing:** The code provides an endpoint to list available models.  
  
In summary, this file handles the registration and implementation of API endpoints for the openAI compatible API, including request handling, endpoint implementation, and static file serving.  
  
# core/http/routes/ui.go  
## Package: routes  
  
This package handles the routing and serving of web pages for the LocalAI application. It registers various endpoints for different functionalities, such as displaying models, managing installations, and providing access to chat and text-to-image generation features.  
  
### External Data and Input Sources  
  
The package relies on several external data sources and input sources to function correctly:  
  
1. `config.BackendConfigLoader`: This is used to load and manage backend configurations for models.  
2. `model.ModelLoader`: This is used to load and manage models.  
3. `config.ApplicationConfig`: This contains the application-wide configuration settings.  
4. `services.GalleryService`: This service is responsible for managing the gallery of available models.  
  
### TODOs  
  
1. Implement a mechanism to dismiss the job status display when the job is done.  
  
### Major Code Parts  
  
1. `modelOpCache`: This struct is used to keep track of the status of models being processed (installation or deletion). It stores a map of model names to their corresponding status and provides methods to set, get, and delete entries.  
  
2. `RegisterUIRoutes`: This function registers all the necessary routes for the UI. It sets up endpoints for displaying models, managing installations, and providing access to chat and text-to-image generation features.  
  
3. `modelStatus`: This function returns the current status of models being processed (installation or deletion). It is called asynchronously from the UI to update the progress of ongoing jobs.  
  
4. `WelcomeEndpoint`: This function handles the welcome page, displaying information about the application and available models.  
  
5. `P2P-related endpoints`: These endpoints handle the P2P dashboard, showing nodes, statistics, and other related information.  
  
6. `Browse endpoint`: This endpoint displays the models page, allowing users to search, filter, and install models.  
  
7. `Installation and deletion endpoints`: These endpoints handle the installation and deletion of models, interacting with the gallery service to manage the process.  
  
8. `Chat and text-to-image endpoints`: These endpoints provide access to chat and text-to-image generation features, allowing users to interact with their models.  
  
9. `Text-to-speech endpoints`: These endpoints provide access to text-to-speech functionality, allowing users to generate audio from their models.  
  
### Summary  
  
The `routes` package plays a crucial role in the LocalAI application by handling the routing and serving of web pages. It provides a user-friendly interface for managing models, accessing various functionalities, and interacting with the application's core components.  
  
