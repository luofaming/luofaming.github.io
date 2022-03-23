---
layout: default
---

[返回主页](https://luofaming.github.io/)

关于Python的一些学习笔记

* 在Linux下编译python是显示ModuleNotFoundError: No module named 'tkinter'时
``` bash
sudo apt-get install python3.8-tk #根据实际python版本来
```

* 输出
``` python
print("123")
```

* 删除字符串前后空格
``` python
a=" 123 "
#删除左边空格
b=a.lstrip()
#删除右边空格
c=a.rstrip()
#左右都删除
d=a.strip()
```

* python可以同时给多个变量赋值
``` python
x,y,z = 0,0,0
```
