---
title: 격리 셸의 요소 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode
ms.assetid: f8d68c3d-9134-4a8f-b566-485956cd321e
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3a95b7da718f050357f6ecd79c90c389dd6085d5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68204609"
---
# <a name="elements-of-the-isolated-shell"></a>격리 셸의 요소
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

레지스트리 설정, 런타임 설정 및 격리 셸 응용 프로그램 및.vsct,.pkgdef, and.pkgundef 파일의 응용 프로그램 진입점을 수정할 수 있습니다.  
  
## <a name="registry-settings"></a>레지스트리 설정  
 .pkgdef 및.pkgundef 파일 격리 셸 응용 프로그램에 대 한 레지스트리 설정을 수정 합니다. 응용 프로그램을 실행 하는 경우 레지스트리 설정은 다음 순서 대로 정의 됩니다.  
  
 응용 프로그램을 실행 하는 경우 레지스트리 설정은 다음 순서 대로 정의 됩니다.  
  
1. 응용 프로그램에 대 한 레지스트리 키가 만들어집니다.  
  
2. 레지스트리에 지정 된 키 및 항목을 정의 하 여 응용 프로그램의.pkgdef 파일에서 업데이트 됩니다.  
  
3. 응용 프로그램의 일부인 모든 패키지에 대 한 레지스트리는 해당 패키지의.pkgdef 파일에서 업데이트 됩니다. 각 패키지는 $RootKey$ \Packages 하 여 응용 프로그램의.pkgdef 파일에 정의 된\\{0}*vsPackageGuid*} 패키지에 대 한 키입니다.  
  
4. AppEnvConfig.pkgdef와에서 BaseConfig.pkgdef 레지스트리 업데이트 되는 *Visual Studio SDK 설치 경로*\Common7\IDE\ShellExtensions\Platform 디렉터리. 이러한 파일은 Visual Studio의 일부 및도 Visual Studio Shell (격리 모드) 재배포 가능 패키지의 일부입니다.  
  
5. 레지스트리에 지정 된 키 및 항목을 제거 하 여 응용 프로그램의.pkgundef 파일에서 업데이트 됩니다.  
  
## <a name="run-time-settings"></a>런타임 설정  
 격리 셸 응용 프로그램을 시작 하는 경우 Visual Studio shell의 시작 진입점을 호출 합니다. 응용 프로그램 설정에는 응용 프로그램이 시작 되 면 다음과 같이 정의 됩니다.  
  
1. Visual Studio shell 특정 키에 대 한 응용 프로그램 레지스트리를 확인합니다. 키에 대 한 설정을 시작 진입점에 대 한 호출에 지정 되어 있으면 해당 값 레지스트리 값을 재정의 합니다.  
  
2. 레지스트리 나 항목 지점 설정의 값을 지정 하는 매개 변수 경우 설정의 기본값이 사용 됩니다.  
  
   명령줄에서 응용 프로그램을 시작 하면 모든 명령줄 스위치는 Devenv를 동일한 방식으로 처리 하는 Visual Studio shell에 전달 됩니다. Devenv 스위치에 대 한 자세한 내용은 참조 하십시오 [Devenv 명령줄 스위치](../ide/reference/devenv-command-line-switches.md) 하 고 [VSPackage 개발을 위한 Devenv 명령줄 스위치](../extensibility/devenv-command-line-switches-for-vspackage-development.md)합니다. 명령줄 스위치에 대 한 패키지를 등록 하는 방법에 대 한 자세한 내용은 참조 하세요. [명령줄 스위치 추가](../extensibility/adding-command-line-switches.md)합니다.  
  
## <a name="the-start-entry-point"></a>시작 진입점  
 Appenvstub.dll 파일 격리 셸 액세스에 대 한 진입점을 포함 합니다. 응용 프로그램이 시작 되 면 시작 항목 Appenvstub.dll 지점을 호출 합니다.  
  
 시작 진입점에 전달 되는 마지막 매개 변수 값을 변경 하 여 응용 프로그램의 동작을 변경할 수 있습니다. 자세한 내용은 [격리 셸 진입점 매개 변수 (C++)](../extensibility/isolated-shell-entry-point-parameters-cpp.md)합니다.  
  
## <a name="the-vsct-file"></a>합니다. Vsct 파일  
 .Vsct 파일을 응용 프로그램에서 사용할 수는 표준 Visual Studio UI 요소를 지정할 수 있습니다. 자세한 내용은 참조 하세요. [합니다. Vsct 파일](../extensibility/modifying-the-isolated-shell-by-using-the-dot-vsct-file.md)합니다.  
  
## <a name="the-pkgundef-file"></a>합니다. Pkgundef 파일  
 응용 프로그램 Visual Studio가 이미 설치 된 컴퓨터에 설치 될 때 응용 프로그램에 대 한 Visual Studio 레지스트리 항목의 복사본이 만들어집니다. 기본적으로 응용 프로그램에서는 이미 컴퓨터에 설치 되는 Vspackage를 사용 합니다. .Pkgundef 파일에는 응용 프로그램에서 Visual Studio 셸 또는 확장의 특정 요소를 제거 하기 위해 레지스트리 항목을 제외할 수 있습니다. 자세한 내용은 참조 하세요. [합니다. Pkgundef 파일](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md)합니다.  
  
 .Pkgundef 파일에는 응용 프로그램에서 Visual Studio 셸 또는 확장의 특정 요소를 제거 하기 위해 레지스트리 항목을 제외할 수 있습니다. 자세한 내용은 참조 하세요. [합니다. Pkgundef 파일](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md)합니다.  
  
 패키지를 제외할 수 있습니다 하는 Guid의 집합에 나와 [Visual Studio 기능의 패키지 Guid](../extensibility/package-guids-of-visual-studio-features.md)합니다.  
  
## <a name="the-pkgdef-file"></a>합니다. Pkgdef 파일  
 .Pkgdef 파일에는 응용 프로그램을 설치할 때 설정 되는 응용 프로그램에 대 한 레지스트리 항목을 정의할 수 있습니다. Visual Studio shell을 사용 하는 레지스트리 항목의 목록 및.pkgdef 파일에 대 한 설명을 참조 하세요. [합니다. Pkgdef 파일](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)합니다.  
  
## <a name="substitution-strings"></a>대체 문자열  
 .Pkgdef 및.pkgundef 파일에 사용 되는 대체 문자열에 나열 된 [대체 문자열에 사용 됩니다. Pkgdef 및 합니다. Pkgundef 파일](../extensibility/substitution-strings-used-in-dot-pkgdef-and-dot-pkgundef-files.md)합니다.  
  
## <a name="other-settings"></a>기타 설정  
 격리 셸 응용 프로그램 Microsoft.VisualStudio.GraphModel.dll에 의존 하는 경우 격리 셸 응용 프로그램의.config 파일에 다음 바인딩 리디렉션을 추가 해야 합니다.  
  
```  
<dependentAssembly>  
    <assemblyIdentity name="Microsoft.VisualStudio.GraphModel" publicKeyToken="b03f5f7f11d50a3a" culture="neutral" />  
    <bindingRedirect oldVersion="11.0.0.0" newVersion="12.0.0.0"/>  
</dependentAssembly>  
  
```
