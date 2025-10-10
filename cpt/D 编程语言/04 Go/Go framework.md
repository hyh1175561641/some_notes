
http://revel.github.io/ Revel Web框架

GoFlyAdmin 基于Gin 后台系统框架
Iris 轻量级Web框架
https://beego.me/ Beego Web应用框架
https://echo.labstack.com/ Echo Web框架
https://go-micro.dev/ go-micro 微服务框架
https://gorm.io/ Gorm 支持多种数据库

https://grpc.io/ gRPC 微服务之间通信
https://github.com/smallnest/rpcx Rpcx RPC服务治理框架 Alibaba

aah Web框架
Aero Web框架
Air 框架

https://go-kratos.dev/ Kratos Go微服务框架
Goa go微服务框架



# Gin
https://gin-gonic.com/
https://gin-gonic.com/docs/
https://pkg.go.dev/github.com/gin-gonic/gin
https://github.com/gin-gonic/gin

https://gin-gonic.com/zh-cn/docs/

https://go.dev/doc/tutorial/web-service-gin
https://www.jetbrains.com/guide/go/tutorials/rest_api_series/gin/

Gin 轻量级Web 框架

```bash

go get -u github.com/gin-gonic/gin # 下载安装

go run example.go # 开启Web服务

```

```go

package main
import "github.com/gin-gonic/gin"
func main() {
	print("aa")
	r := gin.Default()
	r.GET("/", func(c *gin.Context) {
		c.JSON(200, gin.H{
			"message": "pong",
		})
	})
	r.Run()
}


```