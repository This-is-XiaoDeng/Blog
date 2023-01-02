---
title: XChat Server V1.2-beta
date: 2022-08-07 12:47:00
categories: 项目
tags:
---

<gb>This-is-XiaoDeng/XChat</gb>

## 简介
> 版本：V1.2-beta

XChat Server 是软件 XChat 的服务端，可以让您在1分钟内拥有一个自己的 XChat 服务器。

## 依赖

1. Python3
2. rich

## 使用教程

1. 安装依赖，打开 XChat Server
2. 输入端口
3. 完成

## 源代码

```python
from rich.console import Console
import socket
import json
import threading
import time

console = Console()
threads = {}
messages = [
    {"from":"Server","msg":"Server Started","time":time.time()}
]
threadList = []
users = {}

def handle(sock, addr):
    global console, messages, threads, threadList, users
    msgid = 0
    username = ""

    while True:
        resp_data = {
            "code":200,
            "msg":"OK",
            "data":{}
        }

        recv_data = sock.recv(1024)
        try:
            recv_data = recv_data.decode("utf-8")
            recv_data = json.loads(recv_data)

            if username != "":
                if recv_data["mode"] == "getMsg":
                    try:
                        resp_data["data"]["messages"] = messages[msgid:]
                        msgid = messages.__len__()
                    except:
                        resp_data["data"]["messages"] = []
                elif recv_data["mode"] == "sendMsg":
                    messages += [
                        {
                            "from":username,
                            "msg":recv_data["data"]["msg"],
                            "time":time.time()
                        }
                    ]
                    console.log(f"[CHAT] <{username}> {recv_data['data']['msg']}")

                elif recv_data["mode"] == "exit":
                    sock.close()
                    return 0

                elif recv_data["mode"] == "getList":
                    userList = []
                    for t in threadList:
                        if threads[t].is_alive():
                            userList += [users[t].getName()]
                    resp_data["data"]["list"] = userList


                else:
                    resp_data["code"] = 404
                    resp_data["msg"] = "Unkown mode"

            elif recv_data["mode"] == "login":
                username = recv_data["data"]["username"]
                # threads[addr[1]].setName(username)
                users[addr[1]] = username

            else:
                resp_data["code"] = 403
                resp_data["msg"] = "Please Login First"


        except Exception as e:
            console.print_exception(show_locals=True)
            resp_data["code"] = 500
            resp_data["msg"] = "Internal Server Error"
            resp_data["data"]["exception"] = str(e)

        # 回复
        resp_data = json.dumps(resp_data)
        sock.send(resp_data.encode("utf-8"))



if __name__ == "__main__":
    port = int(console.input("[blue]Port: "))

    sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    sock.bind(
        (
            "",
            port
        )
    )
    sock.listen(128)

    console.log(f"Server started on 0.0.0.0:{port}.")

    while True:
        s, addr = sock.accept()
        console.log(f"{addr[1]} connected to this server.")
        threadList += [addr[1]]
        users[addr[1]] = ""

        threads[addr[1]] = threading.Thread(None, lambda: handle(s, addr))
        threads[addr[1]].setDaemon(True)
        threads[addr[1]].start()
```

