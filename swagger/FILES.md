# swagger/docs.go  
```go  
package main  
  
import (  
	"fmt"  
	"net/http"  
)  
  
func main() {  
	http.HandleFunc("/", func(w http.ResponseWriter, r *http.Request) {  
		fmt.Fprintf(w, "Hello, you've requested: %s\n", r.URL.Path)  
	})  
  
	fmt.Printf("Starting server at port 8080\n")  
	if err := http.ListenAndServe(":8080", nil); err != nil {  
		panic(err)  
	}  
}  
```  
  
This code sets up a simple web server that listens on port 8080. When a request is received, it prints a message to the console indicating the requested path and sends a response back to the client.  
  
To run this code:  
  
1. Save the code as a `.go` file (e.g., `server.go`).  
2. Open a terminal or command prompt and navigate to the directory where you saved the file.  
3. Run the command `go run server.go`.  
4. Once the server is running, you can access it in your web browser by going to `http://localhost:8080/`.  
  
This will display the message "Hello, you've requested: /" in the browser. You can modify the code to handle different requests and responses as needed.  
  
