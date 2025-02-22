# core/application/application.go  
Package: application  
  
Imports:  
- "github.com/mudler/LocalAI/core/config"  
- "github.com/mudler/LocalAI/pkg/model"  
- "github.com/mudler/LocalAI/pkg/templates"  
  
External data, input sources:  
- The code uses the `config.BackendConfigLoader` to load backend configuration.  
- It uses the `model.ModelLoader` to load models.  
- It uses the `templates.Evaluator` to evaluate templates.  
  
TODOs:  
- There are no TODO comments in the provided code.  
  
Summary:  
The `application` package provides the main application object, which is responsible for managing the backend configuration, model loading, and template evaluation. The `Application` struct contains the necessary components for these tasks, such as the `backendLoader`, `modelLoader`, `applicationConfig`, and `templatesEvaluator`. The package also includes functions to access these components.  
  
The `newApplication` function creates a new instance of the `Application` struct, initializing the required components with the provided application configuration. The `BackendLoader`, `ModelLoader`, `ApplicationConfig`, and `TemplatesEvaluator` functions provide access to the corresponding components of the `Application` struct.  
  
This package is essential for the overall functionality of the LocalAI system, as it handles the core components required for the application to run.  
  
# core/application/config_file_watcher.go  
Package: application  
  
Imports:  
- "encoding/json"  
- "fmt"  
- "os"  
- "path"  
- "path/filepath"  
- "time"  
- "dario.cat/mergo"  
- "github.com/fsnotify/fsnotify"  
- "github.com/mudler/LocalAI/core/config"  
- "github.com/rs/zerolog/log"  
  
External data, input sources:  
- Configuration files in the `DynamicConfigsDir` directory specified in the `appConfig`  
  
TODOs:  
- Make `configFileHandler` a singleton so other parts of the code can register config file handlers.  
- When graceful shutdown is implemented, call `Stop()` method of `configFileHandler` to close the watcher.  
  
Summary:  
- The `configFileHandler` struct is responsible for handling configuration file updates. It registers handlers for specific files and watches for changes in the configuration directory.  
- The `Register` method allows registering a handler for a specific file. If `runNow` is set to true, the handler is called immediately.  
- The `Watch` method starts watching the configuration directory for changes. If a change is detected, the corresponding handler is called.  
- The `Stop` method closes the watcher and stops monitoring the configuration directory.  
- The `readApiKeysJson` and `readExternalBackendsJson` functions are examples of handlers that process JSON files and update the application configuration accordingly.  
  
# core/application/startup.go  
Package: application  
  
Imports:  
- "fmt"  
- "os"  
- "github.com/mudler/LocalAI/core/backend"  
- "github.com/mudler/LocalAI/core/config"  
- "github.com/mudler/LocalAI/core/services"  
- "github.com/mudler/LocalAI/internal"  
- "github.com/mudler/LocalAI/pkg/assets"  
- "github.com/mudler/LocalAI/pkg/library"  
- "github.com/mudler/LocalAI/pkg/model"  
- "github.com/mudler/LocalAI/pkg/startup"  
- "github.com/mudler/LocalAI/pkg/xsysinfo"  
- "github.com/rs/zerolog/log"  
  
External data, input sources:  
- Configuration options passed to the New function.  
- Environment variables.  
- Files in the model path, image directory, audio directory, and upload directory.  
  
TODOs:  
- Add support for loading models from a URL.  
- Add support for loading models from a local file.  
- Add support for loading models from a remote server.  
  
Summary:  
- The New function initializes a new Application instance with the given configuration options.  
- It sets up the backend, loads the models, and starts the configuration watcher.  
- The startWatcher function starts a watcher to monitor the configuration directory for changes.  
- The newConfigFileHandler function creates a new ConfigFileHandler instance.  
- The Watch function starts the watcher and monitors the configuration directory for changes.  
- The Handle function handles the configuration file changes.  
- The Stop function stops the watcher.  
  
- The Application struct represents the main application object.  
- It contains the backend loader, model loader, and configuration loader.  
- The BackendLoader method returns the backend loader instance.  
- The ModelLoader method returns the model loader instance.  
- The ConfigLoader method returns the configuration loader instance.  
- The Start method starts the application.  
- The Stop method stops the application.  
  
- The ConfigFileHandler struct handles the configuration file changes.  
- It contains the configuration loader and the watcher.  
- The Watch method starts the watcher and monitors the configuration directory for changes.  
- The Handle method handles the configuration file changes.  
- The Stop method stops the watcher.  
  
- The Watcher struct monitors the configuration directory for changes.  
- It contains the file system watcher and the configuration handler.  
- The Watch method starts the watcher and monitors the configuration directory for changes.  
- The Handle method handles the configuration file changes.  
- The Stop method stops the watcher.  
  
