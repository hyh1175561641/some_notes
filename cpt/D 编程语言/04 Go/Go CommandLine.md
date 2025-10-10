





### Go命令行
Command go https://golang.google.cn/cmd/go/

```
$ go
Go is a tool for managing Go source code.
Go是一个管理go源代码的工具
Usage:用法：

	go <command> [arguments]

The commands are:这些命令有

	bug         start a bug report启动错误报告
	build       compile packages and dependencies编译包和依赖
	clean       remove object files and cached files删除目标文件和缓存文件
	doc         show documentation for package or symbol显示包或符号的文档
	env         print Go environment information打印go环境信息
	fix         update packages to use new APIs更新包以使用新的API
	fmt         gofmt (reformat) package sources
	generate    generate Go files by processing source
	get         add dependencies to current module and install them
	install     compile and install packages and dependencies
	list        list packages or modules列出包或模块
	mod         module maintenance模块的维护
	run         compile and run Go program编译和运行go程序
	test        test packages测试包
	tool        run specified go tool运行指定的go工具
	version     print Go version打印Go版本
	vet         report likely mistakes in packages

Use "go help <command>" for more information about a command.
使用"go help <command>"获取关于该主题的更多信息

Additional help topics:额外的帮助主题

	buildmode   build modes
	c           calling between Go and C  go和c之间的通话
	cache       build and test caching
	environment environment variables
	filetype    file types文件类型
	go.mod      the go.mod file
	gopath      GOPATH environment variable
	gopath-get  legacy GOPATH go get
	goproxy     module proxy protocol
	importpath  import path syntax
	modules     modules, module versions, and more
	module-get  module-aware go get
	module-auth module authentication using go.sum
	module-private module configuration for non-public modules
	packages    package lists and patterns
	testflag    testing flags
	testfunc    testing functions

Use "go help <topic>" for more information about that topic.
使用"go help <topic>"获取关于该主题的更多信息
```







## start a bug report

启动错误报告

go bug









## compile packages and dependencies

编译包和依赖

go build



例子

```
编译源文件，生成一个hello的二进制文件
go build hello.go

如果$GOPATH=/.../go/
/.../go/src/aaa/bbb/ccc/g.go
go build aaa/bbb/ccc
可以直接编译源代码，不需要指定
无论pwd在哪一条路径，都能将编译好的二进制文件放在pwd下

编译时指定二进制文件的路径和名字
go build -o bin/hello aaa/bbb/ccc

```



## remove object files and cached files

删除目标文件和缓存文件

go clean







## show documentation for package or symbol
显示包或符号的文档

go doc

## print Go environment information
打印go环境信息

go env


## update packages to use new APIs
更新包以使用新的API
go fix


## gofmt (reformat) package sources

go fmt


## generate Go files by processing source

go generate


## add dependencies to current module and install them

go get


## compile and install packages and dependencies

go install

用法和build类似

自动创建bin目录和pkg目录




## list packages or modules
列出包或模块

go list

## module maintenance
模块的维护
go mod

### Download modules to local cache



Go mod download

### Edit go.mod from tools or scripts

go mod edit



### Print module requirement graph

go mod graph



### Initialize new module in current directory

go mod init



### Add missing and remove unused modules

go mod tidy



### Make vendored copy of dependencies

go mod vendor



### Verify dependencies have expected content

go mod verify

### Explain why packages or modules are needed

go mod why





## compile and run Go program

编译和运行go程序
go run





例子：

```
运行程序，可以把go源代码当做脚本来运行
go run hello.go
```



## test packages
测试包
go test



## run specified go tool
运行指定的go工具
go tool


## print Go version
打印Go版本
go version



## report likely mistakes in packages

go vet









Build modes

Calling between Go and C

Build and test caching

Environment variables

File types

The go.mod file


# 单词
maintenance 维护 维修 保持
specification 规格 说明书 详述
specified 规定的 指定 详细说明
specify 指定 列举 详细说明
specific 特殊的 特定的 明确的 详细的
depend 依赖 依靠 相信 信赖
dependence 依赖 依靠 信任 信赖
dependencies 依赖性 相关性 管理
mode 模式 方法 风格 时尚
model 模型 典型 
additional 附加的 额外的
topic 主题 题目
usage 使用 用法
instance 实例 情况 建议

