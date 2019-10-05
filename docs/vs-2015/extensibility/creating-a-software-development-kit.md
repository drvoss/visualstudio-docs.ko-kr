---
title: 소프트웨어 개발 키트 만들기 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 8496afb4-1573-4585-ac67-c3d58b568a12
caps.latest.revision: 55
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 791400746247d71c06e133d10469132f38544b21
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65689986"
---
# <a name="creating-a-software-development-kit"></a>소프트웨어 개발 키트 만들기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

소프트웨어 개발 키트 (SDK)은 Visual Studio에서 단일 항목으로 참조할 수 있는 Api 컬렉션입니다. 합니다 **참조 관리자** 대화 상자는 프로젝트에 관련 된 모든 Sdk를 나열 합니다. 프로젝트에 SDK를 추가 하면 Api는 Visual Studio에서 사용할 수 있습니다.  
  
 Sdk는 다음과 같은 두 종류가 있습니다.  
  
- 플랫폼 Sdk는 플랫폼용 앱 개발을 위한 필수 구성 요소입니다. 예를 들어 합니다 [!INCLUDE[win81](../includes/win81-md.md)] 개발에 SDK가 필요 [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] 앱.  
  
- 확장 Sdk는 선택적 구성 요소는 플랫폼을 확장 하지만 해당 플랫폼용 앱 개발을 위한 필수는 아닙니다.  
  
  다음 섹션에서는 Sdk 및 플랫폼 SDK를 만드는 방법의 일반적인 인프라를 설명 하 고 확장 SDK.  
  
- [플랫폼 Sdk](#PlatformSDKs)  
  
- [확장 Sdk](#ExtensionSDKs)  
  
## <a name="PlatformSDKs"></a> 플랫폼 Sdk  
 플랫폼 Sdk 플랫폼용 앱을 개발 해야 합니다. 예를 들어 합니다 [!INCLUDE[win81](../includes/win81-md.md)] SDK에 대 한 앱을 개발 해야 [!INCLUDE[win81](../includes/win81-md.md)]합니다.  
  
### <a name="installation"></a>설치  
 HKLM\Software\Microsoft\Microsoft Sdk에서 모든 플랫폼 Sdk를 설치할\\[TPV] [TPI] \v\\ @InstallationFolder [SDK 루트] =. 따라서는 [!INCLUDE[win81](../includes/win81-md.md)] HKLM\Software\Microsoft\Microsoft SDKs\Windows\v8.1에서 SDK가 설치 되어 있습니다.  
  
### <a name="layout"></a>레이아웃  
 플랫폼 Sdk에는 다음 레이아웃을 제공 됩니다.  
  
```  
\[InstallationFolder root]  
            SDKManifest.xml  
            \References  
                  \[config]  
                        \[arch]  
            \DesignTime  
                  \[config]  
                        \[arch]  
```  
  
|노드|설명|  
|----------|-----------------|  
|참조 폴더|에 대해 코딩할 수 있는 Api를 포함 하는 이진 파일을 포함 합니다. 이러한 Windows 메타 데이터 (WinMD) 파일 또는 어셈블리에 포함할 수 있습니다.|  
|DesignTime 폴더|사전-run/디버깅 타임에만 필요한 파일이 포함 됩니다. XML 문서, 라이브러리, 헤더, 도구 상자 디자인 타임 이진 파일, MSBuild 아티팩트 등을 포함 될 수 있습니다 이러한<br /><br /> XML 문서와 마찬가지로 이상적으로 \DesignTime 폴더에 배치할 수 있지만 Visual Studio에서 참조 파일과 함께 배치할 참조에 대 한 XML 문서를 계속 합니다. 예를 들어, XML 문서에 대 한 참조 \References\\[구성]\\[arch]\sample.dll \References 됩니다\\[구성]\\[arch]\sample.xml, 및는 doc의 지역화 된 버전 \References됩니다\\[구성]\\[arch]\\[locale]\sample.xml 합니다.|  
|구성 폴더|만 세 개의 폴더가 있을 수 있습니다: 디버그, 소매 및 CommonConfiguration 합니다. SDK 소비자의 대상이 되는 구성에 관계 없이 동일한 SDK 파일 집합에 사용할 수 해야 하는 경우 SDK 작성자 CommonConfiguration에서 해당 파일을 배치할 수 있습니다.|  
|아키텍처 폴더|모든 지원 되는 아키텍처 폴더 존재할 수 있습니다. Visual Studio는 다음 아키텍처를 지원 합니다: x86, x64, ARM 및 neutral입니다. 참고: Win32, x86에 매핑되고 AnyCPU 중립에 매핑됩니다.<br /><br /> MSBuild는 플랫폼 Sdk \CommonConfiguration\neutral에만 찾습니다.|  
|SDKManifest.xml|이 파일은 Visual Studio SDK를 사용 해야 하는 방법을 설명 합니다. SDK 매니페스트에서 살펴봅니다 [!INCLUDE[win81](../includes/win81-md.md)]:<br /><br /> `<FileList             DisplayName = "Windows"             PlatformIdentity = "Windows, version=8.1"             TargetFramework = ".NET for Windows Store apps, version=v4.5.1; .NET Framework, version=v4.5.1"             MinVSVersion = "14.0">              <File Reference = "Windows.winmd">                <ToolboxItems VSCategory = "Toolbox.Default" />             </File> </FileList>`<br /><br /> **DisplayName:** 개체 브라우저 찾아보기 목록에 표시 하는 값입니다.<br /><br /> **PlatformIdentity:** 이 특성의 존재 여부 지시 로컬 Visual Studio 및 MSBuild SDK 플랫폼 SDK는 및에서 추가 된 참조를 복사 하면 안 됩니다.<br /><br /> **TargetFramework:** 이 값에 지정 된 대로 동일한 프레임 워크를 대상으로 하는 프로젝트는 되도록 Visual Studio에서이 특성은 사용 특성 SDK를 사용할 수 있습니다.<br /><br /> **MinVSVersion:** 이 특성에 적용 되는 Sdk만을 사용 하려면 Visual Studio에서 사용 됩니다.<br /><br /> **참조:** 이 특성 컨트롤을 포함 하는 참조만 지정 해야 합니다. 에 대 한 참조를 컨트롤에 포함 되는지 여부를 지정 하는 방법에 대 한 내용은 아래 참조 합니다.|  
  
## <a name="ExtensionSDKs"></a> 확장 Sdk  
 다음 섹션에서는 확장 SDK를 배포 하기 위해 수행 해야 합니다.  
  
### <a name="installation"></a>설치  
 확장 Sdk는 레지스트리 키를 지정 하지 않고 특정 사용자 또는 모든 사용자에 대해 설치할 수 있습니다. 모든 사용자에 대 한 SDK를 설치 하려면 다음 경로 사용 합니다.  
  
 `%Program Files%\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs`  
  
 사용자 고유의 설치의 경우 다음 경로 사용 합니다.  
  
 `%USERPROFILE%\AppData\Local\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs`  
  
 다른 위치를 사용 하려는 경우 두 가지 중 하나를 수행 해야 합니다.  
  
1. 레지스트리 키에서이 지정 합니다.  
  
     `HKLM\Software\Microsoft\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs\<SDKName>\<SDKVersion>\`  
  
     값이 있는 (기본값) 하위 키를 추가 하 고 `<path to SDK><SDKName><SDKVersion>`입니다.  
  
2. MSBuild 속성을 추가 `SDKReferenceDirectoryRoot` 프로젝트 파일에 있습니다. 이 속성의 값은 참조 하려는 확장 Sdk에는 디렉터리의 반으로 구분한 목록.  
  
### <a name="installation-layout"></a>설치 레이아웃  
 확장 Sdk 설치 레이아웃은:  
  
```  
\<ExtensionSDKs root>  
           \<SDKName>  
                 \<SDKVersion>  
                        SDKManifest.xml  
                        \References  
                              \<config>  
                                    \<arch>  
                        \Redist  
                              \<config>  
                                    \<arch>  
                        \DesignTime  
                               \<config>  
                                     \<arch>  
  
```  
  
1. \\< SDKName\>\\< SDKVersion\>: 이름 및 버전의 SDK가 SDK 루트 경로에 해당 폴더 이름은에서 파생 된 확장 합니다. MSBuild에서이 id를 사용 하 여 디스크에서 SDK를 찾을 수 및 Visual Studio에서이 id를 표시 합니다 **속성** 창 및 **참조 관리자** 대화 합니다.  
  
2. References 폴더: Api를 포함 하는 이진 파일. Windows 메타 데이터 (WinMD) 파일이 나 어셈블리 될 수 있습니다.  
  
3. Redist 폴더: 런타임/디버깅을 위해 필요 하 고 사용자의 응용 프로그램의 일부로 패키지 가져오기는 파일에 있습니다. \Redist 아래에 있는 모든 이진 파일을 배치할\\< config\>\\< arch\>, 이진 이름 고유성을 보장 하려면 다음 형식 이어야 하 고:  **\<회사 >.\< 제품 >. \<용도 >. \<확장 >** 합니다. 예: Microsoft.Cpp.Build.dll \Redist 아래에 있는 다른 Sdk (예: javascript, css, pri, xaml, png 및 jpg 파일)에서 파일 이름이 충돌할 수 있습니다 하는 이름 가진 모든 파일을 배치할\\< config\>\\< arch\> \\< sdkname\>\ XAML과 사용 하 여 연결 된 파일을 제외 하 고 제어 합니다. \Redist 아래 이러한 파일을 배치할\\< config\>\\< arch\>\\< componentname\>\\합니다.  
  
4. DesignTime 폴더:만 사전-run/디버깅에 필요한 파일 시간 및 사용자의 응용 프로그램의 일부분으로 패키지할 수 없습니다. XML 문서, 라이브러리, 헤더, 도구 상자 디자인 타임 이진 파일, MSBuild 아티팩트 등 될 수 있습니다. 네이티브 프로젝트를 사용 해야 합니다. 대상으로 하는 모든 SDK를 *SDKName*.props 파일입니다. 다음이 유형의 파일의 예제를 보여 줍니다.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <PropertyGroup>  
        <ExecutablePath>C:\Temp\ExecutablePath;$(ExecutablePath)</ExecutablePath>  
        <IncludePath>$(FrameworkSDKRoot)\..\v8.1\ExtensionSDKs\cppimagingsdk\1.0\DesignTime\CommonConfiguration\Neutral\include;$(IncludePath)</IncludePath>  
        <AssemblyReferencePath>C:\Temp\AssemblyReferencePath;(AssemblyReferencePath)</AssemblyReferencePath>  
        <LibraryPath>$(FrameworkSDKRoot)\..\v8.1\ExtensionSDKs\cppimagingsdk\1.0\DesignTime\Debug\ARM;$(LibraryPath)</LibraryPath>  
        <SourcePath>C:\Temp\SourcePath\X64;$(SourcePath)</SourcePath>  
        <ExcludePath>C:\Temp\ExcludePath\X64;$(ExcludePath)</ExcludePath>  
        <_PropertySheetDisplayName>DevILSDK, 1.0</_PropertySheetDisplayName>  
      </PropertyGroup>  
    </Project>  
  
    ```  
  
     XML 참조 문서는 참조 파일과 함께 배치 됩니다. 예를 들어,에 대 한 XML 참조 문서를 **\References\\< 구성\>\\< arch\>\sample.dll** 어셈블리가 **\References\\ < config\>\\< arch\>\sample.xml**, 해당 문서의 지역화 된 버전 이며 **\References\\< config\>\\< arch\>\\< 로캘\>\sample.xml**합니다.  
  
5. 구성 폴더: 세 개의 하위 폴더: 디버그, 소매 및 CommonConfiguration 합니다. SDK 소비자의 대상 구성에 관계 없이 동일한 SDK 파일 집합에 사용할 수 해야 하는 경우 SDK 작성자 CommonConfiguration에서 해당 파일을 배치할 수 있습니다.  
  
6. 아키텍처 폴더: 다음 아키텍처는 지원: x86, x64, ARM, neutral입니다. Win32, x86에 매핑되고 AnyCPU 중립에 매핑됩니다.  
  
### <a name="sdkmanifestxml"></a>SDKManifest.xml  
 이 파일은 Visual Studio SDK를 사용 해야 하는 방법을 설명 합니다. 다음은 예제입니다.  
  
```  
<FileList>  
DisplayName = "My SDK"  
ProductFamilyName = "My SDKs"  
TargetFramework = ".NETCore, version=v4.5.1; .NETFramework, version=v4.5.1"  
MinVSVersion = "14.0"  
MaxPlatformVersion = "8.1"  
AppliesTo = "WindowsAppContainer + WindowsXAML"  
SupportPrefer32Bit = "True"  
SupportedArchitectures = "x86;x64;ARM"  
SupportsMultipleVersions = "Error"  
CopyRedistToSubDirectory = "."  
DependsOn = "SDKB, version=2.0"  
MoreInfo = "https://msdn.microsoft.com/MySDK">  
<File Reference = "MySDK.Sprint.winmd" Implementation = "XNASprintImpl.dll">  
<Registration Type = "Flipper" Implementation = "XNASprintFlipperImpl.dll" />  
<Registration Type = "Flexer" Implementation = "XNASprintFlexerImpl.dll" />  
<ToolboxItems VSCategory = "Toolbox.Default" />  
</File>  
</FileList>  
```  
  
 다음은 파일의 요소를 제공합니다.  
  
1. 표시 이름: 참조 관리자, 솔루션 탐색기, 개체 브라우저 및 Visual Studio에 대 한 사용자 인터페이스의 다른 위치에 표시 되는 값입니다.  
  
2. ProductFamilyName: 전체 SDK 제품 이름입니다. 예를 들어를 [!INCLUDE[winjs_long](../includes/winjs-long-md.md)] SDK "Microsoft.WinJS" SDK 제품 패밀리의 동일한 제품군에 속하는 "Microsoft.WinJS.1.0" 및 "Microsoft.WinJS.2.0" 라고 합니다. 이 특성에는 Visual Studio 및 MSBuild 해당 연결을 만들 수 있습니다. 이 특성이 없는 경우 SDK 이름 제품 제품군 이름으로 사용 됩니다.  
  
3. FrameworkIdentity: 사용 중인 앱의 매니페스트에이 특성의 값을 추가할 하나 이상의 Windows 구성 요소 라이브러리 종속성을 지정 합니다. 이 특성은 Windows 구성 요소 라이브러리에만 적용 됩니다.  
  
4. TargetFramework: 참조 관리자 및 도구 상자에서 사용할 수 있는 Sdk를 지정 합니다. 예를 들어 이것은 대상 프레임 워크 모니커의 목록을 세미콜론으로 구분 된 ".NET Framework, 버전 = v2.0;.NET Framework, 버전 v4.5.1 =". 여러 버전의 동일한 대상 프레임 워크의 지정 된 경우 참조 관리자는 필터링 용도로 지정된 된 가장 낮은 버전을 사용 합니다. 예를 들어 경우 ".NET Framework, 버전 v2.0; = 버전,.NET Framework v4.5.1 ="를 지정 하면 참조 관리자를 사용 하 여 ".NET Framework, 버전 v2.0 =". 특정 대상 프레임 워크 프로필을 지정 된 경우 해당 프로필에만 필터링 목적으로 하는 것에 대 한 참조 매니저가 사용 됩니다. 예를 들어, "Silverlight 버전 v4.0, 프로필 = WindowsPhone =" 지정 된 참조 관리자에만 Windows Phone 프로필에 대 한 필터 전체 Silverlight 4.0 Framework를 대상으로 프로젝트 참조 관리자에서 SDK를 표시 하지 않습니다.  
  
5. MinVSVersion: 최소 Visual Studio 버전입니다.  
  
6. MaxPlatformVerson: 최대 대상 플랫폼 버전 확장 SDK가 작동 하지는 플랫폼 버전을 지정 하는 것 같습니다. Microsoft Visual 예를 들어, C++ 런타임 패키지 v11.0만 Windows 8 프로젝트에서 참조 해야 합니다. 따라서 Windows 8 프로젝트의 MaxPlatformVersion 8.0입니다. 즉, Microsoft Visual 필터링 참조 관리자 C++ Windows 8.1 프로젝트의 경우 런타임 패키지 및 MSBuild 오류를 throw 경우는 [!INCLUDE[win81](../includes/win81-md.md)] 프로젝트에서 참조 합니다. 참고:이 요소는 지원부터 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]합니다.  
  
7. AppliesTo: 적용 되는 Visual Studio 프로젝트 유형을 지정 하 여 참조 관리자에서 사용할 수 있는 Sdk를 지정 합니다. 9 개의 값이 인식 됩니다. WindowsAppContainer VisualC, VB, CSharp, WindowsXAML, JavaScript, 관리 및 네이티브 합니다. SDK 작성자가 사용할 수 있습니다 하 고 ("+'), 또는 ("&#124;")가 아닌 ("! ") 정확 하 게 SDK에 적용 되는 프로젝트 형식의 범위를 지정 하는 연산자입니다.  
  
     프로젝트를 식별 하는 WindowsAppContainer [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] 앱.  
  
8. SupportPrefer32Bit: 지원 되는 값은 "True" 및 "False"입니다. 기본값은 "True"입니다. 값을 "False"로 설정 하는 경우 MSBuild에 대 한 오류를 반환 하는 [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] 프로젝트 (또는 데스크톱 프로젝트에 대 한 경고) SDK를 참조 하는 프로젝트에 사용 된 Prefer32Bit 있으면 됩니다. Prefer32Bit에 대 한 자세한 내용은 참조 하세요. [빌드 페이지, 프로젝트 디자이너 (C#)](../ide/reference/build-page-project-designer-csharp.md) 하거나 [컴파일 페이지, 프로젝트 디자이너 (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md)합니다.  
  
9. SupportedArchitectures: 세미콜론으로 구분한 목록 SDK에서 지 원하는 아키텍처입니다. MSBuild 대상된 SDK 아키텍처를 사용 하는 프로젝트에서 지원 되지 않는 경우 경고를 표시 합니다. 이 특성을 지정 하지 않으면 MSBuild는이 유형의 경고를 표시 되지 않습니다.  
  
10. SupportsMultipleVersions:이 특성 설정 된 경우 **오류** 또는 **경고**, 동일한 프로젝트 같은 SDK 제품군의 여러 버전을 참조할 수 없습니다는 MSBuild 나타냅니다. 이 특성이 존재 하지 않거나로 설정 된 경우 **허용**, MSBuild는 이러한 유형의 오류 또는 경고가 표시 되지 않습니다.  
  
11. AppX: 디스크에서 Windows 구성 요소 라이브러리에 대 한 앱 패키지의 경로 지정합니다. 이 값은 로컬 디버깅 하는 동안 Windows 구성 요소 라이브러리의 등록 구성 요소에 전달 됩니다. 파일 이름에 대 한 명명 규칙은  **\<회사 >.\< 제품 >. \<아키텍처 >. \<구성 >. \<버전 >.appx**합니다. 구성 및 아키텍처는 Windows 구성 요소 라이브러리를 적용 하지는 선택적 특성 이름과 특성 값입니다. 이 값은 Windows 구성 요소 라이브러리에만 적용 됩니다.  
  
12. CopyRedistToSubDirectory: 앱 패키지 루트에 상대적인 \redist 폴더 아래에 있는 파일을 복사할 위치 지정 (즉, 합니다 **패키지 위치** 앱 패키지 만들기 마법사에서 선택) 및 런타임 레이아웃 루트. 기본 위치는 앱 패키지 및 F5 레이아웃의 루트입니다.  
  
13. DependsOn: 이 SDK가 종속 된 Sdk를 정의 하는 SDK id의 목록입니다. 이 특성은 참조 관리자의 세부 정보 창에 나타납니다.  
  
14. MoreInfo: 도움말 및 자세한 정보를 제공 하는 웹 페이지에 대 한 URL입니다. 이 값은 참조 관리자의 오른쪽 창에서 자세한 정보 링크에 사용 됩니다.  
  
15. 등록 유형: 앱 매니페스트에서 WinMD 등록 지정 되며 누구 구현이 DLL는 네이티브 WinMD에 대 한 필요 합니다.  
  
16. 파일 참조: 네이티브 Winmd 또는 컨트롤을 포함 하는 참조만 지정 합니다. 참조를 컨트롤에 포함 되는지 여부를 지정 하는 방법에 대 한 정보를 참조 하세요 [도구 상자 항목의 위치 지정](#ToolboxItems) 아래.  
  
## <a name="ToolboxItems"></a> 도구 상자 항목의 위치를 지정합니다.  
 SDKManifest.xml 스키마의 ToolBoxItems 요소 플랫폼 및 확장 Sdk의 도구 상자 항목의 위치와 범주를 지정합니다. 다음 예제에서는 서로 다른 위치를 지정 하는 방법을 보여 줍니다. WinMD 또는 DLL에 대 한 참조에 적용 됩니다.  
  
1. 도구 상자 기본 범주에 컨트롤을 배치 합니다.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Toolbox.Default"/>       
    </File>  
    ```  
  
2. 특정 범주 이름으로 컨트롤을 배치 합니다.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory= "MyCategoryName"/>  
    </File>  
    ```  
  
3. 특정 범주 이름 아래에서 컨트롤을 배치 합니다.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Graph">  
        <ToolboxItems/>  
        <ToolboxItems VSCategory = "Data">  
        <ToolboxItems />  
    </File>  
    ```  
  
4. Blend 및 Visual Studio에서 다양 한 범주 이름 아래에서 컨트롤을 배치 합니다.  
  
    ```  
    // Blend accepts a slightly different structure for the category name because it allows a path rather than a single category.  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Graph" BlendCategory = "Controls/sample/Graph">   
        <ToolboxItems />  
    </File>  
    ```  
  
5. Blend 및 Visual Studio에서 다르게 특정 컨트롤을 열거 합니다.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Graph">  
        <ToolboxItems/>  
        <ToolboxItems BlendCategory = "Controls/sample/Graph">  
        <ToolboxItems/>  
    </File>  
    ```  
  
6. 특정 컨트롤을 열거 하 고 모든 컨트롤 그룹 또는 Visual Studio 일반 경로 아래에 배치 합니다.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Toolbox.Common">  
        <ToolboxItems />  
        <ToolboxItems VSCategory = "Toolbox.All">  
        <ToolboxItems />  
    </File>  
    ```  
  
7. 특정 컨트롤을 열거 하 고 없으면 ChooseItems의 특정 집합에만 표시 도구 상자에 있는 것입니다.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Toolbox.ChooseItemsOnly">  
        <ToolboxItems />  
    </File>  
    ```  
  
## <a name="see-also"></a>참고 항목  
 [연습: 사용 하 여 SDK 만들기C++](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)   
 [연습: 사용 하 여 SDK 만들기 C# 또는 Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [프로젝트의 참조 관리](../ide/managing-references-in-a-project.md)
