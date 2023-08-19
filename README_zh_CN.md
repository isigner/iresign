# iresign

艾瑞签名，通用全平台多语言苹果应用签名工具，支持Win/Linux/MacOS/iOS

### 语言

    目前支持简体中文和英文，根据系统自动切换

#### Windows

     1.直接解压缩
     2.如果你需要命令行模式，打开终端, 进入目录, 执行iresign.exe即可
     3.如果你需要图形界面模式，直接双击iresign_ui.exe

#### IOS:

    签名后下载即可, 我提供了测试版链接: [黑猫工具箱](https://6us.fun/ipa/1139gcmSEO)

#### MacOS

     1.直接解压缩
     3.如果你需要图形界面模式，直接双击iresign_ui.app
     2.如果你需要命令行模式，打开终端, 进入目录, 执行iresign.macos即可

### 命令行版本使用说明

      Usage: ./iresign.linux [options]
      通用全平台苹果应用签名工具，支持Win/Linux/MacOS/iOS
      
      Options:
      -h, --help                  Displays help on commandline options.
      --help-all                  Displays help including Qt specific options.
      -v, --version               Displays version information.
      --debug                     开启调试日志, <.resign_debug>.
      -l, --license <file>        高级版授权文件
      -W, --workspace <dir>       缓存临时目录
      -u, --speedup               生成加速签名包
      -d, --data <data>           签名时输入文件, .app/_config
      -c, --cert <cert>           证书文件, 支持PEM或DER
      -k, --pkey <key>            私钥或P12文件, 支持PEM或DER
      -m, --prov <prov>           描述文件
      -p, --password <password>   私钥/P12文件的密码
      -i, --bundleid <text>       设置应用标识
      -n, --bundlename <text>     设置应用名
      -e, --entitlements <file>   附加资格文件
      -r, --bundleversion <text>  设置应用版本
      -z, --ziplevel <number>     压缩登记, (0-9)
      -f, --force < >             强制重签模式
      -s, --source <file|dir>     源包路径或应用目录
      -o, --output <file>         输出IPA文件的路径
      -j, --inject                批量注入插件,使用','分割多个
      -J, --remove                批量删除插件,使用','分割多个
      -w, --weak                  弱注入模式
      -t, --install               使用外部指令安装到设备,仅适用PC
      -q, --quiet                 安静模式

### 下面是使用的例子

1. 显示 mach-o 签名段信息.

    ./iresign -s demo.app/execute

2. 注入(LC_LOAD_DYLIB)插件到执行文件.

    ./iresign -s demo.app/execute -j demo1.dylib,demo2.dylib

3. 弱注入(LC_LOAD_WEAK_DYLIB)插件到执行文件.

    ./iresign -w -s demo.app/execute -j demo1.dylib,demo2.dylib

4. 从执行文件中删除插件依赖.

    ./iresign -s demo.app/execute -g @executable_path/Frameworks/demo1.dylib,@executable_path/Frameworks/demo2.dylib

5. 使用私钥和描述文件进行签名.

    ./iresign -k privkey.pem -m dev.prov -o output.ipa -z 5 -s demo.ipa

6. 使用P12文件和描述文件签名(使用缓存).

    ./iresign -k dev.p12 -p 123 -m dev.prov -o output.ipa -s Payload/demo.app

7. 使用P12文件和描述文件签名(无缓存).

    ./iresign -f -k dev.p12 -p 123 -m dev.prov -o output.ipa -s Payload/demo.app

8. 注入插件并且签名，该模式下仅仅支持单个插件注入.

    ./iresign -k dev.p12 -p 123 -m dev.prov -o output.ipa -j demo.dylib -s demo.ipa

9. 修改应用的ID和名称

    ./iresign -k dev.p12 -p 123 -m dev.prov -o output.ipa -i 'com.tree.new.bee' -n 'TreeNewBee' -s demo.ipa

10. 设置签名工作目录.

    ./iresign -W./ -k privkey.pem -m dev.prov -o output.ipa -s demo.ipa

11. 生成加速包.

    ./iresign -k privkey.pem -m dev.prov -u -o output_s.ipa -s demo.ipa

### 感谢

     签名的原始逻辑来自于zsign, 非常感谢作者提供了该工具

### 交流

用户交流，请加入Telegram群
[IResignTG](https://t.me/isign_service)
或者加入QQ群
[IResignQQ](http://qm.qq.com/cgi-bin/qm/qr?_wv=1027&k=zSU5coJ5P9sfFzocG48N-BRSfUspUnQR&authKey=m49xy32aWUCi7UBJDR19gDLk1Ar4B0uywMEmPtzTNQm0RkX3JLi6p4odcuZA5Kjb&noverify=0&group_code=181337255)
