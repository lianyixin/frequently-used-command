# frequently-used-command
frequently used command in terminal, ssh, etc.

### windows快捷键
win+D: 最小化所有窗口
win+下：部分小化当前窗口
win+左：当前窗口占满左部分屏幕
alt+空格+N: 最小化当前窗口

### SSH
软件: mobaxterm, new session, 输入用户名密码

修改用户名密码: passwd

从本地上传文件到远程服务器，使用本地terminal：scp C:\Users\l00556051\Desktop\NLU lianyixin@10.67.42.42:~/

### Terminal
查看系统：cat /etc/os-release

top命令：查看处理器和任务情况

nvidia-smi: 查看显存情况

安装创建virtualenv: pip install virtualenv; 新建环境：virtualenv envname; 进入环境：source envname/bin/activate; 退出：deactivate

修改软件默认路径：vim ~/.bashrc

jupyter: jupyter notebook, 在网址输入：http://10.67.42.43:8080/user/lianyixin/lab?redirects=1

下载单个文件： wget+路径

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



