---
title: hello
date: 2020-03-18 02:55:41
tags:
---
# OS 安裝&維護

#### 2019/11/11 @==HOME==

> - 完成 `ubuntu` + `win10` on `surface pro` dual boot
    1. [關閉分頁檔](https://ez3c.tw/5704) > [磁碟壓縮](https://ofeyhong.pixnet.net/blog/post/221438016) 
    2. 關閉windows快速啟動、調整secure boot
    3. [用Unetbootin製作usb開機碟](https://walker-a.com/archives/5787)
    4. [安裝ubuntu+win10雙系統(特別注意內文中的硬碟分割)](https://www.itread01.com/content/1550369173.html)
    5. [安裝linux-surface kernel ver. 5.15.1](https://github.com/jakeday/linux-surface)
    6. [sign the updated kernel for secure boot](https://github.com/jakeday/linux-surface/blob/master/SIGNING.md)

#### 2019/11/12 @==HOME==

> - grub2.02 解析度調整(在grub裡下videoinfo沒反應） / [++解法出處++](https://askubuntu.com/questions/54067/how-do-i-safely-change-grub2-screen-resolution)
uncomment `/etc/default/grub`裡的`#GRUB_GFXMODE=640x480` 
> - update from python3.6 to 3.7, some packages missed / [++解法出處++](https://stackoverflow.com/questions/13708180/python-dev-installation-error-importerror-no-module-named-apt-pkg)
`cd /usr/lib/python3/dist-packages`
`sudo ln -s apt_pkg.cpython-{35m,34m}-x86_64-linux-gnu.so` 

#### 2019/11/13 @==HOME==
> - [install docker](https://hackmd.io/EId9SvcZRSy4nPEwqpAZZA?view#20191113-Disfactory)

#### 2019/11/18 @==HOME==
> - 休眠後無法wifi裝置會消失
    > `ip` `iwconfig` 
> - 成功安裝jupyter, 但執行時發生錯誤
    > [解:套件間衝突](https://stackoverflow.com/questions/54390490/ipython3-does-not-work-in-the-terminal-with-python3-7)
    > 
#### 2019/11/19 @==HOME==
> - 安裝powerline `sudo apt install powerline` 
    > ref. [Powerline：漂亮的 Vim 狀態列與 Bash Shell 命令提示字串外掛](https://blog.gtwang.org/linux/powerline-adds-powerful-statuslines-and-prompts-to-vim-and-bash/)

#### 2019/11/20 @==DISFACTORY==
- pipenv
- test

#### 2019/11/22 @HOME
> - 安裝Unity
    - vs code integrated
    - install `dotnet`, `mono-complete`, [vscode asset](https://assetstore.unity.com/packages/tools/utilities/vscode-45320)
    ref. [Setting up Unity 2019.x with VSCode on Ubuntu 18.04 LTS: A Troubleshooting Guide](https://medium.com/@nosuchstudio/setting-up-unity-2019-x-with-vscode-on-ubuntu-18-04-lts-a-troubleshooting-guide-75da7ff29ff5)
    
#### 2019/11/25 @HOME
>- read <<python爬蟲技術與項目實踐>>

#### 2019/11/28 @HOME
>- [Vim register](https://www.brianstorti.com/vim-registers/) 開啟visual mode選取欲複製的文字之後, 下指令`"+y"`, 就會把文字複製到, 其中`y`就是vim的複製指令(yank), `"+`則是暫存器的名稱("+這個很特別, 因為這和作業系統的clipboard是同一個, 文字存到裡頭, 可以在vim以外的其他地方使用)
>- 要裝`vim-gui-common`才有支援`"+`這個暫存器, 參考[這篇](http://fcamel-life.blogspot.com/2011/02/vim-terminal-windows-clipboard.html)
>- 要看所有暫存器的內容可以下`:reg`

#### 2019/11/29 @monospace
>- change the notification sound in terminal
> `mv /usr/share/sounds/ubuntu/stero/bell.ogg /usr/share/sounds/ubuntu/stero/.bell.ogg`
`cp /usr/share/sounds/gnome/default/alerts/sonar.ogg /usr/share/sounds/ubuntu/stereo/bell.ogg`

#### 2021/1/18 @home
>- 安裝[oh my zshe](https://blog.kkbruce.net/2019/03/wsl-ubuntu-zsh-windows-command-line.html#.XiJHfmgzZQI)
>
#### 2021/2/21 @home
>- [**狀況**] 接上外接螢幕之後，沒有鏡像模式，而且以延伸桌面顯示時，surface本身的螢幕解析度會過高
> [**解法**] adjust the display setting using xrandr
>> 1. `$ cvt 1680 1120 60` (cvt是用來產生modeline, 解細度得用試誤來找) 
>> 2. `$ xrandr --addmode <Modeline後面的整串>` (定義新的解析度)
>> 3. `$ xrandr --newmode eDP-1 <Modeline後面雙引號內的字串>` (指派新定義的解析度給螢幕, eDP-1是用xrndr找connected找到的)
>> 4. create ~/.xprofile and insert code below (才會每次login前都去讀這個檔案執行指令)
>> `#!/bin/sh`
`xrandr --newmode "1680x1120_60.00"  157.00  1680 1792 1968 2256  1120 1123 1133 1162 -hsync +vsync
xrandr --addmode eDP-1 1680x1120_60.00`
>> 
>> [**google kw**] resolution ubuntu surface
>> [**ref.**] [resolution @ubuntu wiki](https://wiki.ubuntu.com/X/Config/Resolution/#Adding_undetected_resolutions) & [.xprofile](https://askubuntu.com/questions/419934/where-is-xprofile-in-ubuntu-13-10)
>> 
>> [**意外發現**] 把同一個解析度指派surface的螢幕和外接螢幕後, 鏡像模式就出現了, 因為鏡像模式必須在兩個螢幕解析度相同的條件才成立

>- [**狀況**] 找出外接螢幕的規格
>> 1. `sudo apt install get-edid`
>> 2. `get-edid|parse edid`
>> 
>> [**ref.**]  [get-edid @ubuntu manpages](http://manpages.ubuntu.com/manpages/trusty/man1/get-edid.1.html)
> 
> [**意外發現**] [Tweaks for Ubuntu on Surface Book](https://medium.com/@trungd/tweaks-for-ubuntu-on-surface-book-cd05cdb8f378), 解了wifi, 休眠, grub menu太小的問題
