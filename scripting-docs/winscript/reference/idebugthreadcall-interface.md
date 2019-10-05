---
title: IDebugThreadCall 인터페이스 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugThreadCall interface
ms.assetid: 9a9a9892-f310-4ef3-8db2-4f868be52d7e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 89f0fba2f5210cdcf4bb8f17443f948cb9ba1f4e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63004864"
---
# <a name="idebugthreadcall-interface"></a>IDebugThreadCall 인터페이스
합니다 `IDebugThreadCall` 인터페이스는 일반적으로 사용 하 여 크로스 스레드 호출 하는 구성 요소에 의해 구현 됩니다는 `IDebugThread` 마샬링 프로세스 디버그 관리자 (PDM)에서 제공 하는 구현 합니다.  
  
 PDM 호출을 `IDebugThreadCall` 원하는 스레드에서 인터페이스 및 `IDebugThreadCall` 인터페이스 원하는 구현에 대 한 호출을 발송 합니다. `IDebugThreadCall` 인터페이스 맨 위에 적절 한 매개 변수에서 전달 된 매개 변수 정보를 캐스팅 합니다.  
  
 `IDebugThreadCall` 인터페이스 자유 스레드 개체입니다.  
  
## <a name="methods"></a>메서드  
 상속 된 메서드 외에도 `IUnknown`, `IDebugThreadCall` 인터페이스는 다음 메서드를 노출 합니다.  
  
|메서드|설명|  
|------------|-----------------|  
|[IDebugThreadCall::ThreadCallHandler](../../winscript/reference/idebugthreadcall-threadcallhandler.md)|다른 스레드에서 코드 실행에 대 한 호출을 처리 합니다.|