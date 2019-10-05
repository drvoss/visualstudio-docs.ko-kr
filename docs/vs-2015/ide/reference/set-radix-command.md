---
title: 기수 설정 명령 | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.setradix
helpviewer_keywords:
- Set Radix command
- Debug.SetRadix command
ms.assetid: 6ffd1554-7530-4da4-b5f5-e276a5034f3b
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: bee6368931dc47b78186ec870039ab292960fa77
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68163313"
---
# <a name="set-radix-command"></a>기수 설정 명령
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

정수 값을 표시하는 데 사용할 숫자 기준을 설정하거나 반환합니다.  
  
## <a name="syntax"></a>구문  
  
```  
Debug.SetRadix [10 | 16 | hex | dec]  
```  
  
## <a name="arguments"></a>인수  
 `10`, `16`, `hex` 또는 `dec`  
 선택 사항입니다. 10진수(10 또는 dec) 또는 16진수(16 또는 hex)를 나타냅니다. 인수를 생략하면 현재 기수 값이 반환됩니다.  
  
## <a name="example"></a>예  
 이 예제에서는 16진수 형식의 정수 값을 표시하도록 환경을 설정합니다.  
  
```  
>Debug.SetRadix hex  
```  
  
## <a name="see-also"></a>참고 항목  
 [Visual Studio 명령](../../ide/reference/visual-studio-commands.md)   
 [명령 창](../../ide/reference/command-window.md)   
 [찾기/명령 상자](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
