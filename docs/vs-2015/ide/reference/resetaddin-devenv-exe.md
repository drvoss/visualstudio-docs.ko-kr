---
title: -ResetAddin(devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- disable addin
- addin state
- reset addin
ms.assetid: 9e339c8d-d768-4d86-8f45-2f479fc8255b
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6321433b506d41df57150b5a135a800a16cef0ab
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65689675"
---
# <a name="resetaddin-devenvexe"></a>/ResetAddin(devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

지정된 추가 기능과 연결된 명령 및 명령 UI를 제거합니다.  
  
## <a name="syntax"></a>구문  
  
```  
Devenv /ResetAddin AddIn  
```  
  
## <a name="arguments"></a>인수  
 `AddIn`  
 선택 사항입니다. 추가 기능의 명령 이름입니다.  
  
## <a name="remarks"></a>주의  
 기본적으로 추가 기능의 명령 이름은 *\<AddInSolutionName>*.Connect<em>.\<AddInSolutionName></em>과 같고 Connect.cs에 `Exec` 메서드의 `commandName` 매개 변수로 표시됩니다. 먼저 Visual Studio의 명령 창에 추가 기능 이름을 입력하고 IntelliSense를 사용하여 나머지 부분을 입력하는 방식으로 명령 이름을 확인할 수도 있습니다.  
  
## <a name="example"></a>예제  
 다음 예제에서는 Visual Studio를 시작하고 `MyAddin` 추가 기능이 시작 시 실행되지 않도록 합니다.  
  
```  
Devenv.exe /ResetAddin MyAddin.Connect.MyAddin  
```  
  
## <a name="see-also"></a>참고 항목  
 [Visual Studio에서 개발 설정 사용자 지정](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Devenv 명령줄 스위치](../../ide/reference/devenv-command-line-switches.md)
