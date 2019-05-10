### 为什么使用Python进行数据分析
>Python作为一种脚本语言，为什么可以作为数据分析非常流行的语言呢，本书给出以下总结：

+ Python现在已经成为最受欢迎的一门动态编程语言,拥有大量的web框架，如**Django**
+ 拥有巨大而活跃的**科学计算**社区，如Scipy、EuroSciPy、Numpy-discussion
+ 拥有不断改良的库，主要是**Pandas**([离线安装](https://www.lfd.uci.edu/~gohlke/pythonlibs/)、[在线安装](http://pandas.pydata.org/))、**Numpy**([离线安装](https://www.lfd.uci.edu/~gohlke/pythonlibs/)、[在线安装](http://www.numpy.org/))等等
+ 作为**粘合剂**，成功集成了C、C++、Fortran代码（大量现代计算环境都是使用Fortran和C库来实现线性代数、积分、快速博利叶变换等算法，使用Python可以粘合那些已经使用30年的遗留程序软件）
+ 解决两种语言问题，许多组织使用领域特定语言(如MATLAB和R)对新的想法进行研究、模型构建以及测试，然后再将研究结果转移到更大的生产系统中，而Python既适用于研究和模型构建，也可以构建巨大的生产系统

### 为什么不选Python
>Python的缺点
+ Python是解释型编程语言，所以运行慢得多
+ Python不容易实现高并发、多线程（有一种[全局解释器锁](https://baike.baidu.com/item/%E5%85%A8%E5%B1%80%E8%A7%A3%E9%87%8A%E5%99%A8%E9%94%81/13859226?fr=aladdin)的东西）,Python只是不能在单个进程中执行多线程并行代码。