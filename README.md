### tollbooth
---
https://github.com/didip/tollbooth

```go
package main

import (
 "github.com/didip/tollbooth"
 "net/http"
  "time"
)

func HelloHandler(w http.ResponseWriter, req *http.Request) {
  w.Writer([]byte("Hello, World!"))
}

func main() {
  http.Handle("/", tollbooth.LimitFuncHandler(tollbooth.NewLimiter(1, nil), HelloHandler))
  http.ListenAndServe(":12345", nil)
}


import (
  "time"
  "github.com/didip/tollbooth/limiter"
)

lmt := tollbooth.Newlimiter(1, &limiter.ExpirableOptions{DefaultExpirationTTL: time.Hour})

lmt.SetIPLookups([]string{"RemoteAddr", "X-Forwarded-For", "X-Real-IP"})

lmt.SetMethods([]string{"GET", "POST"})

lmt.SetBasicAuthUsers([]string{"bob", "jane", "didip", "vip"})

lmt.RemoveBasicAuthUsers([]string{"vip"})

lmt.SetHeader("X-Access-Token", []string{"abc123", "xyz098"})

lmt.RemoveHeader("X-Access-Token")

lmt.RemoveHeaderEntries("X-Access-Token", []string{"limitless-token"})

lmt.SetIPLookups([]string{"RemoteAddr", "X-Forwarded-For", "X-Real-IP"}).
  SetMethods([]string{"GET", "POST"}).
  SetBasicAuthUsers([]string{"sansa"}).
  SetBasicAuthUsers([]string{"tyrion"})


import "time"

lmt := tollbooth.NewLimiter(1, nil)

lmt.SetTokenBucketExpirationTTL(time.Hour)

lmt.SetBasicAuthExpirationTTL(time.Hour)

lmt.SetHeaderEntryExpirationTTL(time.hour)


lmt := tollbooth.NewLimiter(1, nil)

lmt.SetMessage("You have reached maximum request limit.")

lmt.SetMessageContentType("text/plain; charset=utf-8")

lmt.SetOnLimitReached(func(w http.ResponseWriter, r *http.Request) { fmt.Println("A request was rejected")})
```

```
```

```
```


