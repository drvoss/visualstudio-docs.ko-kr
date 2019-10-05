---
title: 중단점 설정/해제 명령 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.togglebreakpoint
helpviewer_keywords:
- ToggleBreakpoint command
- Debug.ToggleBreakPoint command
- Toggle Breakpoint command
ms.assetid: d50dfadb-ce79-4d5e-9c09-1cfddd57876d
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5a57f02a7c1b9845f4248daf2282b6f285f95489
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68193369"
---
# <a name="toggle-breakpoint-command"></a>중단점 설정/해제 명령
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

파일의 현재 위치에서 현재 상태에 따라 중단점을 켜거나 끕니다.  
  
## <a name="syntax"></a>구문  
  
```  
Debug.ToggleBreakpoint [text]  
```  
  
## <a name="arguments"></a>인수  
 `text`  
 선택 사항입니다. 텍스트를 지정하는 경우 해당 줄은 명명된 중단점으로 표시됩니다. 그렇지 않은 경우 해당 줄은 F9 키를 누를 때처럼 명명되지 않은 중단점으로 표시됩니다.  
  
## <a name="example"></a>예  
 다음 예제에서는 현재 중단점을 설정/해제합니다.  
  
```  
>Debug.ToggleBreakpoint  
```  
  
## <a name="see-also"></a>참고 항목  
 [Visual Studio 명령](../../ide/reference/visual-studio-commands.md)   
 [명령 창](../../ide/reference/command-window.md)   
 [찾기/명령 상자](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
