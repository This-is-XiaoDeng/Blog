---
title: YOUR-LIFE
date: 2022-01-11 15:19:00
cateories: 项目
tags:
---

> 温馨提示：本文可能已经**过时**

<!-- wp:heading -->
<h2>简介</h2>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>您的生命还有多少天？</p>
<!-- /wp:paragraph -->

<!-- wp:heading -->
<h2>文件</h2>
<!-- /wp:heading -->

<!-- wp:code -->
<pre class="wp-block-code"><code>YOUR-LIFE.zip
     | - YOU-LIFE.py # 主程序
     | - ui_life.py </code></pre>
<!-- /wp:code -->

<!-- wp:heading -->
<h2>依赖</h2>
<!-- /wp:heading -->

<!-- wp:list {"ordered":true} -->
<ol><li>Python 3</li><li>PySide 6</li></ol>
<!-- /wp:list -->

<!-- wp:heading -->
<h2>源代码</h2>
<!-- /wp:heading -->

<!-- wp:heading {"level":3} -->
<h3>/YOU-LIFE.py</h3>
<!-- /wp:heading -->

<!-- wp:code -->
<pre class="wp-block-code"><code>from PySide6.QtWidgets import *
from ui_life import *
import sys
import time

class Life(QMainWindow,Ui_MainWindow):
    def __init__(self):
        super().__init__()
        self.setupUi(self)
        self.pushButton.clicked.connect(self.start)
        self.show()
    def start(self):
        _b = (self.lineEdit.text(),self.lineEdit_2.text(),self.lineEdit_3.text())
        print(_b)
        b_str = f"{_b&#91;0]}-{_b&#91;1]}-{_b&#91;2]} 0:0:0"
        if self.comboBox.currentText() == "男":
            o_str = f"{int(_b&#91;0])+70}-{_b&#91;1]}-{_b&#91;2]} 0:0:0"
            y = 70
        else: 
            o_str = f"{int(_b&#91;0])+73}-{_b&#91;1]}-{_b&#91;2]} 0:0:0"
            y=73
        birthday = time.mktime(time.strptime(b_str, '%Y-%m-%d %H:%M:%S'))
        over = time.mktime(time.strptime(o_str, '%Y-%m-%d %H:%M:%S'))
        print(birthday,over)

        self.progressBar.setValue(int((time.time() - birthday) / y * 100))
        self.progressBar_2.setValue(100 - int((time.time() - birthday) / y * 100))
        
        b = time.time() - birthday - 28800
        b1 = time.localtime(b)
        self.lcdNumber.display(b1&#91;0]-1970)
        self.lcdNumber_2.display(b1&#91;1])
        self.lcdNumber_3.display(b1&#91;2])

        t = time.time()
        b = over - t - 28800
        b2 = time.localtime(b)
        self.lcdNumber_4.display(b2&#91;0] - 1969)
        self.lcdNumber_5.display(b2&#91;1])
        self.lcdNumber_6.display(b2&#91;2])

        self.lcdNumber_7.display((b2&#91;0]-1969)*12+b2&#91;1])
        self.label_15.setText("天。")
        self.lcdNumber_8.display((b2&#91;0]-1969)*12*4+b2&#91;1]*4)
        self.lcdNumber_9.display((b2&#91;0]-1969)*365+b2&#91;1]*30+b2&#91;2])

        

if __name__ == "__main__":
    app = QApplication(sys.argv)
    window = Life()
    sys.exit(app.exec())
</code></pre>
<!-- /wp:code -->
