##tmux命令
```
vim ~/.tmux.conf            //tmux配置文件
brew install tmux           //安装tmux
tmux                        //终端下运行命令
tmux new -s session-name    //新建一个session
tmux attach -t session-name //终端下输入进入这个session
tmux a                      //当只有一个session是最快连接方式
tmux kill-session -a        //删除除了自身之外所有session
tmux kill-session -t session-name   //删除指定名字session
tmux ls                     //查看tmux所有的session

prefix + d  //快捷键返回到终端，这个session依然运行
prefix + %  //水平分割pane
prefix + "  //竖直分割pane
prefix + z  //把当前一个pane放大
exit        //直接输出退出pane,当只有一个pane时，退出整个session
```
##tmux.conf
```
# Send prefix
set-option -g prefix C-a
unbind-key C-a
bind-key C-a send-prefix

# Use Alt-arrow keys to switch panes
bind -n M-Left select-pane -L
bind -n M-Right select-pane -R
bind -n M-Up select-pane -U
bind -n M-Down select-pane -D

# Shift arrow to switch windows
bind -n S-Left previous-window
bind -n S-Right next-window

# Mouse mode
set -g mouse on


# Set easier window split keys
bind-key v split-window -h
bind-key h split-window -v

# Easy config reload
bind-key r source-file ~/.tmux.conf \; display-message "tmux.conf reloaded"
```
Send prefix
把prefix的ctrl+b变为了ctrl+a，因为这样按起来方便些。基本上用tmux的都改了这个。

Use Alt-arrow keys to switch panes
不用按prefix，直接用alt+箭头在pane之间switch。实际用过之后才发现真是太方便了！

Shift arrow to switch windows
不用按prefix，直接用shift+箭头在window之间switch。太方便了！

Mouse mode
开启鼠标模式。用鼠标就能切换window，pane，还能调整pane的大小，方便！

Set easier window split keys
这一部分是用来更方便切分pane的。prefix + v 代表竖着切，prefix + h 代表横着切。比起默认的切割方法不仅直观而且方便。

Easy config reload
下一次如果修改了.tmux.conf的设置的话，不用关掉tmux。直接用prefix+r,就能重新加载设置。
