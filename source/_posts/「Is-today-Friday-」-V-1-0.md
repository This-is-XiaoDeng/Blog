---
title: 「Is today Friday?」 V 1.0
date: 2021-12-24 19:36:24
categories: 项目
tags:
---

> 警告：本文可能已经**过时**

<!-- wp:heading -->
<h2>介绍</h2>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>「Is todat Friday?」是一个用来看今天是不是周五以及还有多少天到周五的程序。</p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":102,"sizeSlug":"large","linkDestination":"none","className":"is-style-rounded"} -->
<figure class="wp-block-image size-large is-style-rounded"><img src="https://www.thisisxd.tk/wp-content/uploads/2021/12/截图_2021-12-24_21-52-00-1024x614.png" alt="" class="wp-image-102"/></figure>
<!-- /wp:image -->

<!-- wp:heading -->
<h2>构建与使用</h2>
<!-- /wp:heading -->

<!-- wp:heading {"level":3} -->
<h3>依赖列表</h3>
<!-- /wp:heading -->

<!-- wp:list {"ordered":true} -->
<ol><li>Python3</li><li>PySide6</li></ol>
<!-- /wp:list -->

<!-- wp:heading {"level":3} -->
<h3>构建步骤</h3>
<!-- /wp:heading -->

<!-- wp:heading {"level":4} -->
<h4>Linux</h4>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>1、安装Python3</p>
<!-- /wp:paragraph -->

<!-- wp:code -->
<pre class="wp-block-code"><code>Manjaro / Arch
$ sudo pacman -S python3

Deepin / Debian
$ sudo apt install python3</code></pre>
<!-- /wp:code -->

<!-- wp:paragraph -->
<p>2、安装PIP（详见：<a href="https://www.thisisxd.tk/?p=81" target="_blank" rel="noreferrer noopener">https://www.thisisxd.tk/?p=81</a>）</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>3、安装依赖库</p>
<!-- /wp:paragraph -->

<!-- wp:code -->
<pre class="wp-block-code"><code>$ python3 -m pip install pyside6</code></pre>
<!-- /wp:code -->

<!-- wp:paragraph -->
<p>4、运行文件</p>
<!-- /wp:paragraph -->

<!-- wp:code -->
<pre class="wp-block-code"><code>$ python3 ./Friday.py</code></pre>
<!-- /wp:code -->

<!-- wp:heading {"level":4} -->
<h4>Windows</h4>
<!-- /wp:heading -->

<!-- wp:list {"ordered":true} -->
<ol><li>安装Python3</li><li>安装PIP（详见：<a rel="noreferrer noopener" href="https://www.thisisxd.tk/?p=81" target="_blank">https://www.thisisxd.tk/?p=81</a>）</li><li>处理PATH（详见百度）</li><li>安装依赖库</li></ol>
<!-- /wp:list -->

<!-- wp:code -->
<pre class="wp-block-code"><code>pip install pyside6</code></pre>
<!-- /wp:code -->

<!-- wp:paragraph -->
<p>5.  双击运行（Friday.py）</p>
<!-- /wp:paragraph -->

<!-- wp:heading -->
<h2>源代码</h2>
<!-- /wp:heading -->

<!-- wp:heading {"level":3} -->
<h3>./Friday.py</h3>
<!-- /wp:heading -->

<!-- wp:code -->
<pre class="wp-block-code"><code>from PySide6.QtWidgets import *
from ui_Friday import *
import sys
import time

print(time.strftime("%a",time.localtime()))
t = time.strftime("%a",time.localtime())
if t != "Fri":
    Fri = False
else:
    Fri = True
if t == "Mon":
    d = 4
elif "Tue" in t:
    d = 3
elif t == "Wed":
    d = 2
elif "Thu" in t:
    d = 1
else:
    d = 0

class Friday(Ui_MainWindow,QMainWindow):
    def __init__(self) -> None:
        super().__init__()
        self.setupUi(self)
        self.lcdNumber.display(d)
        self.IsFri.setText("&lt;center>&lt;h1>"+str(Fri)+"&lt;/h1>&lt;/center>")
        if Fri:
            self.groupBox_2.setEnabled(False)
        self.show()
if __name__ == "__main__":
    app = QApplication(sys.argv)
    window = Friday()
    sys.exit(app.exec())</code></pre>
<!-- /wp:code -->

<!-- wp:heading {"level":3} -->
<h3>./ui_Friday.py</h3>
<!-- /wp:heading -->

<!-- wp:code -->
<pre class="wp-block-code"><code># -*- coding: utf-8 -*-

################################################################################
## Form generated from reading UI file 'Friday.ui'
##
## Created by: Qt User Interface Compiler version 6.2.1
##
## WARNING! All changes made in this file will be lost when recompiling UI file!
################################################################################

from PySide6.QtCore import (QCoreApplication, QDate, QDateTime, QLocale,
    QMetaObject, QObject, QPoint, QRect,
    QSize, QTime, QUrl, Qt)
from PySide6.QtGui import (QBrush, QColor, QConicalGradient, QCursor,
    QFont, QFontDatabase, QGradient, QIcon,
    QImage, QKeySequence, QLinearGradient, QPainter,
    QPalette, QPixmap, QRadialGradient, QTransform)
from PySide6.QtWidgets import (QApplication, QGridLayout, QGroupBox, QHBoxLayout,
    QLCDNumber, QLabel, QMainWindow, QSizePolicy,
    QVBoxLayout, QWidget)

class Ui_MainWindow(object):
    def setupUi(self, MainWindow):
        if not MainWindow.objectName():
            MainWindow.setObjectName(u"MainWindow")
        MainWindow.resize(324, 169)
        self.centralwidget = QWidget(MainWindow)
        self.centralwidget.setObjectName(u"centralwidget")
        self.gridLayout = QGridLayout(self.centralwidget)
        self.gridLayout.setObjectName(u"gridLayout")
        self.groupBox = QGroupBox(self.centralwidget)
        self.groupBox.setObjectName(u"groupBox")
        self.groupBox.setAlignment(Qt.AlignCenter)
        self.verticalLayout_2 = QVBoxLayout(self.groupBox)
        self.verticalLayout_2.setObjectName(u"verticalLayout_2")
        self.IsFri = QLabel(self.groupBox)
        self.IsFri.setObjectName(u"IsFri")

        self.verticalLayout_2.addWidget(self.IsFri)


        self.gridLayout.addWidget(self.groupBox, 1, 0, 1, 1)

        self.groupBox_2 = QGroupBox(self.centralwidget)
        self.groupBox_2.setObjectName(u"groupBox_2")
        self.horizontalLayout = QHBoxLayout(self.groupBox_2)
        self.horizontalLayout.setObjectName(u"horizontalLayout")
        self.lcdNumber = QLCDNumber(self.groupBox_2)
        self.lcdNumber.setObjectName(u"lcdNumber")
        self.lcdNumber.setDigitCount(1)

        self.horizontalLayout.addWidget(self.lcdNumber)

        self.label_2 = QLabel(self.groupBox_2)
        self.label_2.setObjectName(u"label_2")

        self.horizontalLayout.addWidget(self.label_2)


        self.gridLayout.addWidget(self.groupBox_2, 1, 1, 1, 1)

        self.label_3 = QLabel(self.centralwidget)
        self.label_3.setObjectName(u"label_3")

        self.gridLayout.addWidget(self.label_3, 2, 0, 1, 1)

        self.label = QLabel(self.centralwidget)
        self.label.setObjectName(u"label")
        self.label.setMaximumSize(QSize(16777215, 30))

        self.gridLayout.addWidget(self.label, 2, 1, 1, 1)

        MainWindow.setCentralWidget(self.centralwidget)

        self.retranslateUi(MainWindow)

        QMetaObject.connectSlotsByName(MainWindow)
    # setupUi

    def retranslateUi(self, MainWindow):
        MainWindow.setWindowTitle(QCoreApplication.translate("MainWindow", u"\u4eca\u5929\u662f\u5468\u4e94\u5417\uff1f\uff08By XD\uff09", None))
        self.groupBox.setTitle(QCoreApplication.translate("MainWindow", u"\u4eca\u5929\u662f\u5468\u4e94\u5417\uff1f", None))
        self.IsFri.setText("")
        self.groupBox_2.setTitle(QCoreApplication.translate("MainWindow", u"\u8ddd\u79bb\u5468\u4e94\u8fd8\u6709", None))
        self.label_2.setText(QCoreApplication.translate("MainWindow", u"&lt;html>&lt;head/>&lt;body>&lt;p>&lt;span style=\" font-size:22pt;\">\u5929&lt;/span>&lt;/p>&lt;/body>&lt;/html>", None))
        self.label_3.setText(QCoreApplication.translate("MainWindow", u"By thisisx.tk &amp; itcraft.tk", None))
        self.label.setText(QCoreApplication.translate("MainWindow", u"Version: 1.0", None))
    # retranslateUi

</code></pre>
<!-- /wp:code -->

<!-- wp:heading {"level":3} -->
<h3>./Friday.ui</h3>
<!-- /wp:heading -->

<!-- wp:code -->
<pre class="wp-block-code"><code>&lt;?xml version="1.0" encoding="UTF-8"?>
&lt;ui version="4.0">
 &lt;class>MainWindow&lt;/class>
 &lt;widget class="QMainWindow" name="MainWindow">
  &lt;property name="geometry">
   &lt;rect>
    &lt;x>0&lt;/x>
    &lt;y>0&lt;/y>
    &lt;width>324&lt;/width>
    &lt;height>169&lt;/height>
   &lt;/rect>
  &lt;/property>
  &lt;property name="windowTitle">
   &lt;string>今天是周五吗？（By XD）&lt;/string>
  &lt;/property>
  &lt;widget class="QWidget" name="centralwidget">
   &lt;layout class="QGridLayout" name="gridLayout">
    &lt;item row="1" column="0">
     &lt;widget class="QGroupBox" name="groupBox">
      &lt;property name="title">
       &lt;string>今天是周五吗？&lt;/string>
      &lt;/property>
      &lt;property name="alignment">
       &lt;set>Qt::AlignCenter&lt;/set>
      &lt;/property>
      &lt;layout class="QVBoxLayout" name="verticalLayout_2">
       &lt;item>
        &lt;widget class="QLabel" name="IsFri">
         &lt;property name="text">
          &lt;string/>
         &lt;/property>
        &lt;/widget>
       &lt;/item>
      &lt;/layout>
     &lt;/widget>
    &lt;/item>
    &lt;item row="1" column="1">
     &lt;widget class="QGroupBox" name="groupBox_2">
      &lt;property name="title">
       &lt;string>距离周五还有&lt;/string>
      &lt;/property>
      &lt;layout class="QHBoxLayout" name="horizontalLayout">
       &lt;item>
        &lt;widget class="QLCDNumber" name="lcdNumber">
         &lt;property name="digitCount">
          &lt;number>1&lt;/number>
         &lt;/property>
        &lt;/widget>
       &lt;/item>
       &lt;item>
        &lt;widget class="QLabel" name="label_2">
         &lt;property name="text">
          &lt;string>&amp;lt;html&amp;gt;&amp;lt;head/&amp;gt;&amp;lt;body&amp;gt;&amp;lt;p&amp;gt;&amp;lt;span style=&amp;quot; font-size:22pt;&amp;quot;&amp;gt;天&amp;lt;/span&amp;gt;&amp;lt;/p&amp;gt;&amp;lt;/body&amp;gt;&amp;lt;/html&amp;gt;&lt;/string>
         &lt;/property>
        &lt;/widget>
       &lt;/item>
      &lt;/layout>
     &lt;/widget>
    &lt;/item>
    &lt;item row="2" column="0">
     &lt;widget class="QLabel" name="label_3">
      &lt;property name="text">
       &lt;string>By thisisx.tk &amp;amp; itcraft.tk&lt;/string>
      &lt;/property>
     &lt;/widget>
    &lt;/item>
    &lt;item row="2" column="1">
     &lt;widget class="QLabel" name="label">
      &lt;property name="maximumSize">
       &lt;size>
        &lt;width>16777215&lt;/width>
        &lt;height>30&lt;/height>
       &lt;/size>
      &lt;/property>
      &lt;property name="text">
       &lt;string>Version: 1.0&lt;/string>
      &lt;/property>
     &lt;/widget>
    &lt;/item>
   &lt;/layout>
  &lt;/widget>
 &lt;/widget>
 &lt;resources/>
 &lt;connections/>
&lt;/ui>
</code></pre>
<!-- /wp:code -->

<!-- wp:heading -->
<h2>源码（附件）：</h2>
<!-- /wp:heading -->

<!-- wp:file {"id":103,"href":"https://www.thisisxd.tk/wp-content/uploads/2021/12/Is_today_Friday.zip","align":"center"} -->
<div class="wp-block-file aligncenter"><a href="https://www.thisisxd.tk/?attachment_id=103" target="_blank" rel="noreferrer noopener">Is_today_Friday.zip</a><a href="https://www.thisisxd.tk/wp-content/uploads/2021/12/Is_today_Friday.zip" class="wp-block-file__button" download>下载</a></div>
<!-- /wp:file -->
