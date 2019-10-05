---
title: IDebugPropertyEnumType_All 인터페이스 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugPropertyEnumType_All
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugPropertyEnumType_All interface
ms.assetid: 4d0f4fd5-e5f7-47cb-b746-860d6363e2cd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b9ddd9fb24aa83a6027d6d705de6a748a96b2e28
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62979112"
---
# <a name="idebugpropertyenumtypeall-interface"></a>IDebugPropertyEnumType_All 인터페이스
합니다 `IDebugPropertyEnumType` 각 해당 Iid에 필터로 전달 될 수 있도록 인터페이스를 정의 `IDebugProperty::EnumMembers` 적절 한 열거자를 요청 하는 중입니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
IDebugPropertyEnumType_All : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[IDebugPropertyEnumType_All::GetName](../../winscript/reference/idebugpropertyenumtype-all-getname.md)|이름을 설명 하는 텍스트 문자열을 반환 합니다.|  
  
 다음 인터페이스에서 상속할 `IDebugPropertyEnumType_All`, 있고 추가 메서드가 없습니다.  
  
```cpp
IDebugPropertyEnumType_Arguments : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_Locals : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_LocalsPlusArgs : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_Registers : IDebugPropertyEnumType_All  
```  
  
## <a name="see-also"></a>참고 항목  
 [IDebugProperty::EnumMembers](../../winscript/reference/idebugproperty-enummembers.md)