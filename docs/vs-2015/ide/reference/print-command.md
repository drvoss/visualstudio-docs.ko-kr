---
title: 인쇄 명령 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.print
helpviewer_keywords:
- Debug.Print command
- Print method
- Print command
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 65d78387c6d60d0b432db9aab175fbfe8dc2869b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68203560"
---
# <a name="print-command"></a>인쇄 명령
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

식을 계산하거나 지정된 텍스트를 표시합니다.  
  
## <a name="syntax"></a>구문  
  
```  
Debug.Print text  
```  
  
## <a name="arguments"></a>인수  
 `text`  
 필수 요소. 계산할 식 또는 표시할 텍스트입니다.  
  
## <a name="remarks"></a>설명  
 이 명령에 대한 별칭으로 물음표(?)를 사용할 수 있습니다. 따라서 예를 들면  
  
```  
>Debug.Print expA  
```  
  
 명령을 작성할 수도 있습니다.  
  
```  
>? expA  
```  
  
 이 명령의 두 버전은 모두 `expA` 식의 현재 값을 반환합니다.  
  
## <a name="example"></a>예  
  
```  
>Debug.Print varA  
```  
  
## <a name="see-also"></a>참고 항목  
 [문 실행 명령](../../ide/reference/evaluate-statement-command.md)   
 [Visual Studio 명령](../../ide/reference/visual-studio-commands.md)   
 [명령 창](../../ide/reference/command-window.md)   
 [찾기/명령 상자](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
