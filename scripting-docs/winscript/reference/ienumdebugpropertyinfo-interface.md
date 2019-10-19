---
title: IEnumDebugPropertyInfo 인터페이스 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IEnumDebugPropertyInfo interface
ms.assetid: c5eea4da-8414-408a-a8f6-6a9ca8745868
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0ce4f5a114629a473df99b583c77ae7747bcd339
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574181"
---
# <a name="ienumdebugpropertyinfo-interface"></a>IEnumDebugPropertyInfo 인터페이스
@No__t_0 구조체를 열거 합니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 다음 표에서는 `IEnumDebugPropertyInfo`의 메서드를 보여 줍니다.  
  
|메서드|설명|  
|------------|-----------------|  
|[IEnumDebugPropertyInfo::Next](../../winscript/reference/ienumdebugpropertyinfo-next.md)|열거형 시퀀스에서 지정 된 수의 `DebugPropertyInfo` 구조체를 검색 합니다.|  
|[IEnumDebugPropertyInfo::Skip](../../winscript/reference/ienumdebugpropertyinfo-skip.md)|열거형 시퀀스에서 지정 된 수의 `DebugPropertyInfo` 구조체를 건너뜁니다.|  
|[IEnumDebugPropertyInfo::Reset](../../winscript/reference/ienumdebugpropertyinfo-reset.md)|열거형 시퀀스를 시작 부분으로 다시 설정합니다.|  
|[IEnumDebugPropertyInfo::Clone](../../winscript/reference/ienumdebugpropertyinfo-clone.md)|현재 열거자와 동일한 열거 상태를 포함 하는 열거자를 만듭니다.|  
|[IEnumDebugPropertyInfo::GetCount](../../winscript/reference/ienumdebugpropertyinfo-getcount.md)|열거자의 `DebugPropertyInfo` 구조체 수를 가져옵니다.|  
  
## <a name="requirements"></a>요구 사항  
 헤더: dbgprop  
  
## <a name="see-also"></a>참조  
 [DebugPropertyInfo 구조체](../../winscript/reference/debugpropertyinfo-structure.md)