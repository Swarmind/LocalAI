# pkg/downloader/uri_test.go  
Package: downloader_test  
  
Imports:  
- "crypto/rand"  
- "crypto/sha256"  
- "fmt"  
- "net/http"  
- "net/http/httptest"  
- "os"  
- "regexp"  
- "strconv"  
- . "github.com/mudler/LocalAI/pkg/downloader"  
- . "github.com/onsi/ginkgo/v2"  
- . "github.com/onsi/gomega"  
  
External data, input sources:  
- Mock server for testing download functionality.  
  
TODOs:  
- None found.  
  
Summary:  
- The code defines a set of tests for the Gallery API, specifically focusing on parsing URIs and downloading files.  
- It covers various scenarios, including parsing GitHub URLs with and without branches, as well as handling URLs directly.  
- The tests also cover the DownloadFile function, which handles downloading files from a mock server, including scenarios where the server supports or doesn't support range headers.  
- The tests cover cases where the download needs to be resumed from a partially downloaded file, as well as cases where the download needs to be restarted from the beginning.  
- The code includes a custom RangeHeaderError type to handle errors related to invalid or ill-formatted range headers.  
- The tests use a mock server to simulate a remote server and test the download functionality.  
- The code includes functions to extract range headers from HTTP requests and to create a mock server for testing purposes.  
- The tests cover various edge cases, such as when the server doesn't support range headers or when the range header is invalid.  
- The code includes cleanup functions to remove temporary files created during testing.  
  
  
  
