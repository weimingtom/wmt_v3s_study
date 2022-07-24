# wmt_v3s_study
My Allwinner V3S study

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

