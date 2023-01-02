---
title: ITCRAFT ECHO CAVE SEARCH
date: 2022-04-15 23:19:19
categories: 项目
tags:
---

> 温馨提示：文本可能已经**过时**

<!-- wp:heading -->
<h2>基础信息</h2>
<!-- /wp:heading -->

<!-- wp:list -->
<ul><li>文件：<code>cave echo.py</code></li><li>大小：1.52KB</li><li>文件类型：Python3代码</li><li>作者：这里是小邓（xiaodeng@thisisxd.tk）</li><li>介绍：此程序可以在ITCRAFT群已投稿回声洞中查找条目，可以避免重复投稿导致管理员工作时间加长和方便cave文字搜索。</li></ul>
<!-- /wp:list -->

<!-- wp:code -->
<pre class="wp-block-code"><code>import urllib.request
import configparser
import os


#r = requests.get('https://www.12306.cn', )

if __name__ == "__main__":
    print("TICRAFT CAVE SEARCH V1.0")
    print("By This is XiaoDeng")
    print("正在加载配置文件，请稍后\n")

    try:
        reqs = request=urllib.request.Request("http://www.thisisxd.tk/files/cave.ini",headers={"User-Agent" : "Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/63.0.3239.132 Safari/537.36 QIHU 360SE"})
        req = urllib.request.urlopen(reqs)
        text = req.read().decode("utf-8")
        with open("config.ini","w",encoding = "utf-8") as f:
            f.write(text)
    except Exception as e:
        print(e)

    proDir = os.path.split(os.path.realpath(__file__))&#91;0]
    configPath = os.path.join(proDir, "config.ini")
    conf = configparser.RawConfigParser(allow_no_value=True)
    conf.read(configPath,encoding = "utf-8")
    #print(open("config.ini",encoding="gbk").read())
    
    while True:
        text = input("请输入搜索内容：")
        l = int(conf.get("配置","回声洞数量"))
        print(f"正在从{l}条回声洞投稿中查找{text}：")
        out = ""
        for i in range(l-1):
            if (text in conf.get(str(i+1),"内容")):
                out += "&#91;"+ str(i+1) +"] "+conf.get(str(i+1),"内容")+" ——"+conf.get(str(i+1),"投稿人")
                out += "\n\n"
        out = out.replace("§","\n")
        print(out,end = "\n\n")
</code></pre>
<!-- /wp:code -->
