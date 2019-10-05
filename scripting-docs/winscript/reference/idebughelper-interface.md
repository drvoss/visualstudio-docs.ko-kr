---
title: IDebugHelper 인터페이스 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugHelper interface
ms.assetid: ef5691e0-1d82-42c2-997c-888e31c478dd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d1708b742a484a2e7d6d48cf759f15c08711e13d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62979190"
---
# <a name="idebughelper-interface"></a>IDebugHelper 인터페이스
개체 브라우저 및 간단한 연결 지점에 대 한 팩터리 역할을 합니다. 프로세스 디버그 관리자 (PDM) 스크립트 엔진에서 사용 되는이 인터페이스를 구현 합니다.  
  
 상속 된 메서드 외에도 `IUnknown`, `IDebugHelper` 인터페이스는 다음 메서드를 노출 합니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[IDebugHelper::CreatePropertyBrowser](../../winscript/reference/idebughelper-createpropertybrowser.md)|VARIANT를 래핑하는 속성 브라우저를 반환 합니다.|  
|[IDebugHelper::CreatePropertyBrowserEx](../../winscript/reference/idebughelper-createpropertybrowserex.md)|VARIANT를 래핑하고 VARIANT 값 또는 VARTYPE 형식 문자열을 사용자 지정 변환에 대 한 허용 하는 속성 브라우저를 반환 합니다.|  
|[IDebugHelper::CreateSimpleConnectionPoint](../../winscript/reference/idebughelper-createsimpleconnectionpoint.md)|래핑하는 이벤트 인터페이스를 반환 합니다.는 주어진 `IDispatch` 개체입니다.|