## Package: http

Imports:
- "embed"
- "errors"
- "fmt"
- "net/http"
- "github.com/dave-gray101/v2keyauth"
- "github.com/mudler/LocalAI/pkg/utils"
- "github.com/mudler/LocalAI/core/http/endpoints/localai"
- "github.com/mudler/LocalAI/core/http/endpoints/openai"
- "github.com/mudler/LocalAI/core/http/middleware"
- "github.com/mudler/LocalAI/core/http/routes"
- "github.com/mudler/LocalAI/core/application"
- "github.com/mudler/LocalAI/core/schema"
- "github.com/mudler/LocalAI/core/services"
- "github.com/gofiber/contrib/fiberzerolog"
- "github.com/gofiber/fiber/v2"
- "github.com/gofiber/fiber/v2/middleware/cors"
- "github.com/gofiber/fiber/v2/middleware/csrf"
- "github.com/gofiber/fiber/v2/middleware/favicon"
- "github.com/gofiber/fiber/v2/middleware/filesystem"
- "github.com/gofiber/fiber/v2/middleware/recover"
- "github.com/rs/zerolog/log"

External data, input sources:
- Configuration settings from the application config.
- Uploaded files and configuration files from the file system.

TODOs:
- Add support for custom error handlers.

Summary:
- The `API` function sets up and configures a Fiber web server for the LocalAI application.
- It handles various configurations, such as error handling, CORS, and CSRF protection.
- The function registers routes for different API endpoints, including health checks, ElevenLabs, LocalAI, OpenAI, and the web UI.
- It also serves static files and handles 404 errors.
- The function returns the configured Fiber app and any errors encountered during setup.

- The `explorer` function sets up and configures a Fiber application for the explorer component. It registers routes, sets up middleware, and handles static files. The function takes a database instance as input and returns the configured Fiber application.

- The `renderEngine` function creates a new Fiber template engine that uses the views directory as the source for templates. It also adds Sprig's template functions and a custom Markdown-to-HTML converter to the engine.

- The `notFoundHandler` function handles 404 errors by returning a JSON or HTML response depending on the client's preferences.

- The `markDowner` function converts Markdown text to HTML using the Blackfriday library and sanitizes the output using the Bluemonday library.

- The `utils` package provides utility functions for the http package, such as converting Markdown to HTML and handling 404 errors.

- The `routes` package defines the routes for the application, including health checks, ElevenLabs, LocalAI, OpenAI, and the web UI.

- The `middleware` package provides middleware for the application, such as CORS, CSRF protection, and favicon handling.

- The `endpoints` package contains the endpoints for the application, including ElevenLabs, LocalAI, OpenAI, and the web UI.

- The `elements` package contains the UI elements for the application, such as buttons, progress bars, and galleries.

- The `views` package contains the HTML templates for the application.

- The `static` package contains the static files for the application, such as CSS, JavaScript, and images.

- The `explorer` package provides the functionality for the explorer component.

- The `schema` package defines the data models for the application.

- The `services` package provides the services for the application, such as authentication and authorization.

- The `application` package contains the main application logic.

- The `utils` package provides utility functions for the application.

- The `pkg/utils` package provides utility functions for the LocalAI project.

- The `v2keyauth` package provides the key authentication functionality.

- The `core/http/app.go` file contains the main function for the http package, which sets up and configures the Fiber web server.

- The `core/http/explorer.go` file contains the function for setting up and configuring the Fiber application for the explorer component.

- The `core/http/render.go` file contains the functions for rendering HTML templates and handling 404 errors.

- The `core/http/utils/baseurl.go` file contains the function for getting the base URL of the application.

- The `core/http/utils/baseurl_test.go` file contains the unit tests for the base URL function.

- The `core/http/routes/elevenlabs.go` file contains the routes for the ElevenLabs endpoint.

- The `core/http/routes/explorer.go` file contains the routes for the explorer endpoint.

- The `core/http/routes/health.go` file contains the routes for the health check endpoint.

- The `core/http/routes/jina.go` file contains the routes for the Jina endpoint.

- The `core/http/routes/localai.go` file contains the routes for the LocalAI endpoint.

- The `core/http/routes/openai.go` file contains the routes for the OpenAI endpoint.

- The `core/http/routes/ui.go` file contains the routes for the web UI endpoint.

- The `core/http/endpoints/localai/backend_monitor.go` file contains the endpoint for monitoring the LocalAI backend.

- The `core/http/endpoints/localai/gallery.go` file contains the endpoint for the LocalAI gallery.

- The `core/http/endpoints/localai/get_token_metrics.go` file contains the endpoint for getting token metrics.

- The `core/http/endpoints/localai/metrics.go` file contains the endpoint for getting metrics.

- The `core/http/endpoints/localai/p2p.go` file contains the endpoint for the LocalAI P2P connection.

- The `core/http/endpoints/localai/stores.go` file contains the endpoint for the LocalAI stores.

- The `core/http/endpoints/localai/system.go` file contains the endpoint for the LocalAI system.

- The `core/http/endpoints/localai/tokenize.go` file contains the endpoint for tokenizing text.

- The `core/http/endpoints/localai/tts.go` file contains the endpoint for the LocalAI TTS functionality.

- The `core/http/endpoints/localai/vad.go` file contains the endpoint for the LocalAI voice activity detection.

- The `core/http/endpoints/localai/welcome.go` file contains the endpoint for the LocalAI welcome message.

- The `core/http/endpoints/openai/assistant.go` file contains the endpoint for the OpenAI assistant.

- The `core/http/endpoints/openai/assistant_test.go` file contains the unit tests for the OpenAI assistant endpoint.

- The `core/http/endpoints/openai/chat.go` file contains the endpoint for the OpenAI chat functionality.

- The `core/http/endpoints/openai/completion.go` file contains the endpoint for the OpenAI completion functionality.

- The `core/http/endpoints/openai/edit.go` file contains the endpoint for the OpenAI edit functionality.

- The `core/http/endpoints/openai/embeddings.go` file contains the endpoint for the OpenAI embeddings functionality.

- The `core/http/endpoints/openai/files.go` file contains the endpoint for the OpenAI files functionality.

- The `core/http/endpoints/openai/files_test.go` file contains the unit tests for the OpenAI files endpoint.

- The `core/http/endpoints/openai/image.go` file contains the endpoint for the OpenAI image functionality.

- The `core/http/endpoints/openai/inference.go` file contains the endpoint for the OpenAI inference functionality.

- The `core/http/endpoints/openai/list.go` file contains the endpoint for the OpenAI list functionality.

- The `core/http/endpoints/openai/transcription.go` file contains the endpoint for the OpenAI transcription functionality.

- The `core/explorer/dashboard.go` file contains the dashboard functionality for the explorer component.

- The `core/explorer/index.go` file contains the index functionality for the explorer component.

- The `core/explorer/models.go` file contains the models for the explorer component.

- The `core/explorer/partials/footer.go` file contains the footer functionality for the explorer component.

- The `core/explorer/partials/head.go` file contains the head functionality for the explorer component.

- The `core/explorer/partials/inprogress.go` file contains the in progress functionality for the explorer component.

- The `core/explorer/partials/navbar.go` file contains the navbar functionality for the explorer component.

- The `core/explorer/partials/navbar_explorer.go` file contains the navbar explorer functionality for the explorer component.

- The `core/explorer/views/404.html` file contains the 404 page for the explorer component.

- The `core/explorer/views/chat.html` file contains the chat page for the explorer component.

- The `core/explorer/views/explorer.html` file contains the explorer page for the explorer component.

- The `core/explorer/views/index.html` file contains the index page for the explorer component.

- The `core/explorer/views/login.html` file contains the login page for the explorer component.

- The `core/explorer/views/models.html` file contains the models page for the explorer component.

- The `core/explorer/views/p2p.html` file contains the p2p page for the explorer component.

- The `core/explorer/views/partials/footer.html` file contains the footer partial for the explorer component.

- The `core/explorer/views/partials/head.html` file contains the head partial for the explorer component.

- The `core/explorer/views/partials/inprogress.html` file contains the in progress partial for the explorer component.

- The `core/explorer/views/partials/navbar.html` file contains the navbar partial for the explorer component.

- The `core/explorer/views/partials/navbar_explorer.html` file contains the navbar explorer partial for the explorer component.

- The `core/explorer/views/talk.html` file contains the talk page for the explorer component.

- The `core/explorer/views/text2image.html` file contains the text2image page for the explorer component.

- The `core/explorer/views/tts.html` file contains the tts page for the explorer component.

- The `core/schema/schema.go` file contains the data models for the application.

- The `core/services/services.go` file contains the services for the application.

- The `core/application/application.go` file contains the main application logic.

- The `core/utils/utils.go` file contains utility functions for the application.

- The `pkg/utils/utils.go` file contains utility functions for the LocalAI project.

- The `v2keyauth/keyauth.go` file contains the key authentication functionality.

- The `v2keyauth/keyauth_test.go` file contains the unit tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The `v2keyauth/keyauth_suite_test.go` file contains the suite tests for the key authentication functionality.

- The