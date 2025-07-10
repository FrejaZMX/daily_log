https://mp.weixin.qq.com/s?srcid=0426szbjhjqJWh3Hsu74hEW4&scene=22&sharer_shareinfo=7fbbea70a3034215ee502a3f6f32ad48&mid=2247510663&sn=4d572352e146e60668ed667f42efc070&idx=1&sharer_shareinfo_first=8a58ebb102da1de2ddb031557fae9416&__biz=MzAwMzIzOTk5OQ%3D%3D&chksm=9b3cd3d7ac4b5ac1c47b4cc7cc17823c2c37091fc89d07054844bd539f3eb251f1c540269590&mpshare=1#rd
#### *创建R语言的虚拟环境*
首先，我们需要用conda创建一个含有R语言的虚拟环境，这样也方便管理不同的R版本。在Linux终端中运行以下命令查找R不同版本。
```
conda search -c conda-forge r-base
```
然后我们就可以根据需求下载合适版本啦，这里我选择比较新的R4.3.0，先创建一个新的R环境：R430，然后安装，命令如下：
```
conda create -y -n R430   
conda activate R430  
conda install -y -c conda-forge r-base==4.3.0
```
安装完成之后，在终端中输入R，结果如下证明安装成功：
![[Pasted image 20240428162727.png]]

接着安装必须的R包‘IRkernel’
```
install.packages("IRkernel", repos="https://mirrors.tuna.tsinghua.edu.cn/CRAN/")
```
之后退出R，准备安装Jupyterlab
#### *安装Jupyterlab*
直接运行
```
#都是在工作环境里
conda install -y jupyterlab  
#安装成功之后，在terminal中输入命令：  
jupyter-lab --no-browser --port=8889
终端输入ssh -N -f -L localhost:8893:localhost:8889 zhumengxuan@10.10.117.157
#打开浏览器链接
#在浏览器的搜索页面中输入 localhost:8893 即可访问
```
此时jupyterlab的界面只有python文件没有R语言的，所以下一步将jupyterlab和R语言关联起来

#### *关联R与jupyterlab*
再激活Jupyter-lab之后，如果要退出的话很简单，只需要在终端中Ctrl+C并确认即可。然后我们再次运行R，在命令行中输入：
```
IRkernel::installspec()

```
![[Pasted image 20240429134135.png]]

运行完成退出即可，再次运行jupyter-lab，打开链接，此时我们可以看到Jupyter中出现了R！然后我点击就可以创建一个新的R脚本文件了：
![[Pasted image 20240429134209.png]]
每个单元格的运行结果会在下面展示。单元格除了代码之外还可以添加markdown，右键单元格我们还可以看到一系列操作：
![[Pasted image 20240429134230.png]]

![[Pasted image 20240429134236.png]]