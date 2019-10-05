---
title: 현재 스레드 설정 명령 | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.setcurrentthread
helpviewer_keywords:
- Set Current Thread command
- Debug.SetCurrentThread command
ms.assetid: 9917ed1d-6c30-4d94-b2f0-69acce74f1b2
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 107303082202cb1dbb162ef9dfb845c2f6564df4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68163326"
---
# <a name="set-current-thread-command"></a>현재 스레드 설정 명령
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

지정한 스레드를 현재 스레드로 설정합니다.  
  
## <a name="syntax"></a>구문  
  
```  
Debug.SetCurrentThread index  
```  
  
## <a name="arguments"></a>인수  
 `index`  
 필수 요소. 해당 인덱스로 스레드를 선택합니다.  
  
## <a name="example"></a>예  
  
```  
>Debug.SetCurrentThread 1  
```  
  
## <a name="see-also"></a>참고 항목  
 [Visual Studio 명령](../../ide/reference/visual-studio-commands.md)   
 [명령 창](../../ide/reference/command-window.md)   
 [찾기/명령 상자](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
