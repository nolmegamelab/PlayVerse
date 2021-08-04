# [Build] 프로젝트 셋업 

## 오프라인 설치 후 언리얼 등록 

```bat
@echo off
setlocal
pushd "%~dp0"

rem Install prerequisites...
echo Installing prerequisites...
start /wait Engine\Extras\Redist\en-us\UE4PrereqSetup_x64.exe /quiet

rem Register the engine installation...
if not exist .\Engine\Binaries\Win64\UnrealVersionSelector-Win64-Shipping.exe goto :no_unreal_version_selector
.\Engine\Binaries\Win64\UnrealVersionSelector-Win64-Shipping.exe /register
:no_unreal_version_selector

rem Done!
goto :end

rem Error happened. Wait for a keypress before quitting.
:error
pause

:end
popd
```

## uproject에서 solution 갱신 

```cmd
h:/app/UE_4.26/Engine/Binaries/DotNET/UnrealBuildTool.exe  -projectfiles -project="h:/projects/PlayBot/PlayViewer/RealView/RealView.uproject" -game -rocket -progress -log="d:\projects\PlayViewer\Logs\UnrealVersionSelector-2021.05.30-10.21.44.log"
```


