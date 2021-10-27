### #Gollum依赖项

homebrew3.2.17
mac-OS10.15.7

rbenv ——> ruby3.0.2 ——> bundler-2.2.29

Ruby -v ——> rbenv init
Error:缺少cmake ——> brew cmake

Gollum -v ——> Gollum 5.2.3

### #问题：gollum not found

在ruby环境下运行:(启动ruby)

 % ruby -v
 
ruby 2.6.3p62 (系统）

% rbenv init

% eval "$(rbenv init - zsh)"  写入zshrc 。可选操作（export PATH="/Users/yuanwenyu/.rbenv/shims:$PATH"）

% ruby -v

ruby 3.0.2p107 

% gollum -v

Gollum 5.2.3

### #初始化项目git、Gollum   
创建一个空目录  
%mkdir wiki   
进入目录  
%cd wiki   
初始化为git项目目录   
%git init   
启动gollum    
%gollum   

### #访问   http://localhost:4567/   



### #参考资料

[https://sourabhbajaj.com/mac-setup/Ruby/](https://sourabhbajaj.com/mac-setup/Ruby/)

