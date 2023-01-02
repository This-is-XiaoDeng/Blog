---
title: XLogger
date: 2022-03-25 20:30:00
categories: 项目
tags:
---

<!-- wp:quote -->
<blockquote class="wp-block-quote"><p>By 这里是小邓</p></blockquote>
<!-- /wp:quote -->

<!-- wp:heading -->
<h2><a href="https://gitee.com/This-is-XiaoDeng/xpy-logger#%E4%BB%8B%E7%BB%8D"></a>介绍</h2>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>XPyLogger 是提供了一个开箱即用的日志库，较好的解决了Python 自带 logging 库使用繁琐，函数玄学的问题，支持 rich 库彩色输出。</p>
<!-- /wp:paragraph -->

<!-- wp:quote -->
<blockquote class="wp-block-quote"><p>项目原名 XLogger，后因重名，故改名为 XPyLogger</p></blockquote>
<!-- /wp:quote -->

<!-- wp:heading -->
<h2><a href="https://gitee.com/This-is-XiaoDeng/xpy-logger#%E4%BE%9D%E8%B5%96"></a>依赖</h2>
<!-- /wp:heading -->

<!-- wp:list {"ordered":true} -->
<ol><li>Python (3.9+)</li><li>Rich</li></ol>
<!-- /wp:list -->

<!-- wp:heading -->
<h2><a href="https://gitee.com/This-is-XiaoDeng/xpy-logger#%E7%BC%96%E8%AF%91%E6%AD%A5%E9%AA%A4"></a>编译步骤</h2>
<!-- /wp:heading -->

<!-- wp:heading {"level":3} -->
<h3><a href="https://gitee.com/This-is-XiaoDeng/xpy-logger#git"></a>GIT</h3>
<!-- /wp:heading -->

<!-- wp:list {"ordered":true} -->
<ol><li>克隆 XPyLogger</li><li>放入程序文件夹</li><li>安装<code>rich</code>：</li></ol>
<!-- /wp:list -->

<!-- wp:code -->
<pre class="wp-block-code"><code>pip install rich</code></pre>
<!-- /wp:code -->

<!-- wp:list {"ordered":true,"start":4} -->
<ol start="4"><li><code>from XPyLogger import *</code></li></ol>
<!-- /wp:list -->

<!-- wp:heading {"level":3} -->
<h3><a href="https://gitee.com/This-is-XiaoDeng/xpy-logger#pip"></a>PIP</h3>
<!-- /wp:heading -->

<!-- wp:code -->
<pre class="wp-block-code"><code>pip install XPyLogger</code></pre>
<!-- /wp:code -->

<!-- wp:heading -->
<h2><a href="https://gitee.com/This-is-XiaoDeng/xpy-logger#%E5%87%BD%E6%95%B0%E4%BB%8B%E7%BB%8D"></a>函数介绍</h2>
<!-- /wp:heading -->

<!-- wp:heading {"level":3} -->
<h3><a href="https://gitee.com/This-is-XiaoDeng/xpy-logger#xpyloggerlogmsg-level--info-sender--sender_main"></a>XPyLogger.log(msg, level = INFO, sender = SENDER_MAIN)</h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>输出一条日志</p>
<!-- /wp:paragraph -->

<!-- wp:list -->
<ul><li>msg：log信息</li><li>level：日志等级</li><li>sender：发送者</li></ul>
<!-- /wp:list -->

<!-- wp:heading {"level":3} -->
<h3><a href="https://gitee.com/This-is-XiaoDeng/xpy-logger#xpyloggerclose"></a>XPyLogger.close()</h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>关闭日志本地记录文件</p>
<!-- /wp:paragraph -->

<!-- wp:heading {"level":3} -->
<h3><a href="https://gitee.com/This-is-XiaoDeng/xpy-logger#xpyloggerinfo"></a>XPyLogger.INFO</h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>日志等级-信息</p>
<!-- /wp:paragraph -->

<!-- wp:heading {"level":3} -->
<h3><a href="https://gitee.com/This-is-XiaoDeng/xpy-logger#xpyloggerwarn"></a>XPyLogger.WARN</h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>日至等级-警告</p>
<!-- /wp:paragraph -->

<!-- wp:heading {"level":3} -->
<h3><a href="https://gitee.com/This-is-XiaoDeng/xpy-logger#xpyloggererr"></a>XPyLogger.ERR</h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>日志等级-错误</p>
<!-- /wp:paragraph -->

<!-- wp:heading {"level":3} -->
<h3><br>XPyLogger.init(file_enable = True,file_name = int(time.time()),dir_name = "logs")</h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>自定义初始化log对象</p>
<!-- /wp:paragraph -->

<!-- wp:list -->
<ul><li>file_enable：是否启用文件记录</li><li>file_name：日志文件名(不含.log)</li><li>dir_name：日志文件夹名</li></ul>
<!-- /wp:list -->

<!-- wp:heading -->
<h2><a href="https://gitee.com/This-is-XiaoDeng/xpy-logger#demo"></a>Demo</h2>
<!-- /wp:heading -->

<!-- wp:code -->
<pre class="wp-block-code"><code><strong>import</strong> <strong>XPyLogger</strong> <strong>as</strong> log
log.init(file_enable = False)
log.log("This is a information!",log.INFO)
log.log("This is a warning!",log.WARN)
log.log("This is a error!",log.ERR)
log.close()</code></pre>
<!-- /wp:code -->
