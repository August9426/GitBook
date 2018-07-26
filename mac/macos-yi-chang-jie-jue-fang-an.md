# MacOS 异常解决方案

## 任何来源消失

> `> sudo spctl --master-disable`

## 蓝牙异常

> 关掉蓝牙，在 Mac 上打开目录： /Library/Preferences/。 找到文件： com.apple.Bluetooth.plist 删除。此时需要管理员权限。 关机电脑，等待10秒以上，然后再开启。 再次开启蓝牙连接设备。
>
> 按住 Option 和 Shift 键，点击状态栏蓝牙图标。 选择 调试 、 还原蓝牙模块 选择确定进行初始化。 终极解决办法 过了两天又出现了同样的问题，打给苹果客服后进行了 PRAM 和 SMC 重置。具体步骤如下

## 其他异常

> PRAM 重置 关机，拔掉所有外设，接上电源。 启动时同时按住 Command, Option, p, r ， 听到三次 dang 的开机声音后放开。 启动电脑
>
> SMC 重置 关机，拔掉所有外设，接上电源。 同时按住 Shift, Control, Option, 电源键 ，此时电脑没有任何反应，等待十秒放开。 继续等待十秒，启动电脑。

