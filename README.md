# frequently-used-command
frequently used command in terminal, ssh, etc.

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

从本地上传文件到远程服务器，使用本地terminal：scp C:\Users\l00556051\Desktop\NLU lianyixin@10.67.42.42:~/

在不同窗口切换：ctrl+tab



### Terminal
查看系统：cat /etc/os-release

top命令：查看处理器和任务情况

nvidia-smi: 查看显存情况

安装创建virtualenv: pip install virtualenv; 新建环境：virtualenv envname 或者 virtualenv -p python3 myenv; 进入环境：source envname/bin/activate; 退出：deactivate

修改软件默认路径：vim ~/.bashrc

jupyter: jupyter notebook, 在网址输入：http://10.67.42.43:8080/user/lianyixin/lab?redirects=1

下载单个文件： wget+路径（容易出现文件损坏的问题）

显示当前路径： pwd

在 Python 环境中增加搜索路径：
1. import sys；  sys.path.append('/home/wang/workspace')
2. vim ~/.bashrc； export PYTHONPATH=$PYTHONPATH:/home/wang/workspace； source ~/.bashrc # 或者 . ~/.bashrc 
3. 在 /usr/local/lib/python3.5/site-packages 下添加一个扩展名为 .pth 的配置文件（例如：extras.pth），内容为要添加的路径：/home/wang/workspace

退回原目录： cd - 返回上一级目录：cd ..

查看安装包情况：pip show 安装包； 查看所有安装包：pip list

解压tar.xz文件： tar xf 文件名

centos系统内置： yum install xxx; yum remove xxx

查看系统python版本：python --version; python3 --version；

设置python版本默认指向python3： echo alias python=python3 >> ~/.bashrc；source ~/.bashrc


### Git
git remote -v: 显示远程路径

git remote add origin +路径：添加origin路径

git remote rm origin：删除origin路径

复制子目录：

git init ConvLab && cd ConvLab     //新建仓库并进入文件夹

git config core.sparsecheckout true //设置允许克隆子目录
 
echo 'convlab/modules/nlu/multiwoz/bert*' >> .git/info/sparse-checkout //设置要克隆的仓库的子目录路径, 空格别漏
 
git remote add origin https://github.com/ConvLab/ConvLab.git  //这里换成你要克隆的项目和库
 
git pull origin master    //下载



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

### 更改terminal界面
安装zsh：

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

**下载oh-my-zsh:**

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
