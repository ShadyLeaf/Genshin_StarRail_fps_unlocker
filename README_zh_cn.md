## 原神&崩铁 帧率解锁


- **这个repo魔改自34736384的[unlocker](https://github.com/34736384/genshin-fps-unlock) **
- **为了方便个人需求，将两款游戏集成在一起，方便启动**

# -----------------------------------------------------------------
 - 工作原理通过**WriteProcessMemory**把FPS数值写进游戏
 - 不需要通过驱动进行读写操作
 - 支持国服和外服
 - 理论上支持后续版本，不需要更新源码
 - 如果需要更新我会尽快更新
 - 如果不想手动编译的话去[Release](https://github.com/winTEuser/genshin-StarRail-fps-unlock/releases)下载编译好的
# -----------------------------------------------------------------
## 自定义参数启动
 - 给unlockfps.exe创建一个快捷方式, 改个图标, 在快捷方式的属性处加上需要的参数例如-popupwindow，支持多参数
 - **注意：第一个参数必须是要启动的游戏，详情看下面命令行**
 - ![image](https://github.com/winTEuser/Genshin_StarRail_fps_unlocker/blob/main/assets/Quick_link.jpg)
# -----------------------------------------------------------------
## 食用指南
 - 第一次运行的话先以管理员运行，然后手动打开游戏，这样解锁器能够获取到游戏路经并保存在配置文件里，这只需要执行一次，以后就可以直接用解锁器启动游戏了
 - 解锁器放哪都行 **除了游戏目录**
 - 运行之前确保游戏是关闭的
 - 用管理员运行解锁器
 - 自行编译 使用 Visual Studio 或 配置好msvc环境的Vscode
>使用管理员运行是因为游戏必须由解锁器启动，游戏本身就需要管理员权限了，所以负责启动的也是需要的

## 快速启动命令行
 - unlocker.exe -[游戏] -[给解锁器的参数在游戏参数前] -[游戏参数...]
 - 例 unlocker.exe -Genshin -screen-width 3840 -screen-height 1620 -screen-fullscreen 1
 - 例 unlocker.exe -HKSR -...
 - 给解锁器的参数包括
   - `-EnableMobileUI`：在启动的游戏后面添加参数"**-EnableMobileUI**"来便捷启用移动端ui，例：`unlocker.exe -Genshin -EnableMobileUI`
   - `-loadlib [绝对路径]`：DLL注入，使用前确保来源可靠性，例：`unlocker.exe -[游戏] -loadlib [绝对路径]`
   - `-nc`或`--no-console`：无控制台模式（如果配置存在则隐藏控制台窗口），例：`unlocker.exe -[游戏] -nc`或`unlocker.exe -[游戏] --no-console`
 - 综合示例：`unlocker.exe -Genshin -EnableMobileUI -loadlib C:\\Folder\\plug.dll -nc -[游戏参数...]`

### 默认热键           PS:按键要按一次改一次，不是长按
- **END** 开/关
- **右ctrl + 上方向键** 增大FPS上限 （+20）
- **右ctrl + 右方向键** 增大FPS上限 （+2）
- **右ctrl + 下方向键** 减少FPS上限 （-20）
- **右ctrl + 左方向键** 减少FPS上限 （-2）
- 源里默认的FPS数值是120

## 代码注入
 - 到目前为止只能注入解锁
 - 改变游戏里的帧数设置(目前只对原神有效):**(需在hoyofps_config.ini里面打开IsHookGameSet)**
 - 30 -> 60(打开游戏里的浏览器不会卡顿, 默认为60, 配置文件可改)
 - 45 -> 同步解锁器里的帧数设置
 - 60 -> 无限制(默认设置1000，配置文件可改)

## 注意
- 目前测试冒险等级到60级，没有发现有被封禁的情况
- 想要更改热键的话，修改下源里开头的定义 （[热键码](http://cherrytree.at/misc/vk.htm)）
- 游戏登录的时候会进行文件完整性检测，如果游戏目录内有其他文件也会当做是游戏的文件进行检测。如果把解锁器和游戏放一起的话游戏会把解锁器当成游戏文件检测，会导致报错（31-4302）
- 要转载的话随便，毕竟开源，可以的话就注明下出处
- 这么个破工具请不要拿去倒卖
- 解锁帧率后产生的bug请交给官方

## 致谢
- **34736384**
- **xiaonian233**


