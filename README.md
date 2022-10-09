# Visual Studio Code C++ Setting
這裡的檔案是 Visual Studio Code 撰寫 C++ 所需要的環境設定，下載所有檔案壓縮成的 Zip 檔，在電腦中創建一個您要儲存和撰寫 C++ 檔案的資料夾，並在其中建立一個名為 .vscode 的資料夾，再將剛才的 Zip 檔解壓縮到剛剛建立的 .vscode 資料夾，接著就能成功撰寫 C++ 程式，此環境檔案適用於 Windows，更多詳細教學內容，請點選下方連結。  
### [Vscode 撰寫 C++ 詳細教學](https://smallshawn95.notion.site/Visual-Studio-Code-C-5fb2e43c622e46a7bb9d4e9d7fec634a)
## c_cpp_properties.json 程式碼完成
當使用者在撰寫程式時，會列出接下來使用者可能會使用到的變數、方法、函式等等。
```json
{
    "configurations": [
        {
            "name": "Win32"
            "intelliSenseMode": "windows-msvc-x64",
            "includePath": [
                "${workspaceRoot}",
                "C:\\MinGW\\include",
                "C:\\MinGW\\lib\\gcc\\mingw32\\9.2.0\\include",
                "C:\\MinGW\\lib\\gcc\\mingw32\\9.2.0\\include\\c++"
            ],
            "defines": [
                "_DEBUG",
                "UNICODE",
                "__GNUC__=5",
                "__cdecl=__attribute__((__cdecl__))"
            ],
            "browse": {
                "path": [
                    "${workspaceRoot}",
                    "C:\\MinGW\\include",
                    "C:\\MinGW\\lib\\gcc\\mingw32\\9.2.0\\include",
                    "C:\\MinGW\\lib\\gcc\\mingw32\\9.2.0\\include\\c++"
                ],
                "limitSymbolsToIncludedHeaders": true,
                "databaseFilename": ""
            }
        }
    ],
    "version": 3
}
```
## tasks.json 編譯
```json
{
    "version": "2.0.0",
    "tasks": [
        {
            "label": "build",
            "type": "shell",
            "command": "g++",
            "args": [
                "-g", "${file}", "-o", "${fileBasenameNoExtension}.exe"
            ],
            "group": {
                "kind": "build",
                "isDefault": true
            }
        }
    ]
}
```
## launch.json 偵錯
```json
{
    "version": "0.2.0",
    "configurations": [
        {
            "name": "(gdb) Launch",
            "type": "cppdbg",
            "request": "launch",
            "program": "${workspaceRoot}/${fileBasenameNoExtension}.exe",
            "args": [],
            "stopAtEntry": false,
            "cwd": "${workspaceRoot}",
            "environment": [],
            "externalConsole": true,
            "MIMode": "gdb",
            "miDebuggerPath": "C:\\MinGW\\bin\\gdb.exe",
            "setupCommands": [
                {
                    "description": "Enable pretty-printing for gdb",
                    "text": "-enable-pretty-printing",
                    "ignoreFailures": true
                }
            ],
            "preLaunchTask": "build"
        }
    ]
}
```
