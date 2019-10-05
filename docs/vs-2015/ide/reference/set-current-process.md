---
title: 현재 프로세스 설정 | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Debug.SetCurrentProcess command
- Set Current Process command
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ed19c5b95351f8e9c34255a915fc6a446800f761
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68163338"
---
# <a name="set-current-process"></a>현재 프로세스 설정
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

디버거에서 지정한 프로세스를 활성 프로세스로 설정합니다.  
  
## <a name="syntax"></a>구문  
  
```  
Debug.SetCurrentProcess index  
```  
  
## <a name="arguments"></a>인수  
 `index`  
 필수 요소. 프로세스의 인덱스입니다.  
  
## <a name="remarks"></a>설명  
 디버그하는 동안 여러 프로세스에 연결할 수 있지만 한 번에 프로세스 하나만 디버거에서 활성화됩니다. `SetCurrentProcess` 명령을 사용하여 활성 프로세스를 설정할 수 있습니다.  
  
## <a name="example"></a>예  
  
```  
>Debug.SetCurrentProcess 1  
```  
  
## <a name="see-also"></a>참고 항목  
 [Visual Studio 명령](../../ide/reference/visual-studio-commands.md)   
 [명령 창](../../ide/reference/command-window.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
