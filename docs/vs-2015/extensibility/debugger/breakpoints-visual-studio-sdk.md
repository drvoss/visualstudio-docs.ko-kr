---
title: 중단점 (Visual Studio SDK) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- breakpoints
ms.assetid: acfcabed-9f2f-436c-ad18-7ca2f45d631b
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 39c13271bad984291f609ef45505549855bee99f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68146429"
---
# <a name="breakpoints-visual-studio-sdk"></a>중단점(Visual Studio SDK)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

중단점의 세 가지 종류가 있습니다: 보류 중 및 오류입니다.  
  
 **중단점 보류 중인는:**  
  
- 하나 이상의 응용 프로그램에서 하나 이상의 코드 컨텍스트에 중단점을 바인딩할 때 필요한 모든 정보를 포함 하는 추상화가입니다. 때마다 원인 로드 하는 코드 디버깅 중인 프로그램의 디버그 엔진 확인를 바인딩할 수 있으면 모든 보류 중인 중단점 합니다.  
  
   자체 보류 중인 중단점 되지 코드에 바인딩합니다 하지만 대신 수집 하 고 생성 하는 모든 바인딩된 중단점을 포함 합니다.  
  
- 표시 되는 [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) 인터페이스입니다.  
  
  **바인딩된 중단점:**  
  
- 중단점에 대 한 추상화와 연결 된 또는 단일 코드 컨텍스트에 바인딩. 각각의 바인딩된 중단점은 보류 중인 중단점에 대 한 응답으로 생성 됩니다. 그러나 보류 중인 중단점 둘 이상의 바인딩된 중단점을 생성할 수 있습니다.  
  
   코드를 로드 하는 경우 바인딩된 중단점을 바인딩 해제 하 고 삭제 수 있습니다.  
  
- 표시 되는 [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) 인터페이스입니다.  
  
  **오류 중단점:**  
  
- 보류 중인 중단점 코드 컨텍스트를 바인딩할 때 오류를 설명 하기 위한 추상화가입니다. 오류 중단점을 중단점 식 자체 또는 위치에서 두 오류를 설명 합니다. 자세한 내용은 [바인딩 중단점](../../extensibility/debugger/binding-breakpoints.md)합니다.  
  
   중단점 오류는 오류 또는 경고 중 수 있습니다.  
  
- 표시 되는 [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) 인터페이스입니다.  
  
## <a name="see-also"></a>참고 항목  
 [프로그램](../../extensibility/debugger/programs.md)   
 [디버거 개념](../../extensibility/debugger/debugger-concepts.md)   
 [코드 컨텍스트](../../extensibility/debugger/code-context.md)   
 [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
