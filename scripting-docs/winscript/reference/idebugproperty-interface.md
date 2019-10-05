---
title: IDebugProperty 인터페이스 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugProperty interface
ms.assetid: 7e8f5341-23ef-4029-814d-f5c2307b9203
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 963b11a4760fad8086822f13db129fae76467802
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62979064"
---
# <a name="idebugproperty-interface"></a>IDebugProperty 인터페이스
이름, 형식 및 값에는 디버깅 중인 엔터티의 계층적 속성에 설명 하는 데 사용 합니다. 가장 일반적으로 `IDebugProperty` 식 계산, 문이 평가 또는 등록 평가의 결과 설명 하는 데 사용 됩니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 다음 표에의 메서드는 `IDebugProperty` 인터페이스입니다.  
  
|메서드|설명|  
|------------|-----------------|  
|[IDebugProperty::GetPropertyInfo](../../winscript/reference/idebugproperty-getpropertyinfo.md)|가져오기는 `DebugPropertyInfo` 이 설명 하는 `IDebugProperty``.`|  
|[IDebugProperty::GetExtendedInfo](../../winscript/reference/idebugproperty-getextendedinfo.md)|속성 확장된 정보를 가져옵니다.|  
|[IDebugProperty::SetValueAsString](../../winscript/reference/idebugproperty-setvalueasstring.md)|문자열에서 속성의 값을 설정 합니다.|  
|[IDebugProperty::EnumMembers](../../winscript/reference/idebugproperty-enummembers.md)|속성의 멤버를 열거합니다.|  
|[IDebugProperty::GetParent](../../winscript/reference/idebugproperty-getparent.md)|속성의 부모를 가져옵니다.|  
  
## <a name="requirements"></a>요구 사항  
 헤더: dbgprop.h