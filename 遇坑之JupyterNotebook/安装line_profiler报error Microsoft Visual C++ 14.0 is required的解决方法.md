### 安装`line_profiler`报error: Microsoft Visual C++ 14.0 is required的解决方法
该问题出现在windows系统，Linux系统直接使用`pip install line_profiler`可以直接安装，解决方法如下：
1. 安装VS2015，但是组件太多太大（不推荐）
2. 手动下载whl文件，[下载地址](https://www.lfd.uci.edu/~gohlke/pythonlibs/),直接搜索line_profiler，根据Python安装的是32位还是64位，下载对应的安装包，最后直接执行`pip install XXX.whl`完成安装。

