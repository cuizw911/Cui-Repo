# vagrant中centos7的配置
---
### 1. 更换yum国内源

* 备份
```bash
mv /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo.backup
```

* 下载
```bash
curl -o /etc/yum.repos.d/CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-7.repo
```

* 生成缓存
```bash
yum makecache
```

### 2. 基础命令安装
```bash
sudo yum install wget

sudo yum install vim
```

### 3. Go环境安装配置
* 下载安装包
```bash
wget https://dl.google.com/go/go1.14.1.linux-amd64.tar.gz
```

* 解压
```bash
sudo tar -C /usr/local -xzf go1.4.2.linux-amd64.tar.gz
```

* 创建gopath目录
Vagrant启动后,会默认把Vagrant这个目录挂载到系统的/vagrant目录，因此我们设置GOPATH到该目录：
```bash
cd ~
mkdir /vagrant/gopath
```

切换到用户目录，打开bashrc进行设置GOPATH，并将GOPATH添加到PATH中：
```
vim ~/.bashrc

export GOPATH=/vagrant/gopath
export PATH=$PATH:/usr/local/go/bin:$GOPATH/bin
```

设置完成后,使用`source`命令使其生效
```
source ~/.bashrc
```

执行`go env`命令查看
```
GO111MODULE=""                                                                                                     
GOARCH="amd64"                                                                                                     
GOBIN=""                                                                                                           
GOCACHE="/home/vagrant/.cache/go-build"                                                                            
GOENV="/home/vagrant/.config/go/env"                                                                               
GOEXE=""                                                                                                           
GOFLAGS=""                                                                                                         
GOHOSTARCH="amd64"                                                                                                 
GOHOSTOS="linux"                                                                                                   
GOINSECURE=""                                                                                                      
GONOPROXY=""                                                                                                       
GONOSUMDB=""                                                                                                       
GOOS="linux"                                                                                                       
GOPATH="/vagrant/gopath"                                                                                           
GOPRIVATE=""                                                                                                       
GOPROXY="https://proxy.golang.org,direct"                                                                          
GOROOT="/usr/local/go"                                                                                             
GOSUMDB="sum.golang.org"                                                                                           
GOTMPDIR=""                                                                                                        
GOTOOLDIR="/usr/local/go/pkg/tool/linux_amd64"                                                                     
GCCGO="gccgo"                                                                                                      
AR="ar"                                                                                                            
CC="gcc"                                                                                                           
CXX="g++"                                                                                                          
CGO_ENABLED="1"                                                                                                    
GOMOD=""                                                                                                           
CGO_CFLAGS="-g -O2"                                                                                                
CGO_CPPFLAGS=""                                                                                                    
CGO_CXXFLAGS="-g -O2"                                                                                              
CGO_FFLAGS="-g -O2"                                                                                                
CGO_LDFLAGS="-g -O2"                                                                                               
PKG_CONFIG="pkg-config"                                                                                            
GOGCCFLAGS="-fPIC -m64 -pthread -fno-caret-diagnostics -Qunused-arguments -fmessage-length=0 -fdebug-prefix-map=/tm
build295842250=/tmp/go-build -gno-record-gcc-switches"                                                             
```


参考来源
---
[《Go语言开发环境配置》](https://github.com/astaxie/go-best-practice/blob/master/ebook/zh/01.0.md)
