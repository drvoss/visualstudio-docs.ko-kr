---
title: 파일 이름 확장명에 대 한 동사 등록 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- verbs, registering
ms.assetid: 81a58e40-7cd0-4ef4-a475-c4e1e84d6e06
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dbd97310163a4eb3ae5502c6341dc73322ca653d
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65685275"
---
# <a name="registering-verbs-for-file-name-extensions"></a>파일 이름 확장명에 대한 동사 등록
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

응용 프로그램의 파일 이름 확장명을 연결에는 일반적으로 사용자가 파일을 두 번 클릭할 때 발생 하는 기본 작업이 있습니다. 이 작업 동사 예를 들어 열기 작업에 해당 하는 연결 된 것이 좋습니다.  
  
 HKEY_CLASSES_ROOT에 있는 셸 키를 사용 하 여 확장에 대 한 프로그래밍 방식 식별자 (ProgID)을 사용 하 여 연결 된 동사를 등록할 수 있습니다\\*progid*\shell 합니다. 자세한 내용은 [파일 형식](https://msdn.microsoft.com/library/windows/desktop/cc144148\(v=vs.85\).aspx)합니다.  
  
## <a name="registering-standard-verbs"></a>표준 동사 등록  
 운영 체제는 다음 표준 동사를 인식합니다.  
  
- 열기  
  
- 편집  
  
- 재생  
  
- 용  
  
- 미리 보기  
  
  가능 하면 표준 동사를 등록 합니다. 가장 일반적인 선택은 Open 동사입니다. 지우기 차이가 파일을 열고 파일을 편집 하는 경우에 편집 동사를 사용 합니다. 예를 들어,.htm 파일을 열면 표시 브라우저에서 HTML 편집기를 시작 하는.htm 파일을 편집 하는 반면 합니다. 표준 동사는 운영 체제 로캘을 사용 하 여 지역화 되어 있습니다.  
  
> [!NOTE]
> 표준 동사를 등록할 때 열린 키에 대 한 기본값을 설정 하지 마십시오. 메뉴의 표시 문자열을 포함 하는 기본값입니다. 운영 체제 표준 동사에 대 한이 문자열을 제공합니다.  
  
 프로젝트 파일의 새 인스턴스를 시작 하려면 등록 해야 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 경우 사용자는 파일을 엽니다. 다음 예제에 대 한 표준 동사 등록을 [!INCLUDE[csprcs](../includes/csprcs-md.md)] 프로젝트입니다.  
  
```  
[HKEY_CLASSES_ROOT\.csproj]  
@="VisualStudio.csproj.8.0"  
  
[HKEY_CLASSES_ROOT\.csproj\OpenWithList]  
[HKEY_CLASSES_ROOT\.csproj\OpenWithList\VSLauncher.exe]  
@=""  
  
[HKEY_CLASSES_ROOT\.csproj\OpenWithProgids]  
"VisualStudio.csproj.8.0"=""  
  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe]  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell]  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell\Open]  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell\Open\Command]  
@="C:\\Program Files\\Common Files\\Microsoft Shared\\MSEnv\\VSLauncher.exe \"%1\""  
  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0]  
@="C# Project file"  
  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\DefaultIcon]  
@="C:\\VisualStudioPath\\VC#\\VCSPackages\\csproj.dll,0"  
  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell]  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell\Open]  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell\Open\Command]  
@="\"C:\\Program Files\\Common Files\\Microsoft Shared\\MSEnv\\VSLauncher.exe\" \"%1\""  
```  
  
 기존 인스턴스에 파일을 열려고 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], DDEEXEC 키를 등록 합니다. 다음 예제에 대 한 표준 동사 등록을 [!INCLUDE[csprcs](../includes/csprcs-md.md)] .cs 파일입니다.  
  
```  
[HKEY_CLASSES_ROOT\.cs]  
@="VisualStudio.cs.8.0"  
  
[HKEY_CLASSES_ROOT\.cs\OpenWithList]  
[HKEY_CLASSES_ROOT\.cs\OpenWithList\devenv.exe]  
@=""  
  
[HKEY_CLASSES_ROOT\.cs\OpenWithProgids]  
"VisualStudio.cs.8.0"=""  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0]  
@="C# Source file"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\DefaultIcon]  
@="C:\\VisualStudioPath\\VC#\\VCSPackages\\csproj.dll,1"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell]  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open]  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\Command]  
@="\"C:\\VisualStudioPath\\Common7\\IDE\\devenv.exe\" /dde \"%1\""  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec]  
@="Open(\"%1\")"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec\Application]  
@="VisualStudio.8.0"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec\Topic]  
@="system"  
```  
  
## <a name="setting-the-default-verb"></a>기본 동사를 설정합니다.  
 기본 동사에는 사용자가 Windows 탐색기에서 파일을 두 번 클릭할 때 실행 되는 동작입니다. 기본 동사는를 HKEY_CLASSES_ROOT에 대 한 기본 값으로 지정 된 동사\\*progid*\Shell 키입니다. 값은 지정 하지 않으면 기본 동사가 인지를 HKEY_CLASSES_ROOT에 지정 된 첫 번째 동사\\*progid*\Shell 키 목록입니다.  
  
> [!NOTE]
> Side-by-side-배포에서 확장의 기본 동사가 변경 하려는 경우 설치 및 제거에 미치는 영향을 고려 합니다. 설치 하는 동안 원래 기본 값을 덮어씁니다.  
  
## <a name="see-also"></a>참고 항목  
 [병렬 파일 연결 관리](../extensibility/managing-side-by-side-file-associations.md)
