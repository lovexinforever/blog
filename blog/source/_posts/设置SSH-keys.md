title: 设置SSH keys
date: 2015-12-25 10:47:16
tags:
- git
categories: 
- 技术
- 日志

---
### 本文主要详细解释怎样用git 连接远程仓库,至于git怎么下载安装,请自行百度.
<!-- more -->
1. 在Git Bash输入以下指令（任意位置点击鼠标右键），检查是否已经存在了SSH keys。<font color="#f00">`ls -al ~/.ssh`</font>
<img src='/imgs/blog4/img1.png' />
2.如果不存在就没有关系，如果存在的话，直接删除.ssh文件夹里面所有文件：
3.输入以下指令（邮箱就是你注册Github时候的邮箱）后，回车：
<font color="#f00">`ssh-keygen -t rsa -C "tim_ding@qq.com"`</font>
<img src="/imgs/blog4/img2.png" />
4.然后它会提示要你输入passphrase（如上图，我没有输入直接回车，如果你输入的话，要记得，到时候会用到）。之后，如果出现类似下图：
<img src="/imgs/blog4/img3.png" />
5.然后键入以下指令：
<font color="#f00">`ssh-agent -s`</font>
<img src="/imgs/blog4/img4.png" />
6.继续输入指令：
<font color="#f00">`ssh-add ~/.ssh/id_rsa`</font>
7.输入之后可能出错,如果出错,继续执行,如果不出错,跳到第九步
8.输入以下命令
{% codeblock  %}
eval `ssh-agent -s`
ssh-add
{% endcodeblock %}
<img src="/imgs/blog4/img5.png" />
9.到了这一步，就可以添加SSH key到你的Github账户了。键入以下指令，拷贝Key（先拷贝了，等一下可以直接粘贴）：
<font color="#f00">`clip < ~/.ssh/id_rsa.pub`</font>
10.然后到Github里面，点击右上角的设置图标：
<img src="/imgs/blog4/img6.png" />
11.在Settings sidebar那里，点击SSH keys：
<img src="/imgs/blog4/img7.png" />
12.点击Add SSH key：
<img src="/imgs/blog4/img8.png" />
13.输入Title，作为这个key的描述吧（你可以输入Personal MacBook Air，瞬间高大上）
<img src="/imgs/blog4/img9.png" />
14.然后这个Key就是刚刚拷贝的，你直接粘贴就好
15.点击Add Key：
16.输入你的Github密码即可完成SSH Key的添加。嗯，最后还是测试一下吧，键入以下命令：
<font color="#f00">`ssh -T git@github.com`</font>
17.你可能会看到有警告，没事，输入“yes”就好。


至此就可以连接远程仓库了.
                          谢谢