---
title: KeyCode Beta 1
date: 2021-12-05 20:40:00
categories: 项目
tags:
---



<!-- wp:list -->
<ul><li>程序名称：KeyCode</li><li>版本：Beta 1</li><li>作者：This is XD</li></ul>
<!-- /wp:list -->

<!-- wp:heading -->
<h2>简介</h2>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>KeyCode 是一个轻便的键盘按键码查询工具，TA拥有瘦小的体积，强大<s>（是不是有点过了）</s>的功能，值得您的尝试。</p>
<!-- /wp:paragraph -->

<!-- wp:heading {"level":3} -->
<h3>使用方法</h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>启动后使用键盘操作，按下一个按键则会显示该按键的KEYCODE和其他一些信息</p>
<!-- /wp:paragraph -->

<!-- wp:heading {"level":3} -->
<h3>使用截图</h3>
<!-- /wp:heading -->

<!-- wp:gallery {"ids":[77,78],"linkTo":"none"} -->
<figure class="wp-block-gallery columns-2 is-cropped"><ul class="blocks-gallery-grid"><li class="blocks-gallery-item"><figure><img src="https://www.thisisxd.tk/wp-content/uploads/2021/12/QQ截图20211205201151.png" alt="" data-id="77" data-full-url="https://www.thisisxd.tk/wp-content/uploads/2021/12/QQ截图20211205201151.png" data-link="https://www.thisisxd.tk/?attachment_id=77" class="wp-image-77"/></figure></li><li class="blocks-gallery-item"><figure><img src="https://www.thisisxd.tk/wp-content/uploads/2021/12/QQ图片20211205200815.png" alt="" data-id="78" data-full-url="https://www.thisisxd.tk/wp-content/uploads/2021/12/QQ图片20211205200815.png" data-link="https://www.thisisxd.tk/?attachment_id=78" class="wp-image-78"/></figure></li></ul></figure>
<!-- /wp:gallery -->

<!-- wp:heading -->
<h2>依赖</h2>
<!-- /wp:heading -->

<!-- wp:list {"ordered":true} -->
<ol><li>Python3</li><li>PyGame (>= 2.0)</li></ol>
<!-- /wp:list -->

<!-- wp:heading -->
<h2>构建步骤</h2>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>1、安装Python3（Windows请自行下载安装包安装）</p>
<!-- /wp:paragraph -->

<!-- wp:code -->
<pre class="wp-block-code"><code># Debian
sudo apt install python3

# Arch/Manjaro
sudo pacman -S python3

# CentOS
sudo yum install python3</code></pre>
<!-- /wp:code -->

<!-- wp:paragraph -->
<p>2、安装PyGame</p>
<!-- /wp:paragraph -->

<!-- wp:code -->
<pre class="wp-block-code"><code>python3 -m pip install pygame</code></pre>
<!-- /wp:code -->

<!-- wp:paragraph -->
<p>3、运行程序（请不要隔空运行）</p>
<!-- /wp:paragraph -->

<!-- wp:code -->
<pre class="wp-block-code"><code>python3 ./main.py</code></pre>
<!-- /wp:code -->

<!-- wp:heading -->
<h2>源代码</h2>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>./main.py</p>
<!-- /wp:paragraph -->

<!-- wp:code -->
<pre class="wp-block-code"><code>import pygame
import sys

pygame.init()

screen = pygame.display.set_mode((400,340))
pygame.display.set_caption("KeyBoard - KeyCode (By: This is XiaoDeng)")
bg = (200,255,255)
font = None

keycode_show = pygame.font.Font(font,200)
msg = pygame.font.Font(font,45)
key_name_show = pygame.font.Font(font,90)
p = pygame.font.Font(font,40)
uc = pygame.font.Font(font,35)

keycode = {
    97: 'A', 98: 'B', 99: 'C', 100: 'D', 101: 'E', 102: 'F', 103: 'G', 104: 'H', 105: 'I', 106: 'J', 107: 'K', 108: 'L', 109: 'M', 110: 'N', 111: 'O', 112: 'P', 113: 'Q', 114: 'R', 115: 'S', 116: 'T', 117: 'U', 118: 'V', 119: 'W', 120: 'X', 121: 'Y', 122: 'Z',
    1073741882: 'F1', 1073741883: 'F2', 1073741884: 'F3', 1073741885: 'F4', 1073741886: 'F5', 1073741887: 'F6', 1073741888: 'F7', 1073741889: 'F8', 1073741890: 'F9', 1073741891: 'F10', 1073741892: 'F11', 1073741893: 'F12',
    27:'ESC',1073741894:'PrintScreen',1073741895:"SrollLock",1073741896:"Pause &amp; Break",
    1073741897:"Inserent",127:"Delete",107374189:"Home",1073741901:"End",1073741899:"Page Up",1073741902:"Page Down",
    1073741906:"Side::Up",1073741905:"Side::Down",1073741904:"Side::Left",1073741903:"Side::Right",
    1073741913: 'Number::1', 1073741914: 'Number::2', 1073741915: 'Number::3', 1073741916: 'Number::4', 1073741917: 'Number::5', 1073741918: 'Number::6', 1073741919: 'Number::7', 1073741920: 'Number::8', 1073741921: 'Number::9',
    32:"Space"
}

key = "NAN"
key_name= "NULL"
k_x = 79
plus = False
unic = "NULL"
# 107374
while True:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            sys.exit()
        if event.type == pygame.KEYUP:
            print(event)
            key = event.key
            if key > 1000:
                plus = True
                key = int(str(key)&#91;7:])
            else:
                plus = False
            if 10 &lt; key &lt; 100:
                key = "0" + str(key)
            elif key &lt; 10:
                key = "00" + str(key)
            else:
                key = str(key)
            try:
                key_name = keycode&#91;event.key]
            except:
                key_name = "NULL"
            try:
                unic = f"Text:{event.unicode}  ASCII:{ord(event.unicode)}"
            except:unic = f"Text:{event.unicode}  ASCII:ERROR -1"
    screen.blit(keycode_show.render(key,True,(0,0,0),bg),(k_x,20))
    if plus:
        screen.blit(p.render("1073741",0,(0,0,0)),(5,5))
    screen.blit(msg.render("KEY NAME",True,(0,0,0),bg),(15,170))
    screen.blit(key_name_show.render(key_name,True,(0,0,0),bg),(30,210))
    screen.blit(msg.render("INFORMATION",True,(0,0,0),bg),(15,270))
    screen.blit(uc.render(unic,True,(0,0,0),bg),(30,305))

    pygame.display.update()
    screen.fill(bg)</code></pre>
<!-- /wp:code -->

<!-- wp:heading -->
<h2>说明</h2>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>此程序还处于公测状态，可能会有多种不稳定因素，如发现bug请在评论区反馈或直接联系作者，感谢支持！</p>
<!-- /wp:paragraph -->

<!-- wp:heading {"level":3} -->
<h3>INFORMATION 栏 Text 项目显示方框怎么解决？</h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>字体问题，将源代码 09 行 <code>None </code>改为自己喜欢的字体的TTF路径即可（如字体文件在 <code>/home/xxx/demo.ttf</code> 则将源代码第九行改为 <code>font = "/home/xxx/demo.ttf"</code> 即可）</p>
<!-- /wp:paragraph -->

<!-- wp:heading {"level":3} -->
<h3>KEY NAME 栏为什么会显示NULL？</h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>时间比较紧，KEYNAME字典没写完，所以……</p>
<!-- /wp:paragraph -->

<!-- wp:heading {"level":3} -->
<h3>INFORMATION 栏 ASCII 项目为什么会 ERROR -1？</h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>你按下的这个键没有对应的ASCII码</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p></p>
<!-- /wp:paragraph -->
