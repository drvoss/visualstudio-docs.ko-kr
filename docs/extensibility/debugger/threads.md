---
title: 스레드 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], threads
- threading [Debugging SDK]
ms.assetid: 2243d24a-c3d2-41d1-abbb-6db21a2db9ee
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 456ec81c5f39f533bddd58d0a9e4d9d5889f066d
ms.sourcegitcommit: 8d38d5d2f2b75fc1563952c0d6de0fe43af12766
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/26/2018
ms.locfileid: "39276636"
---
# <a name="threads"></a>스레드
디버거 아키텍처에는 *스레드*:  
  
-   기본 단위 계산입니다. 스레드는 순차적으로 하나의 코드 컨텍스트에서 다음으로 이동 하는 단일 호출 스택, 컨텍스트 내에서 명령을 실행 합니다.  
  
-   자체 및에서 실행 중인 프로그램을 식별할 수 있습니다. 스레드는 라는, 일시 중단 및 다시 시작할 수 있습니다. 스레드가 해당 연결 된 스택 프레임을 열거할 수도 수 있습니다 하 고 조건에 따라 다른 스택 프레임으로 이동할 수 있습니다. 스택 프레임의 컨텍스트를 지정 하는, 스레드 수 반환은 연결된의 논리적 스레드를 있는 경우. 스레드가에 표시 될 수 있는 일시 중단 횟수가 등의 속성을 **스레드** IDE의 창.  
  
-   로 표시 됩니다는 [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) 일반적으로 디버그 엔진 (DE) 또는 프로그램 실행의 결과로 가상 머신을 만든 인터페이스입니다.  
  
## <a name="see-also"></a>참고자료  
 [프로그램](../../extensibility/debugger/programs.md)   
 [스택 프레임](../../extensibility/debugger/stack-frames.md)   
 [디버그 엔진](../../extensibility/debugger/debug-engine.md)   
 [디버거 개념](../../extensibility/debugger/debugger-concepts.md)   
 [세션 디버그 관리자](../../extensibility/debugger/session-debug-manager.md)