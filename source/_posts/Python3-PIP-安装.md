---
title: Python3 PIP 安装
date: 2021-12-11 15:11:00
categories: 教程
tags:
---

<!-- wp:quote {"align":"left","className":"is-style-large"} -->
<blockquote class="wp-block-quote has-text-align-left is-style-large"><p>pip is the <a href="https://packaging.python.org/guides/tool-recommendations/">package installer for Python</a>. You can use it to install packages from the <a href="https://pypi.org/">Python Package Index</a> and other indexes.</p><cite>——pip.pypa.io</cite></blockquote>
<!-- /wp:quote -->

<!-- wp:paragraph -->
<p>鲁迅先生曾经说过这样一句话：“没有pip的Python是没有灵魂的（是不是有点过了）。”</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>但是，很多人在使用pip的时候，或多或少会遇到这种情况：</p>
<!-- /wp:paragraph -->

<!-- wp:code -->
<pre class="wp-block-code"><code>&#91;xiaodeng@xd-pc ~]$ python3 -m pip
/usr/bin/python3: No module named pip</code></pre>
<!-- /wp:code -->

<!-- wp:paragraph -->
<p>如果你遇到了这个提示，那么恭喜你，你  的  Python  没  装  pip！</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>其实，这种情况很好解决，但是我曾经也被整的晕头转向，话不多说，上解决方案！</p>
<!-- /wp:paragraph -->

<!-- wp:heading -->
<h2>解决方案</h2>
<!-- /wp:heading -->

<!-- wp:heading {"level":3} -->
<h3>通用</h3>
<!-- /wp:heading -->

<!-- wp:list {"ordered":true} -->
<ol><li>下载<a href="https://bootstrap.pypa.io/get-pip.py">https://bootstrap.pypa.io/get-pip.py</a>;</li><li>执行</li></ol>
<!-- /wp:list -->

<!-- wp:heading {"level":3} -->
<h3>Linux</h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>可以吧这一段代码复制到终端执行：</p>
<!-- /wp:paragraph -->

<!-- wp:code -->
<pre class="wp-block-code"><code>wget https://bootstrap.pypa.io/get-pip.py
python3 ./get-pip.py
rm ./get-pip.py</code></pre>
<!-- /wp:code -->

<!-- wp:paragraph -->
<p>输出（因人而异）：</p>
<!-- /wp:paragraph -->

<!-- wp:code -->
<pre class="wp-block-code"><code>&#91;xiaodeng@xd-pc ~]$ wget https://bootstrap.pypa.io/get-pip.py
--2021-12-11 15:07:06--  https://bootstrap.pypa.io/get-pip.py
SSL_INIT
已载入 CA 证书“/etc/ssl/certs/ca-certificates.crt”
正在解析主机 bootstrap.pypa.io (bootstrap.pypa.io)... 151.101.76.175, 2a04:4e42:12::175
正在连接 bootstrap.pypa.io (bootstrap.pypa.io)|151.101.76.175|:443... 已连接。
已发出 HTTP 请求，正在等待回应... 200 OK
长度：2159352 (2.1M) &#91;text/x-python]
正在保存至: “get-pip.py”

get-pip.py          100%&#91;===================>]   2.06M  3.34MB/s  用时 0.6s    

2021-12-11 15:07:07 (3.34 MB/s) - 已保存 “get-pip.py” &#91;2159352/2159352])

&#91;xiaodeng@xd-pc ~]$ python3 ./get-pip.py
Defaulting to user installation because normal site-packages is not writeable
Collecting pip
  Downloading pip-21.3.1-py3-none-any.whl (1.7 MB)
     |████████████████████████████████| 1.7 MB 1.7 MB/s            
Collecting wheel
  Downloading wheel-0.37.0-py2.py3-none-any.whl (35 kB)
Installing collected packages: wheel, pip
Successfully installed pip-21.3.1 wheel-0.37.0
&#91;xiaodeng@xd-pc ~]$ rm ./get-pip.py
&#91;xiaodeng@xd-pc ~]$ </code></pre>
<!-- /wp:code -->

<!-- wp:heading {"level":3} -->
<h3>验证安装</h3>
<!-- /wp:heading -->

<!-- wp:code -->
<pre class="wp-block-code"><code>&#91;xiaodeng@xd-pc ~]$ python3 -m pip

Usage:   
  /usr/bin/python3 -m pip &lt;command> &#91;options]

Commands:
  install                     Install packages.
  download                    Download packages.
  uninstall                   Uninstall packages.
  freeze                      Output installed packages in requirements format.
  list                        List installed packages.
  show                        Show information about installed packages.
  check                       Verify installed packages have compatible dependencies.
  config                      Manage local and global configuration.
  search                      Search PyPI for packages.
  cache                       Inspect and manage pip's wheel cache.
  index                       Inspect information available from package indexes.
  wheel                       Build wheels from your requirements.
  hash                        Compute hashes of package archives.
  completion                  A helper command used for command completion.
  debug                       Show information useful for debugging.
  help                        Show help for commands.

General Options:
  -h, --help                  Show help.
  --debug                     Let unhandled exceptions propagate outside the
                              main subroutine, instead of logging them to
                              stderr.
  --isolated                  Run pip in an isolated mode, ignoring
                              environment variables and user configuration.
  -v, --verbose               Give more output. Option is additive, and can be
                              used up to 3 times.
  -V, --version               Show version and exit.
  -q, --quiet                 Give less output. Option is additive, and can be
                              used up to 3 times (corresponding to WARNING,
                              ERROR, and CRITICAL logging levels).
  --log &lt;path>                Path to a verbose appending log.
  --no-input                  Disable prompting for input.
  --proxy &lt;proxy>             Specify a proxy in the form
                              &#91;user:passwd@]proxy.server:port.
  --retries &lt;retries>         Maximum number of retries each connection should
                              attempt (default 5 times).
  --timeout &lt;sec>             Set the socket timeout (default 15 seconds).
  --exists-action &lt;action>    Default action when a path already exists:
                              (s)witch, (i)gnore, (w)ipe, (b)ackup, (a)bort.
  --trusted-host &lt;hostname>   Mark this host or host:port pair as trusted,
                              even though it does not have valid or any HTTPS.
  --cert &lt;path>               Path to PEM-encoded CA certificate bundle. If
                              provided, overrides the default. See 'SSL
                              Certificate Verification' in pip documentation
                              for more information.
  --client-cert &lt;path>        Path to SSL client certificate, a single file
                              containing the private key and the certificate
                              in PEM format.
  --cache-dir &lt;dir>           Store the cache data in &lt;dir>.
  --no-cache-dir              Disable the cache.
  --disable-pip-version-check
                              Don't periodically check PyPI to determine
                              whether a new version of pip is available for
                              download. Implied with --no-index.
  --no-color                  Suppress colored output.
  --no-python-version-warning
                              Silence deprecation warnings for upcoming
                              unsupported Pythons.
  --use-feature &lt;feature>     Enable new functionality, that may be backward
                              incompatible.
  --use-deprecated &lt;feature>  Enable deprecated functionality, that will be
                              removed in the future.
&#91;xiaodeng@xd-pc ~]$ 
</code></pre>
<!-- /wp:code -->
