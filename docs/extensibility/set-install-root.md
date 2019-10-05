---
title: VSIX v3 사용 하 여 확장 폴더 외부에 설치 | Microsoft Docs
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 913c3745-8aa9-4260-886e-a05aecfb2225
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2d5fc36c1244edd0988b6b76f8106020369cd90b
ms.sourcegitcommit: da4079f5b6ec884baf3108cbd0519d20cb64c70b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/12/2019
ms.locfileid: "67852208"
---
# <a name="install-outside-the-extensions-folder"></a>확장 폴더 외부에 설치

(버전 3) 확장 자산을 Visual Studio 2017 및 VSIX v3을 사용 하 여 시작 하는 확장 폴더 외부에서 설치할 수 있습니다. 현재 다음 위치 (여기서 [INSTALLDIR]에 매핑되는 Visual Studio 인스턴스의 설치 디렉터리)는 올바른 설치 위치로 사용 됩니다.

* [INSTALLDIR]\MSBuild
* [INSTALLDIR]\Xml\Schemas
* [INSTALLDIR]\Common7\IDE\PublicAssemblies
* [INSTALLDIR]\Licenses
* [INSTALLDIR]\Common7\IDE\ReferenceAssemblies
* [INSTALLDIR]\Common7\IDE\RemoteDebugger
* [INSTALLDIR] \Common7\IDE\VC\VCTargets (만 Visual Studio 2017에 대 한 지원 되는; Visual Studio 2019에 대 한 사용 되지 않는 이상)

> [!NOTE]
> VSIX 형식은 Visual Studio 설치 폴더 구조 외에 설치 하도록 허용 하지 않습니다. 

이러한 디렉터리에 설치를 지원 하기 위해 VSIX "인스턴스별 컴퓨터별" 설치 되어야 합니다. 이 extension.vsixmanifest 디자이너에서 "모든 사용자" 확인란을 선택 하 여 활성화할 수 있습니다.

![모든 사용자를 확인 합니다.](media/check-all-users.png)

## <a name="how-to-set-the-installroot"></a>InstallRoot를 설정 하는 방법

설치 디렉터리를 설정 하려면 사용할 수 있습니다 합니다 **속성** Visual Studio의 창. 예를 들어, 설정할 수 있습니다는 `InstallRoot` 위의 위치 중 하나에 대 한 프로젝트의 속성:

![설치 루트 속성](media/install-root-properties.png)

일부 메타 데이터에 해당 요소에 추가이 `ProjectReference` VSIX 프로젝트의.csproj 파일 내에서 속성:

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
        <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
        <Name>ClassLibrary1</Name>
        <InstallRoot>PublicAssemblies</InstallRoot>
 </ProjectReference>
```

> [!NOTE]
> 원하는 경우.csproj 파일을 직접 편집할 수 있습니다.

## <a name="how-to-set-a-subpath-under-the-installroot"></a>InstallRoot 아래의 하위 경로 설정 하는 방법

하위 경로 아래에 설치 하려는 경우는 `InstallRoot`를 설정 하 여 수행할 수는 `VsixSubPath` 속성 처럼는 `InstallRoot` 속성입니다. 예를 들어 한다면 우리의 프로젝트 참조의 출력을 설치 하려면 ' [INSTALLDIR]\MSBuild\MyCompany\MySDK\1.0'. 속성 디자이너를 사용 하 여이 작업을 쉽게 수행할 수 했습니다.

![하위 집합 경로](media/set-subpath.png)

해당.csproj 변경 내용이 다음과 같이 표시 됩니다.

```xml
<ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
       <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
       <Name>ClassLibrary1</Name>
       <InstallRoot>MSBuild</InstallRoot>
       <VSIXSubPath>MyCompany\MySDK\1.0</VSIXSubPath>
</ProjectReference>
```

## <a name="extra-information"></a>추가 정보

디자이너 속성 변경 내용을 이상의 프로젝트 참조에 적용 설정할 수 있습니다는 `InstallRoot` 프로젝트에도 내부 항목에 대 한 메타 데이터 (위에서 설명한 동일한 메서드를 사용 하 여).
