## Node JS Express Server

```
const express = require('express')
const path = require('path')
const port = process.env.PORT || 8080
const app = express()

app.use(express.static(__dirname + '/public'))

app.get('*', function (request, response){
  response.sendFile(path.resolve(__dirname, 'public', 'index.html'))
})

app.listen(port)
console.log("Server successfully started on port: " + port)
```

### Python HTTP Server

```
import SimpleHTTPServer, SocketServer
import urlparse, os

PORT = 3000
INDEXFILE = 'index.html'

class MyHandler(SimpleHTTPServer.SimpleHTTPRequestHandler):
   def do_GET(self):

    # Parse query data to find out what was requested
    parsedParams = urlparse.urlparse(self.path)

     # See if the file requested exists
    if os.access('.' + os.sep + parsedParams.path, os.R_OK):
        # File exists, serve it up
        SimpleHTTPServer.SimpleHTTPRequestHandler.do_GET(self);
    else:
        # send index.html, but don't redirect
        self.send_response(200)
        self.send_header('Content-Type', 'text/html')  
        self.end_headers()
        with open(INDEXFILE, 'r') as fin:
          self.copyfile(fin, self.wfile)

Handler = MyHandler

httpd = SocketServer.TCPServer(("", PORT), Handler)

print "serving at port", PORT
httpd.serve_forever()
```
