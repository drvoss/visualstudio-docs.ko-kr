---
title: IEnumDebugExtendedPropertyInfo 인터페이스 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugExtendedPropertyInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumDebugExtendedPropertyInfo interface
ms.assetid: 316d5aa7-c949-48fc-89c1-239f00566cae
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8ceae13f2a785a0920598fa79b237a9c8ae1da1c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72568933"
---
# <a name="ienumdebugextendedpropertyinfo-interface"></a>IEnumDebugExtendedPropertyInfo 인터페이스
@No__t_0 구조체를 열거 합니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 다음 표에서는 `IEnumDebugExtendedPropertyInfo`의 메서드를 보여 줍니다.  
  
|메서드|설명|  
|------------|-----------------|  
|[IEnumDebugExtendedPropertyInfo::Clone](../../winscript/reference/ienumdebugextendedpropertyinfo-clone.md)|현재 열거자와 동일한 열거 상태를 포함 하는 열거자를 만듭니다.|  
|[IEnumDebugExtendedPropertyInfo::GetCount](../../winscript/reference/ienumdebugextendedpropertyinfo-getcount.md)|열거자의 `ExtendedDebugPropertyInfo` 구조체 수를 가져옵니다.|  
|[IEnumDebugExtendedPropertyInfo::Next](../../winscript/reference/ienumdebugextendedpropertyinfo-next.md)|열거형 시퀀스에서 지정 된 수의 `ExtendedDebugPropertyInfo` 구조체를 검색 합니다.|  
|[IEnumDebugExtendedPropertyInfo::Skip](../../winscript/reference/ienumdebugextendedpropertyinfo-skip.md)|열거형 시퀀스에서 지정 된 수의 `ExtendedDebugPropertyInfo` 구조체를 건너뜁니다.|  
|[IEnumDebugExtendedPropertyInfo::Reset](../../winscript/reference/ienumdebugextendedpropertyinfo-reset.md)|열거형 시퀀스를 시작 부분으로 다시 설정합니다.|  
  
## <a name="requirements"></a>요구 사항  
 헤더: dbgprop  
  
## <a name="see-also"></a>참조  
 [ExtendedDebugPropertyInfo 구조체](../../winscript/reference/extendeddebugpropertyinfo-structure.md)