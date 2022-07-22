# 修复 Python 3.10 在 Windows 11 使用 pyreadline 错误

```
Python 3.10.5 (tags/v3.10.5:f377153, Jun  6 2022, 16:14:13) [MSC v.1929 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
Failed calling sys.__interactivehook__
Traceback (most recent call last):
  File "C:\Users\vip\AppData\Local\Programs\Python\Python310\lib\site.py", line 446, in register_readline
    import readline
  File "C:\Users\vip\AppData\Local\Programs\Python\Python310\lib\site-packages\readline.py", line 34, in <module>
    rl = Readline()
  File "C:\Users\vip\AppData\Local\Programs\Python\Python310\lib\site-packages\pyreadline\rlmain.py", line 422, in __init__
    BaseReadline.__init__(self)
  File "C:\Users\vip\AppData\Local\Programs\Python\Python310\lib\site-packages\pyreadline\rlmain.py", line 62, in __init__
    mode.init_editing_mode(None)
  File "C:\Users\vip\AppData\Local\Programs\Python\Python310\lib\site-packages\pyreadline\modes\emacs.py", line 633, in init_editing_mode
    self._bind_key('space',       self.self_insert)
  File "C:\Users\vip\AppData\Local\Programs\Python\Python310\lib\site-packages\pyreadline\modes\basemode.py", line 162, in _bind_key
    if not callable(func):
  File "C:\Users\vip\AppData\Local\Programs\Python\Python310\lib\site-packages\pyreadline\py3k_compat.py", line 8, in callable
    return isinstance(x, collections.Callable)
AttributeError: module 'collections' has no attribute 'Callable'
```

## 修改替换两个文件
```
modified:   pyreadline/lineeditor/history.py
modified:   pyreadline/py3k_compat.py
```

## [给VSCode终端一点颜色看看: Python 解释器交互模式查看整个命令历史](https://262235.xyz/index.php/archives/664/)

![](https://262235.xyz/usr/uploads/2021/11/842700694.webp)

## Python 自动补全模块 readline 解析
readline模块定义了一系列函数用来读写Python解释器中历史命令，并提供自动补全命令功能。这个模块可以通过relcompleter模块直接调用，模块中的设置会影响解释器中的交互提示，以及内置函数raw_input()和input()提供的提示。
readline模块定义了以下方法： 输入 readline. 然后按 TAB 就能自动补全显示

![](https://262235.xyz/usr/uploads/2021/11/2172231727.gif)
## python windows 安装 readline 模块
```
python -m pip install pyreadline
# 不能直接用pip install pyreadline
```
![](https://262235.xyz/usr/uploads/2021/11/2036123219.png)

## Python 交互模式 历史命令、清屏和调用Shell模块
- 源码: [git.io/me.py](https://git.io/me.py)
```
:: Usage:  python -i me.py     or [import me] , import the module me.py
:: Function:  cls()  ls()  cd(path)  cat(file)  pwd()  bash()  info()  history()
```

==========
pyreadline
==========


The pyreadline package is a python implementation of GNU readline functionality
it is based on the ctypes based UNC readline package by Gary Bishop. 
It is not complete. It has been tested for use with windows 2000 and windows xp.

Version 2.0 runs on Python 2.6, 2.7, and >3.2 using the same code.

Features:
 *  keyboard text selection and copy/paste
 *  Shift-arrowkeys for text selection
 *  Control-c can be used for copy activate with allow_ctrl_c(True) in config file
 *  Double tapping ctrl-c will raise a KeyboardInterrupt, use ctrl_c_tap_time_interval(x)
    where x is your preferred tap time window, default 0.3 s.
 *  paste pastes first line of content on clipboard. 
 *  ipython_paste, pastes tab-separated data as list of lists or numpy array if all data is numeric
 *  paste_mulitline_code pastes multi line code, removing any empty lines.
 
 
 The latest development version is always available at the IPython git 
 repository_.

.. _repository: https://github.com/pyreadline/pyreadline.git
