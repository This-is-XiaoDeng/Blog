---
title: PyFinder
date: 2022-02-27 14:20:00
categories: 项目
tags:
---

<!-- wp:heading {"level":3} -->
<h3><a href="https://gitee.com/This-is-XiaoDeng/py-finder/blob/master/README.md#%E4%BB%8B%E7%BB%8D"></a>介绍</h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>PyFinder是由 这里是小邓 编写的一个 Python 本地文件查找解决方案。此库支持传统递归查找和多线程查找，是Python文件查找较好的解决方案之一。</p>
<!-- /wp:paragraph -->

<!-- wp:heading {"level":3} -->
<h3>仓库</h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p><a href="https://gitee.com/This-is-XiaoDeng/py-finder">https://gitee.com/This-is-XiaoDeng/py-finder</a></p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>PS：有条件的建议直接去仓库看，毕竟下文是我从README.md照搬的</p>
<!-- /wp:paragraph -->

<!-- wp:list -->
<ul><li>注意：此项目目前未以【PyFinder】上传至pypi，至于pypi那个PyFinder只是重名了而已</li></ul>
<!-- /wp:list -->

<!-- wp:heading {"level":3} -->
<h3><a href="https://gitee.com/This-is-XiaoDeng/py-finder/blob/master/README.md#%E8%BD%AF%E4%BB%B6%E6%9E%B6%E6%9E%84"></a>软件架构</h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>主要文件结构：</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>py-finder</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>|-README.md 自述文件</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>|- pyfinder.py 主库文件</p>
<!-- /wp:paragraph -->

<!-- wp:heading {"level":3} -->
<h3><a href="https://gitee.com/This-is-XiaoDeng/py-finder/blob/master/README.md#%E5%AE%89%E8%A3%85%E6%96%B9%E6%B3%95"></a>安装方法</h3>
<!-- /wp:heading -->

<!-- wp:list {"ordered":true} -->
<ol><li>克隆本仓库</li></ol>
<!-- /wp:list -->

<!-- wp:preformatted -->
<pre class="wp-block-preformatted">git clone https://gitee.com/This-is-XiaoDeng/py-finder.git</pre>
<!-- /wp:preformatted -->

<!-- wp:list {"ordered":true,"start":2} -->
<ol start="2"><li>将<code>pyfinder.py</code>复制到（您要使用这个库的程序）的目录下</li><li>导入库</li></ol>
<!-- /wp:list -->

<!-- wp:preformatted -->
<pre class="wp-block-preformatted"><strong>import</strong> <strong>pyfinder</strong></pre>
<!-- /wp:preformatted -->

<!-- wp:paragraph -->
<p>or</p>
<!-- /wp:paragraph -->

<!-- wp:preformatted -->
<pre class="wp-block-preformatted"><strong>from</strong> <strong>pyfinder</strong> <strong>import</strong> *</pre>
<!-- /wp:preformatted -->

<!-- wp:heading {"level":3} -->
<h3><a href="https://gitee.com/This-is-XiaoDeng/py-finder/blob/master/README.md#%E4%BD%BF%E7%94%A8%E8%AF%B4%E6%98%8E"></a>使用说明</h3>
<!-- /wp:heading -->

<!-- wp:quote -->
<blockquote class="wp-block-quote"><p>我之后会上传几个Demo，到时候问题就不大了</p></blockquote>
<!-- /wp:quote -->

<!-- wp:heading {"level":4} -->
<h4><a href="https://gitee.com/This-is-XiaoDeng/py-finder/blob/master/README.md#%E5%87%BD%E6%95%B0%E5%88%97%E8%A1%A8"></a>函数列表</h4>
<!-- /wp:heading -->

<!-- wp:table -->
<figure class="wp-block-table"><table><thead><tr><th>函数</th><th>参数列表</th><th>支持最大文件夹深度</th><th>说明</th><th>返回值</th></tr></thead><tbody><tr><td>find()</td><td>name = 文件名关键字 start=起始目录 wait=防死机等级(默认0.1)</td><td>无限</td><td>传统单线程递归查找法（不受递归次数约束）</td><td>符合筛选条件的文件路径列表(list)</td></tr><tr><td>find_threads()</td><td>name = 文件名关键字 start=起始目录 wait=防死机等级(默认0.01)</td><td>约800层</td><td>多线程查找法（受<code>threading</code>最大线程影响）</td><td>符合筛选条件的文件路径列表(list)</td></tr></tbody></table></figure>
<!-- /wp:table -->

<!-- wp:heading {"level":4} -->
<h4><a href="https://gitee.com/This-is-XiaoDeng/py-finder/blob/master/README.md#%E8%B0%83%E7%94%A8%E7%A4%BA%E4%BE%8B"></a>调用示例</h4>
<!-- /wp:heading -->

<!-- wp:preformatted -->
<pre class="wp-block-preformatted"><strong>import</strong> <strong>pyfinder</strong>
f = pyfinder.find_threads(name="exe",start="C:\\")
<strong>print</strong>(f)</pre>
<!-- /wp:preformatted -->

<!-- wp:quote -->
<blockquote class="wp-block-quote"><p>千万表像上面那么做，相信我，查找的时候永远也不要让符合筛选的文件过多，会内存溢出的（我就这么做过）</p></blockquote>
<!-- /wp:quote -->

<!-- wp:heading {"level":3} -->
<h3><a href="https://gitee.com/This-is-XiaoDeng/py-finder/blob/master/README.md#%E5%8F%82%E4%B8%8E%E8%B4%A1%E7%8C%AE"></a>参与贡献</h3>
<!-- /wp:heading -->

<!-- wp:list {"ordered":true} -->
<ol><li>Fork 本仓库</li><li>新建 Feat_xxx 分支</li><li>提交代码</li><li>新建 Pull Request</li></ol>
<!-- /wp:list -->

<!-- wp:heading {"level":3} -->
<h3><a href="https://gitee.com/This-is-XiaoDeng/py-finder/blob/master/README.md#%E8%AE%B8%E5%8F%AF%E8%AF%81"></a>许可证</h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>此程序采用 MIT 许可证</p>
<!-- /wp:paragraph -->

<!-- wp:heading {"level":3} -->
<h3><a href="https://gitee.com/This-is-XiaoDeng/py-finder/blob/master/README.md#todo"></a>TODO</h3>
<!-- /wp:heading -->

<!-- wp:list -->
<ul><li>&nbsp;完成多线程查找</li><li>&nbsp;写demo</li><li>&nbsp;打包上pypi</li><li>&nbsp;大力宣传</li><li>&nbsp;修复内存溢出的bug</li></ul>
<!-- /wp:list -->

<!-- wp:heading {"level":3} -->
<h3><a href="https://gitee.com/This-is-XiaoDeng/py-finder/blob/master/README.md#%E8%B4%A1%E7%8C%AE%E5%90%8D%E5%8D%95"></a>贡献名单</h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>代码</p>
<!-- /wp:paragraph -->

<!-- wp:quote -->
<blockquote class="wp-block-quote"><p>这里是小邓</p></blockquote>
<!-- /wp:quote -->

<!-- wp:paragraph -->
<p>调试</p>
<!-- /wp:paragraph -->

<!-- wp:quote -->
<blockquote class="wp-block-quote"><p>这里是小邓 熊熊糖果</p></blockquote>
<!-- /wp:quote -->

<!-- wp:paragraph -->
<p></p>
<!-- /wp:paragraph -->
