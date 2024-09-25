+++
title = "GO微服务开发环境搭建"
date = 2024-09-25

[taxonomies]
categories = ["笔记"]
tags = ["私人", "GO", "微服务"]
+++

# 依赖环境
- 开发工具：neovim 0.10.1
- go版本：1.23.1

# 工程环境
```bash
mkdir gomall && cd gomall
mkdir helloworld && cd gomall
go mod init github.com/echemoo/gomall/helloworld
go get -u github.com/cloudwego/hertz
touch main.go
vim main.go
# 编写文件
go mod tidy
go run main.go
```  
main.go文件内容：
```go
package main

import (
	"context"

	"github.com/cloudwego/hertz/pkg/app"
	"github.com/cloudwego/hertz/pkg/app/server"

	// "github.com/cloudwego/hertz/pkg/common/utils"
	"github.com/cloudwego/hertz/pkg/protocol/consts"
)

func main() {
	h := server.Default()

	h.GET("/hello", func(ctx context.Context, c *app.RequestContext) {
		// c.JSON(consts.StatusOK, utils.H{"message": "pong"})
		c.Data(consts.StatusOK, consts.MIMETextPlain, []byte("hello world!"))
	})

	h.Spin()
}
```
