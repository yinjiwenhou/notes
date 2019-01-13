1、卸载sublime text
找到桌面快捷方式文件
/usr/share/applications/Sublime_Text_3.desktop

在文件中可以看到软件安的安装路经
Exec=/opt/sublime_text_3/sublime_text

删除快捷方式文件和安装软件
sudo rm /usr/share/applications/Sublime_Text_3.desktop
sudo rm -rf /opt/sublime_text_3

如果是用apt-get的方式安装的，卸载方式如下：
sudo dpkg -r sublime-text
sudo apt-get remove sublime-text
sudo rm -rf /home/$USER/.config/sublime-text-3/

2、安装sublime text
获取linux安装包
sublime_text_3_build_3176_x64.tar.bz2

解压安装包
tar -xjf sublime_text_3_build_3176_x64.tar.bz2

放到安装目录下
sudo mv sublime_text_3 /opt/

创建桌面快捷方式
sudo cp sublime_text.desktop /usr/share/applications/

**无法调用install package：
channe_v3.json错误，重新下载一份后运行正常
http://cst.stu.126.net/u/json/cms/channel_v3.json






