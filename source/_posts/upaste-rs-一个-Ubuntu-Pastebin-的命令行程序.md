---
title: 'upaste-rs: 一个 Ubuntu Pastebin 的命令行程序'
date: 2024-02-06 23:51:25
categories: 项目
tags:
---

- 仓库: [This-is-XiaoDeng/upaste-rs][1]
- 许可: [GPL-3.0][2]
- 下载: [Releases]

# 简介

UPaste-Rs 是一个命令行应用程序，允许您更快速的、直接在终端上创建 Paste

# 用法

```bash
upaste-rs [选项] [文本]

参数:
  [文本]  将要提交的文本

Options:
  -s, --syntax <SYNTAX>          语法高亮类型 [默认: text]
  -e, --expiration <EXPIRATION>  过期时间 [默认: ]
  -p, --poster <POSTER>          Ubuntu Pastebin 用户名
  -h, --help                     查看帮助
  -V, --version                  查看版本
```

> 不指定文本时，将从系统默认编辑器输入

# 许可证

```
upaste-rs - A CLI Application for Ubuntu PasteBin
Copyright (C) 2024  XiaoDeng3386, Shirasawa-CN

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program.  If not, see <https://www.gnu.org/licenses/>.
```

[1]: https://github.com/This-is-XiaoDeng/upaste-rs
[2]: https://github.com/This-is-XiaoDeng/upaste-rs/blob/main/LICENSE
[3]: https://github.com/This-is-XiaoDeng/upaste-rs/releases
