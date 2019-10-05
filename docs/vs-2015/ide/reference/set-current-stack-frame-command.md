---
title: 현재 스택 프레임 설정 명령 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.setcurrentstackframe
helpviewer_keywords:
- Set Current Stack Frame command
- Debug.SetCurrentStackFrame command
ms.assetid: 3dcf52c0-6781-4598-bac2-0094dce67c20
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 87d830e492420844de72a2cd34dbea336e365dfd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68163354"
---
# <a name="set-current-stack-frame-command"></a>현재 스택 프레임 설정 명령
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

특정 스택 프레임을 설정할 수 있습니다.  
  
## <a name="syntax"></a>구문  
  
```  
Debug.SetCurrentStackFrame index  
```  
  
## <a name="arguments"></a>인수  
 `index`  
 필수 요소. 해당 인덱스로 스택 프레임을 선택합니다.  
  
## <a name="example"></a>예  
  
```  
>Debug.SetCurrentStackFrame 1  
```  
  
## <a name="see-also"></a>참고 항목  
 [Visual Studio 명령](../../ide/reference/visual-studio-commands.md)   
 [명령 창](../../ide/reference/command-window.md)   
 [찾기/명령 상자](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
