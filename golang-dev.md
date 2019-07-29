# IDE
[Visual Studio Code](https://code.visualstudio.com/)

# 入门书籍
1. [Go语言程序设计](https://github.com/gopl-zh/gopl-zh.github.com "需要Go和Gitbook编译")
2. Go语言实战

# 进阶书籍
1. [Go语言高级编程](https://github.com/chai2010/advanced-go-programming-book)

# 团队开发
1. [Effective Go](https://golang.org/doc/effective_go.html)
2. [CodeReviewComments](https://github.com/golang/go/wiki/CodeReviewComments)

# 补充知识

- `golang.org/x/`包的镜像地址为`github.com/golang/`
  - Windows 目录联接

        mklink /J %GOPATH%\src\golang.org\x %GOPATH%\src\github.com\golang

  - Linux 软连接

        ln -s $GOPATH/src/github.com/golang $GOPATH/src/golang.org/x

  - 下载示例 / [vscode-go extension](https://github.com/Microsoft/vscode-go/wiki/Go-tools-that-the-Go-extension-depends-on)

        git clone https://github.com/golang/text %GOPATH%/src/github.com/golang/text
        git clone https://github.com/golang/crypto %GOPATH%/src/github.com/golang/crypto
        git clone https://github.com/golang/net %GOPATH%/src/github.com/golang/net
        git clone https://github.com/golang/tools %GOPATH%/src/github.com/golang/tools
        git clone https://github.com/golang/sys %GOPATH%/src/github.com/golang/sys
        git clone https://github.com/golang/lint %GOPATH%/src/github.com/golang/lint

        #vscode-go
        go get -u -v github.com/go-delve/delve/cmd/dlv
        go get -u -v github.com/ramya-rao-a/go-outline
        go get -u -v github.com/acroca/go-symbols
        go get -u -v github.com/mdempsky/gocode
        go get -u -v github.com/rogpeppe/godef
        go get -u -v github.com/golang/tools/cmd/godoc
        go get -u -v github.com/zmb3/gogetdoc
        go get -u -v github.com/golang/lint/golint
        go get -u -v github.com/fatih/gomodifytags
        go get -u -v github.com/golang/tools/cmd/gorename
        go get -u -v github.com/sqs/goreturns
        go get -u -v github.com/golang/tools/cmd/goimports
        go get -u -v github.com/cweill/gotests/...
        go get -u -v github.com/golang/tools/cmd/guru
        go get -u -v github.com/josharian/impl
        go get -u -v github.com/haya14busa/goplay/cmd/goplay
        go get -u -v github.com/uudashr/gopkgs/cmd/gopkgs
        go get -u -v github.com/davidrjenni/reftools/cmd/fillstruct
        go get -u -v github.com/alecthomas/gometalinter
        gometalinter --install
