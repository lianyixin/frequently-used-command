# frequently-used-command
frequently used command during my work in Linux environment. 

### Terminal
/usr/local/bin /usr/bin，usr不是用户名，是unix system的缩写，存放系统文件。local适合存放用户的文件。

查看系统：cat /etc/os-release

top命令：查看处理器和任务情况, nvtop查看完整信息。

nvidia-smi: 查看显存情况

安装创建virtualenv: pip install virtualenv; 新建环境：virtualenv envname 或者 virtualenv -p python3 myenv; 进入环境：source envname/bin/activate; 退出：deactivate

生成requirements文件： pip freeze > requirements.txt； 安装requirements文件：pip install -r requirements.txt

修改软件默认路径：vim ~/.bashrc

jupyter: jupyter notebook, 在网址输入：http://IP地址:8080/user/xxxxxx

下载单个文件： wget+路径（容易出现文件损坏的问题）

显示当前路径： pwd

在 Python 环境中增加搜索路径：
1. import sys；  sys.path.append('/home/wang/workspace')
2. vim ~/.bashrc； export PYTHONPATH=$PYTHONPATH:/home/wang/workspace； source ~/.bashrc # 或者 . ~/.bashrc 
3. 在 /usr/local/lib/python3.5/site-packages 下添加一个扩展名为 .pth 的配置文件（例如：extras.pth），内容为要添加的路径：/home/wang/workspace

退回原目录： cd - 返回上一级目录：cd ..

查看安装包情况：pip show 安装包； 查看所有安装包：pip list

解压tar.xz文件： tar xf 文件名 解压tar.gz文件：tar -zxvf xxx

centos系统内置： yum install xxx; yum remove xxx

查看系统python版本：python --version; python3 --version；

设置python版本默认指向python3： echo alias python=python3 >> ~/.bashrc；source ~/.bashrc （注意这个alias不能随意更改，否则虚拟环境的python路径也会受这个影响）

查询进程id号：ps aux | grep xxx；杀掉进程：kill -9 id号；

后台运行进程：nohup python xxx >> output.log 2>&1 &; jobs -l(查看当前终端的)；ps -aux|grep chat.js| grep -v grep | awk '{print $2}' （用awk提取进程id号）

显示所有隐藏文件： ls -a 

查看系统磁盘占用情况：df -h

更改文件权限：chmod -R a+rw xxx文件

Linux下载csv文件Windows打开中文乱码解决方案：iconv -f UTF-8 -t GBK 源文件 -o 现文件名； 上面的命令将utf-8格式转化为GBK格式，也就是windows默认打开csv文件的格式。

### windows快捷键
win+D: 最小化所有窗口

win+下：部分小化当前窗口

win+左：当前窗口占满左部分屏幕

alt+空格+N: 最小化当前窗口

win+L: 一键锁屏

alt+tab: 切换屏幕

### SSH
软件: mobaxterm, new session, 输入用户名密码

修改用户名密码: passwd

从本地上传文件到远程服务器，使用本地terminal：scp C:\Users\l00xxxxx\Desktop\NLU 用户名@ip地址:~/

在不同窗口切换：ctrl+tab

### Git

新建用户后需要设置ssh key。根据GitHub ssh key设置指导，在本地生成加密密码后，在GitHub网页更新钥匙。然后添加全局变量：

git config --global user.name "XXX"；git config --global user.email "XXX"

git remote -v: 显示远程路径

git remote add origin +路径：添加origin路径

git remote rm origin：删除origin路径

复制子目录：

git init ConvLab && cd ConvLab     //新建仓库并进入文件夹

git config core.sparsecheckout true //设置允许克隆子目录
 
echo 'convlab/modules/nlu/multiwoz/bert*' >> .git/info/sparse-checkout //设置要克隆的仓库的子目录路径, 空格别漏
 
git remote add origin https://github.com/ConvLab/ConvLab.git  //这里换成你要克隆的项目和库
 
git pull origin master    //下载

删除当地git信息：rm -rf ./.git/

删除本地关联远程库：git remote remove origin 添加本地关联远程库：git remote add origin git@github.com:git_username/repository_name.git

### vim
gg: 调到最上面

shift+g：调到最下面

?xxx+Enter：查找字符串，n: 向上选择；N：向下选择

/xxx+Enter: 查找字符串，n：向下选择；N:向上

取消高亮  :noh

显示行数 :set nu 取消行数 :set nonu

向上翻页：ctrl+b 向下翻页：ctrl+f

删除一行：dd

复制粘贴：v进入visual模式，y复制，p粘贴

撤销操作：u

长期vim设置：在~新建.vimrc文件，将命令放在里面即可。

自动indent：:set autoindent

tab为四个空格：:set ts=4 sw=4 expandtab

批量注释：ctrl+v，选中行数，大写I插入“#”，连续按两次esc，会将所有选中的行都注释；

批量取消注释：ctrl+v，选中行数，按d取消选中所有。

调到指定行 :n, n为行数

zz: 将当前行置于屏幕中间 zt: 将当前行置于屏幕顶端 zb：底端
ctrl-e: 所在行向上移 ctrl-y: 所在行向下移

自动补全：ctrl+p向上补全  ctrl+n向下补全

整行补全：ctrl+x进入x模式，再ctrl+l，关于更多补全的命令：https://blog.easwy.com/archives/advanced-vim-skills-auto-complete/

yy：复制，p：粘贴

rar文件解压：

下载tar.gz文件，解压后，在当前目录解压：unrar e -r /home/work/software/myfile.rar 在源文件目录解压：unrar x -r /home/work/software/myfile.rar


### Conda
下载conda sh文件，sh该文件开始安装。source下bashrc文件。

conda create -n mypython3 python=3

conda activate xxx; conda deactivate

conda env remove -n xxx

安装jupyter kernel：在虚拟环境里，首先安装：conda install ipykernel。其次：python -m ipykernel install --user --name （名字） --display-name"python （名字）"

删除kernel：jupyter kernelspec remove 环境名称

打开jupyter的方法，一是：jupyter notebook，复制网址，将ip地址改为服务器地址，端口改为8080（跟配置有关）。

二是：jupyter lab --ip 0.0.0.0，地址可以是任意的，打开的lab不会因为远程连接断掉而断掉。复制网址，将IP地址改为服务器地址，端口默认为8888即可。

### Pycharm
安装pycharm：将pycharm安装包压缩文件复制到自己主页的某个folder并解压，cd into "{installation home}/bin" and type: ./pycharm.sh，设置alias :vim ~/.bashrc；alias pycharm="nohup {path}/pycharm.sh &" 保存修改，退出 .bashrc 运行以下命令 source ~/.bashrc

添加python路径： 在Project Interpreter里找到python路径的设置，添夹新的environment的python路径。

pycharm debug: 具体参考这个[链接](https://zhuanlan.zhihu.com/p/62610785)

change font size, appearances. 

常见快捷键：具体参考这个[链接](https://blog.csdn.net/BobYuan888/article/details/79885960)

ctrl+y删除当前行；ctrl+d复制当前行；ctrl+home跳到首行；ctrl+end跳到尾行；home/end跳到当前行首/行尾；ctrl+g弹出框，可以选择跳转到具体行数

### 更改terminal界面
安装zsh（注意：以下的方法适用于没有root权限的用户账户，且该方法会导致一些功能比如scp，sftp不可以使用。同时注意要小心更改bashrc文件，否则出错后将无法远程登录系统）：

Download and extract
wget http://www.zsh.org/pub/zsh-5.4.2.tar.gz
tar -xzf zsh-5.4.2.tar.gz
rm zsh-5.4.2.tar.gz
cd zsh-5.4.2

I will install to $HOME/local -- change it to suit your case
mkdir ~/local

check install directory
./configure --prefix=$HOME/local
make

all tests should pass or skip
make check
make install

放进bashrc:
echo "export PATH=$HOME/local/bin:$PATH" >> ~/.bashrc
echo "exec zsh" >> ~/.bashrc

下载oh-my-zsh:

switch to zsh first: exec zsh
curl https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh | sed -e 's/grep\ \/zsh\$\ \/etc\/shells/which zsh/g' | zsh

最后将之前在bashrc设置的路径复制到zshrc文件里。

更改主题：vim ~/.zshrc里面更换theme

添加新的插件：

语法高亮：cd /home/shellhub/.oh-my-zsh/custom/plugins；git clone https://github.com/zsh-users/zsh-syntax-highlighting

语法建议：git clone https://github.com/zsh-users/zsh-autosuggestions

vim ~/.zshrc添加在plugins

oh-my-zsh基本快捷键：
CTRL + a 回到行首
有时候打了一条命令，发现需要加 sudo，这时候就可以 按下 CTRL + a 回到行首，然后回车执行
CTRL + e 回到行尾
CTRL + d 删掉光标所在处的一个字符（删除键删的是光标前的一个字符）
CTRL + w 删掉光标前的一个单词
这比一个字母一个字母地删快多了。
CTRL + k 删掉光标后的所有字符
CTRL + u 清空整行
CTRL + b 前移一个字符（相当于左箭头）
CTRL + f 后移一个字符（相当于右箭头）
CRTL + l（L的小写字母）清屏
