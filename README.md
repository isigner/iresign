# iresign

IResign，Universal signing tool on all platform for Apple application, supporting Win/Linux/MacOS/iOS.

### Language

    Currently supports Simplified Chinese and English, will switching based on the system automaticly

## Environment

    you must install openssl libzip libplist first.

#### macOS:

    brew install openssl libplist libzip

#### ArchLinux:

    pacman -S icu openssl-1.1 libplist libzip qt6-base

#### Windows

     1.decompress the software package
     2.Open the command window, change to directory, and execute the command

#### IOS:

    just download after signing 

#### UI Version:

     1.decompress the software package with ui named
     2.change to directory, and double click the execute file

### Usage

      Usage: ./iresign.linux [options]
      Universal signing tool on all platform for Apple application, supporting Win/Linux/MacOS/iOS.
      
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

     The original logic of the signature comes from zsign. Thank you very much for providing this tool

### Communicate

communicate betewwn uses，please add the group of telegram
[IResign](https://t.me/isign_service)
