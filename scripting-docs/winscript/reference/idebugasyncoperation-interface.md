---
title: IDebugAsyncOperation 인터페이스 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugAsyncOperation interface
ms.assetid: ebb2ea75-1443-4d8a-812d-171a166f5f9d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 820ecc40924ace4153b76f46c8b8fd1603512ebb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62821785"
---
# <a name="idebugasyncoperation-interface"></a>IDebugAsyncOperation 인터페이스
프로세스 디버그 관리자를 구현 하는 `IDebugAsyncOperation` 인터페이스입니다. 언어 엔진을 호출 합니다 `IDebugApplication::CreateAsyncDebugOperation` 이 인터페이스에 대 한 참조를 가져오는 방법입니다. 언어 엔진에서 사용할 수는 `IDebugAsyncOperation` 동기식 디버그 작업에 대 한 비동기 액세스를 제공 하는 인터페이스입니다.  
  
 상속 된 메서드 외에도 `IUnknown`, `IDebugAsyncOperation` 인터페이스는 다음 메서드를 노출 합니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[IDebugAsyncOperation::GetSyncDebugOperation](../../winscript/reference/idebugasyncoperation-getsyncdebugoperation.md)|이 개체와 연결 된 동기식 디버그 작업을 반환 합니다.|  
|[IDebugAsyncOperation::Start](../../winscript/reference/idebugasyncoperation-start.md)|비동기 작업을 시작 하면 됩니다.|  
|[IDebugAsyncOperation::Abort](../../winscript/reference/idebugasyncoperation-abort.md)|작업을 취소합니다.|  
|[IDebugAsyncOperation::QueryIsComplete](../../winscript/reference/idebugasyncoperation-queryiscomplete.md)|디버그 작업을 완료 하는 경우를 결정 합니다.|  
|[IDebugAsyncOperation::GetResult](../../winscript/reference/idebugasyncoperation-getresult.md)|반환 값 및 동기식 디버그 작업에서 반환 된 개체 매개 변수를 제공합니다.|