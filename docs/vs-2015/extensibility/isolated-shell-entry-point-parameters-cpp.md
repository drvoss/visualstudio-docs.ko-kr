---
title: 격리 셸 진입점 매개 변수 (C++) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Shell [Visual Studio], isolated mode%2C Start entry point
- Visual Studio shell, isolated mode%2C Start entry point
ms.assetid: 18f4b18b-2173-4afa-ba0a-42fe33e61118
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9e736343212c4bf6acd833f5740b996c6c032c3f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63439815"
---
# <a name="isolated-shell-entry-point-parameters-c"></a>격리 셸 진입점 매개 변수 (C++)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 셸 기반 응용 프로그램을 시작 하는 경우 Visual Studio shell의 시작 진입점을 호출 합니다. 셸 시작 진입점에 대 한 호출에서 다음 설정은 재정의할 수 있습니다. 각 설정에 대 한 참조 [합니다. Pkgdef 파일](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)합니다.  
  
- AddinsAllowed  
  
- AllowsDroppedFilesOnMainWindow  
  
- AppName  
  
- CommandLineLogo  
  
- DefaultHomePage  
  
- DefaultProjectsLocation  
  
- DefaultSearchPage  
  
- DefaultUserFilesFolderRoot  
  
- DisableOutputWindow  
  
- HideMiscellaneousFilesByDefault  
  
- HideSolutionConcept  
  
- NewProjDlgInstalledTemplatesHdr  
  
- NewProjDlgSlnTreeNodeTitle  
  
- SolutionFileCreatorIdentifier  
  
- SolutionFileExt  
  
- UserFilesSubFolderName  
  
- UserOptsFileExt  
  
  Visual Studio Shell 격리 템플릿은 소스 파일을 만듭니다 *solutionName*.cpp, 여기서 *solutionName* 응용 프로그램에 대 한 솔루션 이름입니다. 이 파일은 _tWinMain 함수 응용 프로그램에 대 한 주 진입점을 정의 합니다. 이 함수는 셸 시작 진입점을 호출합니다.  
  
  응용 프로그램을 시작 하는 경우 이러한 설정을 변경 하 여 응용 프로그램의 동작을 변경할 수 있습니다.  
  
## <a name="parameters"></a>매개 변수  
 Visual Studio shell의 시작 진입점 5 개의 매개 변수를 정의합니다. 처음 네 개의 매개 변수를 변경 하지 마세요. 다섯 번째 매개 변수는 설정 재정의 목록입니다. 셸 시작 진입점은 응용 프로그램의 주 진입점에서 호출 됩니다.  
  
 셸의 시작 진입점에는 다음 서명이 있습니다.  
  
```  
typedef int (__cdecl *STARTFCN)(LPSTR, LPWSTR, int, GUID *, WCHAR *pszSettings);  
```  
  
 설정의 값을 모든 응용 프로그램 설정을 재정의 하지 않으려면 null 포인터 매개 변수를 재정의 합니다.  
  
 하나 이상의 설정을 재정의 하려면 재정의할 수 설정을 포함 하는 유니코드 문자열을 전달 합니다. 문자열은 이름-값 쌍의 세미콜론으로 구분 된 목록. 각 쌍에 설정을 적용할 값 뒤에 등호 (=) 뒤에 재정의 설정의 이름을 포함 합니다.  
  
> [!NOTE]
> 유니코드 문자열에 공백을 포함 하지 않습니다.  
  
 부울 설정에 대 한 다음 문자열을 나타내는 값이 true입니다. 다른 모든 문자열 값 false를 나타냅니다. 이러한 문자열 대/소문자를 구분 하지 않습니다.  
  
- \+  
  
- 1  
  
- -1  
  
- On  
  
- true  
  
- 예  
  
## <a name="example"></a>예제  
 추가 기능을 사용 하지 않도록 설정 하 고 응용 프로그램에 대 한 기본 프로젝트 위치를 변경 하려면 "AddinsAllowed=false;DefaultProjectsLocation=%USERPROFILE%\temp" 마지막 매개 변수를 설정할 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [격리 셸 사용자 지정](../extensibility/customizing-the-isolated-shell.md)   
 [.pkgdef 파일](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)
