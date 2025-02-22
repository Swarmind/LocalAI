# pkg/templates/cache.go  
Package: templates  
  
Imports:  
- "bytes"  
- "fmt"  
- "os"  
- "path/filepath"  
- "sync"  
- "text/template"  
- "github.com/mudler/LocalAI/pkg/utils"  
- "github.com/Masterminds/sprig/v3"  
- "github.com/nikolalohinski/gonja/v2"  
- "github.com/nikolalohinski/gonja/v2/exec"  
  
External data, input sources:  
- Templates are loaded from the templatesPath directory.  
  
TODOs:  
- Keep the TemplateType enum in sync with config.TemplateConfig.  
  
Summary:  
- The package provides a template cache that stores and manages templates for different template types.  
- It supports both Go templates and Jinja templates.  
- The cache is thread-safe and ensures that templates are loaded only once.  
- The package includes functions to load, evaluate, and manage templates.  
- It also includes security checks to prevent loading templates from outside the specified path.  
- The package is designed to be used in a multi-threaded environment, where multiple components may need to access and use templates concurrently.  
- The use of a cache ensures that templates are loaded only once, improving performance and reducing resource consumption.  
- The package is well-documented and includes comments explaining the purpose and functionality of each function and data structure.  
- The package is designed to be modular and extensible, allowing developers to easily add support for new template types or modify existing functionality.  
  
# pkg/templates/evaluator.go  
Package: templates  
  
Imports:  
- "encoding/json"  
- "fmt"  
- "strings"  
- "github.com/mudler/LocalAI/core/config"  
- "github.com/mudler/LocalAI/core/schema"  
- "github.com/mudler/LocalAI/pkg/functions"  
- "github.com/rs/zerolog/log"  
  
External Data and Input Sources:  
- Configuration data from config.BackendConfig  
- Messages from schema.Message  
- Functions from functions.Function  
  
TODOs:  
- In the `templateJinjaChat` function, the comment mentions that the current implementation covers minimum text templates and can be expanded to cover more complex interactions.  
  
Summary:  
- The `templates` package provides functionality for evaluating prompt templates and chat message templates.  
- It defines various data structures to represent prompt template data and chat message template data.  
- The `Evaluator` struct is responsible for evaluating templates based on the provided template type and configuration.  
- The `EvaluateTemplateForPrompt` function handles the evaluation of prompt templates, while the `evaluateTemplateForChatMessage` function handles chat message templates.  
- The `TemplateMessages` function takes a list of messages, configuration, functions, and a flag indicating whether to use functions, and returns a string containing the templated input.  
- The package uses Jinja templates for templating and supports various template types, such as completion, edit, chat, and functions.  
- It also includes logic for handling system prompts and suppressing them if necessary.  
  
In essence, the `templates` package enables the use of templates to dynamically generate prompts and chat messages based on the provided input and configuration.  
  
# pkg/templates/multimodal.go  
Package: templates  
  
Imports:  
- "bytes"  
- "text/template"  
- "github.com/Masterminds/sprig/v3"  
  
External data, input sources:  
- The code uses a default template string if no template string is provided as input.  
- It takes a template string, MultiModalOptions, and text as input.  
  
TODOs:  
- There are no TODO comments in the code.  
  
Summary:  
- The code defines a MultiModalOptions struct to store the total and message-specific counts of images, audios, and videos.  
- It also defines a MultimodalContent struct to store the ID of each media element.  
- The TemplateMultiModal function takes a template string, MultiModalOptions, and text as input.  
- It compiles the template using the sprig library for additional functions.  
- The function then generates lists of MultimodalContent objects for videos, audios, and images based on the provided MultiModalOptions.  
- Finally, it executes the template with the generated content and text, returning the resulting string.  
  
