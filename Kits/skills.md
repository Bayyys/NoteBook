:hugs:

# 1. CSDN -> Markdown

F12 -->  [markdown编辑器 - 在线工具 (tool.lu)](https://tool.lu/markdown/)

![image-20230227224758979](https://s2.loli.net/2023/02/27/siraNYUjS8Hu2md.png)

# 2.Anaconda

## 0.基本使用

### 1、配置[环境变量](https://so.csdn.net/so/search?q=%E7%8E%AF%E5%A2%83%E5%8F%98%E9%87%8F&spm=1001.2101.3001.7020)

如果是 windows 的话需要去 `控制面板\系统和安全\系统\高级系统设置\环境变量\用户变量\PATH` 中添加 [anaconda](https://so.csdn.net/so/search?q=anaconda&spm=1001.2101.3001.7020)的安装目录的 Scripts 文件夹, 比如我的路径是`D:\Software\Anaconda\Scripts`, 看个人安装路径不同需要自己调整.

之后就可以打开[命令行](https://so.csdn.net/so/search?q=%E5%91%BD%E4%BB%A4%E8%A1%8C&spm=1001.2101.3001.7020)(最好用管理员模式打开) 输入 conda --version

如果输出`conda 4.4.11`之类的就说明环境变量设置成功了.  
为了避免可能发生的错误, 我们在命令行输入`conda upgrade --all` 先把所有工具包进行升级。

### 2、基础操作

#### 2.1、activate

可以直接进入 anaconda 自带的 base 环境。  
![activate](https://img-blog.csdnimg.cn/20181227145810394.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2JhaWR1XzM4Nzc3OTc5,size_16,color_FFFFFF,t_70)

#### 2.2、创建自己的虚拟环境

创建一个名称为 learn 的虚拟环境并指定 python 版本为 3(这里[conda](https://so.csdn.net/so/search?q=conda&spm=1001.2101.3001.7020)会自动找 3 中最新的版本下载。

    conda create -n learn python=3

![新建环境](https://img-blog.csdnimg.cn/20181227154459175.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2JhaWR1XzM4Nzc3OTc5,size_16,color_FFFFFF,t_70)

#### 2.3、切换环境

    activate learn

如果想看一共有哪些环境

    conda env list

![在这里插入图片描述](https://img-blog.csdnimg.cn/20181227154943617.png)

### 3、安装/卸载第三方包

两种方式都可以

    conda install requests
    或者
    pip install requests


    conda remove requests
    或者
    pip uninstall requests

### 4、查看环境包信息

查看当前环境所有包的情况

    conda list

![已安装包情况](https://img-blog.csdnimg.cn/2018122716024022.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2JhaWR1XzM4Nzc3OTc5,size_16,color_FFFFFF,t_70)

### 5、导入导出环境

如果想要导出当前环境的包信息可以用

    conda env export > environment.yaml

将包信息存入 yaml 文件中

当需要重新创建一个相同的虚拟环境时可以用

    conda env create -f environment.yaml

### 6、删除环境（慎用）

    conda remove -n learn --all

### 7、总结当前命令

    activate  // 切换到base环境
    
    activate learn // 切换到learn环境
    
    conda create -n learn python=3  // 创建一个名为learn的环境并指定python版本为3(的最新版本)
    
    conda env list // 列出conda管理的所有环境
    
    conda list // 列出当前环境的所有包
    
    conda install requests 安装requests包
    
    conda remove requests 卸载requets包
    
    conda remove -n learn --all // 删除learn环境及下属所有包
    
    conda update requests 更新requests包
1.关于 [conda](https://so.csdn.net/so/search?q=conda&spm=1001.2101.3001.7020) 切换为国内源
----------------------------------------------------------------------------------

A. 添加清华源：

    conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
    conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge 
    conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/msys2/


设置搜索时显示通道地址：

    conda config --set show_channel_urls yes


B. 添加中科大源：

    conda config --add channels https://mirrors.ustc.edu.cn/anaconda/pkgs/main/
    conda config --add channels https://mirrors.ustc.edu.cn/anaconda/pkgs/free/
    conda config --add channels https://mirrors.ustc.edu.cn/anaconda/cloud/conda-forge/
    conda config --add channels https://mirrors.ustc.edu.cn/anaconda/cloud/msys2/
    conda config --add channels https://mirrors.ustc.edu.cn/anaconda/cloud/bioconda/
    conda config --add channels https://mirrors.ustc.edu.cn/anaconda/cloud/menpo/
    conda config --set show_channel_urls yes


C. 在Linux系统中：

将以上配置文件写在 ~/.condarc 中

使用指令：

    vim ~/.condarc


按 i 键进入 [vim](https://so.csdn.net/so/search?q=vim&spm=1001.2101.3001.7020) 的编辑模式，插入下面的指令后，按 esc 键退出 ，在按‘ ：’键，输入wq,回车保存退出即可。

    channels:
      - https://mirrors.ustc.edu.cn/anaconda/pkgs/main/
      - https://mirrors.ustc.edu.cn/anaconda/cloud/conda-forge/
      - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
      - defaults
    show_channel_urls: true


D. 删除源：

    conda config --remove channels 'https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/'


2\. 关于 pip 指令添加镜像
-----------------

A. Linux系统下：

修改~/.pip/pip.conf（如果没有此文件，可以创建此文件夹和文件），内容如下：

    index-url = https://pypi.tuna.tsinghua.edu.cn/simple
    [install]
    trusted-host = pypi.tuna.tsinghua.edu.cn


B. Windows系统下：

直接在user目录中创建一个pip目录，如：C:\\Users\\xx\\pip，新建文件pip.ini，内容同上：

    [global]
    index-url = https://pypi.tuna.tsinghua.edu.cn/simple
    [install]
    trusted-host = pypi.tuna.tsinghua.edu.cn


C. 每次安装文件时都进行更换的方法，因为有些文件可能在清华源中没有，所以推荐此种方法，包可以放前面也可以放后面：

    pip install 
    -i https://mirrors.aliyun.com/pypi/simple/some-package 
    pip install -i https://pypi.tuna.tsinghua.edu.cn/simple/
    some-package
    pip install some-package -i http://pypi.douban.com/simple/


D. 对于在Windows上安装，如果安装pytorch这种不在国内的网址，在镜像网址中也不存在，可以挂VPN提高下载速度；但是如果对于在清华源存在的，就需要关掉VPN，不然就会报错如下：

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210209110725305.png#pic_center)

3\. conda 操作虚拟环境
----------------

A. 查看所有的虚拟环境：

    conda env list 或者 conda info -e


B. conda 创建虚拟环境

    conda create -n env_name python=x.x


C. 进入虚拟环境

    conda activate env_name


D. 查看虚拟环境的配置

    conda list


E. 退出虚拟环境

    conda deactivate env_name
    conda activate base


F. 删除虚拟环境

删除整个虚拟环境：

    conda remove -n your_env_name(虚拟环境名称) --all


删除虚拟环境的某个包：

    conda remove --name $your_env_name  $package_name


或者在这个虚拟环境中直接删除包即可

4\. 在虚拟环境安装 jupyter notebook
----------------------------

```shell
pip install ipykernel
python -m ipykernel install --user --name pytorch # pytorch
python -m ipykernel install --user --name paddle--display --name "paddle" # paddle
```


在执行第2行指令后，可能会报如下错误：

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201022193348385.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3UwMTI5OTc3NTU=,size_16,color_FFFFFF,t_70#pic_center)  
解决办法：将原来的prompt-toolkit-3.0.3版本降为 2.0.10版本：

    pip uninstall -y ipython prompt_toolkit
    pip install prompt-toolkit==2.0.10


![在这里插入图片描述](https://img-blog.csdnimg.cn/20201022193846399.png#pic_center)  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20201022193856979.png#pic_center)  
检验，使用如下命令行：

    python -m ipykernel --version


如果不报错，正常显示 IPython 版本，则认为成功，如果提示 No module named ‘IPython’，则重新执行如下指令：

    pip install ipykernel


正确结果如下图所示：

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201022194310830.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3UwMTI5OTc3NTU=,size_16,color_FFFFFF,t_70#pic_center)  
然后重新执行如下指令，完成最终操作：

    python -m ipykernel install --user --name pytorch


结果如下图：

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201022194535220.png#pic_center)

# 3.CMD

## 3-1 CMD 常用命令总结

**小技巧：**

- 输入 `help`，查看帮助；
- Tab 键，自动补全；
- 上/下方向键，查看历史命令；
- 右键窗口标题栏 -\> 属性，可以修改外观样式。

![](https://pic1.zhimg.com/v2-305b10997412eb4c66c41d549b84c998_b.jpg)

![](https://pic1.zhimg.com/v2-305b10997412eb4c66c41d549b84c998_r.jpg)

### **\# 关机、重启、注销、休眠、定时**

- 关机：`shutdown /s`
- 重启：`shutdown /r`
- 注销：`shutdown /l`
- 休眠：`shutdown /h /f`
- 取消关机：`shutdown /a`
- 定时关机：`shutdown /s /t 3600`（3600 秒后关机）

![](https://pic4.zhimg.com/v2-dbeb7973c980d06635bb518399a55a67_b.jpg)

![](https://pic4.zhimg.com/v2-dbeb7973c980d06635bb518399a55a67_r.jpg)

### **\# 目录操作**

**切换目录，进入指定文件夹：**

- 切换磁盘：`d:`（进入 d 盘）
- 切换磁盘和目录：`cd /d d:/test`（进入 d 盘 test 文件夹）
- 进入文件夹：`cd \test1\test2`（进入 test2 文件夹）
- 返回根目录：`cd \`
- 回到上级目录：`cd ..`
- 新建文件夹：`md test`

**显示目录内容：**

- 显示目录中文件列表：`dir`
- 显示目录结构：`tree d:\test`（d 盘 test 目录）
- 显示当前目录位置：`cd`
- 显示指定磁盘的当前目录位置：`cd d:`

![](https://pic4.zhimg.com/v2-0356938ec7e1d3d2fcb94e389275a65f_b.jpg)

![](https://pic4.zhimg.com/v2-0356938ec7e1d3d2fcb94e389275a65f_r.jpg)

### **\# 网络操作**

- 延迟和丢包率：`ping ip/域名`
- Ping 测试 5 次：`ping ip/域名 -n 5`
- 清除本地 DNS 缓存：`ipconfig /flushdns`
- 路由追踪：`tracert ip/域名`

### **\# 进程/服务操作**

**进程管理：**

- 显示当前正在运行的进程：`tasklist`
- 运行程序或命令：`start 程序名`
- 结束进程，按名称：`taskkill /im notepad.exe`（关闭记事本）
- 结束进程，按 PID：`taskkill /pid 1234`（关闭 PID 为 1234 的进程）

**服务管理：**

- 显示当前正在运行的服务：`net start`
- 启动指定服务：`net start 服务名`
- 停止指定服务：`net stop 服务名`

## 3-2 保存为 .bat 可执行文件

我们可以将常用的命令输入记事本中，并保存为后缀为 `.bat` 的可执行文件。

以后只要双击该文件即可执行指定命令；将文件放入系统【启动】目录中，可以实现开机自动运行。

![](https://pic1.zhimg.com/v2-a885bc0a6844470fb43f2025c2991abc_b.jpg)

![](https://pic1.zhimg.com/v2-a885bc0a6844470fb43f2025c2991abc_r.jpg)

**注：**启动目录位置：\[C:\\Users\\用户名\\AppData\\Roaming\\Microsoft\\Windows\\Start Menu\\Programs\\Startup\]

## 3-3 使用实践

**使用示例 1：**

在资源管理器卡死时，我们可以使用 `taskkill` 命令重启。将下面命令保存为 `ReExplorer.bat`，在需要时双击即可强制重启资源管理器。或直接打开 CMD 运行命令也可以。

```shell
taskkill /f /im explorer.exe & start explorer.exe
```

**使用示例 2：**

迅雷会在后台自动运行 ThunderPlatform.exe 进程和 XLServicePlatform 服务，如果当前没有使用迅雷的话显然没必要。

我们可以将如下代码保存为 `killxl.bat`，并放入【启动】目录，开机后会自动运行该脚本，清除这两个进程。

```shell
net stop XLServicePlatform
taskkill /F /im ThunderPlatform.exe
```

# 4. Jupyter

Jupyter Notebook 有两种模式，一种是命令行模式(Command Mode, 蓝色单元格)，一种是编辑模式(Edit Mode, 绿色单元格)

- 进入命令模式： ESC/ Ctrl + M
- 进入编辑模型： Enter/鼠标左键
- 编辑快捷键：帮助-编辑快捷键

## 1.1 命令模式 (Command Mode)

- H 显示快捷键

### 1.1.1. 内核

- I,I : 中断Notebook内核
- 0,0 : 重启Notebook内核
- **Enter** : 转入编辑模式
- **Shift-Enter** : 运行本单元，选中下个单元
- **Ctrl-Enter** : 运行本单元
- **Alt-Enter** : 运行本单元，在其下插入新单元

### 1.1.2. 单元格格式

- Y: 单元格进入代码格式
- M: 单元格进入Markdown 模式
- R: 清除单元格格式
- 1：把代码块变成heading 1
- 2：把代码块变成heading 2
- 3：把代码块变成heading 3
- 4：把代码块变成heading 4

### 1.1.3. 选择单元格

- K/上(J/下) 选择上(下)方单元格
- Shift + 上/K(下/J): 扩展向上选择
- Shift + 空格 向上滚动
- 空格 向下滚动

### 1.1.4. 编辑单元格

- Shift + M 合并单元格
- A/B 在上(下)插入单元格
- X 剪切单元格
- C 复制单元格
- Shift+V 粘贴在上面
- V 粘贴在下面
- Z 撤销删除
- D,D 删除选中单元格
- S/Ctrl + S 保存并检查
- Shift + L 全部代码块显示行号
- L 显示当前代码块行号
- F 查找替换
- O 隐藏输出

## 1.2. 编辑模式

- ALT + 鼠标左键 多行编辑
- Shift + Tab会显示你刚才输入对象的文档
- Ctrl + A 全选
- Ctrl + X/C/V 剪切/复制/粘贴
- Ctrl + Z 撤销
- Ctrl + Y 重做
- Ctrl + / 注释
- Ctrl + D 删除整行
- Ctrl + U 撤销选择
- Ctrl + S 保存
- Ctrl + Shift + M 在光标处分割代码块

### 1.2.1. 跳转

- Ctrl + Home/上 跳到单元格起始处
- Ctrl + End/下 跳到单元格末尾
- Ctrl + 左/右 跳至单词左/右边

### 1.2.2. 运行

- Shift + Enter 运行代码块, 选择下面的代码块
- Ctrl + Enter 运行选中的代码块

# 5. Git

## 一、学习目标

## 二、版本控制

版本控制是一种记录若干文件内容变化，以便将来查阅特定版本修订情况的系统.简单讲就是备份和记录。

三种不同版本控制的发展历程。

### 1、本地版本控制系统

人们把项目拷贝到本地磁盘上进行备份，然后以命名方式来区分.这种做法好处是简单，但坏处也不少比如备份比较多或许就会混淆不同版本之间的区别。

本地版本管理就是把版本号存入数据库来记录文件的历次更新差异。

### 2、集中化版本控制系统

本地版本控制系统能够将不同版本的文档保存下来并且借助版本记录可以很方便定位相关文件但又引入了新的问题，如何让在不同系统上的开发者协同工作？

于是，集中化的版本控制系统（Centralized Version Control Systems，简称CVCS)应运而生。这类系统，诸如CVS,Subversion以及Perforce等，都有一个单一的集中管理的服务器，保存所有文件的修订版本，而协同工作的人们都通过客户端连到这台服务器，取出最新的文件或者提交更新。多年以来，这已成为版本控制系统的标准做法。

这样做的好处是解决了人们开发协同的问题，但是把所有的代码提交到同一台服务器上有一个很明显的问题就是单点故障，如果这台服务器宕机了，那所有人都不能提交代码，还有如果这台服务器如果磁盘发生故障，碰巧没做备份，或者备份不够及时，就还是会有丢失数据的风险。最坏的情况是彻底丢失整个项目的所有历史更改记录，而被客户端提取出来的某些快照数据除外，但这样的话依然是个问题，你不能保证所有的数据都已经有人事先完整提电出来过。本地版本控制系统也存在类似问题，只要整个项目的历史记录被保存在单一位置，就有丢失所有历史更新记录的风险。

### 3、分布式版本控制系统

为了解决集中化版本管理所带来的问题分布式版本管理控制系统（Distributed Version Control System，简称DVCS)就应运而生了.在这类系统中，像Git,Mercurial,Bazaar以及Darcs等，客户端不只是提取出最新版的文件快照，而是把最原始的代码仓库镜像到本地.这样一来，任何一处协同工作用的服务器发生故障，事后都可以用任何一个镜像出来的本地仓库恢复。因为每一次的提取操作，实际上都是一次对代码仓库的完整备份。

## 三、Windows安装

在使用用Git工作之前，我们需要做个一次性的配置。方便后续Git能跟踪到谁做了修改，我们需要设置对应的用
户名与邮箱地址。

```shell
git config--global user.name"your_username"
git config--global user.email your_email@domain.com
git config--list	# 查看所有配置
```

注意`git config`命令的`--global`参数，用了这个参数，表示这台机器上所有的Git仓库都会使用这个配置，当然也可以对某个仓库指定不同的用户名和Email地址。

## 四、理解Git文件的三种状态与工作模式

使用Git操作文件时，文件的状态有以下三种状态：

| 状态              | 描述                                                         |
| ----------------- | ------------------------------------------------------------ |
| 已提交(committed) | 数据已经安全的保存在本地数据库中                             |
| 已修改(modified)  | 修改了文件，但还没保存到数据库中                             |
| 已暂存(staged)    | 对一个已修改文件的当前版本做了标记，使之包含在下次提交的快照中 |

针对Git文件的三种状态，需要了解Git项目的三个工作区域：工作区、暂存区和Git仓库：

| 分类    | 描述                                                         |
| ------- | ------------------------------------------------------------ |
| 工作区  | 简单的理解为在电脑里能看到的目录，比如自己创建的本地项目目录 |
| 暂存区  | Git的版本库里存了很多东西，其中最重要的就是称为stage（或者叫index）的暂存区，还有Git自动创建的第一个分支master，以及指向master的一个指针叫HEAD |
| Git仓库 | 工作区有一个隐藏目录`.git`，这个不算工作区，而是Git的版本库  |

基本的Git工作流程描述如下：

- 在工作区中进行修改
- 对修改后的内容进行快照，然后添加到暂存区
- 提交更新，将保存在暂存区域的文件快照永久转储到Git仓库中

## 五、创建版本库并提交文件

版本库又名仓库，可以简单理解成一个目录，这个目录里面的所有文件都可以被Git管理起来，每个文件的修改、删除，Git都能跟踪，以便任何时刻都可以追踪历史，或者在将来某个时刻可以“还原”。理解了Git文件状态与三种工作区域之后，通过一个例子来体验Git对于文件的基本操作。

`编写一个文本文件并将文件提交到git仓库`

- 初始化git本地仓库

  通过执行`git init`命令在本地初始化一个本地仓库，执行该命令后会在本地初始化一个没有任何文件的空仓库。

  ![image-20220730221718394](https://s2.loli.net/2022/07/30/NfGStJIwlpEDBZz.png)

- 创建内容并添加到暂存区

  进行一定的内容书写后，使用`git status`查看工作目录与暂存区文件状态

  ```
  git status 命令用于显示工作目录和暂存区的状态。使用此命令能看到那些修改被暂存到了，哪些没有，哪些文件没有被Git tracked到。
  ```

  ![image-20220730222237839](https://s2.loli.net/2022/07/30/8o2fbdvsLXyKzPp.png)

- 执行 git add 命令添加文件到暂存区

  ```
  git add path 通常是通过git add <path>的形式把<path>添加到素引库中，<path>可以是文件也可以是目录。git不仅能判断出<path>中，修改（不包括已删除）的文件，还能判断出新添的文件，并把它们的信息添加到素引库中。
  ```

  ![image-20220730222218556](https://s2.loli.net/2022/07/30/k6sJmXcvYz4Wg8x.png)

- 提交文件到本地版本库

  文件被添加到暂存区后，执行`git commit`命令提交暂存区文件到本地版本库中

  ```
  git commit 命令用于将更改记录（提交）到存储库。将索引的当前目录内容与描述更改的用户和日志消息一起存储在新的提交中。通常在执行提交时再用 git commit 后跟上 -m 属性，加入本次提交的记录说明，方便后续查看提交或改动记录。
  ```

  ![image-20220730222558497](https://s2.loli.net/2022/07/30/PFxHSlEvn9qm5cg.png)

- 用于显示提交日志信息`git log`

  ![image-20220730223019300](https://s2.loli.net/2022/07/30/xbTcewdNvXMO1PF.png)

## 六、时光穿梭机

企业中在多人项目开发环境下，使用Git版本控制工具对项目版本进行管理时，通常会对项目不同版本的文件进行查看，项目历史版本，未来版本的切换操作，对于一个项目开发人员，此时对于Git的这些基本操作命令操作就成为了一项基本技能。

### 1、修改文件与文件提交

#### `git add [file]`

#### `git status`

#### `git commit [-m] […]`

#### `git log`

#### `git diff HEAD -- [file]`

可以执行上述操作与版本库内容进行对比

![image-20220730224235132](https://s2.loli.net/2022/07/30/4VztqOw3HupghZB.png)

```
差异比较说明：
`---`：表示变动前的文件
`+++`：表示变动后的文件
变动的位置用两个@作为起首和结束
@@ -2,4 +2,6 @@：减号表示第一个文件，“2”表示第2行，’4‘表示连续4行。同样的，“+2,6”表示变动后，成为第二个文件从第2行开始的连续6行。
```

#### `git reset HEAD`

可以用以上命令对暂存区文操作进行撤销

![image-20220730224716692](https://s2.loli.net/2022/07/30/QIfRhbHLMpDKnEy.png)

### 2、版本回退

当文件修改后被提交的次数很多时，对于版本库中存放的文件就会出现不同的版本，在多人开发的项目环境中，通常会对不同版本文件进行查看甚至回退的情况（比如某些游戏中所提供的状态保存功能，能够在某一时刻保存整个游戏场景状态以方便后续继续在该状态下进行游戏进行而不是从头开始）值得庆幸的是Git也提供了同样的功能，能够让开发者在不同版本的项目中进行切换，达到时空穿梭自如的目的！

#### `git log`

对于上面操作的0731.txt文件已有几个版本，对于历史版本的查看使用`git log`命令：

![image-20220730224900468](https://s2.loli.net/2022/07/30/O7giAzIubXd6SwP.png)

- 简化log显示

  `git log -5 --pretty=oneline`

  ![image-20220730225432049](https://s2.loli.net/2022/07/30/qKONLQJH9hU5fR4.png)

#### `git reset --hard HEAD`

- `git reset --hard HEAD^`：一个^回退一个版本

- `git reset --hard HEAD~1`：数字表示后退相应版本

- `git reset --hard [版本号]`：回退到版本号对应版本

  ![image-20220730230000733](https://s2.loli.net/2022/07/30/KMOCmwrjZg2J73X.png)

#### `git reflog`

![image-20220730231449364](https://s2.loli.net/2022/07/30/rvsPHzxU1jLBWma.png)

### 3、文件删除

#### `git checkout [file]`

删除误操作的恢复，从Git仓库拉取工作区删除的文件

![image-20220730232131952](https://s2.loli.net/2022/07/30/EWjqvniQXDhlwTr.png)

#### `git rm [file]`

确认执行删除操作

![image-20220730232421623](https://s2.loli.net/2022/07/30/ECnGFWkqQZ873cU.png)

## 七、远程仓库

​	Git是一个分布式版本控制系统，同一个Git仓库，可以分布到不同的机器上。截止目前，并没有看到分布式的环境，因为以上的操作都在在本地发生的，对于Git,除了前面提到的本地版本库外，Git支持远程仓库的托管服务即
使用者可以将本地版本库中的文件托管到远程服务器进行存储，这样就极大的方便开发，无论你走到哪，只要你的机器能够联网，就可以通过远程的仓库地址得到一份相同的项目库文件，并且下载到本地的文件版本记录与远程文件版本保持一致，并且可以很方便的实现多人协同开发操作。
​	对于Git远程仓库，GitHub(https://github.com/)是比较知名的一个，目前已被微软收购，而国内比较知名的当属码云（https://gitee.com/)了，当然除了这些远程仓库外，在公司，有的公司处于安全考虑，可能会自己搭建一
套Git服务区来自Git的远程仓库，对于内部仓库会有专门人员来进行维护操作。这里以当下比较流行的GitHub仓库来介绍Git远程仓库基本操作与使用。

### 1、克隆远程项目到本地

初次接触GitHub的话，在没有账号的情况下，也可以很容易得到一些比较好的开源项目，即通过克隆的方式将远程项目下载到本地比如现在java12都已经发布，想要找一些java12相关的项目入门，这里就可以借助GitHub来发现你想要的相关项目

#### git clone [https://...]

#### Download ZIP...

### 2、上传到远程仓库

#### 2.1 HTTPS

```shell
echo "# git01" >> README.md
git init
git add [file]
git commit -m "first commit"
git remote add origin https://github.com/Bayyys/git01.git
git push -u origin master
```

#### 2.2 SSH

```shell
echo "# git01" >> README.md
git init
git add [file]
git commit -m "first commit"
git remote add origin git@github.com:Bayyys/git01.git
git push -u origin master
```

- 需要先申请公钥&秘钥

  `ssh-keygen -t rsa -C "475417309@qq.com"`

  ![image-20220731104444471](https://s2.loli.net/2022/07/31/Vo9K1wEiQRSkT3X.png)

- 到`/c/users/BAY/.ssh/id_rsa.pub`中找到公钥

- 添加公钥到SSH Keys

  ![image-20220731105042282](https://s2.loli.net/2022/07/31/n15fE9Rs4MZTguS.png)

  ![image-20220731105337774](https://s2.loli.net/2022/07/31/jYwyApZHl1gPSi5.png)

- 检查测试链接 执行命令`ssh -T git@github.com`

  ![image-20220731105402124](https://s2.loli.net/2022/07/31/4JKWSmEALM1fzXQ.png)

## 八、Git分支操作

开发企业项目中在使用Git或者其他类似版本控制软件对项目版本进行管理时，多人合作的项目在开发时通常不会直接在主干master上进行操作，而是重新开辟新的分支，在新的分支上进行开发调试等操作，当项目调试通过时才会将分支项目的代码合并到主干中，这是在实战中比较好的一种策略，特别是多人协同开发一个项目的情况下尤其明显。Git对于分支操作提供了一下基本命令：

| 命令                                         | 描述                                                         |
| -------------------------------------------- | ------------------------------------------------------------ |
| `git checkout [branch]`                      | 切换到指定分支                                               |
| `git checkout -b [new_branch`]               | 新建分支并切换到新建分支                                     |
| `git branch -d [branch`]                     | 删除指定分支                                                 |
| `git branch`                                 | 查看所有分支，并且*号标记当前所在分支                        |
| `git merge [branch]`                         | 合并分支                                                     |
| `git branch -m | -M [oldbranch] [newbranch]` | 重命名分支，如果newbranch名字分支已经存在，则需要使用-M强制重命名，否则，使用-m进行重命名。 |

- 对不关联分支的提交操作

  `git push --set-upstream origin [main`]

- 查看当前分支文件

  `git ls-files`

#### 1、本地分支创建、合并、重命名与删除

#### 2、分支push与pull操作

相关命令操作：

| 命令                                                    | 描述                             |
| ------------------------------------------------------- | -------------------------------- |
| `git branch -a`                                         | 查看本地与远程分支               |
| `git push origin [branch_name`]                         | 推送本地分支到远程               |
| `git push origin :[remote_branch]`                      | 删除远程分支（本地分支还在保留） |
| `git checkout -b [local_branch] origin/[remote_branch]` | 拉取远程指定分支并在本地创建分支 |

##### git branch -a

查看远程仓库

![image-20220731133504256](https://s2.loli.net/2022/07/31/lDYdzVte4EyNrXF.png)

##### git checkout -b [local_branch] origin/[remote_branch]

拉取远程指定分支并在本地创建分支

![image-20220731135150567](https://s2.loli.net/2022/07/31/7NGZ9eIvCdJAXi5.png)

##### git push origin [branch_name]

推送本地分支

![image-20220731134132944](https://s2.loli.net/2022/07/31/KIAOt2FsCMZhzab.png)

##### git push origin :[remote_branch]

删除远程分支（本地分支还在保留）

![image-20220731134255545](https://s2.loli.net/2022/07/31/BKHo1aWmjpQ9q3T.png)

##### git fetch

读取远程仓库状态

![image-20220731134719899](https://s2.loli.net/2022/07/31/QZiy6KxjlN5zqBO.png)

### 3、分支操作冲突出现与解决

开发中对不同分支下同一文件进行修改后执行合并操作时就会出现文件修改冲突情况，这里说明一种比较常见的冲突问题。

![image-20220731140348223](https://s2.loli.net/2022/07/31/vUP5VoW2XLlIHBu.png)

![image-20220731140428573](https://s2.loli.net/2022/07/31/VGyMcNsfbFjUC64.png)

```
git 用<<<<<<<<,========,>>>>>>>>标记出不同分支的内容
<<<<<<<< HEAD 当前git 指向分支 这里指的为master
======== 分离不同分支修改的内容
>>>>>>>> leaf 同时操作（不允许情况）
```

![image-20220731140732564](https://s2.loli.net/2022/07/31/iuQrWR47qkoHmtc.png)

`git log --graph --pretty=oneline`

分支合并图

![image-20220731141151452](https://s2.loli.net/2022/07/31/K3b9zhfx7H8QwWq.png)

### 2、多人协同操作冲突

先执行pull拉取操作

## 九、标签管理

标签操作基本命令`git tag`

| 命令                                  | 描述                             |
| ------------------------------------- | -------------------------------- |
| git tag [tag_name]                    | 新建标签，默认为HEAD             |
| git tag -a [tag_name] -m 'xxx'        | 添加标签并制定标签描述信息       |
| git tag                               | 查看所有标签                     |
| git tag -d [tag_name]                 | 删除一个本地标签                 |
| git push origin [tag_name]            | 推送本地标签到远程               |
| git push origin --tags                | 推送算不未推送过的本地标签到远程 |
| git push origin :refs/tags/[tag_name] | 删除一个远程标签                 |

Git可以对某一时间点上的版本打上标签。开发中在发布某个软件版本（比如v1.0等等）的时候，通常使用版本命令对某一版本打上一个标签，以方便标识。

## 十、Idea下Git基本操作

### 1、 环境集成配置

全局setting下git环境指定

![image-20220731184853916](https://s2.loli.net/2022/07/31/omDcsRSIClP7KZQ.png)

![image-20220731184908478](https://s2.loli.net/2022/07/31/6KcSj73nDVf8t5O.png)

### 2、设置推送忽略文件

![image-20220731185007785](https://s2.loli.net/2022/07/31/RHuV2EjrpmZxXdN.png)

- 若无效，则需要清除已有缓存、

```shell
1、查看git跟踪的列表
git ls-files

2、删除被跟踪的文件或文件夹
git rm --cached 文件名称
git rm  --cached 文件夹名称 -r

3、重新添加gitignore规则
```

### 3、 冲突解决

与终端操作类似。

## 十一、上传大文件

```shell
git lfs track "*.*"[files]
git add .gitattributes
git add all
……
```

# 6. Markdown  

1 概述
--

### 1-1 设计理念

Markdown 易于阅读，方便创作web文档，利于各平台无缝分发。  
Markdown 语法灵感最大的来源还是纯文本 email 的格式，完全由标点符号标签组成的纯文本。  
Markdown 文件应该以纯文本形式原样发布，不应该包含标记标签和格式化指令。

### 1-2 内联 HTML 语法

HTML 是一种发布格式，Markdown 是一种创作格式。  
Markdown语法集合比较小，只是HTML标签的一小部分。  
对于 Markdown 中未包含的标签, 可以直接使用 HTML标签，例如用 HTML `<a>`标签替代 Markdown 的链接语法。

### 0-3 特殊字符自动[转义](https://so.csdn.net/so/search?q=%E8%BD%AC%E4%B9%89&spm=1001.2101.3001.7020)

在 HTML 中, 有两个字符需要特殊对待: < 和 &，左尖括号用于起始标签。果你想将它们用作字面量, 你必须将它们转义为字符实体, 例如(`&lt;`)< 和 (`&amp;`)&。

2 行内语法讲解
------

### 2-1 注释的表述

#### 代码法

    <div style='display: none'>
    哈哈我是注释，不会在浏览器中显示。
    </div>


这种方法CSDN不支持，但是直接转成html是可行的

#### html注释

既然支持html语法，那也支持html注释，快捷键 command + /。

    <!--哈哈我是注释，不会在浏览器中显示。-->
    
    <!--
    哈哈我是多段注释，
    不会在浏览器中显示。
        -->

<!--哈哈我是注释，不会在浏览器中显示。-->

_这里真的有注释···_

#### hack方法

hack方法就是利用markdown的解析原理来实现注释的。  
一般有的markdown解析器不支持上面的注释方法，这个时候就可以用hack方法。  
hack方法比上面2种方法稳定得多，但是语义化太差。

    [//]: # (哈哈我是最强注释，不会在浏览器中显示。)
    [^_^]: # (哈哈我是最萌注释，不会在浏览器中显示。)
    [//]: <> (哈哈我是注释，不会在浏览器中显示。)
    [comment]: <> (哈哈我是注释，不会在浏览器中显示。)

### 2-2 分级标题、任务列表

#### 分级标题

    # 一级标题
    ## 二级标题
    ### 三级标题
    #### 四级标题
    ##### 五级标题
    ###### 六级标题  <!--最多6级标题-->


#### 任务列表

Markdown 语法：

    - [ ] 任务一 未做任务 `- + 空格 + [ ]`
    - [x] 任务二 已做任务 `- + 空格 + [x]`


效果如下：

- [ ] 任务一 未做任务 `- + 空格 + [ ]`
- [x] 任务二 已做任务`- + 空格 + [x]`

### 2-3 缩进、换行、空行、对齐方式

#### 首行缩进

不同特殊占位符所占空白是不一样大的。

1.  `&emsp;` 或`&#8195;`  //全角
2.  `&ensp;` 或`&#8194;` //半角
3.  `&nbsp;` 或`&#160;`  //半角之半角（你还真的能看出来吗）
4.  或//啥也没有

#### 换行

由于markdown编辑器的不同,可能在一行字后面，直接换行回车，也能实现换行，但是在有的地方，想要换行必须得在一行字后面空两个格子才行。

#### 空行

在编辑的时候有多少个空行(只要这一行只有回车或者space没有其他的字符就算空行)，在渲染之后，只隔着一行。

对齐方式  
代码：

    <center>行中心对齐</center>
    <p align="left">行左对齐</p>
    <p align="right">行右对齐</p>


显示效果：

行中心对齐

行左对齐

行右对齐

### 2-4 斜体、粗体、删除线、下划线、背景高亮

代码：

    *斜体* 或 _斜体_
    **粗体** 或 __粗体__
    ***加粗斜体***
    ~~删除线~~
    ++下划线++（又是CSDN不支持···）
    ==背景高亮==

显示效果：  
_斜体_ 或 _斜体_  
**粗体** 或 **粗体**  
_**加粗斜体**_  
~~删除线~~  
++下划线++  
==背景高亮==

### 2-5 超链接、页内链接、自动链接、注脚

#### 行内式

> 语法说明：  
> \[\]里写链接文字，()里写链接地址, ()中的""中可以为链接指定title属性，title属性可加可不加。title属性的效果是鼠标悬停在链接上会出现指定的 title文字，链接地址与title前有一个空格。

代码：

    欢迎阅读 [Lapland Stark](https://blog.csdn.net/weixin_45494811)


显示效果：

欢迎阅读 [Lapland Stark](https://blog.csdn.net/weixin_45494811)

#### 参考式

参考式超链接一般用在学术论文上面，或者另一种情况，如果某一个链接在文章中多处使用，那么使用_引用_ 的方式创建链接将非常好，它可以让你对链接进行统一的管理。

> 语法说明：  
> 参考式链接分为两部分，文中的写法 \[链接文字\]\[链接标记\]，在文本的任意位置添加\[链接标记\]:链接地址。

如果链接文字本身可以做为链接标记，你也可以写成

    [链接文字][Num]
    [链接文字]：链接地址的形式，见代码的最后一行。


代码：

    我经常去的几个网站[Google][1]、[Leanote][2]。
    
    [1]:http://www.google.com
    [2]:http://www.leanote.com

显示效果：

我经常去的几个网站[Google](http://www.google.com)、[Leanote](http://www.leanote.com)。

#### 脚注

在需要添加注脚的文字后加上脚注名字 \[^注脚名字\] ,称为加注。 然后在文本的任意位置(一般在最后)添加脚注，脚注前必须有对应的脚注名字。

注意：经测试注脚与注脚之间必须空一行，不然会失效。成功后会发现，即使你没有把注脚写在文末，经Markdown转换后，也会自动归类到文章的最后。

代码：

    使用 Markdown[^1]可以效率的书写文档, 直接转换成 HTML[^2]。
    
    [^1]:Markdown是一种纯文本标记语言
    
    [^2]:HyperText Markup Language 超文本标记语言


显示效果：

使用 Markdown[^6.1]可以效率的书写文档, 直接转换成 HTML[^6.2]。

注：脚注自动被搬运到最后面，请到文章末尾查看，脚注后方的链接可以直接跳转回到加注的地方。

#### [锚点](https://so.csdn.net/so/search?q=%E9%94%9A%E7%82%B9&spm=1001.2101.3001.7020)（页内超链接）

网页中，锚点其实就是页内超链接，也就是链接本文档内部的某些元素，实现当前页面中的跳转。比如我这里写下一个锚点，点击回到目录，就能跳转到目录。 在目录中点击这一节，就能跳过来。还有下一节的注脚。这些根本上都是用锚点来实现的，只支持在标题后插入锚点，其它地方无效。

#### 自动链接

语法说明：  
Markdown 支持以比较简短的自动链接形式来处理网址和电子邮件信箱，只要是用<>包起来， Markdown 就会自动把它转成链接。一般网址的链接文字就和链接地址一样，例如：

代码：

    &lt;http://example.com/&gt; &emsp;&emsp;
    &lt;address@example.com&gt;
    <http://example.com/>   
    <address@example.com>

显示效果：  
<http://example.com/>     
<address@example.com>  
[http://example.com/](http://example.com/)     
[address@example.com](mailto:address@example.com)

#### 页内跳转

```html
[内容](#编号)
[跳转](#1.1)

<div id="编号">跳转内容</div>
<div id="1.1">跳转结果</div>
```

显示效果：
[跳转](#1.1)

<div id="1.1">跳转结果</div>

### 2-6 无序列表、有序列表、定义型列表

#### 无序列表

使用 \*，\+，\- 表示无序列表。  
代码：

    * 无序列表项 一
    + 无序列表项 二
    - 无序列表项 三


显示效果：

*   无序列表项 一

*   无序列表项 二

*   无序列表项 三

#### 有序列表

有序列表则使用数字接着一个英文句点。  
代码：

    1. 有序列表项 一
    2. 有序列表项 二
    3. 有序列表项 三


显示效果：

1.  有序列表项 一
2.  有序列表项 二
3.  有序列表项 三

#### 定义型列表

> 语法说明：  
> 定义型列表由名词和解释组成。空一行，然后一行写上定义，紧跟一行写上解释。解释的写法:紧跟一个缩进(Tab)

代码

    Markdown
    :   轻量级文本标记语言（左侧有一个可见的冒号和四个不可见的空格）

显示效果：

Markdown

:   轻量级文本标记语言（左侧有一个可见的冒号和四个不可见的空格）

### 2-7 插入图像

语法中图片Alt的意思是如果图片因为某些原因不能显示，就用定义的图片Alt文字来代替图片。 图片Title则和链接中的Title一样，表示鼠标悬停y于图片上时出现的文字。 Alt 和 Title 都不是必须的，可以省略，但建议写上。

> 语法：

    <center>  <!--开始居中对齐-->
    
    ![Lapland](https://img-blog.csdnimg.cn/20200214111424248.jpeg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTQ5NDgxMQ==,size_16,color_FFFFFF,t_70 "Lapland")
    </center> <!--结束居中对齐-->


效果如下：

![Lapland](https://img-blog.csdnimg.cn/20200214111424248.jpeg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTQ5NDgxMQ==,size_16,color_FFFFFF,t_70 "Lapland")

### 2-8 多级引用

> 语法说明：

引用需要在被引用的文本前加上>符号和空格，允许多层嵌套，也允许你偷懒只在整个段落的第一行最前面加上 \> 。

代码：

    >>> 请问 Markdwon 怎么用？ - 小白
    >> 自己看教程！ - 愤青
    > 教程在哪？ - 小白


显示效果：

> > > 请问 Markdwon 怎么用？ - 小白  
> > > 自己看教程！ \- 愤青  
> > > 教程在哪？ \- 小白

### 2-9 转义字符、字体、字号、颜色

Markdown中的转义字符为\\，转义的有：

\ 反斜杠 ` 反引号 * 星号 _ 下划线 {} 大括号 \[\] 中括号 () 小括号  # 井号 + 加号 - 减号 . 英文句号 ! 感叹号

字体、字号、颜色  
代码：

    <font face="黑体">我是黑体字</font>
    <font face="微软雅黑">我是微软雅黑</font>
    <font face="STCAIYUN">我是华文彩云</font>
    <font color=#0099ff size=12 face="黑体">黑体</font>
    <font color=gray size=5>gray</font>
    <font color=#00ffff size=3>null</font>

显示效果：  
<font face="黑体">我是黑体字</font>
<font face="微软雅黑">我是微软雅黑</font>
<font face="STCAIYUN">我是华文彩云</font>
<font color=#0099ff size=12 face="黑体">黑体</font>
<font color=gray size=5>gray</font>
<font color=#00ffff size=3>null</font>

3 块语法讲解
-----

### 内容目录

在段落中填写 \[TOC\] 以显示全文内容的目录结构。

`@[toc]`  
效果参见最上方的目录。

### 代码块

对于程序员来说这个功能是必不可少的，插入程序代码的方式有两种，一种是利用缩进(Tab), 另一种是利用”`”符号（一般在ESC键下方）包裹代码。

#### 行内式

代码：

    C语言里的函数 `scanf()` 怎么使用？


显示效果：

C语言里的函数 `scanf()`怎么使用？

### 缩进式多行代码

缩进 4 个空格或是 1 个制表符

一个代码区块会一直持续到没有缩进的那一行（或是文件结尾）。

代码：

    	#include &lt;stdio.h&gt;
    	int main(void)
    	{
    	    printf(&#34;Hello world\n&#34;);
    	}


显示效果：

    #include &lt;stdio.h&gt;
    int main(void)
    {
        printf(&#34;Hello world\n&#34;);
    }


用六个`包裹多行代码  
代码：

    ```
    include <stdio.h>
    int main(void)
    {
    printf("Hello world\n");
    }
    ```


显示效果：

    include <stdio.h>
    int main(void)
    {
    printf("Hello world\n");
    }


### 流程图

编辑自有道云笔记，代码：

    ```mermaid
    graph LR
    A-->B
    ```
    
    ```mermaid
    sequenceDiagram
    A->>B: How are you?
    B->>A: Great!
    ```


显示效果：

A

B

A B How are you? Great! A B

### 表格

> 语法说明：  
> 不管是哪种方式，第一行为表头，第二行分隔表头和主体部分，第三行开始每一行为一个表格行。  
> 列于列之间用管道符|隔开。原生方式的表格每一行的两边也要有管道符。  
> 第二行还可以为不同的列指定对齐方向。默认为左对齐，在-右边加上:就右对齐。

*   左对齐， :-: 中心对齐，-: 右对齐

表格代码：

| 学号 | 姓名 | 性别 |
| ----: | :---: | --:-- |
| ---: | :--: | :--- |

### LaTeX 公式

表示行内公式  
代码：

质能守恒方程可以用一个很简洁的方程式 `$E = m c^2$`来表达。

$E = m c^2$

### 分隔线

你可以在一行中用三个以上的星号、减号、底线来建立一个分隔线，行内不能有其他东西。你也可以在星号或是减号中间插入空格。下面每种写法都可以建立分隔线：

代码：

    * * *
    ***
    *****
    - - -
    -----------


* * *

* * *

* * *

* * *

* * *

显示效果都一样：

### HTML 原始码

在代码区块里面， & 、 < 和 \> 会自动转成 HTML 实体，这样的方式让你非常容易使用 Markdown 插入范例用的 HTML 原始码，只需要复制贴上，剩下的 Markdown 都会帮你处理，例如：

代码：

    第一个例子：
    <div class="footer">
    © 2004 Foo Corporation
    </div>
    第二个例子：
    <center>
    
    <table>
    <tr>
    <th rowspan="2">值班人员</th>
    <th>星期一</th>
    <th>星期二</th>
    <th>星期三</th>
    </tr>
    <tr>
    <td>李强</td>
    <td>张明</td>
    <td>王平</td>
    </tr>
    </table>
    
    第三个例子：
    <details>
    <summary>展开查看</summary>
    <pre><code>
    System.out.println("Hello to see U!");
    </code></pre>
    </details>



显示效果：

第一个例子：

© 2004 Foo Corporation

第二个例子：

<table>
<tr>
<th rowspan="2">值班人员</th>
<th>星期一</th>
<th>星期二</th>
<th>星期三</th>
</tr>
<tr>
<td>李强</td>
<td>张明</td>
<td>王平</td>
</tr>
</table>

第三个例子：

<details>
<summary>展开查看</summary>
<pre><code>
System.out.println("Hello to see U!");
</code></pre>
</details>

### 特殊字

特殊字符 描述 字符的代码  
空格符    
< 小于号 <

> 大于号 >  
> & 和号 &  
> ￥ 人民币 ¥  
> © 版权 ©  
> ® 注册商标 ®  
> °C 摄氏度 °C  
> ± 正负号 ±  
> × 乘号 ×  
> ÷ 除号 ÷  
> ² 平方（上标²） ²  
> ³ 立方（上标³） ³

注：本文根据[简书文章](https://www.jianshu.com/p/ebe52d2d468f)修改完成

* * *

[^6.1]:Markdown是一种纯文本标记语言
[^6.2]:HyperText Markup Language 超文本标记语言

# 7.Docker

## 1.简介和安装

[🎉 Docker 简介和安装 - Docker 快速入门 - 易文档 (easydoc.net)](https://docker.easydoc.net/doc/81170005/cCewZWoN/lTKfePfP)

### Docker 是什么

> Docker 是一个应用打包、分发、部署的工具
> 你也可以把它理解为一个轻量的虚拟机，它只虚拟你软件需要的运行环境，多余的一点都不要，
> 而普通虚拟机则是一个完整而庞大的系统，包含各种不管你要不要的软件。

### 跟普通虚拟机的对比

| 特性   | 普通虚拟机                                                   | Docker                                               |
| ------ | ------------------------------------------------------------ | ---------------------------------------------------- |
| 跨平台 | 通常只能在桌面级系统运行，例如 Windows/Mac，无法在不带图形界面的服务器上运行 | 支持的系统非常多，各类 windows 和 Linux 都支持       |
| 性能   | 性能损耗大，内存占用高，因为是把整个完整系统都虚拟出来了     | 性能好，只虚拟软件所需运行环境，最大化减少没用的配置 |
| 自动化 | 需要手动安装所有东西                                         | 一个命令就可以自动部署好所需环境                     |
| 稳定性 | 稳定性不高，不同系统差异大                                   | 稳定性好，不同系统都一样部署方式                     |

### 打包、分发、部署

**打包**：就是把你软件运行所需的依赖、第三方库、软件打包到一起，变成一个安装包
**分发**：你可以把你打包好的“安装包”上传到一个镜像仓库，其他人可以非常方便的获取和安装
**部署**：拿着“安装包”就可以一个命令运行起来你的应用，自动模拟出一摸一样的运行环境，不管是在 Windows/Mac/Linux。
<img src="https://sjwx.easydoc.xyz/46901064/files/kv7rlicu.png" alt="docker_logo.png" style="zoom: 25%;" />

### Docker 部署的优势

常规应用开发部署方式：自己在 Windows 上开发、测试 --> 到 Linux 服务器配置运行环境部署。

> 问题：我机器上跑都没问题，怎么到服务器就各种问题了

用 Docker 开发部署流程：自己在 Windows 上开发、测试 --> 打包为 Docker 镜像（可以理解为软件安装包） --> 各种服务器上只需要一个命令部署好

> 优点：确保了不同机器上跑都是一致的运行环境，不会出现我机器上跑正常，你机器跑就有问题的情况。

例如 [易文档](https://easydoc.net/)，[SVNBucket](https://svnbucket.com/) 的私有化部署就是用 Docker，轻松应对客户的各种服务器。

### Docker 通常用来做什么

- 应用分发、部署，方便传播给他人安装。特别是开源软件和提供私有部署的应用
- 快速安装测试/学习软件，用完就丢（类似小程序），不把时间浪费在安装软件上。例如 Redis / MongoDB / ElasticSearch / ELK
- 多个版本软件共存，不污染系统，例如 Python2、Python3，Redis4.0，Redis5.0
- Windows 上体验/学习各种 Linux 系统

### 重要概念：镜像、容器

**镜像**：可以理解为软件安装包，可以方便的进行传播和安装。
**容器**：软件安装后的状态，每个软件运行环境都是独立的、隔离的，称之为容器。

### 镜像加速源

| 镜像加速器          | 镜像加速器地址                          |
| ------------------- | --------------------------------------- |
| Docker 中国官方镜像 | https://registry.docker-cn.com          |
| DaoCloud 镜像站     | http://f1361db2.m.daocloud.io           |
| Azure 中国镜像      | https://dockerhub.azk8s.cn              |
| 科大镜像站          | https://docker.mirrors.ustc.edu.cn      |
| 阿里云              | https://<your_code>.mirror.aliyuncs.com |
| 七牛云              | https://reg-mirror.qiniu.com            |
| 网易云              | https://hub-mirror.c.163.com            |
| 腾讯云              | https://mirror.ccs.tencentyun.com       |

<img src="https://sjwx.easydoc.xyz/46901064/files/l25jdwrn.png" alt="mirrors_set.png" style="zoom: 50%;" />

## 2.快速安装软件

### 直接安装的缺点

- 安装麻烦，可能有各种依赖，运行报错。例如：WordPress，ElasticSearch，Redis，ELK
- 可能对 Windows 并不友好，运行有各种兼容问题，软件只支持 Linux 上跑
- 不方便安装多版本软件，不能共存。
- 电脑安装了一堆软件，拖慢电脑速度。
- 不同系统和硬件，安装方式不一样

### Docker 安装的优点

- 一个命令就可以安装好，快速方便
- 有大量的镜像，可直接使用
- 没有系统兼容问题，Linux 专享软件也照样跑
- 支持软件多版本共存
- 用完就丢，不拖慢电脑速度
- 不同系统和硬件，只要安装好 Docker 其他都一样了，一个命令搞定所有

### 演示 Docker 安装 Redis

Redis 官网：https://redis.io/

> 官网下载安装教程只有源码安装方式，没有 Windows 版本。想要自己安装 windows 版本需要去找别人编译好的安装包。

Docker 官方镜像仓库查找 Redis ：https://hub.docker.com/
![Docker镜像官网](https://sjwx.easydoc.xyz/46901064/files/kv8zs4qr.png)

一个命令跑起来：`docker run -d -p 6379:6379 --name redis redis:latest`
命令参考：https://docs.docker.com/engine/reference/commandline/run/

![Docker运行Redis后](https://sjwx.easydoc.xyz/46901064/files/kv8zy4xn.png)

### 安装 Wordpress

docker-compose.yml

```
version: '3.1'

services:

  wordpress:
    image: wordpress
    restart: always
    ports:
      - 8080:80
    environment:
      WORDPRESS_DB_HOST: db
      WORDPRESS_DB_USER: exampleuser
      WORDPRESS_DB_PASSWORD: examplepass
      WORDPRESS_DB_NAME: exampledb
    volumes:
      - wordpress:/var/www/html

  db:
    image: mysql:5.7
    restart: always
    environment:
      MYSQL_DATABASE: exampledb
      MYSQL_USER: exampleuser
      MYSQL_PASSWORD: examplepass
      MYSQL_RANDOM_ROOT_PASSWORD: '1'
    volumes:
      - db:/var/lib/mysql

volumes:
  wordpress:
  db:
```

### 安装 ELK

```
docker run -p 5601:5601 -p 9200:9200 -p 5044:5044 -it --name elk sebp/elk
```

[内存不够解决方法](https://docs.microsoft.com/en-us/windows/wsl/wsl-config#global-configuration-options-with-wslconfig)
转到用户目录 `cd ~`，路径类似这个：`C:\Users\<UserName>`
创建 `.wslconfig` 文件填入以下内容

```
[wsl2]
memory=10GB # Limits VM memory in WSL 2 to 4 GB
processors=2 # Makes the WSL 2 VM use two virtual processors
```

生效配置，命令行运行 `wsl --shutdown`

### 更多相关命令

`docker ps` 查看当前运行中的容器
`docker images` 查看镜像列表
`docker rm container-id` 删除指定 id 的容器
`docker stop/start container-id` 停止/启动指定 id 的容器
`docker rmi image-id` 删除指定 id 的镜像
`docker volume ls` 查看 volume 列表
`docker network ls` 查看网络列表

## 3.制作自己的镜像

### 为自己的 Web 项目构建镜像

示例项目代码：https://github.com/gzyunke/test-docker
这是一个 Nodejs + Koa2 写的 Web 项目，提供了简单的两个演示页面。
软件依赖：[nodejs](https://nodejs.org/zh-cn/)
项目依赖库：koa、log4js、koa-router

### 编写 Dockerfile

```
FROM node:11
MAINTAINER easydoc.net

# 复制代码
ADD . /app

# 设置容器启动后的默认运行目录
WORKDIR /app

# 运行命令，安装依赖
# RUN 命令可以有多个，但是可以用 && 连接多个命令来减少层级。
# 例如 RUN npm install && cd /app && mkdir logs
RUN npm install --registry=https://registry.npm.taobao.org

# CMD 指令只能一个，是容器启动后执行的命令，算是程序的入口。
# 如果还需要运行其他命令可以用 && 连接，也可以写成一个shell脚本去执行。
# 例如 CMD cd /app && ./start.sh
CMD node app.js
```

[Dockerfile文档](https://docs.docker.com/engine/reference/builder/#run)

> 实用技巧：
> 如果你写 Dockerfile 时经常遇到一些运行错误，依赖错误等，你可以直接运行一个依赖的底，然后进入终端进行配置环境，成功后再把做过的步骤命令写道 Dockerfile 文件中，这样编写调试会快很多。
> 例如上面的底是`node:11`，我们可以运行`docker run -it -d node:11 bash`，跑起来后进入容器终端配置依赖的软件，然后尝试跑起来自己的软件，最后把所有做过的步骤写入到 Dockerfile 就好了。
> 掌握好这个技巧，你的 Dockerfile 文件编写起来就非常的得心应手了。

### Build 为镜像（安装包）和运行

编译 `docker build -t test:v1 .`

> `-t` 设置镜像名字和版本号
> 命令参考：https://docs.docker.com/engine/reference/commandline/build/

运行 `docker run -p 8080:8080 --name test-hello test:v1`

> `-p` 映射容器内端口到宿主机
> `--name` 容器名字
> `-d` 后台运行
> 命令参考文档：https://docs.docker.com/engine/reference/run/

### 更多相关命令

`docker ps` 查看当前运行中的容器
`docker images` 查看镜像列表
`docker rm container-id` 删除指定 id 的容器
`docker stop/start container-id` 停止/启动指定 id 的容器
`docker rmi image-id` 删除指定 id 的镜像
`docker volume ls` 查看 volume 列表
`docker network ls` 查看网络列表

## 4.目录挂载

### 现存问题

- 使用 Docker 运行后，我们改了项目代码不会立刻生效，需要重新`build`和`run`，很是麻烦。
- 容器里面产生的数据，例如 log 文件，数据库备份文件，容器删除后就丢失了。

> 目录挂载解决以上问题

### 几种挂载方式

- `bind mount` 直接把宿主机目录映射到容器内，适合挂代码目录和配置文件。可挂到多个容器上
- `volume` 由容器创建和管理，创建在宿主机，所以删除容器不会丢失，官方推荐，更高效，Linux 文件系统，适合存储数据库数据。可挂到多个容器上
- `tmpfs mount` 适合存储临时文件，存宿主机内存中。不可多容器共享。

文档参考：https://docs.docker.com/storage/

![image.png](https://sjwx.easydoc.xyz/46901064/files/kv96dc4q.png)

### 挂载演示

```
bind mount` 方式用绝对路径 `-v D:/code:/app
volume` 方式，只需要一个名字 `-v db-data:/app
```

示例：
`docker run -p 8080:8080 --name test-hello -v D:/code:/app -d test:v1`

> 注意！
> 因为挂载后，容器里的代码就会替换为你本机的代码了，如果你代码目录没有`node_modules`目录，你需要在代码目录执行下`npm install --registry=https://registry.npm.taobao.org`确保依赖库都已经安装，否则可能会提示“Error: Cannot find module ‘koa’”
> 如果你的电脑没有安装 [nodejs](https://nodejs.org/en/)，你需要安装一下才能执行上面的命令。

## 5.多容器通信

### 学习目标

项目往往都不是独立运行的，需要数据库、缓存这些东西配合运作。
这节我们把前面的 Web 项目增加一个 Redis 依赖，多跑一个 Redis 容器，演示如何多容器之间的通信。

> 本文档课件配套 [视频教程](https://www.bilibili.com/video/BV11L411g7U1?p=5)

### 创建虚拟网络

要想多容器之间互通，从 Web 容器访问 Redis 容器，我们只需要把他们放到同个网络中就可以了。

文档参考：https://docs.docker.com/engine/reference/commandline/network/

### 演示

##### 创建一个名为`test-net`的网络：

```
docker network create test-net
```

##### 运行 Redis 在 `test-net` 网络中，别名`redis`

```
docker run -d --name redis --network test-net --network-alias redis redis:latest
```

##### 修改代码中访问`redis`的地址为网络别名

![image.png](https://sjwx.easydoc.xyz/46901064/files/kv98rfvb.png)

##### 运行 Web 项目，使用同个网络

```
docker run -p 8080:8080 --name test -v D:/test:/app --network test-net -d test:v1
```

##### 查看数据

`http://localhost:8080/redis`
容器终端查看数据是否一致

### 更多相关命令

`docker ps` 查看当前运行中的容器
`docker images` 查看镜像列表
`docker rm container-id` 删除指定 id 的容器
`docker stop/start container-id` 停止/启动指定 id 的容器
`docker rmi image-id` 删除指定 id 的镜像
`docker volume ls` 查看 volume 列表
`docker network ls` 查看网络列表

## 6.Docker-Compose

### 现存问题

在上节，我们运行了两个容器：Web 项目 + Redis
如果项目依赖更多的第三方软件，我们需要管理的容器就更加多，每个都要单独配置运行，指定网络。
这节，我们使用 docker-compose 把项目的多个服务集合到一起，一键运行。

### 安装 Docker Compose

- 如果你是安装的==桌面版 Docker==，不需要额外安装，已经包含了。
- 如果是没图形界面的服务器版 Docker，你需要单独安装 [安装文档](https://docs.docker.com/compose/install/#install-compose-on-linux-systems)
- 运行`docker-compose`检查是否安装成功

### 编写脚本

要把项目依赖的多个服务集合到一起，我们需要编写一个`docker-compose.yml`文件，描述依赖哪些服务
参考文档：https://docs.docker.com/compose/

```
version: "3.7"

services:
  app:
    build: ./
    ports:
      - 80:8080
    volumes:
      - ./:/app
    environment:
      - TZ=Asia/Shanghai
  redis:
    image: redis:5.0.13
    volumes:
      - redis:/data
    environment:
      - TZ=Asia/Shanghai

volumes:
  redis:
```

> 容器默认时间不是北京时间，增加 TZ=Asia/Shanghai 可以改为北京时间

### 跑起来

在`docker-compose.yml` 文件所在目录，执行：`docker-compose up`就可以跑起来了。
命令参考：https://docs.docker.com/compose/reference/up/

在后台运行只需要加一个 -d 参数`docker-compose up -d`
查看运行状态：`docker-compose ps`
停止运行：`docker-compose stop`
重启：`docker-compose restart`
重启单个服务：`docker-compose restart service-name`
进入容器命令行：`docker-compose exec service-name sh`
查看容器运行log：`docker-compose logs [service-name]`

## 7.发布和部署

### 镜像仓库介绍

镜像仓库用来存储我们 build 出来的“安装包”，Docker 官方提供了一个 [镜像库](https://hub.docker.com/)，里面包含了大量镜像，基本各种软件所需依赖都有，要什么直接上去搜索。

我们也可以把自己 build 出来的镜像上传到 docker 提供的镜像库中，方便传播。
当然你也可以搭建自己的私有镜像库，或者使用国内各种大厂提供的镜像托管服务，例如：阿里云、腾讯云

> 本文档课件配套 [视频教程](https://www.bilibili.com/video/BV11L411g7U1?p=7)

### 上传我们的镜像

- 首先你要先 [注册一个账号](https://hub.docker.com/)
- 创建一个镜像库
  ![image.png](https://sjwx.easydoc.xyz/46901064/files/kv9a2wty.png)
- 命令行登录账号：
  `docker login -u username`
- 新建一个tag，名字必须跟你注册账号一样
  `docker tag test:v1 username/test:v1`
- 推上去
  `docker push username/test:v1`
- 部署试下
  `docker run -dp 8080:8080 username/test:v1`

##### docker-compose 中也可以直接用这个镜像了

```
version: "3.7"

services:
  app:
#    build: ./
    image: helloguguji/test:v1
    ports:
      - 80:8080
    volumes:
      - ./:/app
    environment:
      - TZ=Asia/Shanghai
  redis:
    image: redis:5.0.13
    volumes:
      - redis:/data
    environment:
      - TZ=Asia/Shanghai

volumes:
  redis:
```

### 阿里云容器托管

docker 官方的镜像托管有时候上传和下载都太慢了，如果你想要更快的速度，可以使用阿里云的免费镜像托管
登录 [阿里云](https://www.aliyun.com/)

![image.png](https://sjwx.easydoc.xyz/46901064/files/kv9dqxuo.png)

## 8.备份和迁移数据

### 迁移方式介绍

容器中的数据，如果没有用挂载目录，删除容器后就会丢失数据。
前面我们已经讲解了如何 [挂载目录](doc:kze7f0ZR)
如果你是用`bind mount`直接把宿主机的目录挂进去容器，那迁移数据很方便，直接复制目录就好了
如果你是用`volume`方式挂载的，由于数据是由容器创建和管理的，需要用特殊的方式把数据弄出来。

> 本文档课件配套 [视频教程](https://www.bilibili.com/video/BV11L411g7U1?p=8)

### 备份和导入 Volume 的流程

备份：

- 运行一个 ubuntu 的容器，挂载需要备份的 volume 到容器，并且挂载宿主机目录到容器里的备份目录。
- 运行 tar 命令把数据压缩为一个文件
- 把备份文件复制到需要导入的机器

导入：

- 运行 ubuntu 容器，挂载容器的 volume，并且挂载宿主机备份文件所在目录到容器里
- 运行 tar 命令解压备份文件到指定目录

### 备份 MongoDB 数据演示

- 运行一个 mongodb，创建一个名叫`mongo-data`的 volume 指向容器的 /data 目录
  `docker run -p 27018:27017 --name mongo -v mongo-data:/data -d mongo:4.4`
- 运行一个 Ubuntu 的容器，挂载`mongo`容器的所有 volume，映射宿主机的 backup 目录到容器里面的 /backup 目录，然后运行 tar 命令把数据压缩打包
  `docker run --rm --volumes-from mongo -v d:/backup:/backup ubuntu tar cvf /backup/backup.tar /data/`

最后你就可以拿着这个 backup.tar 文件去其他地方导入了。

### 恢复 Volume 数据演示

- 运行一个 ubuntu 容器，挂载 mongo 容器的所有 volumes，然后读取 /backup 目录中的备份文件，解压到 /data/ 目录
  `docker run --rm --volumes-from mongo -v d:/backup:/backup ubuntu bash -c "cd /data/ && tar xvf /backup/backup.tar --strip 1"`

> 注意，volumes-from 指定的是容器名字
> strip 1 表示解压时去掉前面1层目录，因为压缩时包含了绝对路径

# 8.Typora 图片上传

1. ```json
   // smms
   {
     "picBed": {
       "current": "smms-user",
       "uploader": "smms-user",
       "smms-user": {
         "Authorization": "0OKZ3jSmfYW8akn5pvjkuxhekJJpPmYk"
       },
       "transformer": "path"
     },
     "picgoPlugins": {
       "picgo-plugin-smms-user": true
     }
   }
   ```
   
2. ```json
    / github
    {
    "picBed": {
   "current": "github",
   "github": {
     "repo": "Bayyys/PicX",
     "branch": "main",
     "token": "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",
     "path": "img/",
     "customUrl": "https://github.com/Bayyys/PicX"
   },
   "uploader": "github",
   "transformer": "path"
    },
    "picgoPlugins": {
   "picgo-plugin-gitee-uploader": true,
   "picgo-plugin-smms-user": true
    }
    }
```

# 9.LaTeX

前言
--

若想学习Markdown，请参见我的其他博客：[_Markdown详细教程+技巧总结_](https://blog.csdn.net/NSJim/article/details/89697630) 。 
若想学习LaTeX，请参见我的其他博客：[_LaTeX详细教程+技巧总结_](https://blog.csdn.net/NSJim/article/details/109066847) 。

若使用LaTeX编译器编写LaTeX数学公式，需要在导言区引用数学公式的宏包，代码为`\usepackage{amsmath}`；若要修改公式的字体，还需要引用宏包`\usepackage{amsfonts}`。

若使用Markdown编写LaTeX数学公式，CSDN支持LaTeX数学公式，但有些本地编辑器可能不支持LaTeX数学公式，Typroa可以更改设置支持，VS Code可以通过安装扩展的方式支持。

本篇博客内容包含前言，注意事项，插入公式，注释，编号，[转义](https://so.csdn.net/so/search?q=%E8%BD%AC%E4%B9%89&spm=1001.2101.3001.7020)字符，换行与对齐，字体，空格，上下标，括号，大括号和行标，分式，开方，对数，省略号，最值，方程组和分段函数，累加和累乘，矢量，积分，极限，导数与偏导，矩阵，表格，希腊字母，运算符，黑板粗体（空心字母），戴帽符号，特殊符号，等等。

1.  官方文档（英文）： 
    传送门：[_官方文档_](http://www.ctex.org/documents/packages/math/index.htm) 
    网址：`http://www.ctex.org/documents/packages/math/index.htm`
2.  中文文档： 
    传送门：[_中文教程_](https://www.latexlive.com/help) 
    网址：`https://www.latexlive.com/help`
3.  技巧：使用[_在线LaTeX公式编辑器_](https://www.latexlive.com/)，来生成LaTeX公式代码，然后复制到LaTeX编辑器（或Markdown编辑器）中，并在两边加上`$`或`$$`即可。 
    在线LaTeX公式编辑器网址：`https://www.latexlive.com/`
4.  插入公式  
    左对齐公式（行中公式）：`$数学公式$` 
    居中公式（独立公式）：`$$数学公式$$` 
    注意：使用`$`行中公式时，`数学公式`与`$`连接处不要有空格，否则公式不会显示；使用`$$`居中公式时，`数学公式`与`$$`连接处可以有空格。即`$ 数学公式 $` 不显示公式。
5.  注释：`%`为单行注释。
6.  细节请参照下文。

注意事项
----

1.  使用`$`，即行中公式时，`数学公式`与`$`连接处不要有空格，否则公式不会显示。即`$ 数学公式 $` 不显示公式。
2.  使用`$$`，即居中公式时，`数学公式`与`$$`连接处可以有空格。
3.  使用`$$`时，上方要空一行。
4.  `=`不要单独打一行，否则可能会出错。
5.  `+ - * / = ( ) | , . '`等符号直接在`$`或`$$`之间输入即可识别。

插入公式
----

左对齐公式（行中公式）：`$数学公式$` 
居中公式（独立公式）：`$$数学公式$$`

**注意：** 注意事项请参照目录章节中的**注意事项**子章节。

左对齐例子：`$x+y=z$`  

$$
x + y = z
$$
居中对齐例子：`$$x+y=z$$`  
$$
x + y = z
$$


注释
--

`%`为单行注释。

例子：

    $$
    %第一个极限
    \lim_{n \to +\infty} \frac{1}{n(n+1)}
    \quad %空一格
    and %英文单词and
    \quad %空一格
    %第2个极限
    \lim_{x\leftarrow{example} \infty} \frac{1}{n(n+1)}
    $$

显示：  
$$
\lim_{n \to +\infty} \frac{1}{n(n+1)} \quad  and \quad \lim_{x\leftarrow{example} \infty} \frac{1}{n(n+1)}
$$


编号
--

### Markdown编辑器

在公式末尾使用`\tag{编号}`来实现公式手动编号，大括号内的内容可以自定义。

例子：

    $$
    x+y=z
    \tag{1}
    $$

$$
x+y=z
\tag{1}
$$

### LaTeX编辑器

包含`自动编号`和`手动编号`两种方式。 
详情请参见我的另一篇博客[LaTeX详细教程](https://blog.csdn.net/NSJim/article/details/109066847)中的`公式编号`章节。 
此处简单介绍使用方法。

**自动编号** 
使用`\begin{equation}`和`\end{equation}`进行公式输入，要同时使用，且编号不能够修改。

例子：

    \begin{equation}
    a^2+b^2=c^2
    \end{equation}

显示： 
![在这里插入图片描述](https://img-blog.csdnimg.cn/20201025210116600.png)

**手动编号** 
在公式末尾使用`\tag{编号}`来实现公式手动编号，大括号内的内容可以自定义。需要使用`\usepackage{amsmath}`宏包，不能写在`$`或`$$`中，会报错。

例子：

    \begin{equation}
    a^2+b^2=c^2
    \tag{2}
    \end{equation}

显示： 
![在这里插入图片描述](https://img-blog.csdnimg.cn/20201025211527968.png)

转义字符
----

在公式中输入`_`或`^`等符号时，会产生上下标功能，若想输入符号本身则需要转义字符`\`，写法为`\+字符`，示例如下：

例子：

    $$
    % \ 为转义字符
    home\_name=honor
    $$

显示： 
$$
% \ 为转义字符
home\_name=honor
$$

换行与对齐
-----

### 换行

使用`\\`进行换行，最后一行的`\\`可写可不写。

例子：

    $$
    f(x)=2x+1 \\
    =2+1 \\
    =3
    $$

显示：  
$$
f(x)=2x+1 \\
=2+1 \\
=3
$$

### 对齐

使用`\begin{aligned}`进行对齐，`&`表示对齐位置，一般都在`=`前面。

例子：

    \begin{aligned}
    f(x)&=2x+1 \\
    &=2+1 \\
    &=3
    \end{aligned}

显示：
$$
\begin{aligned}
f(x)&=2x+1 \\
&=2+1 \\
&=3
\end{aligned}
$$

## 字体

若要对公式的某一部分字符进行字体转换，可以用 `\字体{需转换的字符}` 命令，其中 `\字体` 部分可以参照下表选择合适的字体。一般情况下，公式默认为意大利体，直体为罗马体 `\rm`。一般里面一层大括号可省略。

注意：在LaTeX编辑器中，修改公式字体时，需要引入宏包`\usepackage{amsmath}`和`\usepackage{amsfonts}`，且在公式中输入。

![image-20221019173747300](https://s2.loli.net/2022/10/19/PsO48aACQcSdU7b.png)

例子： 
`$$A+\mathbb{BC}+D$$`

显示：  
$$
A+\mathbb{BC}+D
$$

空格
--

`\quad`：空一格 
`\qquad`：空两格

例子： 
`$$x \quad y \qquad z$$`

显示：  
$$
x \quad y \qquad z
$$

上下标
---

`^`表示上标， `_` 表示下标。如果上下标的内容多于一个字符，需要用 `{}`将这些内容括成一个整体。上下标可以嵌套，也可以同时使用。

例子： 
`$$x^{y^z_w}=(1+{\rm e}^x)^{-2xy^w}$$`

显示：  
$$
x^{y^z_w}=(1+{\rm e}^x)^{-2xy^w}
$$
上下标同时使用例子： 
`$$f(x) = x_1^2 + {x}_{2}^{2}$$`

显示：  
$$
f(x) = x_1^2 + {x}_{2}^{2}
$$

括号
--

`()、[]、|`表示符号本身，使用 `\{\}` 来表示 {}。当要显示大号的括号或分隔符时，要用 `\left` 和 `\right` 命令，如`$\left(表达式\right)$`，大号的括号详见下一节）。

一些特殊的括号：

![image-20221019173912975](https://s2.loli.net/2022/10/19/qcnofwHLbDiNk4G.png)

例子： 
`$$f(x,y,z) = 3y^2z \left( 3+\frac{7x+5}{1+y^2} \right)$$`

显示：  
$$
f(x,y,z) = 3y^2z \left( 3+\frac{7x+5}{1+y^2} \right)
$$

大括号
---

**方法1** 
使用 `\left`和 `\right`来创建自动匹配高度的括号，包含 (圆括号)、\[方括号\]、|绝对值|。

例子：

    $$
    f\left(
       \left[
         \frac{
           1+\left\{x,y\right\}
         }{
           \left(
              \frac{x}{y}+\frac{y}{x}
           \right)
           \left(u+1\right)
         }+a
       \right]^{3/2}
    \right)
    $$

显示：  
$$
f\left(
   \left[
     \frac{
       1+\left\{x,y\right\}
     }{
       \left(
          \frac{x}{y}+\frac{y}{x}
       \right)
       \left(u+1\right)
     }+a
   \right]^{3/2}
\right)
$$


有时候要用`\left.`或`\right.`进行匹配而不显示本身。

例子： 
`$$\left. \frac{ {\rm d}u}{ {\rm d}x} \right| _{x=0}$$`

显示：  
$$
\left. \frac{ {\rm d}u}{ {\rm d}x} \right| _{x=0}
$$
**方法2** 
使用`\big`和`\bigg`来创建逐级变大的括号，包含 (圆括号)、\[方括号\]、|绝对值|。

例子：

    $$\bigg( \big( ( ) \big) \bigg)$$
    $$\bigg[ \big[ [ ] \big] \bigg]$$
    $$\bigg| \big| | | \big| \bigg|$$

显示：  
$$
\bigg( \big( ( ) \big) \bigg)\\
\bigg[ \big[ [ ] \big] \bigg]\\
\bigg| \big| | | \big| \bigg|
$$

分式
--

通常使用 `\frac {分子} {分母}` 命令产生一个分式，分式可嵌套。 
便捷情况可直接输入 `\frac ab`来快速生成一个 a b \\frac ab ba。 
如果分式很复杂，亦可使用 `分子 \over 分母` 命令，此时分式仅有一层。

例子： 
`$$\frac{a-1}{b-1} \quad and \quad {a+1\over b+1}$$`

显示：  
$$
\frac{a-1}{b-1} \quad and \quad {a+1\over b+1}
$$

根式
--

`\sqrt [根指数] {被开方数}`

注意：缺省根指数时为2

例子： 
`$$\sqrt{2} \quad and \quad \sqrt[n]{x+y}$$`

显示：  
$$
\sqrt{2} \quad and \quad \sqrt[n]{x+y}
$$

对数
--

`\log_{对数底数}{表达式}`

表达式的大括号可省略

显示：  
$$
log_{x+y}(z+1)
$$

省略号
---

数学公式中常见的省略号有两种，`\ldots` 表示与文本底线对齐的横向省略号 … \\ldots …，`\cdots` 表示与文本中线对齐的横向省略号 ⋯ \\cdots ⋯，`\vdots`表示纵向省略号 ⋮ \\vdots ⋮，`\ddots`表示斜向省略号 ⋱ \\ddots ⋱。

例子： 
`$$f(x_1,x_2,\underbrace{\ldots}_{\rm ldots} ,x_n) = x_1^2 + x_2^2 + \underbrace{\cdots}_{\rm cdots} + x_n^2$$`

显示：  
$$
f(x_1,x_2,\underbrace{\ldots}_{\rm ldots} ,x_n) = x_1^2 + x_2^2 + \underbrace{\cdots}_{\rm cdots} + x_n^2
$$

最值
--

`\max_{下标表达式}{最值表达式}`表示最大值，`\min_{下标表达式}{最值表达式}`表达最小值。 
例子： 
`$$||x||_\infty=\max_{1\leq i\leq n}{|x_i|}$$`

显示：  
$$
||x||_\infty=\max_{1\leq i\leq n}{|x_i|}
$$

[方程组](https://so.csdn.net/so/search?q=%E6%96%B9%E7%A8%8B%E7%BB%84&spm=1001.2101.3001.7020)和分段函数
-----------------------------------------------------------------------------------------------

### 方程组

方程组有2种方式，分别是`\begin{aligned}`和`\begin{cases}`方式，`&`表示对齐位置，推荐使用`\begin{cases}`方式，使用方法如下：

`\begin{aligned}`方式：可以使方程组根据`=`对齐

    $$
    \left\{
    \begin{aligned}
    a+b&=2 \\
    a-b&=4 \\
    \end{aligned}
    \right.
    $$

显示：  
$$
\left\{
\begin{aligned}
a+b&=2 \\
a-b&=4 \\
\end{aligned}
\right.
$$
`\begin{cases}`方式（推荐）：简便，但无法根据`=`对齐

    $$
    \begin{cases}
    a+b=2 \\
    a-b=4 \\
    \end{cases}
    $$

显示：  
$$
\begin{cases}
a+b=2 \\
a-b=4 \\
\end{cases}
$$

### 分段函数

分段函数可以通过`\begin{cases}`方式实现，不同的是方程式和条件之间要用`&`符号隔开。

例子：

    $$
    y =
    \begin{cases}
    \sin(x)       & x<0 \\
    x^2 + 2x +4   & 0 \leq x < 1 \\
    x^3           & x \geq 1 \\
    \end{cases}
    $$

显示：  
$$
y =
\begin{cases}
\sin(x)       & x<0 \\
x^2 + 2x +4   & 0 \leq x < 1 \\
x^3           & x \geq 1 \\
\end{cases}
$$

累加和累乘
-----

使用 `\sum_{下标表达式}^{上标表达式}{累加表达式}`来输入一个累加。 
与之类似，使用 `\prod \bigcup \bigcap`来分别输入累乘、并集和交集。 
此类符号在行内显示时上下标表达式将会移至右上角和右下角。

例子： 
`$$\sum_{i=1}^n \frac{1}{i^2} \quad and \quad \prod_{i=1}^n \frac{1}{i^2} \quad and \quad \bigcup_{i=1}^{2} R$$`

显示：  
$$
\sum_{i=1}^n \frac{1}{i^2} \quad and \quad \prod_{i=1}^n \frac{1}{i^2} \quad and \quad \bigcup_{i=1}^{2} R
$$

矢量
--

使用 `\vec{矢量}`来自动产生一个矢量。 
也可以使用 `\overrightarrow`等命令自定义字母上方的符号。

例子： 
`$$\vec{a} \cdot \vec{b}=0\$$`

显示：  
$$
\vec{a} \cdot \vec{b}=0\
$$
例子： 
`$$\overleftarrow{xy} \quad and \quad \overleftrightarrow{xy} \quad and \quad \overrightarrow{xy}$$`

显示：  
$$
\overleftarrow{xy} \quad and \quad \overleftrightarrow{xy} \quad and \quad \overrightarrow{xy}
$$

极限
--

`\lim_{变量 \to 表达式} 表达式` 
如有需求，可以更改 \\to 符号至任意符号。

例子： 
`$$\lim_{n \to +\infty} \frac{1}{n(n+1)} \quad and \quad \lim_{x\leftarrow{example} \infty} \frac{1}{n(n+1)}$$`

显示： 
$$
\lim_{n \to +\infty} \frac{1}{n(n+1)} \quad and \quad \lim_{x\leftarrow{example} \infty} \frac{1}{n(n+1)}
$$

导数
--

**导数** 
`${\rm d}x$`或`${\text d}x$`或`$\text{d}x$`
$$
{\rm d}x或{\text d}x或\text{d}x
$$
**偏导**  
`$\frac{\partial y}{\partial x}$`
$$
\frac{\partial y}{\partial x}
$$
**梯度**  
`$\nabla f(x)$`
$$
\nabla f(x)
$$

积分
--

`\int_积分下限^积分上限 {被积表达式}`

例子：  
`$$\int_0^1 {x^2} \,{\rm d}x$$`

显示：  
∫ 0 1 x 2   d x \\int_0^1 {x^2} \\,{\\rm d}x ∫01x2dx

矩阵
--

### 基础矩阵

使用`\begin{matrix}…\end{matrix}` 这样的形式来表示矩阵，在`\begin` 与`\end` 之间加入矩阵中的元素即可。矩阵的行之间使用`\\` 分隔，`\\`表示换行，列之间使用`&` 分隔，`&`表示对齐位置。

例子：

    $$
    \begin{matrix}
    1 & x & x^2 \\
    1 & y & y^2 \\
    1 & z & z^2 \\
    \end{matrix}
    $$

显示：  
$$
\begin{matrix}
1 & x & x^2 \\
1 & y & y^2 \\
1 & z & z^2 \\
\end{matrix}
$$

### 带括号的矩阵

**使用`\left` 与`\right` 表示括号**

如果要对矩阵加括号，可以像上文中提到的一样，使用`\left` 与`\right` 配合表示括号符号。

例子：

    $$
    \left[
    \begin{matrix}
    1 & x & x^2 \\
    1 & y & y^2 \\
    1 & z & z^2 \\
    \end{matrix}
    \right]
    $$

显示： 
$$
\left[
\begin{matrix}
1 & x & x^2 \\
1 & y & y^2 \\
1 & z & z^2 \\
\end{matrix}
\right]
$$
**使用特殊的`matrix`**

带括号的矩阵也可以使用特殊的`matrix` 。即替换`\begin{matrix}…\end{matrix}` 中`matrix` 为`pmatrix` ，`bmatrix` ，`Bmatrix` ，`vmatrix` , `Vmatrix` 。

1.  pmatrix：`$\begin{pmatrix}1 & 2 \\ 3 & 4\\ \end{pmatrix}$`  
    $$
    \begin{pmatrix}1 & 2 \\ 3 & 4\\ \end{pmatrix}
    $$
    
2.  bmatrix：`$\begin{bmatrix}1 & 2 \\ 3 & 4\\ \end{bmatrix}$`  
    $$
    \begin{bmatrix}1 & 2 \\ 3 & 4\\ \end{bmatrix}
    $$
    
3.  Bmatrix：`$\begin{Bmatrix}1 & 2 \\ 3 & 4\\ \end{Bmatrix}$`  
    $$
    \begin{Bmatrix}1 & 2 \\ 3 & 4\\ \end{Bmatrix}
    $$
    
4.  vmatrix：`$\begin{vmatrix}1 & 2 \\ 3 & 4\\ \end{vmatrix}$`  
    $$
    \begin{vmatrix}1 & 2 \\ 3 & 4\\ \end{vmatrix}
    $$
    
5.  Vmatrix：`$\begin{Vmatrix}1 & 2 \\ 3 & 4\\ \end{Vmatrix}$`  
    $$
    \begin{Vmatrix}1 & 2 \\ 3 & 4\\ \end{Vmatrix}
    $$

### 行列式

方法已经在上一节**带括号的矩阵**中有所介绍，此处只写一个例子。

例子1：使用`\left` 与`\right` 表示括号

    $$
    \left|
    \begin{matrix}
    1 & x & x^2 \\
    1 & y & y^2 \\
    1 & z & z^2 \\
    \end{matrix}
    \right|
    $$

显示：  
$$
\left|
\begin{matrix}
1 & x & x^2 \\
1 & y & y^2 \\
1 & z & z^2 \\
\end{matrix}
\right|
$$
例子2：使用特殊的`matrix`

    $$
    \begin{vmatrix}
    1 & x & x^2 \\
    1 & y & y^2 \\
    1 & z & z^2 \\
    \end{vmatrix}
    $$

显示：  
$$
\begin{vmatrix}
1 & x & x^2 \\
1 & y & y^2 \\
1 & z & z^2 \\
\end{vmatrix}
$$

### 元素省略的矩阵

可以使用`\cdots` ： ⋯ \\cdots ⋯，`\ddots`： ⋱ \\ddots ⋱ ，`\vdots`： ⋮ \\vdots ⋮ ，来省略矩阵中的元素。

例子：

    $$
    \begin{pmatrix}
    1&a_1&a_1^2&\cdots&a_1^n\\
    1&a_2&a_2^2&\cdots&a_2^n\\
    \vdots&\vdots&\vdots&\ddots&\vdots\\
    1&a_m&a_m^2&\cdots&a_m^n\\
    \end{pmatrix}
    $$

显示：  
$$
\begin{pmatrix}
1&a_1&a_1^2&\cdots&a_1^n\\
1&a_2&a_2^2&\cdots&a_2^n\\
\vdots&\vdots&\vdots&\ddots&\vdots\\
1&a_m&a_m^2&\cdots&a_m^n\\
\end{pmatrix}
$$

### 增广矩阵

增广矩阵需要使用前面的表格中使用到的`\begin{array} ... \end{array}` 来实现。

例子：

    $$
    \left[  \begin{array}  {c c | c} %这里的c表示数组中元素对其方式：c居中、r右对齐、l左对齐，竖线表示2、3列间插入竖线
    1 & 2 & 3 \\
    \hline %插入横线，如果去掉\hline就是增广矩阵
    4 & 5 & 6
    \end{array}  \right]
    $$

显示：  
$$
\left[  \begin{array}  {c c | c} %这里的c表示数组中元素对其方式：c居中、r右对齐、l左对齐，竖线表示2、3列间插入竖线
1 & 2 & 3 \\
\hline %插入横线，如果去掉\hline就是增广矩阵
4 & 5 & 6
\end{array}  \right]
$$


表格
--

使用`\begin{array}{列样式}…\end{array}` 这样的形式来创建表格，列样式可以是`clr` 表示居中，左，右对齐，还可以使用`|` 表示一条竖线。表格中各行使用`\\` 分隔，各列使用`&` 分隔。使用`\hline` 在本行前加入一条直线。

例子：

    $$
    \begin{array}{c|lcr}
    n & \text{Left} & \text{Center} & \text{Right} \\
    \hline
    1 & 0.24 & 1 & 125 \\
    2 & -1 & 189 & -8 \\
    3 & -20 & 2000 & 1+10i \\
    \end{array}
    $$

显示：  
$$
\begin{array}{c|lcr}
n & \text{Left} & \text{Center} & \text{Right} \\
\hline
1 & 0.24 & 1 & 125 \\
2 & -1 & 189 & -8 \\
3 & -20 & 2000 & 1+10i \\
\end{array}
$$

希腊字母
----

输入 `\小写希腊字母英文全称`和`\首字母大写希腊字母英文全称`来分别输入小写和大写希腊字母。  
对于大写希腊字母与现有字母相同的，直接输入大写字母即可。

![image-20221019175103747](https://s2.loli.net/2022/10/19/fn3roL2ZxFTRsNM.png)

黑板粗体（空心字母）
----------

空心字母属于一种字体，官方名称为黑板粗体，仅对大写字母起作用。若使用LaTeX编辑器，使用前需要在导言区引入宏包`\usepackage{amsfonts}`，并在公式中修改字体。

使用`$\mathbb{字母}$`即可使用空心字母，下方示例仅展示3个字母（M，R，L），其它字母同理。

![image-20221019175120928](https://s2.loli.net/2022/10/19/wq81dWLfE2TieB9.png)

## 运算符

对于加减除，对应键盘上便可打出来，但是对于乘法，键盘上没有这个符号，所以我们应该输入 `\times` 来显示一个 × \\times × 号。

普通字符在数学公式中含义一样，除了 `# $ % & ~ _ { }` 若要在数学环境中表示这些符号`# $ % & _ { }`，需要分别表示为`\# \$ \% \& \_ \{ \}`，即在个字符前加上转义字符 `\` 。

### 关系运算符

<img src="https://s2.loli.net/2022/10/19/B9Nycqf8AoRvrsY.png" alt="image-20221019175158528"  />

其中，部分公式添加前缀`big`可以放大，删掉`big`前缀即为正常大小。  
例如，`$\odot$`为 ⊙ \\odot ⊙，`$\bigodot$`为 ⨀ \\bigodot ⨀。

### 三角运算符

![image-20221019175308604](https://s2.loli.net/2022/10/19/GDfVOQMBJx2n9Lo.png)

### 箭头运算符

![image-20221019175244206](https://s2.loli.net/2022/10/19/fD2cQzCem5JO68k.png)

### 离散数学符号

![image-20221019175323693](https://s2.loli.net/2022/10/19/wzTRkHi6CaIq5LU.png)

戴帽符号（各种帽子）
----------

![image-20221019175339890](https://s2.loli.net/2022/10/19/cNigruVP7XsRKYk.png)

特殊符号
----------------------------------------------------------------------------------------------------

上述内容仅包含一些常用公式及符号，一些不常用的符号可以查找官方文档获取，此处提供一个比较全的LaTeX符号博客：[链接](https://www.oscaner.com/skill/others/mathjax-symbol.html)，供大家参考。

下方展示一些不常用特殊符号：

无穷大符号：`$\infty$`  
$$
\infty
$$
领结符号：`$\bowtie$`  
$$
\bowtie
$$
帽：`$\hat x$`  
$$
\hat x
$$
范数：`$\ell_p$`  
$$
\ell_p
$$
箭头备注：`$\xrightarrow{f}$`  
$$
\xrightarrow{f}
$$
上备注：`$\overset{def}{=}$`  
$$
\overset{def}{=}
$$
下备注：`$\underset{x\in S\subseteq X}{max}$`  
$$
\underset{x\in S\subseteq X}{max}
$$
And so on.

# 10. Emacs

## 1.Emacs简介

- GNU Emacs
- 于1984年，Richard Stallman发起并维护
- GNU顶级项目
- 跨平台，内核解释器C写成，通过ELisp语言进行拓展

### 2.基本操作

- C-n，下一行（速记：Nextline）
- C-p，前一行（速记：Previous line）
- C-f，向前移动一个字符（速记：Forward）
- C-b，向后退一个字符（速记：Backforward）
- C-k，从光标位置到末尾删掉（速记：Kill）
- C-a，回到行首（速记：a是字母表的开始）
- C-e，去往行尾（速记：End of line）
- M - <，回到编辑区域最开始位置（速记：<）
- M - >，去往编辑区域最后的位置（速记：>）
- C-v，向下翻一屏
- M-v，向上翻一屏

## 3.自带文档

- `C-h + t` 帮助文档
- `C-h + k` 快捷键帮助文档
- `C-h + f` 查看函数定义

## 4.外观变化

图形化配置: `M-x : customize`

- 菜单栏 `menu-bar-mode`
- 工具栏 `tool-bar-mode`
- 滚动条 `scroll-bar-mode`

# 11. Scoop

## 1. 安装和卸载

```shell
#powershell允许安装脚本权限
set-executionpolicy remotesigned -scope currentuser
```

修改默认安装位置：

- 默认安装应用到C:\User\用户名\scoop

  默认全局安装的在C:\ProgramData\scoop

```shell
#修改默认安装位置，打开powershell，设置变量，安装即可
$env:SCOOP='D:\Scoop\scoop'
[environment]::setEnvironmentVariable('SCOOP',$env:SCOOP,'User')

#如果需要修改全局安装变量，管理员打开powershelll，设置变量，上面的变量也要一起设置一下，然后安装
$env:SCOOP_GLOBAL='D:\Scoop\scoop_global'
[Environment]::SetEnvironmentVariable('SCOOP_GLOBAL', $env:SCOOP_GLOBAL, 'Machine')

#安装
irm get.scoop.sh -outfile 'install.ps1'
.\install.ps1 -RunAsAdmin
#或者
iex "& {$(irm get.scoop.sh)} -RunAsAdmin"
```

卸载：

```shell
scoop uninstall scoop
```

## 2. 设置/取消代理

```shell
#设置http代理 -> 无需设置
scoop config proxy 127.0.0.1:8080
#删除代理
scoop config rm proxy
```

## 3. 软件库bucket

```shell
#查看已知库
scoop bucket known
#查看已经安装的库
scoop bucket list

#添加软件库
scoop bucket add <bucketname>
#比如：
scoop bucket add extras
#添加第三方库
scoop bucket add <bucketname> <bucket_url>

#删除安装的库
scoop bucket rm <bucketname>
```

## 4. 简单使用

```shell
#查看帮助
scoop help

#搜索软件
scoop search xxx
#安装软件
scoop install xxx
#全局安装，需要管理员权限
scoop install -g xxx
#卸载软件，不推荐使用第三方软件卸载，如果需要卸载也最好使用scoop。
scoop uninstall xxx
#卸载全局安装的软件
scoop uninstall -g xxx
#查看已安装的软件
scoop list
#更新
scoop update *
#查看软件信息
scoop info xxx

#清理旧版安装包：
scoop cleanup *
#清理下载缓存
scoop cache rm *

#其他命令
alias       Manage scoop aliases # 管理指令的替身
cache       Show or clear the download cache # 查看与管理缓存
checkup     Check for potential problems # 做个体检
config      Get or set configuration values # 配置Scoop
create      Create a custom app manifest # 创建自定义软件包
depends     List dependencies for an app # 查看依赖
export      Exports (an importable) list of installed apps # 导出软件包列表
hold        Hold an app to disable updates # 禁止软件包更新
home        Opens the app homepage # 打开软件包主页
prefix      Returns the path to the specified app # 查看软件包路径
reset       Reset an app to resolve conflicts # 恢复软件包版本
status      Show status and check for new app versions # 查看软件包更新状态
unhold      Unhold an app to enable updates # 启动软件包更新
virustotal  Look for app hash on virustotal.com # 查看哈希值
which       Locate a shim/executable (similar to 'which' on Linux) # 查看可执行程序路径
```

# 11.vscode

## 1. launch.json

```json
{
    // 使用 IntelliSense 了解相关属性。 
    // 悬停以查看现有属性的描述。
    // 欲了解更多信息，请访问: https://go.microsoft.com/fwlink/?linkid=830387
    "version": "0.2.0",	// 版本号
    "configurations": [
        {
            "name": "(gdb) Launch", 	//  配置名称，将会在启动配置的下拉菜单中显示
            "type": "cppdbg",	//  调试器类型, cppdbg for C/C++, Node debugger for node, php for PHP, go for GO           
            "request": "launch",	//  请求配置类型，可以为launch（启动）或attach（附加）  
            "program": "${workspaceFolder}/${fileBasenameNoExtension}.out",	// 可执行文件的路径
            "args": [],	//  调试参数
            "stopAtEntry": false,	// 设为true时程序将暂停在程序入口处，一般设置为false  
            "cwd": "${workspaceFolder}",	//  调试程序时的工作目录，一般为${workspaceFolder}即代码所在目录
            "environment": [],	//  当前项目环境变量
            "externalConsole": true,	// 调试时是否显示控制台窗口，设置为true显示控制台
            "MIMode": "gdb",	//  调试器模式/类型
            "miDebuggerPath": "D:/Coding/mingw64/bin/gdb.exe",	//  调试器的位置
            "preLaunchTask":"build",	//  调试前编译任务名称， 该值需要与tasks.json中的label相同，否则调试时会提示找不到
            "setupCommands": [
                {
                    "description": "为 gdb 启用整齐打印",
                    "text": "-enable-pretty-printing",
                    "ignoreFailures": true
                },
                {
                    "description": "将反汇编风格设置为 Intel",
                    "text": "-gdb-set disassembly-flavor intel",
                    "ignoreFailures": true
                }
            ]
        }
    ]
}
```



## 2. tasks.json

```json
{
    // See https://go.microsoft.com/fwlink/?LinkId=733558
    // for the documentation about the tasks.json format
    "tasks":[  // 可以有多个任务
        {
            "type": "shell",	// 编译任务的类型，通常为shell/process类型
            "label": "build",	// 编译任务名, 需要与launch.json中的preLaunchTask保持一致，否则调试时会提示找不到；
            "command": "D:\\Coding\\mingw64\\bin\\gcc.exe",	// 编译命令	-> "cd build && cmake ../ && make",	shell 编译命令，做并运算，即前一命令执行失败，则后一命令也不执行
            "args":[
                "-g",	// 该参数使编译器在编译的时候产生调试信息
                "${workspaceFolder}/${fileBasename}",	// 被编译文件，通常为.cpp/.c/.cc文件等
                "-Wall",	// 开启额外警告
                "-I",	// include path指令
                "/usr/include",                          
                "-L",	// lib路径
                "/usr/lib/x86_64-linux-gnu",             
                "-l",	// 链接库文件1
                "opencv_core",                           
                "-l",	// 链接库文件2
                "opencv_highgui",                        
                "-o",	// 生成指定名称的可执行文件, 默认为a.exe(a.out)
                "${workspaceFolder}/${fileBasenameNoExtension}.out"  　　　　　　　　　　/* -g hello.cpp -I/usr/include -L/usr/lib/x86_64-linux-gnu -lopencv_core -o hello.out */
            ],
            "options": {	// 其他命令选项
                "cwd": "${fileDirname}"	// 已执行程序或脚本的当前工作目录。如果省略，则使用代码的当前工作区根
            },
            "problemMatcher": [	// 已执行程序或脚本的当前工作目录。如果省略，则使用代码的当前工作区根
                "$gcc"	// 设置捕获错误的工具
            ],
            "group": {
                "kind": "build",	// 任务的执行组。 build: 将任务标记为可通过 "运行生成任务" 命令访问的生成任务。
                "isDefault": true	// 定义此任务是组中的默认任务，还是与应触发此任务的文件匹配的 glob。
            }
        },
        {
            "label": "cmakebuild",      
            "type": "shell", 
            "command": "cd build && cmake ../ && make",	// shell 编译命令，做并运算，即前一命令执行失败，则后一命令也不执行
            "args": []
        }
    ]
    "version": "2.0.0",  

}
```

## 3. 预定义变量解释

```json
${workspaceFolder} : 表示当前workspace文件夹路径，如C:\Users\admin\Desktop\test
${workspaceRootFolderName} : 表示workspace的文件夹名，如test
${file} : 文件自身的绝对路径，如C:\Users\admin\Desktop\test\.vscode\launch.json
${relativeFile} : 文件在workspace中的路径，如.vscode\launch.json
${fileBasenameNoExtension} : 当前文件的文件名，不带后缀，如hello/launch
${fileBasename} : 当前文件的文件名，如 hello.cpp/launch.json等
${fileDirname} : 文件所在的文件夹路径，也即C:\Users\admin\Desktop\test\.vscode
${fileExtname} : 当前文件的后缀，也即.json
${lineNumber} : 当前文件光标所在的行号
${env:PATH} : 系统中的环境变量
```

# 12. Linux

## 1. 基本命令

### top(持续监听进程运行状态)

- -d 秒数：指定 top 命令每隔几秒更新。默认是 3 秒；
- -b：使用批处理模式输出。一般和"-n"选项合用，用于把 top 命令重定向到文件中；
- -n 次数：指定 top 命令执行的次数。一般和"-"选项合用；
- -p 进程PID：仅查看指定 ID 的进程；
- -s：使 top 命令在安全模式中运行，避免在交互模式中出现错误；
- -u 用户名：只监听某个用户的进程；


在 top 命令的显示窗口中，还可以使用如下按键，进行一下交互操作：

- ? 或 h：显示交互模式的帮助；
- P：按照 CPU 的使用率排序，默认就是此选项；
- M：按照内存的使用率排序；
- N：按照 PID 排序；
- T：按照 CPU 的累积运算时间排序，也就是按照 TIME+ 项排序；
- k：按照 PID 给予某个进程一个信号。一般用于中止某个进程，信号 9 是强制中止的信号；
- r：按照 PID 给某个进程重设优先级（Nice）值；
- q：退出 top 命令；

### jobs(后台进程)

| 选项           | 含义                                   |
| -------------- | -------------------------------------- |
| -l（L 的小写） | 列出进程的 PID 号。                    |
| -n             | 只列出上次发出通知后改变了状态的进程。 |
| -p             | 只列出进程的 PID 号。                  |
| -r             | 只列出运行中的进程。                   |
| -s             | 只列出已停止的进程                     |

### dpkg --list(查看已安装软件)

```shell
# 查看已安装软件
dpkg --list

# 卸载软件
sudo apt remove --purge [name] #卸载软件同时删除配置文件
sudo apt remove [name]  #卸载该软件
```

### shell快捷的删除

`CTRL + H`  #相当于按了一次退格键，一次删除一个字母

`CTRL + U`  #一次删一行

`CTRL + W` #一次删一个单词，也可以这么理解，一次删一个空格的位置，比如:face book abcd edff，这种情况要按四次才能删完的工具

### 文档格式化

`gg` + `=` + `G`

## 2. vim内插件

#### ctrlp(vim 内文件树)

![image-20221121204804627](https://s2.loli.net/2022/11/21/tIhxL1OXejQGdZu.png)

- `ctrl + j/k` 进行上下选择
- ` ctrl + x` 在当前窗口水平分屏打开文件 
- `ctrl + v` 同上, 垂直分屏 
- `ctrl + t `在tab中打开
- `ctrl + r`在 **字符串模式** 和 **正则表达式模式** 之间切换

#### NERDTree(文件树)

![image-20221201182125369](https://s2.loli.net/2022/12/01/kH8f53Q1KTUzxhI.png)

- `?`: 快速帮助文档
- `o`: 打开一个目录或者打开文件，创建的是 buffer，也可以用来打开书签
- `go`: 打开一个文件，但是光标仍然留在 NERDTree，创建的是 buffer
- `t`: 打开一个文件，创建的是Tab，对书签同样生效
- `T`: 打开一个文件，但是光标仍然留在 NERDTree，创建的是 Tab，对书签同样生效
- `i`: 水平分割创建文件的窗口，创建的是 buffer
- `gi`: 水平分割创建文件的窗口，但是光标仍然留在 NERDTree
- `s`: 垂直分割创建文件的窗口，创建的是 buffer
- `gs`: 和 gi，go 类似
- `x`: 收起当前打开的目录
- `X`: 收起所有打开的目录
- `e`: 以文件管理的方式打开选中的目录
- `D`: 删除书签

#### auto-pairs(括号自动匹配)

#### NerdCommenter(注释)

- `\cc` 注释当前行和选中行
- `\cu` 取消注释
- `\c<space>` 如果被选区域有部分被注释，则对被选区域执行取消注释操作，其它情况执行反转注释操作
- ` \ci` 执行反转注释操作，选中区域注释部分取消注释，非注释部分添加注释
- ` \cA` 跳转到该行结尾添加注释，并进入编辑模式
- ` \cn `没有发现和\cc有区别
- ` \cm` 对被选区域用一对注释符进行注释，前面的注释对每一行都会添加注释
- `\cs` 添加性感的注释，代码开头介绍部分通常使用该注释
- `\cy` 添加注释，并复制被添加注释的部分
- `\c$` 注释当前光标到改行结尾的内容
- `\ca `转换注释的方式，比如： /\*\*/和//
- `\cl`  `\cb` 左对齐和左右对其，左右对其主要针对/**/

#### fd(文件查找)

#### shellcheck(查错)

![shellcheck](https://s2.loli.net/2022/11/18/bWGyigK2Mm8aeSc.png)

#### tldr (Too long; Didn't read)

![image-20221120191539960](https://s2.loli.net/2022/11/20/NuKy618WfhsYAUj.png)

#### rg(riggrep)(在当前文件下文件内查找)

![image-20221120193545743](https://s2.loli.net/2022/11/20/75dKjeGfFAt1YwN.png)

#### fzf(命令行的模糊搜索)

![image-20221120200210604](https://s2.loli.net/2022/11/20/lvd1MqCVTIUj438.png)

![image-20221120200217174](https://s2.loli.net/2022/11/20/oM3DWE5nYg9Gky1.png)

#### fish(History存储的command-line)

![image-20221120201126673](https://s2.loli.net/2022/11/20/3PG6VL4XSpqb1hz.png)

#### tree(or broot nnn)(文件树)

![image-20221120201107434](https://s2.loli.net/2022/11/20/u9JIPvXUfKjpdm3.png)



#### sed(脚本编写方式读文本)

```shell
#sed

cat file.sh | sed 's/REGEX/SUBSTITUTION/'
# 其中 REGEX 部分是我们需要使用的正则表达式，而 SUBSTITUTION 是用于替换匹配结果的文本。
```

![image-20221122222441207](https://s2.loli.net/2022/11/22/rAY4eyK8dtOUgkc.png)

#### less(逐页滚动读文本)

```shell
# less

less [filename]
```

![image-20221122222756073](https://s2.loli.net/2022/11/22/u5U1ImSTP4xd2Hj.png)

#### perl(文本处理工具[正则])

![image-20221123204439531](https://s2.loli.net/2022/11/23/GN2rCPIp8VkFfDg.png)

#### wc(文本统计工具)

![image-20221123210116651](https://s2.loli.net/2022/11/23/PKXk3jwEgvJfDQA.png)

#### awk(适合处理文本的编程语言)

![image-20221123211814842](https://s2.loli.net/2022/11/23/Iugqzd7Pb4hiaKC.png)

#### bc(计算器语言)

![image-20221123213912118](https://s2.loli.net/2022/11/23/UNDIPkxln9Tu4LC.png)

#### xargs(将标准输入作为参数)

#### kill[(终止进程)](https://blog.csdn.net/WJSZMD/article/details/89331751)

```shell
kill -STOP[-TERM/-QUIT/-INT] <PID>
# STOP 暂停进程
# INT (Ctrl+C) : 只对当前前台进程,和他的所在的进程组的每个进程都发送SIGINT信号,之后这些进程会执行信号处理程序再终止
# QUIT (Ctrl+\) : 
# TERM : 当前进程会收到信号,而其子进程不会收到.如果当前进程被kill(即收到SIGTERM),则其子进程的父进程将为init,即pid为1的进程(kill <PID>)
# KILL : 当前进程收到该信号,注意该信号时无法被捕获的,也就是说进程无法执行信号处理程序,会直接发送默认行为,也就是直接退出 (kill -9 <PID>)
# HUP : 终止进程(无法终止nohup进程)
```

> ```shell
> SIGHUP     终止进程     终端线路挂断
> SIGINT     终止进程     中断进程
> SIGQUIT   建立CORE文件终止进程，并且生成core文件
> SIGILL   建立CORE文件       非法指令
> SIGTRAP   建立CORE文件       跟踪自陷
> SIGBUS   建立CORE文件       总线错误
> SIGSEGV   建立CORE文件       段非法错误
> SIGFPE   建立CORE文件       浮点异常
> SIGIOT   建立CORE文件       执行I/O自陷
> SIGKILL   终止进程     杀死进程
> SIGPIPE   终止进程     向一个没有读进程的管道写数据
> SIGALARM   终止进程     计时器到时
> SIGTERM   终止进程     软件终止信号
> SIGSTOP   停止进程     非终端来的停止信号
> SIGTSTP   停止进程     终端来的停止信号
> SIGCONT   忽略信号     继续执行一个停止的进程
> SIGURG   忽略信号     I/O紧急信号
> SIGIO     忽略信号     描述符上可以进行I/O
> SIGCHLD   忽略信号     当子进程停止或退出时通知父进程
> SIGTTOU   停止进程     后台进程写终端
> SIGTTIN   停止进程     后台进程读终端
> SIGXGPU   终止进程     CPU时限超时
> SIGXFSZ   终止进程     文件长度过长
> SIGWINCH   忽略信号     窗口大小发生变化
> SIGPROF   终止进程     统计分布图用计时器到时
> SIGUSR1   终止进程     用户定义信号1
> SIGUSR2   终止进程     用户定义信号2
> SIGVTALRM 终止进程     虚拟计时器到时
> ```

##### pkill

> Mostly used for stopping processes.

```shell
# Kill all processes which match their full command instead of just the process name
pkill -f 'filename'
```

##### wait

> Wait for a process to complete before proceeding.

![image-20221127203916231](https://s2.loli.net/2022/11/27/Nz14KJksgQxqAWY.png)

#### tmux(终端多路复用)[^2]

![image-20221124221659078](https://s2.loli.net/2022/11/24/1qT2nSRvPBL74wM.png)

##### - sessions会话

- `tmux` 开始一个新的会话
- `tmux new -s NAME` 以指定名称开始一个新的会话
- `tmux ls` 列出当前所有会话
- 在 `tmux` 中输入 `<C-b> d` ，将当前会话分离
- `tmux a` 重新连接最后一个会话。您也可以通过 `-t` 来指定具体的会话

##### - windows窗口

- `<C-b> c` 创建一个新的窗口，使用 `<C-d>`关闭
- `<C-b> N` 跳转到第 *N* 个窗口，注意每个窗口都是有编号的
- `<C-b> p` 切换到前一个窗口
- `<C-b> n` 切换到下一个窗口
- `<C-b> ,` 重命名当前窗口
- `<C-b> w` 列出当前所有窗口

##### - panes面板

- `<C-b> "` 水平分割
- `<C-b> %` 垂直分割
- `<C-b> <方向>` 切换到指定方向的面板，<方向> 指的是键盘上的方向键
- `<C-b> z` 切换当前面板的缩放
- `<C-b> [` 开始往回卷动屏幕。您可以按下`<C-space>`来开始选择(上下左右)，`<Alt+w`复制选中的部分；`<C-b> }` 粘贴
- `<C-b> <空格>` 在不同的面板排布间切换
- `<C-b> <C-arrow>` 界面移动1行
- `<C-b> <Alt-arrow>` 界面移动5行
- `<C-b> x` 销毁面板
- `<C-b> t` 显示时钟
