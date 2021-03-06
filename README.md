# Swagger UI
Library to display Swagger documentation in HTML format

## Install

	go get github.com/predixdeveloperACN/swagger-ui
	
## Prerequisite

A valid Swagger document with a filename of **swagger.json** should exists under the **api** folder.
```
<GO project root>/api/swagger.json
```

## How to use

To use Swagger UI, just pass MUX router and the API's base path.

Code:

```go
package server
import (
        "log"
	    "net/http"
        "github.com/gorilla/mux"
        sw "github.com/predixdeveloperACN/swagger-ui"
)
const base_path = "/api/v1/"
func SetupRestServer() {
        // Register a handler for each route pattern
        router := mux.NewRouter()
        
        // attach the swagger routes
        sw.AttachSwaggerUI(router, base_path)
        
        // start listening on the configured port and routes
        log.Fatal(http.ListenAndServe(":8080", router))
}
```

##How to view
To view the swagger HTML endpoint, go to the following URL format.
```
<host url>/<base api path>/help
```

Example:
[https://aviation-ia-route-manager-svc-dev.run.asv-pr.ice.predix.io/api/v1/help](https://aviation-ia-route-manager-svc-dev.run.asv-pr.ice.predix.io/api/v1/help)

##Available Function
### func AttachSwaggerUI
``` go
func AttachSwaggerUI (router *mux.Router, base_path string) (err error)
```
Sets the routes for the static page and the swagger document file.

##Issues
If you encounter the following reference issue, just delete the **Godeps** and **vendor** folder to sync the libraries.
```
cannot use router (type *"github.build.ge.com/aviation-intelligent-airport/route-manager-svc.git/vendor/github.com/gorilla/mux".Router) as type *"github.com/gorilla/mux".Router in argument to swagger_ui.AttachSwaggerUI
```