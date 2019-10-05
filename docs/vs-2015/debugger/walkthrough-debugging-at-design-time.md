---
title: '연습: 디자인 타임에 디버그 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], design-time
- breakpoints, design-time debugging
- Immediate window, design-time debugging
- design-time debugging
ms.assetid: 35bfdd2c-6f60-4be1-ba9d-55fce70ee4d8
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 54466cc3561c194199bbad2b35cd00433da2b0f3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68149423"
---
# <a name="walkthrough-debugging-at-design-time"></a>연습: 디자인 타임에 디버깅
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio를 사용할 수 있습니다 **직접 실행** 응용 프로그램이 실행 되지 않는 상태 함수나 서브루틴을 실행 하는 창입니다. 함수 또는 서브루틴에 중단점이 포함 된, Visual Studio는 해당 시점에서 실행을 중단 합니다. 그런 다음 디버거 창을 사용하여 프로그램 상태를 조사할 수 있습니다. 이 기능은 디자인 타임에 디버깅 호출 됩니다.  
  
 다음 절차에서는이 기능을 사용 하는 방법을 보여 줍니다.  
  
### <a name="to-hit-breakpoints-from-the-immediate-window"></a>직접 실행 창에서 중단점을 적중 하려면  
  
1. Visual Basic 콘솔 응용 프로그램에 다음 코드를 붙여 넣습니다.  
  
    ```  
    Module Module1  
  
        Sub Main()  
            MySub()  
        End Sub  
  
        Function MyFunction() As Decimal  
            Static i As Integer  
            i = i + 1  
            Dim s As String  
  
            s = "Add Breakpoint here"  
            Return 4  
        End Function  
  
        Sub MySub()  
            MyFunction()  
        End Sub  
    End Module  
    ```  
  
2. 읽기는 줄에 중단점을 설정할 `s="Add BreakPoint Here"`합니다.  
  
3. 다음을 입력 합니다 **직접 실행** 창: `?MyFunction<enter>`  
  
4. 중단점에 도달 했는지, 호출 스택을 정확한 지 확인 합니다.  
  
5. 에 **디버그** 메뉴에서 클릭 **계속**, 디자인 모드에 여전히 있는지 확인 합니다.  
  
6. 다음을 입력 합니다 **직접 실행** 창: `?MyFunction<enter>`  
  
7. 다음을 입력 합니다 **직접 실행** 창: `?MySub<enter>`  
  
8. 중단점에 도달 하 고 정적 변수의 값을 검사 하는 확인 `i` 에 **지역** 창입니다. 값 3 있어야 합니다.  
  
9. 호출 스택의 정확한 지 확인 합니다.  
  
10. 에 **디버그** 메뉴에서 클릭 **계속**, 디자인 모드에 여전히 있는지 확인 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [디버거 보안](../debugger/debugger-security.md)   
 [디버거 기본 사항](../debugger/debugger-basics.md)
