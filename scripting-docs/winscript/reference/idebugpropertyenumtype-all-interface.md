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
ms.openlocfilehash: 737d1c5d4279a0a727f79326749dbf14a2fcd4c7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574312"
---
# <a name="idebugpropertyenumtype_all-interface"></a>IDebugPropertyEnumType_All 인터페이스
적절 한 열거자를 요청 하는 동안 각 Iid를 `IDebugProperty::EnumMembers` 필터로 전달할 수 있도록 `IDebugPropertyEnumType` 인터페이스가 정의 됩니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
IDebugPropertyEnumType_All : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[IDebugPropertyEnumType_All::GetName](../../winscript/reference/idebugpropertyenumtype-all-getname.md)|이름을 설명 하는 텍스트 문자열을 반환 합니다.|  
  
 다음 인터페이스는 `IDebugPropertyEnumType_All`에서 상속 되며 추가 메서드를 포함 하지 않습니다.  
  
```cpp
IDebugPropertyEnumType_Arguments : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_Locals : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_LocalsPlusArgs : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_Registers : IDebugPropertyEnumType_All  
```  
  
## <a name="see-also"></a>참조  
 [IDebugProperty::EnumMembers](../../winscript/reference/idebugproperty-enummembers.md)