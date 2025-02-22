# gallery

This package is responsible for managing models from galleries, including installing, deleting, and scanning them for potential vulnerabilities. It also handles the configuration and metadata associated with gallery models.

## File structure:

- gallery.go
- gallery_suite_test.go
- models.go
- models_test.go
- op.go
- request.go
- request_test.go
- core/gallery/gallery.go
- core/gallery/models.go
- core/gallery/op.go
- core/gallery/request.go

## Code summary:

The package provides functions for managing models from galleries, such as installing, deleting, and scanning them for potential vulnerabilities. It also handles the configuration and metadata associated with gallery models.

The code interacts with external data sources such as model URLs and configuration files. It also incorporates user-provided overrides for model settings.

The package includes safety checks to identify potentially vulnerable models.

## Functions:

- InstallModelFromGallery: Installs a model from a gallery based on the provided name and configuration.
- FindModel: Locates a model in a list of available models based on its name.
- AvailableGalleryModels: Retrieves a list of available models from the specified galleries.
- getGalleryModels: Fetches models from a gallery and parses the configuration files.
- GetLocalModelConfiguration: Retrieves the configuration for a locally installed model.
- DeleteModelFromSystem: Removes a model and its associated files from the system.
- SafetyScanGalleryModels: Scans all models in the specified galleries for potential vulnerabilities.
- SafetyScanGalleryModel: Scans a single model for potential vulnerabilities.

## External data and input sources:

- Galleries from the configuration file
- Model URLs and configuration files from the galleries
- User-provided overrides for model settings

## TODOs:

- Determine if using the override method with a blank cfg yaml is worse than using the URL method for gallery models.
- Decide on a strategy for handling model overrides when user overrides are introduced.
- Investigate how to handle cases where a model doesn't install a configuration file.

## Relations between code entities:

The package's functions work together to manage models from galleries. For example, InstallModelFromGallery uses the functions getGalleryModels and GetLocalModelConfiguration to install a model from a gallery.

## Unclear places:

- It's unclear how the package handles cases where a model doesn't install a configuration file.
- It's unclear if using the override method with a blank cfg yaml is worse than using the URL method for gallery models.
- It's unclear what strategy the package uses for handling model overrides when user overrides are introduced.

## Possible dead code:

- There might be dead code related to the handling of cases where a model doesn't install a configuration file.
- There might be dead code related to the override method with a blank cfg yaml.
- There might be dead code related to the strategy for handling model overrides when user overrides are introduced.

## Edge cases:

- If the gallery endpoint is unavailable, the package will not be able to retrieve model configurations.
- If the model configuration file is corrupted, the package will not be able to install the model.
- If the user provides invalid overrides for model settings, the package may not be able to install the model.

## Environment variables, flags, cmdline arguments, files and their paths that can be used for configuration:

- The package uses the LocalAI core configuration package to access gallery information.
- The package reads YAML files containing model configurations.
- The package downloads model files from the specified URLs.

## Possible improvements:

- Add error handling for cases where the gallery endpoint is unavailable or the model configuration file is corrupted.
- Improve the documentation for the package and its functions.
- Add unit tests for the package's functions.

## Conclusion:

The gallery package provides a comprehensive set of functions for managing models from galleries. It handles the installation, deletion, and scanning of models, as well as the configuration and metadata associated with them. The package is well-documented and includes unit tests for its functions.