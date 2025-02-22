# core/gallery/gallery.go  
Package: gallery  
  
Imports:  
	"errors"  
	"fmt"  
	"os"  
	"path/filepath"  
	"strings"  
	"dario.cat/mergo"  
	"github.com/mudler/LocalAI/core/config"  
	"github.com/mudler/LocalAI/pkg/downloader"  
	"github.com/mudler/LocalAI/pkg/utils"  
	"github.com/rs/zerolog/log"  
	"gopkg.in/yaml.v2"  
  
External data and input sources:  
	- Galleries from the configuration file  
	- Model URLs and configuration files from the galleries  
	- User-provided overrides for model settings  
  
TODOs:  
	- Determine if using the override method with a blank cfg yaml is worse than using the URL method for gallery models.  
	- Decide on a strategy for handling model overrides when user overrides are introduced.  
	- Investigate how to handle cases where a model doesn't install a configuration file.  
  
Summary:  
	- The package provides functions for managing models from galleries.  
	- It includes functions for installing, deleting, and scanning models for potential vulnerabilities.  
	- The package also handles the configuration and metadata associated with gallery models.  
	- The code interacts with external data sources such as model URLs and configuration files.  
	- It also incorporates user-provided overrides for model settings.  
	- The package includes safety checks to identify potentially vulnerable models.  
  
	- InstallModelFromGallery: Installs a model from a gallery based on the provided name and configuration.  
	- FindModel: Locates a model in a list of available models based on its name.  
	- AvailableGalleryModels: Retrieves a list of available models from the specified galleries.  
	- getGalleryModels: Fetches models from a gallery and parses the configuration files.  
	- GetLocalModelConfiguration: Retrieves the configuration for a locally installed model.  
	- DeleteModelFromSystem: Removes a model and its associated files from the system.  
	- SafetyScanGalleryModels: Scans all models in the specified galleries for potential vulnerabilities.  
	- SafetyScanGalleryModel: Scans a single model for potential vulnerabilities.  
  
# core/gallery/models.go  
## Package: gallery  
  
This package is responsible for handling the gallery of models, including downloading, installing, and managing their configurations.  
  
### Imports:  
  
- "errors"  
- "fmt"  
- "os"  
- "path/filepath"  
- "dario.cat/mergo"  
- "github.com/mudler/LocalAI/core/config"  
- "github.com/mudler/LocalAI/pkg/downloader"  
- "github.com/mudler/LocalAI/pkg/utils"  
- "github.com/rs/zerolog/log"  
- "gopkg.in/yaml.v2"  
  
### External Data and Input Sources:  
  
- The package interacts with the gallery endpoint to retrieve model configurations.  
- It reads YAML files containing model configurations.  
- It downloads model files from the specified URLs.  
  
### TODOs:  
  
- There are no TODO comments in the provided code.  
  
### Code Summary:  
  
1. **Model Configuration (Config):**  
   - The `Config` struct represents the model configuration, containing details such as description, license, URLs, files, and prompt templates.  
   - It is used to store and manage the model's metadata and configuration.  
  
2. **File and Prompt Template Structures:**  
   - The `File` struct stores information about each file associated with the model, including filename, SHA256 hash, and URI.  
   - The `PromptTemplate` struct contains the name and content of each prompt template used by the model.  
  
3. **Fetching Gallery Configuration:**  
   - The `GetGalleryConfigFromURL` function retrieves the model configuration from the given URL.  
   - It downloads the YAML file containing the configuration and parses it into a `Config` struct.  
  
4. **Reading Configuration File:**  
   - The `ReadConfigFile` function reads the YAML configuration file from the specified path.  
   - It parses the YAML data into a `Config` struct and returns it.  
  
5. **Installing Model:**  
   - The `InstallModel` function handles the installation of the model.  
   - It downloads the model files, verifies their SHA256 hashes, and saves them to the specified base path.  
   - It also writes the prompt template contents to separate files and updates the configuration file with any provided overrides.  
  
6. **Utility Functions:**  
   - The `galleryFileName` function generates the filename for the gallery file based on the model name.  
  
In summary, the gallery package provides functionalities for managing model configurations, downloading and installing models, and handling prompt templates. It interacts with the gallery endpoint to retrieve model information and downloads the necessary files for the model to function.  
  
# core/gallery/op.go  
Package/Component name: gallery  
  
Imports:  
github.com/mudler/LocalAI/core/config  
  
External data, input sources:  
- GalleryModelName: The name of the gallery model.  
- ConfigURL: The URL of the configuration file.  
- Delete: A boolean value indicating whether the operation is a deletion.  
  
TODOs:  
- There are no TODO comments in the provided code.  
  
Summary of major code parts:  
- GalleryOp: This struct represents a gallery operation. It contains information about the gallery model, the configuration URL, and whether the operation is a deletion.  
- GalleryOpStatus: This struct represents the status of a gallery operation. It contains information about the deletion status, file name, error, processed status, message, progress, total file size, downloaded file size, and gallery model name.  
  
  
  
# core/gallery/request.go  
## Package: gallery  
  
Imports:  
- "fmt"  
- "strings"  
- "github.com/mudler/LocalAI/core/config"  
  
External data, input sources:  
- The code interacts with the LocalAI core configuration package to access gallery information.  
  
TODOs:  
- There are no TODO comments in the provided code.  
  
### GalleryModel struct  
This struct represents a model in the gallery and is used to install the model by resolving the URL and downloading the files. It also allows overriding the configuration of the model.  
  
### Metadata struct  
This struct contains metadata about the model, such as its URL, name, description, license, and tags.  
  
### GalleryModel methods  
- ID(): Returns a unique identifier for the model.  
  
### GalleryModels struct  
This struct represents a collection of GalleryModel objects. It provides methods for searching and finding models by name.  
  
- Search(): Searches for models based on a given term.  
- FindByName(): Finds a model by its name.  
  
### Summary  
The gallery package provides data structures and functions for managing and interacting with models in a gallery. It allows users to search for models, retrieve their metadata, and install them by resolving URLs and downloading files.  
  
