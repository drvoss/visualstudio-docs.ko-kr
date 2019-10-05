---
title: 명령줄 스위치를 추가 합니다. | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- command-line switches, adding
- command-line switches, retrieving
- IVsAppCommandLine::GetOption method
- command line, switches
ms.assetid: 8bbbd87e-76fe-4fb5-8ef9-65f5e31967cf
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e28a3f303849458a407b212d3aad1a8c198f6d25
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62562278"
---
# <a name="adding-command-line-switches"></a>명령줄 스위치 추가
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Devenv.exe를 실행할 때 VSPackage에 적용 되는 명령줄 스위치를 추가할 수 있습니다. 사용 하 여 <xref:Microsoft.VisualStudio.Shell.ProvideAppCommandLineAttribute> 스위치와 해당 속성의 이름을 선언 합니다. 이 예제에서는 myswitch 인 스위치 라는 VSPackage의 서브 클래스에 대 한 항목이 **AddCommandSwitchPackage** 인수 없이 및 자동으로 로드 하는 VSPackage를 사용 하 여 합니다.  
  
```csharp  
[ProvideAppCommandLine("MySwitch", typeof(AddCommandSwitchPackage), Arguments = "0", DemandLoad = 1)]  
```  
  
 명명 된 매개 변수는 다음 표에 표시 됩니다.  
  
 인수  
 스위치에 대 한 인수의 수입니다. 수 "*", 또는 인수 목록입니다.  
  
 DemandLoad  
 그렇지 않으면 0으로 설정 하는 1로 설정 된 경우에 VSPackage를 자동으로 로드 합니다.  
  
 HelpString  
 도움말 문자열 또는 리소스 문자열의 ID를 사용 하 여 표시할 **devenv /?** 합니다.  
  
 이름  
 스위치입니다.  
  
 PackageGuid  
 패키지의 GUID입니다.  
  
 인수의 첫 번째 값은 일반적으로 0 또는 1입니다. 특수 한 값인 ' *' 전체 나머지 명령줄 인수 임을 나타내는 데 사용할 수 있습니다. 이 디버깅 여기서 사용자 디버거 명령 문자열을 전달 해야 하는 시나리오에 유용할 수 있습니다.  
  
 DemandLoad 값은 `true` (1) 또는 `false` (0) VSPackage를 자동으로 로드할지를 나타냅니다.  
  
 HelpString 값은 리소스 ID는 devenv에 표시 되는 문자열의 /? 도움말 표시 합니다. 이 값은 "#nnn" 여기서 nnn은 정수 형식에서 이어야 합니다. 리소스 파일에 문자열 값을 새 줄 문자로 종료 해야 합니다.  
  
 이름 값에 스위치의 이름입니다.  
  
 PackageGuid 값에는이 스위치를 구현 하는 패키지의 GUID입니다. IDE이이 GUID를 사용 하 여 명령줄 스위치를 적용 되는 레지스트리에 VSPackage를 찾습니다.  
  
## <a name="retrieving-command-line-switches"></a>명령줄 스위치를 검색합니다.  
 패키지 로드 되 면 다음 단계를 완료 하 여 명령줄 스위치를 검색할 수 있습니다.  
  
1. VSPackage의의 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> 구현, 호출 `QueryService` 온 <xref:Microsoft.VisualStudio.Shell.Interop.SVsAppCommandLine> 가져오려고는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine> 인터페이스.  
  
2. 호출 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine.GetOption%2A> 에 사용자가 입력 한 명령줄 스위치를 검색 합니다.  
  
   다음 코드에는 사용자가 myswitch 인 명령줄 스위치를 입력 한 여부를 확인 하는 방법을 보여 줍니다.  
  
```csharp  
IVsAppCommandLine cmdline = (IVsAppCommandLine)GetService(typeof(SVsAppCommandLine));  
  
int isPresent = 0;  
string optionValue = "";  
  
cmdline.GetOption("MySwitch", out isPresent, out optionValue);  
```  
  
 것이 패키지를 로드할 때마다 명령줄 스위치에 대 한 확인 해야 합니다.  
  
## <a name="see-also"></a>참고 항목  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 [Devenv 명령줄 스위치](../ide/reference/devenv-command-line-switches.md)   
 [CreatePkgDef 유틸리티](../extensibility/internals/createpkgdef-utility.md)   
 [.pkgdef 파일](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)
