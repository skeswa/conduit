# conduit
A library that makes TCP connections feel more web-like.
```go
client := conduit
    .NewClient()
    .Credentials("me@sandile.io", "somesortofpassword")
    .Route("/thing/other", func(context *conduit.Context, req *conduit.Request, res *conduit.Responder) {
        req.Body.Raw() // Returns the raw string version of the body
        req.Body.Parse(&data) // Performs JSON parsing onto a struct pointer
        anotherConn.Bridge(req, res)
        res.Ok(interface{})
        res.Fault.Unauthorized(interface{})
        res.Fault.BadRequest(interface{})
        res.Fault.NotFound(interface{})
        res.Error(interface{})
    })
    .Route("/*", func(context *conduit.Context, req *conduit.Request, res *conduit.Responder) {
        context.Server
            .Request("/thing/other")
            .Body(Thing{})
            .Send(func(res *conduit.Responder){})
            // OR you can use a channel instead
            .Stream(someChan)
    })

err := client.Connect("www.conduitserver.com", 4242)
    
conduit
    .Server()
    .Authenticator(func(identity string, 
    .Route("/thing/other", func(context *conduit.Context, req *conduit.Request, res *conduit.Responder) {
        conduit.Client("me@sandile.io") // Fetches a client by its identity
        req.Body.Raw() // Returns the raw string version of the body
        req.Body.Parse(&data) // Performs JSON parsing onto a struct pointer
        anotherConn.Bridge(req, res)
        res.Ok(interface{})
        res.Fault.Unauthorized(interface{})
        res.Fault.BadRequest(interface{})
        res.Fault.NotFound(interface{})
        res.Error(interface{})
    })
    .Listen(4242)
```
