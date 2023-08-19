# iresign

IReSign，Universal Signing Tool on all platform for Apple application, Win/Linux/MacOS/iOS is supported.

### Language

    Simplified Chinese and English are supported,  UI will be switched associating with system.

#### Windows

     1.unzip the package
     2.if you want to use termial version, open the command window, cd to directory, and execute the command
     3.if you want to use the UI version, click the iresign_ui.exe

#### IOS:

    download from website, I provided one link: [BlackCat](https://usign.biz/ipa/1139gcmSEO)

#### MacOS:

     1.unzip the package
     2.if you want to use the UI version, click the iresign_ui.app
     3.if you want to user termial version, open the command window, cd to directory, and execute the command

### Usage for termial version

      Usage: ./iresign.[linux|macos|win32] [options]
      Universal Signing Tool on all platform for Apple application, Win/Linux/MacOS/iOS is supported.
      
      Options:
      -h, --help                  Displays help on commandline options.
      --help-all                  Displays help including Qt specific options.
      -v, --version               Displays version information.
      --debug                     debug log output <.iresign_debug>.
      -l, --license <file>        license <file> for platinum
      -W, --workspace <dir>       temporary directory for cache
      -u, --speedup               package ipa for speeding signing
      -d, --data <data>           json data write to .app/_config for validate.
      -c, --cert <cert>           certificate file (PEM or DER format).
      -k, --pkey <key>            private key or p12 file (PEM or DER format).
      -m, --prov <prov>           mobile provisioning profile.
      -p, --password <password>   password for private key or p12 file.
      -i, --bundleid <text>       set the bundleid.
      -n, --bundlename <text>     set the bundle name.
      -e, --entitlements <file>   attach the entitlements file.
      -r, --bundleversion <text>  set the bundle version.
      -z, --ziplevel <number>     compresse level when zipping to ipa. (0-9)
      -f, --force < >             ignore the cache mode.
      -s, --source <file|dir>     source ipa file/app directory.
      -o, --output <file>         target localtion to output ipa.
      -j, --inject                inject dylibs in to execute file, splite with ',' if multiple
      -g, --remove                remove dylibs from execute file, splite with ',' if multiple
      -w, --weak                  weal dylib injecting as LC_LOAD_WEAK_DYLIB.
      -t, --install               install to device using ideviceinstaller command.
      -q, --quiet                 quiet mode.

### Here are examples

1. Show mach-o and codesignature segment info.

    ./iresign -s demo.app/execute

2. inject dylibs(LC_LOAD_DYLIB) in to execute file.

    ./iresign -s demo.app/execute -j demo1.dylib,demo2.dylib

3. inject dylibs(LC_LOAD_WEAK_DYLIB) in to execute file.

    ./iresign -w -s demo.app/execute -j demo1.dylib,demo2.dylib

4. remove dylibs from execute file.

    ./iresign -s demo.app/execute -g @executable_path/Frameworks/demo1.dylib,@executable_path/Frameworks/demo2.dylib

5. Sign ipa with private key and mobileprovisioning file.

    ./iresign -k privkey.pem -m dev.prov -o output.ipa -z 5 -s demo.ipa

6. Sign folder with p12 and mobileprovisioning file (using cache).

    ./iresign -k dev.p12 -p 123 -m dev.prov -o output.ipa -s Payload/demo.app

7. Sign folder with p12 and mobileprovisioning file (without cache).

    ./iresign -f -k dev.p12 -p 123 -m dev.prov -o output.ipa -s Payload/demo.app

8. Inject dylib into ipa and re-sign, only support add one dylib.

    ./iresign -k dev.p12 -p 123 -m dev.prov -o output.ipa -j demo.dylib -s demo.ipa

9. Change bundle id and bundle name

    ./iresign -k dev.p12 -p 123 -m dev.prov -o output.ipa -i 'com.tree.new.bee' -n 'TreeNewBee' -s demo.ipa

10. modify the Cache/Process Directory.

    ./iresign -W./ -k privkey.pem -m dev.prov -o output.ipa -s demo.ipa

11. Genarate the speedup package.

    ./iresign -k privkey.pem -m dev.prov -u -o output_s.ipa -s demo.ipa

### Thanks

     The original logic of the signature comes from zsign. Thanks very much for providing the best tool

### Communicate

communicate between users，please add the group of telegram
[IResign](https://t.me/isign_service)
or the group of QQ
[IResign](https://t.me/isign_service](http://qm.qq.com/cgi-bin/qm/qr?_wv=1027&k=zSU5coJ5P9sfFzocG48N-BRSfUspUnQR&authKey=m49xy32aWUCi7UBJDR19gDLk1Ar4B0uywMEmPtzTNQm0RkX3JLi6p4odcuZA5Kjb&noverify=0&group_code=181337255)http://qm.qq.com/cgi-bin/qm/qr?_wv=1027&k=zSU5coJ5P9sfFzocG48N-BRSfUspUnQR&authKey=m49xy32aWUCi7UBJDR19gDLk1Ar4B0uywMEmPtzTNQm0RkX3JLi6p4odcuZA5Kjb&noverify=0&group_code=181337255)
