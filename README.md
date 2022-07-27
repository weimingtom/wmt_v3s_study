# wmt_v3s_study
My Allwinner V3S study

* some v3s projects about live camera, V3S_OV2640_RTMP, etc      
https://github.com/weimingtom/buildroot_licheepi_zero_hello  

* cherrypi v3s first glance  
我买的lctech cherrypi v3s开发板到手了，不需要tf卡即可启动——需要接三线串口，  
排针要自己焊（附带双排针，普通间距），板载天线但可以用镊子掀起来拔掉。  
接电源、串口和40针4.3寸屏（分辨率480和272）后会进入命令行  
（root无密码，不需要tf卡，可能是nand启动），  
并且在屏幕上面有显示（等待，需要等到login命令行出现才启动）。  
有8个/dev/fb设备。屏幕的程序应该是qt的例程，  
/usr/share/qt/demos/pathstroke/pathstroke -small-screen -nomouse。  
暂时未拿到资料，待考  

* cherrypi v3s nand flash    
根据官方提供的资料，cherrypi v3s使用的存储器是MX35LF1GE4AB-Z4（128MB），  
确实是nand flash，而以前买的荔枝派zero（也是v3s），则是没有焊存储器  
（需要用tf卡启动），应该预留的是nor flash（MX25L12835F，16MB）或  
nand flash（GD5F1GQ4UAYIG，128MB）。   

* cherrypi v3s burn  
根据艾尔赛提供的说明书，cherrypi v3s的fb应该就是/dev/fb0  
（未测试，不知道为什么会有8个fb设备）。烧录系统要按住S6然后按reset，  
然后用PhoenixSuit看到进度条然后烧进去——未试验，  
我猜是进入FEL模式然后读usb——这里的S6是板上靠近排针的最左侧按钮，  
没有丝印，可能就是FEL（其他的开关是S4-S1对应START/SEL/-/+，  
S5在另一个板边缘，对应reset）  

* ref  
https://github.com/puyams/v3s-linux-sdk  

* cherrypi v3s sdk build  
花了九牛二虎之力，三四个小时，终于把cherrypi v3s的固件编译出来了。  
由于u-boot里面有个工具是32位，但u-boot的交叉工具链（也可能是内核的）  
却是非32位，还有如果用xubuntu 20会导致bison编译失败  
（可能bison的特定版本问题，导致fseterr.c编译失败）  
以及后面一些qt的编译失败，所以唯一的选择是旧的ubuntu 14非32位，  
另外还需要解决32位问题，所以需要  
sudo apt install make gcc g++ python git gcc-multilib   
g++multilib lib32z1 lib32ncurses5 u-boot-tools  

