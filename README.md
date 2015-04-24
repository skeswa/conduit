# conduit
A library that makes TCP connections feel more web-like.
```go
conduit.Route("/thing/other", func(req *conduit.Request, res *conduit.Responder) {
  req.Conn
  req.Body.Raw()
  req.Body.Parse(&data)
  req.Headers[0].Name, req.Headers[0].Value
  anotherConn.Bridge(req, res)
  res.Ok(interface{})
  res.Fault.Unauthorized(interface{})
  res.Fault.BadRequest(interface{})
  res.Fault.NotFound(interface{})
  res.Error(interface{})
})

err := conduit.Connect("site.com:4242")
err := conduit.Disconnect()
err := conn.Serve(4242, func(conn *conduit.Conn) {
  conn.Request("/thing/other").Header("Authorization", "4292743562834765987").Body(Thing{}).Send(func(res *conduit.Response) {
    res.Status.IsOk()
    res.Status.IsError()
    res.Status.IsFault()
    res.Status.IsFaultUnauthorized()
    res.Status.IsFaultBadRequest()
    res.Status.IsFaultNotFound()
    res.Body.Raw()
    req.Body.Parse(&data)
  })
  
  conn.OnClose(func() {
  })
})
```
