---
title: pyauetogui基础使用
date: 2022-03-27
tags:
- python
categories:
- [python,python自动化]

---
###  库的安装

> pip install pyautogui

###  导库

> ```
> import pyautogui
> ```

###  基础操作

#####  设置全局停顿时间

> pyautogui 提供了<PAUSE>方法来设置每次执行完一个动作后的等待时间,
>
>  和 time.sleep 相似

~~~
pyautogui.PAUSE = 1     # 每次等待一秒
~~~

#####  边角警报

> pyautogui 在控制鼠标到达(0, 0)点等边角时会触发错误警报, 我们可以通过 <FAILSAFE> 来关闭它
>
> pyautogui.FailSafeException: PyAutoGUI fail-safe triggered from mouse moving to a corner of the screen. To disable this fail-safe, set pyautogui.FAILSAFE to False. DISABLING FAIL-SAFE IS NOT RECOMMENDED.

~~~
pyautogui.FAILSAFE = True	# True 开启, False 关闭.
~~~

#####  获取屏幕分辨率

> pyautogui 提供了<size>方法来获取屏幕的分辨率  可用python解析式分解

~~~
width, height = pyautogui.size() # 屏幕的宽度和高度
print(width, height)			# 1920 1080
~~~

#####  判断某坐标是否在屏幕上

>pyautogui 提供 <onScreen> 方法使我们判断鼠标是否在屏幕内
>
>返回值: True/False

~~~
pyautogui.onScreen(500, 500)		# True
n = pyautogui.onScreen(2000, 2000)	# False
~~~

###  鼠标操作

#####  获取当前鼠标位置

> pyautogui提供了<position>方法来获取鼠标位置

~~~
x, y = pyautogui.position()
print(x, y)					# 1434 460
~~~

#####  鼠标绝对移动

> pyautogui 提供了 <moveTo> 方法来实现鼠标的移动
>
> 参数: 1. x轴	2. y轴	3. duration 拖动时间(不设置则直接移动到此处)

~~~
pyautogui.moveTo(100, 100, duration=2)		# 拖动到100, 100 处
pyautogui.moveTo(100, 100)					# 直接到100, 100 处
~~~

#####   鼠标相对移动

>pyautogui 提供了 <move>和<moveRel> 方法来实现鼠标的移动
>
>参数: 1. x轴	2. y轴	3. duration 拖动时间(不设置则直接移动到此处)

~~~
pyautogui.moveRel(200, 200, duration=2)
pyautogui.move(-200, -200, duration=2)
# 效果是一样的
~~~

#####  鼠标拖动

> pyautogui 提供了<dragTo>方法让我们方便的实现拖拽方法
>
> 参数:  参数1: x轴最终坐标, 参数2: y轴最终坐标, 参数3: duration 拖动时间(必填)  参数4: button 要按下的键(默认左键) 

~~~
pyautogui.dragTo(1000, 100, duration=2,  button="left")
~~~

#####  鼠标相对拖动

> pyautogui 提供了 <drag>和<dragRel> 方法来实现鼠标的相对拖动
>
> 参数:  参数1: x轴最终坐标, 参数2: y轴最终坐标, 参数3: duration 拖动时间(必填)  参数4: button 要按下的键(默认左键) 

~~~
pyautogui.drag(0, -500, duration=2,  button="left")
pyautogui.dragRel(0, 500, duration=2,  button="left")
~~~

#####  鼠标点击

> pyautogui 提供了<click><单次点击><doubleClick><连点2次><tripleClick>><3连>3种点击方法
>
> 参数: x ==> x轴位置, y ==> y轴位置, button ==> "按键"(默认left)

~~~
pyautogui.click(x=1000, y=100, button="left")	# xy可以不填
# 其他同理
~~~

#####  鼠标按下和放开

> mouseDown(按下)   mouseUp(放开)
>
> 参数: 参数: x ==> x轴位置, y ==> y轴位置, button ==> "按键"(默认left)

~~~
pyautogui.mouseDown(button='right') # 按下鼠标右键
pyautogui.mouseUp(button='right', x=100, y=200) # 移动到(100, 200)位置，然后松开鼠标右键
~~~

#####  鼠标滑动

> scroll函数控制鼠标滚轮的滚动，

~~~
pyautogui.scroll(10)
~~~

> 不好用

###  键盘操作

#####  输入字符串

> typewrite 方法可以直接输入字符串
>
> 参数 interval 控制每个字符的输入时间

~~~
pyautogui.typewrite('Hello world!', interval=0.25)
~~~

#####  组合键

> hotkey 可以快速的输入组合键

~~~
pyautogui.hotkey('ctrl', 'v')
pyautogui.hotkey('ctrl', 'shift', "esc")
~~~

#####  按下松开

> press 可以直接执行一整套按下松开 (和pynput库是不同的)

~~~
pyautogui.press('enter')
pyautogui.press(['left', 'left', 'left', 'left']) # 按下并松开（轻敲）四下左方向键
~~~

> <keyDown>和<keyUp>按下松开键

~~~
pyautogui.keyDown('shift') # 按下`shift`键
pyautogui.keyUp('shift') # 松开`shift`键
~~~

#####  所有可输入按键

~~~
'\t', '\n', '\r', ' ', '!', '"', '#', '$', '%', '&', "'", '(', ')', '*', '+', ',', '-', '.','/', '0', '1', '2', '3', '4', '5', '6', '7', '8', '9', ':', ';', '<', '=', '>', '?', '@','[', '\\', ']', '^', '_', '`', 'a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k', 'l', 'm', 'n', 'o', 'p', 'q', 'r', 's', 't', 'u', 'v', 'w', 'x', 'y', 'z', '{', '|', '}', '~', 'accept', 'add', 'alt', 'altleft', 'altright', 'apps', 'backspace', 'browserback','browserfavorites', 'browserforward', 'browserhome', 'browserrefresh', 'browsersearch', 'browserstop', 'capslock', 'clear', 'convert', 'ctrl', 'ctrlleft', 'ctrlright', 'decimal','del', 'delete', 'divide', 'down', 'end', 'enter', 'esc', 'escape', 'execute', 'f1', 'f10', 'f11', 'f12', 'f13', 'f14', 'f15', 'f16', 'f17', 'f18', 'f19', 'f2', 'f20', 'f21', 'f22','f23', 'f24', 'f3', 'f4', 'f5', 'f6', 'f7', 'f8', 'f9', 'final', 'fn', 'hanguel', 'hangul', 'hanja', 'help', 'home', 'insert', 'junja', 'kana', 'kanji', 'launchapp1', 'launchapp2','launchmail', 'launchmediaselect', 'left', 'modechange', 'multiply', 'nexttrack', 'nonconvert', 'num0', 'num1', 'num2', 'num3', 'num4', 'num5', 'num6', 'num7', 'num8', 'num9','numlock', 'pagedown', 'pageup', 'pause', 'pgdn', 'pgup', 'playpause', 'prevtrack', 'print', 'printscreen', 'prntscrn', 'prtsc', 'prtscr', 'return', 'right', 'scrolllock', 'select','separator', 'shift', 'shiftleft', 'shiftright', 'sleep', 'space', 'stop', 'subtract', 'tab', 'up', 'volumedown', 'volumemute', 'volumeup', 'win', 'winleft', 'winright', 'yen', 'command','option', 'optionleft', 'optionright'
~~~

###  弹窗

> alert 方法可以弹出一个对话框
>
> 参数: text : 显示文本, title: 窗口文本, button: 按钮文本
>
> 返回值: 按下的按钮文本
>
> (我没找到多个按键的方法)

~~~
b = pyautogui.alert(text='要开始程序么？', title='请求框', button='OK')
print(b) # 输出结果为OK
~~~

> confirm 类似 alert方法
>
> 参数: text : 显示文本, title: 窗口文本, buttons: 按钮文本
>
> 返回值: 按下的按钮文本

~~~
a = pyautogui.confirm(text='要开始程序么？', title='请求框', buttons=['OK', '取消'])
print(a)    # ok 或 取消
~~~

> prompt 方法开启一个输入框
>
> 参数: text : 显示文本, title: 窗口文本, default: 默认值

~~~
txt = pyautogui.prompt(text='', title='', default='')
print(txt)
~~~

> password 密码弹窗
>
> 参数: text : 显示文本, title: 窗口文本, default: 默认值, mask: 显示值

~~~
pyautogui.password(text='', title='', default='', mask='*')
~~~

###  图像操作

> 需要安装 Pillow 库
>
> pip install Pillow

#####  截图

> screenshot 可以截取屏幕
>
> 参数1: 保留文件的位置和名字, 参数<region> 截取的位置

~~~
pyautogui.screenshot(r"01.png", region=(100, 100, 500, 500))
~~~

#####  获取rgb值

> <getpixel>方法可以获取到截图的某点的rgb值

~~~
pix = pyautogui.screenshot().getpixel((200, 200))
~~~

> pixel 可以获取到屏幕上某点的rgb值

~~~
pix = pyautogui.pixel(500, 500)
~~~

#####  获取图像位置

> <locateOnScreen>方法既可以获取图像是否存在也可以获取图像位置信息
>
> 返回box对象, 可解析为  top, left, width, height
>
> 参数<region> 截取的位置

~~~~
x, y, width, height = pyautogui.locateOnScreen("img.png")
print(x, y, width, height)
~~~~

> center 可以获取到图像中心点坐标
>
> 参数<region> 截取的位置

~~~
x, y = pyautogui.center(pyautogui.locateOnScreen("img.png"))
print(x, y)
~~~

> locateCenterOnScreen 方法是上面两种方法的集合
>
> 参数<region> 截取的位置

~~~
x, y = pyautogui.locateCenterOnScreen("img.png")
print(x, y)
~~~

> <locateAllOnScreen>方法可以获取到所以符合的对象 list
>
> 参数<region> 截取的位置

~~~
imgs = pyautogui.locateAllOnScreen("img_1.png")
for i in imgs:
    print(i)
~~~

