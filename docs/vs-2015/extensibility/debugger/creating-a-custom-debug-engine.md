---
title: 디버그 엔진을 사용자 지정 만들기 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementing
- debug engines, custom
- debugging [Debugging SDK], custom debug engines
ms.assetid: 52794238-6fae-451c-bf1c-99f344c6f173
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b2a73dfae7772d8edec076238704aa1b52c9b028
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63383425"
---
# <a name="creating-a-custom-debug-engine"></a>사용자 지정 디버그 엔진 만들기
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

디버그 엔진 (DE)는 구성 요소로, 특정 런타임 아키텍처를 디버깅할 수 있습니다. 일반적으로 런타임 환경 별로 하나의 DE 구현이입니다.  
  
> [!NOTE]
> TRANSACT-SQL 및 JScript에 대 한 별도 DE 구현을 있기는 VBScript 및 JScript 단일 DE 공유 합니다.  
  
 DE와 같은 디버깅 서비스 실행 제어, 중단점 및 식 평가를 위해 인터프리터 또는 작업 시스템에서 작동 합니다. 이러한 서비스 DE 인터페이스를 통해 구현 되 고 다른 운영 모드를 전환 하도록 디버거를 발생할 수 있습니다. 자세한 내용은 [운영 모드](../../extensibility/debugger/operational-modes.md)합니다.  
  
 만들기는 DE 다음 단계로 구성 됩니다.  
  
1. Visual Studio는 DE 등록  
  
2. 디버그할 프로그램을 사용 하도록 설정  
  
3. 실행 제어 및 상태 평가  
  
4. 이벤트 전송  
  
5. 종료 및 분리  
  
## <a name="in-this-section"></a>섹션 내용  
 [사용자 지정 디버그 엔진 등록](../../extensibility/debugger/registering-a-custom-debug-engine.md)  
 사용할 수 있도록 Visual Studio 디버그 엔진을 등록 하는 데 필요한 단계를 설명 합니다.  
  
 [디버그할 프로그램을 사용하도록 설정](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)  
 프로그램을 디버그할 프로그램 DE 전에 먼저는 DE 시작 하거나 기존 프로그램에 연결에 대해 설명 합니다.  
  
 [실행 제어 및 상태 평가](../../extensibility/debugger/execution-control-and-state-evaluation.md)  
 응용 프로그램을 디버깅할가 실행 제어 기능을 구현 하기 필요한 이유를 설명 합니다.  
  
 [이벤트 보내기](../../extensibility/debugger/sending-events.md)  
 DCOM 기반 이벤트 모델로 디버거는 DE 사이의 통신을 설명 합니다.  
  
 [종료 및 분리](../../extensibility/debugger/termination-and-detaching.md)  
 즉, 없습니다 중단점, 예외, 런타임 오류 또는 응용 프로그램을 디버깅할 수에 무한 루프는 정상 종료를 수행 하는 방법을 설명 합니다.  
  
 [디버거 이벤트 호출](../../extensibility/debugger/calling-debugger-events.md)  
 디버깅 세션에서 발생 하는 이벤트의 호출 순서를 설명 합니다.  
  
 [방법: 사용자 지정 디버그 엔진 디버그](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md)  
 사용자 지정 DE를 디버그 하는 방법에 설명 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [Visual Studio 디버거 확장성](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
