---
title: 명령줄 캡처 도구 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: db75b3a7-80b2-4a74-91d2-fd6e0f73b45d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c4d88e62b1520677ddac3ff66a6891eb805af30d
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63389687"
---
# <a name="command-line-capture-tool"></a>명령줄 캡처 도구
DXCap.exe는 그래픽 진단 캡처 및 재생을 위한 명령줄 도구로, 모든 기능 수준에서 Direct3D 10 - Direct3D 12를 지원합니다.

## <a name="syntax"></a>구문

```cmd
DXCap.exe [-file filename] [-frame frames | -period periods | -manual] -c app [args...]
DXCap.exe -p [filename] [-debug | -warp | -hw] [-config] [-rawmode]
DXCap.exe -p [filename] -screenshot [-frame frames]
DXCap.exe -p [filename] -toXML [xml_filename]
DXCap.exe -v [-file filename] [-examine events] [-haltonfail | -exitonfail] [-showprogress]
DXCap.exe -e [search_string]
DXCap.exe -info
```

#### <a name="parameters"></a>매개 변수
 `-file` `filename` 캡처 모드 (`-c`), `filename` 그래픽 정보가 기록 되는 그래픽 로그 파일의 이름을 지정 합니다. 하는 경우 `filename` 지정 하지 않으면 그래픽 정보 라는 파일에 기록 됩니다 `<appname>-<date>-<time>.vsglog` 기본적으로 합니다.

 유효성 검사(-v) 모드에서 `filename`은 유효성을 검사할 그래픽 로그 파일의 이름을 지정합니다. 경우 `filename` 지정 하지 않으면, 마지막으로 유효성이 검사 된 그래픽 로그 다시 사용 됩니다.

 `-frame` `frames` 캡처 모드에서 `frames`는 캡처하려는 프레임을 지정합니다. 첫 번째 프레임은 1입니다. 쉼표 및 범위를 사용 하 여 여러 프레임을 지정할 수 있습니다. 예를 들어 경우 `frames` 됩니다 `2, 5, 7-9, 15`, 프레임 `2`, `5`, `7`를 `8`, `9`, 및 `15` 캡처됩니다.

> [!TIP]
> 사용 하 여 `-frame` `manual` Print Screen 키를 눌러 프레임을 수동으로 캡처 수를 지정 합니다. 앱이 시작될 때 프레임을 캡처할 수 있습니다. 프레임 캡처를 중지하려면 명령줄 인터페이스로 돌아가서 Enter 키를 누릅니다.

 `-period` `periods` 캡처 모드에서 `periods`는 프레임을 캡처할 시간 범위를 초 단위로 지정합니다. 쉼표 및 범위를 사용 하 여 여러 기간을 지정할 수 있습니다. 예를 들어 경우 `periods` 은 `2.1-5, 7.0-9.3`, 다음 사이 렌더링 된 프레임 `2.1` 하 고 `5` 초와`7` 및 `9.3` 초 캡처됩니다.

 `-c` `app` [`args...`] 캡처 모드입니다. 캡처 모드에서 `app`은 그래픽 정보를 캡처할 앱의 이름을 지정하고 `args...`는 해당 앱에 대한 추가 명령줄 매개 변수를 지정합니다.

 `-p` [`filename`] 재생 모드 (`-p`). 재생 모드에서 `filename`은 재생할 그래픽 로그 파일의 이름을 지정합니다. 경우 `filename` 지정 하지 않으면, 마지막으로 재생 된 그래픽 로그 다시 사용 됩니다.

 `-debug` 재생 모드에서 `-debug` 재생을 사용 하도록 설정 하는 Direct3D 디버그 계층을 사용 하 여 재생 해야 지정 합니다.

 `-warp` 재생 모드에서 `-warp` WARP 소프트웨어 렌더러를 사용 하 여 재생을 재생 해야 지정 합니다.

 `-hw` 재생 모드에서 `-hw` GPU 하드웨어를 사용 하 여 재생을 재생 해야 지정 합니다.

 `-config` 재생 모드에서 `-config` 그래픽 로그 파일을 캡처하는 데 사용 된 컴퓨터에 대 한 정보를 표시 합니다.

 `-rawmode` 재생 모드에서 `-rawmode` 기록된 된 이벤트를 수정 하지 않고 재생을 수행할지를 지정 합니다. 일반 작업 시 재생 모드에서는 디버깅을 간소화하고 재생 속도를 높이기 위해 약간의 변경이 수행될 수 있습니다. 예를 들어 스왑 체인 명령을 실행하지 않고 스왑 체인 출력을 시뮬레이트할 수 있습니다. 일반적으로이 재생은 문제가 되지 않지만 재생을 기록 된 이벤트에 보다 충실 한 방식으로 수행 해야 할 수 있습니다. 예를 들어, 전체 화면 모드에서 실행 하는 동안 캡처된 앱에 전체 화면 렌더링 동작을 복원 하려면이 옵션을 사용할 수 있습니다.

 `-toXML` [`xml_filename`] 재생 모드에서 `xml_filename`은 재생의 XML 표현이 기록되는 파일의 이름을 지정합니다. `xml_filename`을 지정하지 않으면 XML 표현은 재생 중인 파일과 이름이 같은 파일에 기록되며 `.xml` 확장명이 지정됩니다.

 `-v` 유효성 검사 모드입니다. 유효성 검사 모드에서 캡처된 프레임은 하드웨어와 WARP 둘 다에서 재생되며 이미지 비교 기능을 통해 해당 결과를 비교합니다. 이 기능을 사용하여 렌더링에 영향을 주는 드라이버 문제를 신속하게 파악할 수 있습니다.

 `-examine` `events` 유효성 검사 모드에서 `events`는 즉각적인 결과를 비교할 그래픽 이벤트 집합을 지정합니다. 예를 들어 `-examine present,draw,copy,clear` 해당 범주에 속한 이벤트만 비교를 제한 합니다.

> [!TIP]
> 로 시작 하는 것이 좋습니다 `-examine present,draw,copy,clear` 이 대부분의 문제를 표시 하지만 보다 포괄적인 이벤트 집합을 보다 훨씬 적은 시간이 됩니다. 필요한 경우 더 많은 이벤트 집합 또는 다른 이벤트 집합을 지정하여 해당 이벤트의 유효성을 검사하고 다른 종류의 문제를 확인할 수 있습니다.

 `-haltonfail` 유효성 검사 모드에서 `-haltonfail` 하드웨어와 WARP 렌더러 간에 차이점이 검색 되 면 유효성 검사를 중지 합니다. 키를 누르면 유효성 검사를 다시 시작합니다.

 `-exitonfail` 유효성 검사 모드에서 `-exitonfail` 하드웨어와 WARP 렌더러 간에 차이점이 검색 되는 경우 즉시 유효성 검사를 종료 합니다. 이러한 방식으로 프로그램이 종료 되 면 반환 `0` 환경입니다; 그렇지 않으면 반환 `1`합니다.

 `-showprogress` 유효성 검사 모드에서 `-showprogress` 유효성 검사 세션에 대 한 진행률 정보를 표시 합니다. 왼쪽에는 WARP 진행률이 표시되고 오른쪽에는 하드웨어 진행률이 표시됩니다.

 `-e` `search_string` 설치 된 UWP 앱을 열거 합니다. UWP 앱을 사용 하 여 명령줄 캡처를 수행 하려면이 정보를 사용할 수 있습니다.

 `-info` 머신 및 캡처 DLL에 대한 정보를 표시합니다.

## <a name="remarks"></a>설명
 DXCap.exe는 다음의 세 가지 모드로 작동합니다.

 캡처 모드 (-c)를 실행 중인 앱에서 그래픽 정보 캡처 및 그래픽 로그 파일에 기록 합니다. 캡처 기능 및 파일 형식은 Visual Studio와 같습니다.

 재생 모드 (-p) 이전에 캡처한 기존 그래픽 로그 파일에서 대 한 그래픽 이벤트를 재생 합니다. 기본적으로는 전체 화면 앱에서 그래픽 로그 파일을 캡처했더라도 재생은 창에서 수행됩니다. 전체 화면 앱에서 파일을 캡처할 때 그래픽 로그만 전체 화면에서 재생이 수행 및 `-rawmode` 지정 됩니다.

 유효성 검사 모드 (`-v`) 하드웨어와 WARP 둘 다에서 캡처된 프레임을 재생 한 다음 이미지 비교 기능을 사용 하 여 해당 결과 비교 하 여 렌더링 동작을 확인 합니다. 이 기능을 사용하여 렌더링에 영향을 주는 드라이버 문제를 신속하게 파악할 수 있습니다.

 이러한 모드 이외에 dxcap.exe는 그래픽 정보 캡처 또는 재생을 수행하지 않는 두 가지 기타 기능을 수행합니다.

 열거형 함수 (`-e`) 컴퓨터에 설치 된 UWP 앱에 대 한 세부 정보가 표시 됩니다. 이러한 세부 정보에는 UWP 앱에서 실행 파일을 식별 하는 appid 및 패키지 이름이 포함 됩니다. DXCap.exe를 사용하여 windows 스토어 앱에서 그래픽 정보를 캡처하려면 데스크톱 앱을 캡처할 때 사용한 실행 파일 이름 대신 패키지 이름과 appid를 사용합니다.

 정보 함수 (`-info)` 컴퓨터 및 캡처 Dll에 대 한 세부 정보가 표시 됩니다.

## <a name="examples"></a>예제

### <a name="capture-graphics-information-from-a-desktop-app"></a>데스크톱 앱에서 그래픽 정보 캡처
 사용 하 여 `-c` 그래픽 정보 캡처 하려는 앱을 지정 합니다.

```cmd
DXCap.exe -c BasicHLSL11.exe
```

 기본적으로 그래픽 정보 라는 파일에 기록 됩니다 `<appname>-<date>-<time>.vsglog`합니다. 사용 하 여 `-file` 를 기록할 다른 파일을 지정 합니다.

```cmd
DXCap.exe -file regression_test_12.vsglog -c BasicHLSL11.exe
```

 캡처할 앱에 대해 추가 명령줄 매개 변수를 지정하려면 앱 파일 이름 뒤에 해당 매개 변수를 포함합니다.

```cmd
DXCap.exe -c "C:\Program Files\Internet Explorer\iexplorer.exe" "www.fishgl.com"
```

 위 예제의 명령은 WebGL API를 사용하여 3D 콘텐츠를 렌더링하는 [www.fishgl.com](www.fishgl.com) 의 웹 페이지를 보는 동안 데스크톱 버전 Internet Explorer에서 그래픽 정보를 캡처합니다.

> [!NOTE]
> 앱 다음에 표시되는 명령줄 인수는 앱에 전달되므로 `-c` 옵션을 사용하기 전에 DXCap.exe용 인수를 지정해야 합니다.

### <a name="capture-graphics-information-from-a-uwp-app"></a>UWP 앱에서 그래픽 정보를 캡처하십시오.
 UWP 앱에서 그래픽 정보를 캡처할 수 있습니다.

```cmd
DXCap.exe -c Microsof.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe,AppexMaps
```

 Windows 데스크톱 앱에서 캡처를 사용 하 여 비슷합니다 DXCap.exe를 사용 하 여 UWP 앱에서 캡처할 하지만 대신 UWP 앱 패키지 이름 및 이름으로 식별 파일 이름으로 데스크톱 앱을 식별, 또는 패키지 내의 실행 파일의 id  캡처하십시오. 컴퓨터에 설치 된 UWP 앱을 식별 하는 방법을 알아보려면 쉽게 사용 하 여는 `-e` 수 DXCap.exe 사용 하 여 열거 해야 합니다.

```cmd
DXCap.exe -e
```

 원하는 앱을 찾기 위해 선택적 검색 문자열을 입력할 수 있습니다. 검색 문자열이 제공 되 면 DXCap.exe는 해당 패키지 이름, 앱 이름 또는 앱 Id 검색 문자열과 일치 하는 UWP 앱을 열거 합니다. 검색은 대/소문자를 구분합니다.

```cmd
DXCap.exe -e map
```

 위 명령은 "map"과 일치 하는 UWP 앱을 열거 출력은 다음과 같습니다.

 **Package "Microsoft.BingMaps":** **InstallDirectory: C:\Program Files\WindowsApps\Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe** **FullName         : Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe** **UserSID          : S-1-5-21-2127521184-1604012920-1887927527-5603533** **Name             : Microsoft.BingMaps** **Publisher        : CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US** **Version          : 2.1.2914.1734** **시작할 응용 프로그램:** **Id: AppexMaps** **Exe: C:\Program Files\WindowsApps\Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe\Map.exe** **IsWWA: 아니오** **(시작)를 AppSpec: DXCap.exe-c Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe,AppexMaps** 열거 된 각 앱에 대 한 출력의 마지막 줄에서 그래픽 정보 캡처를 사용할 수 있습니다 명령이 표시 됩니다.

### <a name="capture-specific-frames-or-frames-between-specific-times"></a>특정 프레임 또는 특정 시간 사이의 프레임 캡처
 사용 하 여 `-frame` 쉼표 및 범위를 사용 하 여 캡처하려는 프레임을 지정 하려면:

```cmd
DXCap.exe -frame 2,5,7-9,15 -c SimpleBezier11.exe
```

 또는 사용 하 여 `-period` 프레임을 캡처할 시간 범위 집합을 지정할 수 있습니다. 시간 범위는 초로 지정되며 여러 범위를 지정할 수 있습니다.

```cmd
DXCap.exe -period 2.1-5, 7.0-9.3 -c SimpleBezier11.exe
```

### <a name="capture-frames-interactively"></a>대화형으로 프레임 캡처
 사용 하 여 `-manual` 대화형으로 프레임을 캡처할 수 있습니다. 캡처를 시작하려면 Enter 키를 누릅니다. Enter 키를 다시 누르면 캡처가 중지됩니다.

```cmd
DXCap.exe -manual -c SimpleBezier11.exe
```

### <a name="play-back-a-graphic-log-file"></a>그래픽 로그 파일을 재생
 사용 하 여 `-p` 이전에 캡처한 그래픽 로그 파일을 재생 하도록 합니다.

```cmd
DXCap.exe -p regression_test_12.vsglog
```

 가장 최근에 캡처한 그래픽 로그를 재생하려면 파일 이름을 생략합니다.

```cmd
DXCap.exe -p
```

### <a name="play-back-in-raw-mode"></a>원시 모드에서 재생
 사용 하 여 `-rawmode` 발생 하는 대로 정확 하 게 캡처된 명령을 재생 하려면. 일반 재생 시 특정 명령은 에뮬레이트됩니다. 예를 들어 전체 화면 앱에서 캡처한 그래픽 로그 파일이 창에서 재생됩니다. 그러나 원시 모드를 사용하도록 설정하면 동일한 파일이 전체 화면에서 재생됩니다.

```cmd
DXCap.exe -p regression_test_12.vsglog -rawmode
```

### <a name="play-back-using-warp-or-a-hardware-device"></a>WARP 또는 하드웨어 장치를 사용하여 재생
 하드웨어 장치에서 캡처된 그래픽 로그 파일 재생 시 WARP를 사용하거나 WARP에서 캡처된 로그 재생 시 하드웨어 장치를 사용하도록 강제 지정할 수 있습니다. 사용 하 여 `-warp` WARP를 사용 하 여 다시 재생 합니다.

```cmd
DXCap.exe -p regression_test_12.vsglog -warp
```

 사용 하 여 `-hw` 하드웨어를 사용 하 여 다시 재생 합니다.

```cmd
DXCap.exe -p regression_test_12.vsglog -hw
```

### <a name="validate-a-graphics-log-file-against-warp"></a>WARP에 대해 그래픽 로그 파일 유효성 검사
 유효성 검사 모드에서는 그래픽 로그 파일을 하드웨어와 WARP 둘 다에서 재생한 다음 해당 결과를 비교합니다. 따라서 드라이버에 의해 발생하는 렌더링 오류를 파악할 수 있습니다. WARP에 대해 그래픽 하드웨어의 올바른 동작 유효성을 검사하려면 -v를 사용합니다.

```cmd
DXCap.exe -v regression_test_12.vsglog
```

 비교되는 결과의 양을 줄이려면 유효성 검사에 대해 비교할 명령 하위 집합을 지정할 수 있습니다. 그러면 다른 명령은 무시됩니다. 결과를 비교할 명령을 지정하려면 -examine을 사용합니다.

```cmd
DXCap.exe -v regression_test_12.vsglog -examine present,draw,copy,clear
```

### <a name="convert-a-graphics-log-file-to-pngs"></a>그래픽 로그 파일을 PNG로 변환
 그래픽 로그 파일에서 프레임을 확인하거나 분석하려는 경우 DXCap.exe에서 캡처한 프레임을 .png(이동식 네트워크 그래픽) 이미지 파일로 저장할 수 있습니다. 사용 하 여 `-screenshot` 에 출력 하려면 재생 모드에서 캡처된 프레임.png 파일로.

```cmd
DXCap.exe -p BasicHLSL11.vsglog -screenshot
```

 사용 하 여 `-frame` 사용 하 여 `-screenshot` 출력 하려는 프레임을 지정 합니다.

```cmd
DXCap.exe -p BasicHLSL11.vsglog -screenshot -frame 5, 7-9
```

### <a name="convert-a-graphics-log-file-to-xml"></a>그래픽 로그 파일을 XML로 변환
 FindStr, XSLT 등의 익숙한 도구를 사용하여 그래픽 로그를 처리 및 분석하려는 경우 DXCap.exe에서 그래픽 로그 파일을 XML로 변환할 수 있습니다. 사용 하 여 `-toXML` 다시 재생 로그를 재생 하는 대신 XML로 변환 하는 모드입니다.

```cmd
DXCap.exe -p regression_test_12.vsglog -toXML
```

 기본적으로 XML 출력은 그래픽 로그와 이름이 같은 파일에 기록되지만 확장명이 .xml로 지정됩니다. XML 파일의 이름은 위의 예에서 **regression_test_12.xml**합니다. XML 파일을 다른 이름을 지정 하려면 지정 후 `-toXML`합니다.

```cmd
DXCap.exe -p regression_test_12.vsglog -toXML temp.xml
```

 결과 파일에는 다음과 같은 XML이 포함됩니다.

```xml
<Moment value="67"/>
<Method name="CreateDXGIFactory1" >
    <Return type="HRESULT" value="S_OK" />
    <Parameter name="riid" type="IID" value="770AAE78-F26F-4DBA-A829-253C83D1B387" />
    <Parameter name="ppFactory" type="void" handle="1" isOutput="true" />
</Method>

<Moment value="167"/>
<Method name="D3D11CreateDevice" >
    <Return type="HRESULT" value="S_OK" />
    <Parameter name="pAdapter" type="IDXGIAdapter" handle="34" />
    <Parameter name="DriverType" type="D3D_DRIVER_TYPE" value="D3D_DRIVER_TYPE_UNKNOWN" />
    <Parameter name="Software" type="HMODULE" value="pointer" />
    <Parameter name="Flags" type="UINT" value="0" />
    <Parameter name="pFeatureLevels" type="D3D_FEATURE_LEVEL" arrSize="1" >
        <Element value="D3D_FEATURE_LEVEL_11_0" />
    </Parameter>
    <Parameter name="FeatureLevels" type="UINT" value="1" />
    <Parameter name="SDKVersion" type="UINT" value="7" />
    <Parameter name="ppDevice" type="ID3D11Device" handle="35" isOutput="true" />
    <Parameter name="pFeatureLevel" type="D3D_FEATURE_LEVEL" value="D3D_FEATURE_LEVEL_11_0" isOutput="true" />
    <Parameter name="ppImmediateContext" type="ID3D11DeviceContext" value="nullptr" isOutput="true" />
</Method>
```

## <a name="requirements"></a>요구 사항