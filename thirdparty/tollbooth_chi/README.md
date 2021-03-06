## tollbooth_chi

[Chi](https://github.com/pressly/chi) middleware for rate limiting HTTP requests.


## Five Minutes Tutorial

```
package main

import (
    "github.com/syreclabs/tollbooth"
    "github.com/syreclabs/tollbooth/thirdparty/tollbooth_chi"
    "github.com/pressly/chi"
    "net/http"
    "time"
)

func main() {
    // Create a limiter struct.
    limiter := tollbooth.NewLimiter(1, time.Second)

    r := chi.NewRouter()

    r.Use(tollbooth_chi.LimitHandler(limiter))

    r.Get("/", func(w http.ResponseWriter, r *http.Request) {
        w.Write([]byte("Hello, world!"))
    })

    http.ListenAndServe(":12345", r)
}
```
