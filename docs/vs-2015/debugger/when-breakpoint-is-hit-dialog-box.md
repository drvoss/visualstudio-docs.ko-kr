---
title: 중단점 적중 횟수 대화 상자를가 하는 경우 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.whenbreakpointishit
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- SQL
- VB
- CSharp
- C++
ms.assetid: 476e3d98-cf35-4338-b124-cd0f3010d854
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9a7cd140a22c435df0875c089a69476d3e1e61cf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68149418"
---
# <a name="when-breakpoint-is-hit-dialog-box"></a>중단점이 적중될 때 대화 상자
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 대화 상자를 사용 하 여 중단점을 적중 될 때 발생 하는 동작을 사용자 지정할 수 있습니다.  
  
## <a name="uielement-list"></a>UI 요소 목록  
 **메시지 인쇄**  
 DebuggerDisplay 구문을 사용 하 여 메시지를 인쇄 합니다. 자세한 내용은 [DebuggerDisplay 특성을 사용 하 여](../debugger/using-the-debuggerdisplay-attribute.md)입니다.  
  
 또한이 텍스트 상자에이 붙여넣습니다 (예: $ADDRESS) 단독으로 또는 DebuggerDisplay 식의 중괄호 내에서 사용할 수 있는 특수 키워드를 지원 합니다. 사용할 수 있는 키워드는 대화 상자에 나열 됩니다.  
  
 **실행 계속**  
 이 컨트롤은 **메시지 인쇄**를 선택한 경우에만 활성화됩니다. 이 컨트롤을 선택 하면 프로그램 실행을 추적 하려면 추적점으로 중단점을 사용할 수 있습니다 위치 적중 될 때 중단 하는 대신 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [중단점 사용](../debugger/using-breakpoints.md)   
 [DebuggerDisplay 특성 사용](../debugger/using-the-debuggerdisplay-attribute.md)
