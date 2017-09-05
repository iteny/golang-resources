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
# Set status bar
set -g status on
set -g status-bg black
set -g status-fg white
set -g status-interval 5
set -g default-terminal "screen-256color"
set -g status-left-length 90
set -g status-right-length 60
set -g status-left "#[fg=green]HostName:[#[fg=Cyan]#(hostname -s)#[fg=Cyan]] #[fg=green]User:[#[fg=blue]#(whoami)#[fg=green]] #[fg=green]Ip:[#[fg=yellow]#(curl ipecho.net/plain;echo)#[fg=green]] #[fg=green]ProgramName=>"
set -g status-justify left
set -g status-right "#[fg=green]Session:[#[fg=Cyan]#S#[fg=green]] #[fg=green]Time:[#[fg=cyan]%Y-%m-%d %H:%M:%S#[fg=green]]"

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
set -g status on
set -g status-utf8 on                      # 开启状态栏的UTF-8支持
set -g status-bg blue
set -g status-fg '#bbbbbb'
set -g status-left-fg green
set -g status-left-bg blue
set -g status-right-fg green
set -g status-right-bg blue
set -g status-left-length 10               # 状态栏左方的内容长度；
set -g status-right-length 15              # 状态栏右方的内容长度；建议把更多的空间留给状态栏左方（用于列出当前窗口）
set -g status-left '[#(whoami)]'           # 状态栏左方的内容
set -g status-right '[#(date +" %y-%m-%d %H:%M:%S ")]'     # 状态栏右方的内容；这里的设置将得到类似23:59的显示
set -g status-justify "centre"             # 窗口列表居中显示
set -g default-terminal "screen-256color"  # 支持256色显示
