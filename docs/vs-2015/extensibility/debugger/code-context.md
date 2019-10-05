---
title: 상황에 맞는 코드 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d59a4c79cb21386fa6f6e7031404aeb0b435b3b9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68197369"
---
# <a name="code-context"></a>코드 컨텍스트
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 디버깅 하는 **코드 컨텍스트**:  
  
- 디버그 엔진 (DE)에 알려진 코드 위치의 추상화를 제공 합니다. 대부분의 런타임 아키텍처에 대 한 현재 코드 컨텍스트를 생각할 수 있습니다 프로그램의 명령 스트림의 주소로 합니다. 여기서 코드 지침 표시 될 수 있습니다, 않던 언어에 대 한 코드 컨텍스트를 다른 방법으로 나타낼 수 있습니다.  
  
- 디버그 중인 프로그램의 실행 스트림 내의 현재 위치를 설명 합니다.  
  
- 프로그램이 중단점에서 중지 된 경우에 존재 합니다.  
  
- 에 관련된 문서 컨텍스트가 있습니다.  
  
- 에 의해 구현 되는 [IDebugCodeContext2](../../extensibility/debugger/reference/idebugcodecontext2.md) 인터페이스입니다.  
  
## <a name="see-also"></a>참고 항목  
 [문서 컨텍스트](../../extensibility/debugger/document-context.md)   
 [디버거 컨텍스트](../../extensibility/debugger/debugger-contexts.md)
