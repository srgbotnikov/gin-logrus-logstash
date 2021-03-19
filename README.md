# gin-logrus-logstash

## Example

```go
package main

import (
	logstash "github.com/srgbotnikov/gin-logrus-logstash"

	"github.com/gin-gonic/gin"
	"github.com/sirupsen/logrus"
    )

func main() {

	log := logrus.New()

	r := gin.New()
	r.Use(logstash.Logger(log, "127.0.0.1:5050", "appName"), gin.Recovery())

	r.GET("/ping", func(c *gin.Context) {
		c.Data(200, "text/plain", []byte("Hello world"))
	})

	r.Run("127.0.0.1:8090")
}
```
