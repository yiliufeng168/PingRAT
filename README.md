# PingRAT
## PingRAT secretly passes C2 traffic through firewalls using ICMP payloads.

## Features:

- Uses ICMP for Command and Control
- Undetectable by most AV/EDR solutions
- Written in Go

## Installation:
[Download](https://github.com/Nemesis0U/PingRAT/releases) the binaries

or build the binaries and you are ready to go:

    $ git clone https://github.com/Nemesis0U/PingRAT.git
    $ go build client.go
    $ go build server.go

## Usage:

### Server:
```
./server -h
Usage of ./server:
  -d string
    	Destination IP address
  -i string
    	Listener (virtual) Network Interface (e.g. eth0)

```

### Client:
```
./client -h
Usage of ./client:
  -d string
    	Destination IP address
  -i string
    	(Virtual) Network Interface (e.g., eth0)
```

## Screenshot:

![screenshot](screenshot.png)


## 运行逻辑

server端发送ICMP请求

client端接收ICMP，提取命令并执行，并将命令结果通过icmp数据包返回

相对应的实战环境为，server端处于内网，client端处于公网

而对于目标处于内网环境的情况下，则需要对代码进行一些修改，由目标发送icmp请求，并等待要执行的命令。


