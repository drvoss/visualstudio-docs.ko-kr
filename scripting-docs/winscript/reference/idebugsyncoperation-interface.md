---
title: IDebugSyncOperation 인터페이스 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugSyncOperation interface
ms.assetid: 8d714492-1836-462c-980a-c99e91a2c81b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7184be62a8ad2b65e81d1ad82f01f0ce3f4668c5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63004888"
---
# <a name="idebugsyncoperation-interface"></a>IDebugSyncOperation 인터페이스
스크립트 엔진이 차단 된 특정 스레드에 중첩 하는 동안 수행 해야 하는 작업 (예: 식 평가 경우)를 추상화할 수 있습니다. 인터페이스는 또한 응답 하지 않는 작업을 취소 하는 메커니즘을 제공 합니다.  
  
 상속 된 메서드 외에도 `IUnknown`, `IDebugSyncOperation` 인터페이스는 다음 메서드를 노출 합니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[IDebugSyncOperation::GetTargetThread](../../winscript/reference/idebugsyncoperation-gettargetthread.md)|이 동기화 작업에 대해 대상 응용 프로그램 스레드를 반환합니다.|  
|[IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)|동기적으로 작업을 수행 하 고 반환 합니다.|  
|[IDebugSyncOperation::InProgressAbort](../../winscript/reference/idebugsyncoperation-inprogressabort.md)|다른 스레드에서 진행 중인 작업을 취소합니다.|