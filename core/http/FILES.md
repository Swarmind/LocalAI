# core/http/app.go  
Package: http  
  
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
  
# core/http/explorer.go  
## Package: http  
  
Imports:  
- "net/http"  
- "github.com/gofiber/fiber/v2"  
- "github.com/gofiber/fiber/v2/middleware/favicon"  
- "github.com/gofiber/fiber/v2/middleware/filesystem"  
- "github.com/mudler/LocalAI/core/explorer"  
- "github.com/mudler/LocalAI/core/http/middleware"  
- "github.com/mudler/LocalAI/core/http/routes"  
  
External data, input sources:  
- The code uses a database instance from the "explorer" package.  
  
TODOs:  
- There are no TODO comments in the provided code.  
  
### Explorer function  
This function sets up and configures a Fiber application for the explorer component. It registers routes, sets up middleware, and handles static files. The function takes a database instance as input and returns the configured Fiber application.  
  
### Fiber configuration  
The code configures a Fiber application with custom settings, such as disabling the startup message and overriding the default error handler. It also sets up a custom view engine.  
  
### Middleware  
The code registers middleware to strip the path prefix and handle static files. It also includes a custom 404 handler.  
  
### Static file handling  
The code sets up middleware to serve static files from the embedded directory. It also includes a favicon handler.  
  
### Route registration  
The code registers routes for the explorer component using the "routes" package. These routes handle requests related to the explorer functionality.  
  
### Custom 404 handler  
The code defines a custom 404 handler to handle requests for non-existent resources. This handler is registered as the last middleware in the application.  
  
### Return value  
The function returns the configured Fiber application, which can be used to handle incoming requests.  
  
# core/http/render.go  
Package: http  
  
Imports:  
embed  
fmt  
html/template  
net/http  
github.com/Masterminds/sprig/v3  
github.com/gofiber/fiber/v2  
github.com/gofiber/template/html/v2  
github.com/microcosm-cc/bluemonday  
github.com/mudler/LocalAI/core/http/utils  
github.com/mudler/LocalAI/core/schema  
github.com/russross/blackfriday  
  
External data, input sources:  
- Views directory (viewsfs) containing HTML templates.  
  
TODOs:  
- None found.  
  
Summary:  
The http package provides functionality for handling HTTP requests and rendering HTML templates. It includes a custom 404 handler that returns a JSON response if the client accepts JSON or an HTML response if the client accepts HTML. The package also defines a custom template engine that uses Sprig's template functions and a Markdown-to-HTML converter.  
  
- The notFoundHandler function handles 404 errors by returning a JSON or HTML response depending on the client's preferences.  
- The renderEngine function creates a new Fiber template engine that uses the views directory as the source for templates. It also adds Sprig's template functions and a custom Markdown-to-HTML converter to the engine.  
- The markDowner function converts Markdown text to HTML using the Blackfriday library and sanitizes the output using the Bluemonday library.  
  
  
  
