---
title: XChat-CLI pre-1
date: 2022-08-07 12:05:00
categories: 项目
tags:
---

> 温馨提示：本文可能已经**过时**

# XChat Client CLI
> 版本：pre-1

## 依赖

1. Python3（Tested 3.10.6）
2. rich

## 简介

XChat 是一个简单好用的聊天软件，它（指原版，给改了不关我事熬）不会收集任何除必须外的用户信息

## 测试服务器

- IP：124.222.63.135
- Port：19180

## 源代码

```python
import socket
from rich.console import Console
import threading
import json
import time

console = Console()
sock = None
sockThread = None

def send(data):
    global sock
    sock.send(
        json.dumps(data).encode("utf-8")
    )

    return json.loads(
        sock.recv(1024).decode("utf-8")
    )

def getMsg():
    global sock, console
    while True:
        msg = send(
            {
                "mode":"getMsg",
                "data":{}
            }
        )
        try:
            for m in msg["data"]["messages"]:
                t = time.strftime(
                    "%H:%M:%S",
                    time.localtime(m["time"])
                )

                console.print(
                    f'[{t}]<[yellow]{m["from"]}[/]> {m["msg"]}'
                )
        except:
            pass

if __name__ == "__main__":
    console.print("[green]XChat CLI V1")
    sock = socket.socket(
            socket.AF_INET,
            socket.SOCK_STREAM
    )

    sock.connect(
        (
            console.input("[yellow]IP: "),
            int(console.input("[yellow]Port: "))
        )
    )

    loginRecv = send(
        {
            "mode":"login",
            "data":{
                "username":console.input(
                    "[yellow]User: "
                )
            }
        }
    )

    if loginRecv["code"] == 200:
        console.print(
            "[green]Server connected!"
        )

        sockThread = threading.Thread(
            None,
            getMsg
        )
        sockThread.start()

        while True:
            sendMsg = console.input("")
            send(
                {
                    "mode":"sendMsg",
                    "data":{
                        "msg":sendMsg
                    }
                }
            )
```
