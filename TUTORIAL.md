# Genshin CBServer Tutorial v2.0.1 by [TheScore](https://discord.com/users/367308033052770307)

## Prerequisites

- [Visual Studio 2022](<https://visualstudio.microsoft.com/>)*
- [vcpkg](<https://github.com/Microsoft/vcpkg>)
- [soggy](<https://github.com/LDAsuku/soggy>)
- [soggy_resources](<https://codeberg.org/LDA_suku/soggy_resources>)
- [Python 3](<https://www.python.org/downloads/>)>
- CB1 Client

*Add-Ons : Desktop development with C++

## Getting Started

Clone or download as zip [soggy](<https://github.com/LDAsuku/soggy>) and [soggy_resources](<https://codeberg.org/LDA_suku/soggy_resources>)

## Install dependencies (vcpkg)

```ps
vcpkg install protobuf lua[cpp]:x64-windows
```

## Building

1. Open `soggy` folder with Visual Studio
2. Build `soggy.exe`
3. Built output folder will be in `..\out\build\x{Build-Config}`

## Running the Server

1. Move `soggy_resources` inside the built output folder and rename it to `resources`
2. Run game server (`..\out\build\x{Build-Config}\soggy.exe`)
3. Run web dispatch (`.\soggy\dispatch.py`)

    ```ps
    python dispatch.py
    ```

## Connecting

- Fiddler Script

    ```js
    import System;
    import System.Windows.Forms;
    import Fiddler;
    import System.Text.RegularExpressions;
    class Handlers
    {
        static function OnBeforeRequest(oS: Session) {
            if(oS.host.EndsWith(".yuanshen.com")  || oS.host.EndsWith(".yuanshen.com:12401") || oS.host.EndsWith(".hoyoverse.com") || oS.host.EndsWith(".mihoyo.com") || oS.uriContains("http://overseauspider.yuanshen.com:8888/log")) {
                oS.oRequest.headers.UriScheme = "http";
                oS.host = "127.0.0.1"; //This can also be replaced with another ip/domain server.
                oS.port = 8099; //Default soggy port
            }
        }
    };
    ```

1. Save the script
2. Run the game
3. profit ?

## for skill issues

- [Basic guide for building C++](<https://learn.microsoft.com/en-us/cpp/ide/walkthrough-building-a-project-cpp?view=msvc-170>)
- [vcpkg guide](<https://vcpkg.io/en/getting-started.html>) (For [Install dependencies step](#install-dependencies-vcpkg))

## Credits

- [LDAsuku](https://github.com/LDAsuku) for creating the Server software implementation for a game that She forgot its name 💀
