---
title: 【接单日志 01】txtx解析工具
date: 2021-11-28 13:36:00
categories: 小记
tags:
---

> 温馨提示：程序接单目前已经**不再开放**，但您仍然可以在issue中为新项目提供想法

<!-- wp:heading -->
<h2>详细信息</h2>
<!-- /wp:heading -->

<!-- wp:list -->
<ul><li>单号：PYLIB-ORD-20211101</li><li>委托人（QQ）：3627035438</li><li>项目：TXTX解析工具</li><li>类型：Python库-ORD</li><li>收费：1.0/1.0 CNY（付款方式：QQ）</li></ul>
<!-- /wp:list -->

<!-- wp:heading -->
<h2>代码：</h2>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>./txtx.py</p>
<!-- /wp:paragraph -->

<!-- wp:code -->
<pre class="wp-block-code"><code># Powered By XD(www.thisisxd.tk)
import os

def delzhushi(l,start = 0):
    s = l&#91;start].find("#")
    li = l
    if s != -1:
        li&#91;start] = li&#91;start]&#91;0:s]
    if start == l.__len__()-1:
        return li
    else:
        return delzhushi(li,start+1)

def run(txt):
    t = txt
    le = 0
    for tx in t:
        where_w = tx.find("&#91;Run_Windows]")
        where_u = tx.find("&#91;Run_Unix](")
        if os.name == "nt":
            if where_w != -1:
                t.pop(le)
                #print(tx&#91;where_w+14:tx.find(")",where_w)])
                os.popen(tx&#91;where_w+14:tx.find(")",where_w)])
        else:
            if where_u != -1:
                t.pep(le)
                os.popen(tx&#91;where_u+14:tx.find(")",where_u)])
        le += 1
    return t

def get_home(txtx):
    tx = txtx
    l = 0
    for t in tx:
        w = t.find("&lt;&#91;")
        if w != -1:
            home = t&#91;w+2:t.find("]",w)]
            for i in range(l):
                tx.pop(0)
            if  home == "":
                raise TypeError("跟声明不能为空")
            else:
                return tx,home

def load(t):
    txtx = {}
    # 逐行分割
    t1 = t.split("\n")
    # 删除注释
    t1 = delzhushi(t1)
    # 跑命令
    t1 = run(t1)
    # 获取跟声明
    temp = get_home(t1)
    t1 = temp&#91;0]
    home = temp&#91;1]
    # 解析
    f = 1
    s = 0
    tw = &#91;False]
    tg = False
    txtx&#91;home] = {}
    y = 0
    for t in t1:
        s += 1
        temp = {}
        k_start = t.find("&#91;")
        if k_start != -1 and tg == False and t.find("&lt;&#91;") == -1:
            k_end = t.find("]",k_start)
            if k_end != -1:
                v_start = t.find("(",k_end)
                if v_start != -1:
                    v_end = t.find(")",v_start)
                    if v_end == -1:
                        raise KeyError(f"行0{s}：这个值没有结尾")
                else:
                     raise KeyError(f"行0{s}：一个没有意义的键")
            else:
                raise KeyError(f"行0{s}：这个键没有结尾")
            # 能执行到这里这行基本就是有效的了
            print(1,t.find("&lt;&#91;"),tg,home)
            # 分析键
            key = t&#91;k_start+1:k_end]
            value = t&#91;v_start+1:v_end]
            # 储存
            txtx&#91;home]&#91;key] = value
        else:
            tmp = t.find("&lt;&#91;")
            if tmp != -1 and t&#91;tmp+2:t.find("]",tmp)] != home:
                tg = True
                tw&#91;0] = True
                if y != 1:
                    tw  += &#91;&#91;s,t&#91;tmp+2:t.find("]",tmp)]]]
                y += 1
            elif t.find(">") != -1:
                tg = False
                if y == 1:
                    try:
                        tw&#91;tw.__len__()-1] += &#91;s]
                    except:
                        pass
                    y -= 1
                else:
                    y -= 1
                print(t&#91;tmp:t.find("]",tmp)],tw)
            print("y",y)
    if tw&#91;0] == True:
        for tn in tw:
            print("tn",tn,t1)
            if tn != True:
                cs = ""
                for i in t1&#91;tn&#91;0]-1:tn&#91;2]]:
                    cs += str(i)
                    cs += "\n"
                print("cs",cs)
                print("递归后输出：")
                # txtx&#91;home]&#91;t&#91;2]] = load(cs)
                tmp114514  =  load(cs)
                print(tmp114514)
                txtx&#91;home]&#91;tmp114514&#91;1]] = tmp114514&#91;0]&#91;tn&#91;1]]#&#91;&#91;tmp114514&#91;1]]]   #&#91;tmp114514&#91;1]]
    else:
        print("ELSE")
                
        
    # 返回
    return &#91;txtx,home]

def loads(txtx):
    return load(txtx)&#91;0]

def open(path,encoding = "utf-8"):
    with open(path,encoding = encoding) as f:
        return loads(f.read())
</code></pre>
<!-- /wp:code -->

<!-- wp:heading -->
<h2>用法</h2>
<!-- /wp:heading -->

<!-- wp:code -->
<pre class="wp-block-code"><code>import txtx</code></pre>
<!-- /wp:code -->

<!-- wp:table -->
<figure class="wp-block-table"><table><tbody><tr><td>函数</td><td>参数</td><td>函数描述</td><td>返回说明</td></tr><tr><td>txtx.open(path,ecoding="utf-8")</td><td>[path] txtx文件路径 (String)<br>[encoding] 文件编码（默认=utf-8）(string)</td><td>打开txtx文件</td><td>返回解析结果（dictionary）</td></tr><tr><td>txtx.loads(txtx)</td><td>[txtx] txtx内容 (String)</td><td>解析txtx字符串</td><td>返回解析结果（dictionary）</td></tr></tbody></table><figcaption>txtx解析器主要函数说明</figcaption></figure>
<!-- /wp:table -->

<!-- wp:paragraph -->
<p></p>
<!-- /wp:paragraph -->
