---
title: XDbot2 Cave API
date: 2023-06-18 15:18:43
categories: 项目
tags: XDbot2
---

## 请求地址

- [https://caveapi.thisisxd.top](https://caveapi.thisisxd.top)
- [https://caveapi.xdbot2.itcdt.top/](https://caveapi.xdbot2.itcdt.top/)

## 接口列表

### 随机回声洞

获取一个随机的回声洞内容，包括发送者和文本。

|  终结点      | 返回类型                |
|----------------|--------------------------|
| `/v1`           | `application/json` 或 `text/javascript` |

#### 参数

| 参数                | 必须                       | 说明                                  |
|--------------------|--------------------------|----------------------------------|
| `return`           | 否（默认 `json`）| 返回类型（`json`/`js`）  |
| `caveIdVar`    | 否                           | 回声洞ID常量名（默认`cave_id`） |
| `caveContentVar` | 否                   | 回声洞内容常量名（默认`cave_content`） |
| `caveSenderVar`   | 否                   | 回声洞投稿者常量名（默认`cave_sender`） |


#### 返回示例

请求：

```text
https://caveapi.xdbot2.itcdt.top/v1
```

响应：

```json
{"id":538,"sender":"IP:127.0.0.1","content":"风急天高猿啸哀，尚思为国戍轮台。夜兰卧听风吹雨，神里绫华入梦来\n\n—— 哔哩哔哩·UID506743561"}
```

请求：

```text
https://caveapi.thisisxd.top/v1?return=js
```

响应：

```javascript
const cave_id = "984"
const cave_content = "“皇上，奇变偶不变”\n“可以了可以了，我知道你要说啥了，去一下隔壁那旮沓，那里边一大堆穿越者，他们正在研究马克思主义，朕这边已经准备好改革开放了，你们赶紧研究研究怎么最快的切换到中国特色社会主义，赶紧”"
const cave_sender = "IP:127.0.0.1"
```



### 获取回声洞图片

获取一个指定ID的回声洞图片，以PNG格式返回。

| 终结点 | 返回类型 |
|-----------------------|--------------------------|
| `/v1/getImage` | `image/png` |

#### 参数

| 参数 | 必填 | 说明 |
|--------------------|------------------------|----------------------------------------------------------------|
| `id` | 是 | 图片ID（回声洞内容中的 `[[Img:<图片ID>]]`）|

#### 返回示例

请求：

```text
https://api.cave.xdbot2.itcdt.top/v1/getImage?id=1679146457.165848
```

响应：

![图片](https://github.com/ITCraftDevelopmentTeam/Forum/assets/104149371/06b5ba35-fe83-4e46-bff6-af112748b9d6)

### 获取 API 版本

获取当前API的版本号，以纯文本格式返回。

| 终结点 | 返回类型 |
|-----------------------|--------------------------|
| `/v1/version` | `text/plain` |

#### 参数

无

#### 返回示例

请求：

```text
https://api.cave.xdbot2.itcdt.top/v1/version
```

响应：

```text
v1.0.0-beta
```
