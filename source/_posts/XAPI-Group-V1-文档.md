---
title: XAPI-Group V1 文档
date: 2022-06-21 19:08:00
categories: 教程
tags:
---

> 温馨提示：本文可能已经**过时**

<!-- wp:list -->
<ul><li>更新日期：June 21st 2022, Tuesday</li><li>API版本： V1</li><li>运行状态：正常</li></ul>
<!-- /wp:list -->

<!-- wp:table {"className":"is-style-stripes","fontSize":"small"} -->
<figure class="wp-block-table is-style-stripes has-small-font-size"><table><tbody><tr><td>接口名称</td><td>请求方式</td><td>URL</td><td>参数</td><td>说明</td></tr><tr><td>Cave Json Data</td><td>GET</td><td>http://124.222.63.135:8000/</td><td>/</td><td>将ITCraft cave数据（ini）使用JSON格式输出<br>源数据由 xxtg666 提供</td></tr><tr><td>随机回声洞数据</td><td>GET</td><td>http://124.222.63.135:8001/</td><td>/</td><td>从Cave Json Data中随机选取一项回声洞数据返回<br>已屏蔽所有数据删除及图片</td></tr><tr><td>镜像</td><td>GET</td><td>http://124.222.63.135:8002/&lt;url&gt;/</td><td>&lt;url&gt;：原网页</td><td>一个没有任何用处的镜像站， 一般人访问不了的这玩意也访问不了</td></tr><tr><td>随机回声洞文本</td><td>GET</td><td>http://124.222.63.135:8192/</td><td>/</td><td>在 随机回声洞数据 的基础上只返回回声洞的内容</td></tr></tbody></table></figure>
<!-- /wp:table -->

<!-- wp:paragraph {"backgroundColor":"white"} -->
<p class="has-white-background-color has-background">备注：所有接口服务器编码默认采用 <mark style="background-color:rgba(0, 0, 0, 0)" class="has-inline-color has-vivid-green-cyan-color">UTF-8</mark></p>
<!-- /wp:paragraph -->
