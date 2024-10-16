- Python 解释器安装

  - 勾选 Add python.exe to PATH 和 Use admin privileges when installing py.exe

    PATH 实际上是操作系统搜索应用程序的路径，如果同一个应用程序的不同版本的路径都加入了 PATH，则会按照顺序依次搜索，因此只有第一个是有效的。这就是安装程序没有将 Add python.exe to PATH 设置为默认勾选的原因
- Pycharm 安装

  - 勾选全部选项
  - 安装中文语言包插件
- 什么是虚拟环境？

  什么是环境

  安装 Python 解释器时安装的那些东西，主要包括：

  - Libs 库
    - site-packages 以后要安装的包
    - 标准库
  - Scripts 可执行文件
    - pip.exe
  - python.exe

  虚拟环境就是将上述环境再复制一份，所做的改动是：

  - 每个环境都有自己的名字
  - 标准库无需每个环境都复制一份
  - python.exe 也放在了Scripts文件夹下，这样可以避免添加两次环境变量。
- Pycharm 基本使用流程

  - 情况一：新建项目

    1. 新建项目

       Pycharm
    2. 选择解释器（Interpreter）

# 参考文献

[安装不算完事，只有理解了虚拟环境才算真正掌握 Python 环境](https://www.bilibili.com/video/BV1V7411n7CM?spm_id_from=333.788.videopod.episodes&vd_source=b3328ecaea4c890b0870cbe5c6c5e30c&p=1)

[博客园：Python 虚拟环境 pyenv、venv(pyvenv)、virtualenv之间的区别](https://www.cnblogs.com/qinhan/p/9293126.html)
