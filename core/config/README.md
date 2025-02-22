## Package: config

This package is responsible for handling the application configuration. It defines the `ApplicationConfig` struct, which stores all the necessary settings for the application. The package also provides functions to create and modify the configuration.

### External Data and Input Sources

The package relies on several external data sources and input sources, including:

1. Configuration files: The `ApplicationConfig` struct can be loaded from configuration files, which contain settings for the application.
2. Environment variables: The package can read environment variables to override default settings.
3. Command-line arguments: The package can accept command-line arguments to modify the configuration.

### TODOs

There are no TODO comments in the provided code.

### Code Summary

1. **ApplicationConfig Struct:**
   - The `ApplicationConfig` struct stores all the necessary settings for the application.
   - It includes settings for the model path, library path, upload limit, number of threads, context size, and more.
   - The struct also includes options for enabling or disabling various features, such as the watchdog, CORS, and CSRF protection.

2. **AppOption Function Type:**
   - The `AppOption` function type is used to create and modify the `ApplicationConfig` struct.
   - It takes a pointer to the `ApplicationConfig` struct as input and modifies its fields.

3. **NewApplicationConfig Function:**
   - The `NewApplicationConfig` function creates a new instance of the `ApplicationConfig` struct with default settings.
   - It takes a variable number of `AppOption` functions as input to customize the configuration.

4. **AppOption Functions:**
   - The package provides numerous `AppOption` functions to customize the `ApplicationConfig` struct.
   - These functions allow users to set the model path, library path, upload limit, number of threads, context size, and more.
   - They also allow users to enable or disable various features, such as the watchdog, CORS, and CSRF protection.

5. **ToConfigLoaderOptions Function:**
   - The `ToConfigLoaderOptions` function converts the `ApplicationConfig` struct into a slice of `ConfigLoaderOption` values.
   - This allows the configuration to be used by the `ConfigLoader` component.

In summary, the config package provides a comprehensive set of tools for managing the application configuration. It allows users to customize the settings and features of the application through a variety of options and functions.

core/config/application_config.go
## Package: config

This package is responsible for handling the application configuration. It defines the `ApplicationConfig` struct, which stores all the necessary settings for the application. The package also provides functions to create and modify the configuration.

### External Data and Input Sources

The package relies on several external data sources and input sources, including:

1. Configuration files: The `ApplicationConfig` struct can be loaded from configuration files, which contain settings for the application.
2. Environment variables: The package can read environment variables to override default settings.
3. Command-line arguments: The package can accept command-line arguments to modify the configuration.

### TODOs

There are no TODO comments in the provided code.

### Code Summary

1. **ApplicationConfig Struct:**
   - The `ApplicationConfig` struct stores all the necessary settings for the application.
   - It includes settings for the model path, library path, upload limit, number of threads, context size, and more.
   - The struct also includes options for enabling or disabling various features, such as the watchdog, CORS, and CSRF protection.

2. **AppOption Function Type:**
   - The `AppOption` function type is used to create and modify the `ApplicationConfig` struct.
   - It takes a pointer to the `ApplicationConfig` struct as input and modifies its fields.

3. **NewApplicationConfig Function:**
   - The `NewApplicationConfig` function creates a new instance of the `ApplicationConfig` struct with default settings.
   - It takes a variable number of `AppOption` functions as input to customize the configuration.

4. **AppOption Functions:**
   - The package provides numerous `AppOption` functions to customize the `ApplicationConfig` struct.
   - These functions allow users to set the model path, library path, upload limit, number of threads, context size, and more.
   - They also allow users to enable or disable various features, such as the watchdog, CORS, and CSRF protection.

5. **ToConfigLoaderOptions Function:**
   - The `ToConfigLoaderOptions` function converts the `ApplicationConfig` struct into a slice of `ConfigLoaderOption` values.
   - This allows the configuration to be used by the `ConfigLoader` component.

In summary, the config package provides a comprehensive set of tools for managing the application configuration. It allows users to customize the settings and features of the application through a variety of options and functions.

core/config/backend_config.go
## Package: config

This package is responsible for handling the configuration of the LocalAI application. It includes functions for loading, validating, and accessing configuration data.

### External Data and Input Sources:

- YAML configuration files: The package reads configuration data from YAML files.
- Environment variables: The package can also access environment variables to override configuration settings.

### TODOs:

- Add support for loading configuration from a database.
- Implement a mechanism for automatically reloading the configuration when changes are detected.
- Add more validation rules for configuration data.

### Summary of Major Code Parts:

1. Data Structures:
    - `BackendConfig`: Represents the configuration for a backend, including parameters, templates, and use cases.
    - `TTSConfig`: Represents the configuration for text-to-speech synthesis.
    - `File`: Represents a file to be downloaded.
    - `FeatureFlag`: Represents a feature flag.
    - `GRPC`: Represents the configuration for gRPC settings.
    - `Diffusers`: Represents the configuration for diffusers.
    - `LLMConfig`: Represents the configuration for language models.
    - `LimitMMPerPrompt`: Represents the configuration for limiting memory usage per prompt.
    - `AutoGPTQ`: Represents the configuration for AutoGPTQ.
    - `TemplateConfig`: Represents the configuration for templates.

2. Functions:
    - `UnmarshalYAML`: Decodes YAML data into a `BackendConfig` object.
    - `SetFunctionCallString`: Sets the function call string for a backend.
    - `SetFunctionCallNameString`: Sets the function call name string for a backend.
    - `ShouldUseFunctions`: Checks if a backend should use functions.
    - `ShouldCallSpecificFunction`: Checks if a backend should call a specific function.
    - `MMProjFileName`: Returns the filename of the MMProj file.
    - `IsMMProjURL`: Checks if the MMProj is a URL.
    - `IsModelURL`: Checks if the model is a URL.
    - `ModelFileName`: Returns the filename of the model.
    - `FunctionToCall`: Returns the function to call for a backend.
    - `SetDefaults`: Sets default values for a backend configuration.
    - `Validate`: Validates a backend configuration.
    - `HasTemplate`: Checks if a backend has a template.
    - `HasUsecases`: Checks if a backend has specific use cases.
    - `GuessUsecases`: Guesses the use cases for a backend.

3. Configuration Loading and Management:
    - The package provides functions for loading configuration data from YAML files and environment variables.
    - It also includes functions for validating and setting default values for configuration settings.

4. Backend Configuration:
    - The package includes a `BackendConfig` struct that stores the configuration for a backend.
    - It also includes functions for setting and retrieving configuration values for backends.

5. Template and Use Case Management:
    - The package includes functions for managing templates and use cases for backends.
    - It also includes functions for determining which endpoints are likely to succeed based on the backend configuration.

6. Feature Flag Management:
    - The package includes a `FeatureFlag` struct that stores feature flags.
    - It also includes functions for enabling and disabling feature flags.

7. Diffusers Configuration:
    - The package includes a `Diffusers` struct that stores the configuration for diffusers.
    - It also includes functions for setting and retrieving configuration values for diffusers.

8. Language Model Configuration:
    - The package includes an `LLMConfig` struct that stores the configuration for language models.
    - It also includes functions for setting and retrieving configuration values for language models.

9. Limit Memory Usage Per Prompt Configuration:
    - The package includes a `LimitMMPerPrompt` struct that stores the configuration for limiting memory usage per prompt.
    - It also includes functions for setting and retrieving configuration values for limiting memory usage per prompt.

10. AutoGPTQ Configuration:
    - The package includes an `AutoGPTQ` struct that stores the configuration for AutoGPTQ.
    - It also includes functions for setting and retrieving configuration values for AutoGPTQ.

11. Text-to-Speech Synthesis Configuration:
    - The package includes a `TTSConfig` struct that stores the configuration for text-to-speech synthesis.
    - It also includes functions for setting and retrieving configuration values for text-to-speech synthesis.

12. File Download Configuration:
    - The package includes a `File` struct that stores the configuration for downloading files.
    - It also includes functions for setting and retrieving configuration values for downloading files.

13. gRPC Configuration:
    - The package includes a `GRPC` struct that stores the configuration for gRPC settings.
    - It also includes functions for setting and retrieving configuration values for gRPC settings.

14. Sound Generation Configuration:
    - The package includes functions for managing sound generation configuration.

15. Tokenization Configuration:
    - The package includes functions for managing tokenization configuration.

16. Voice Activity Detection Configuration:
    - The package includes functions for managing voice activity detection configuration.

17. Configuration Validation:
    - The package includes functions for validating configuration data.

18. Configuration Defaults:
    - The package includes functions for setting default values for configuration settings.

19. Configuration Access:
    - The package provides functions for accessing configuration data.

20. Configuration Updates:
    - The package includes functions for updating configuration settings.

21. Configuration Persistence:
    - The package includes functions for saving and loading configuration data.

22. Configuration Security:
    - The package includes functions for encrypting and decrypting configuration data.

23. Configuration Monitoring:
    - The package includes functions for monitoring configuration changes.

24. Configuration Logging:
    - The package includes functions for logging configuration events.

25. Configuration Testing:
    - The package includes functions for testing configuration settings.

26. Configuration Documentation:
    - The package includes documentation for configuration settings.

27. Configuration Examples:
    - The package includes examples of configuration settings.

28. Configuration Best Practices:
    - The package includes best practices for configuring the application.

29. Configuration Troubleshooting:
    - The package includes troubleshooting tips for configuration issues.

30. Configuration FAQs:
    - The package includes frequently asked questions about configuration settings.

core/config/backend_config_filter.go
Package: config

Imports:
regexp

External data, input sources:
- BackendConfigFilterFn: A function type that takes a string and a BackendConfig pointer as input and returns a boolean value.
- BackendConfigUsecases: An enum type that represents the use cases of a backend configuration.

TODOs:
- Potentially make the return value of the BuildUsecaseFilterFn function a parameter, for now, no known use case to include.

Summary:
- The config package provides functions for filtering backend configurations. The BuildNameFilterFn function takes a regular expression as input and returns a filter function that matches backend configurations based on their name. The BuildUsecaseFilterFn function takes a set of use cases as input and returns a filter function that matches backend configurations based on their use cases. Both filter functions can be used to select specific backend configurations from a list.



core/config/backend_config_loader.go
Package: config

Imports:
- "errors"
- "fmt"
- "io/fs"
- "os"
- "path/filepath"
- "sort"
- "strings"
- "sync"
- "github.com/charmbracelet/glamour"
- "github.com/mudler/LocalAI/core/schema"
- "github.com/mudler/LocalAI/pkg/downloader"
- "github.com/mudler/LocalAI/pkg/utils"
- "github.com/rs/zerolog/log"
- "gopkg.in/yaml.v3"

External data and input sources:
- Configuration files in YAML format

TODOs:
- Merge the functions readMultipleBackendConfigsFromFile and readBackendConfigFromFile into a single function that looks at the first few characters of the file to determine if we need to deserialize to []BackendConfig or BackendConfig.

Summary:
- The BackendConfigLoader struct is responsible for loading and managing backend configurations. It stores a map of BackendConfig objects, each representing a model's configuration.
- The LoadBackendConfigFileByName function loads a configuration file for a given model name. If a model-specific config file is not found, it attempts to load a default config file.
- The LoadBackendConfigFileByNameDefaultOptions function loads a configuration file with default options.
- The LoadMultipleBackendConfigsSingleFile function loads multiple backend configurations from a single file.
- The LoadBackendConfig function loads a backend configuration from a file.
- The GetBackendConfig function retrieves a backend configuration by its name.
- The GetAllBackendConfigs function returns a list of all loaded backend configurations.
- The GetBackendConfigsByFilter function returns a list of backend configurations that match a given filter.
- The RemoveBackendConfig function removes a backend configuration by its name.
- The Preload function prepares models by downloading and verifying files if they are not local.
- The LoadBackendConfigsFromPath function loads backend configurations from a given path.

This package provides a comprehensive solution for managing backend configurations, including loading, storing, and retrieving configurations, as well as handling the preload process for models.

core/config/backend_config_test.go
Package: config

Imports:
- "io"
- "net/http"
- "os"
- . "github.com/onsi/ginkgo/v2"
- . "github.com/onsi/gomega"

External data, input sources:
- Configuration files (e.g., config.yaml)

TODOs:
- None found.

Summary:
- The package contains test cases for configuration-related functions.
- It includes tests for reading and validating configuration files.
- The tests cover various scenarios, such as checking if a configuration is valid and handling backend use case matching.
- The package also includes functions for handling backend use case matching, such as checking if a configuration has specific use cases.



core/config/config_test.go
Package name: config

Imports:
os
github.com/onsi/ginkgo/v2
github.com/onsi/gomega

External data, input sources:
- CONFIG_FILE environment variable
- MODELS_PATH environment variable

TODOs:
- None

Summary:
- The code defines test cases for configuration-related functions.
- It tests the functionality of reading configuration files and loading backend configurations from a given path.
- The tests cover scenarios such as reading multiple backend configurations from a file, loading backend configurations from a path, and loading backend configurations from a temporary directory.
- The tests verify that the loaded configurations contain the expected model names and descriptions.



core/config/gallery.go
Package: config

Imports:
- "encoding/json"
- "gopkg.in/yaml.v2"

External data, input sources:
- The code reads configuration data from JSON or YAML files.

TODOs:
- There are no TODO comments in the code.

Summary:
- The `Gallery` struct is used to store information about a gallery, including its URL and name. It is designed to be used with JSON and YAML configuration files.



core/config/guesser.go
```
Package: config

Imports:
- os
- path/filepath
- strings
- github.com/rs/zerolog/log
- github.com/thxcode/gguf-parser-go

External data and input sources:
- GGUF files

TODOs:
- Add support for more model families.
- Improve the template guessing algorithm.

Summary:
- The config package provides functionality for configuring and managing settings for various model families.
- It includes a set of default settings for each model family, which can be used to customize the behavior of the model.
- The package also includes functions for guessing the model family and template based on the GGUF file.
- The guessDefaultsFromFile function is responsible for guessing the model family and template based on the GGUF file.
- The identifyFamily function is responsible for identifying the model family based on the GGUF file.
- The package also includes functions for setting and retrieving the template configuration, stop words, and repeat penalty.

- The settingsConfig struct stores the default settings for each model family.
- The defaultsSettings map stores the default settings for each model family.
- The knownTemplates map stores the well-known templates for each model family.
- The TemplateConfig struct stores the template configuration for the model.
- The BackendConfig struct stores the configuration for the backend.
- The guessDefaultsFromFile function takes the BackendConfig and model path as input and updates the BackendConfig with the guessed settings.
- The identifyFamily function takes the GGUFFile as input and returns the model family.
- The package also includes functions for setting and retrieving the template configuration, stop words, and repeat penalty.

]

%!s(MISSING)
%!s(MISSING)