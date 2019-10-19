---
title: IScriptEntry 인터페이스 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IScriptEntry interface
ms.assetid: 86da3bc1-58b7-4d73-87ab-bc3ce34e3f41
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 868322358908a32c8f14b56846cf3237f8531b4c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575389"
---
# <a name="iscriptentry-interface"></a>IScriptEntry 인터페이스
@No__t_0 인터페이스를 구현 하는 개체는 스크립트 블록이 나 함수 개체를 나타냅니다.  
  
 @No__t_0에서 상속 된 메서드 외에도 `IScriptEntry` 인터페이스는 다음 메서드를 노출 합니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[IScriptEntry::GetBody](../../winscript/reference/iscriptentry-getbody.md)|@No__t_0 스크립트 블록, 함수 블록 또는 scriptlet의 본문에 해당 하는 텍스트를 반환 합니다.|  
|[IScriptEntry::GetItemName](../../winscript/reference/iscriptentry-getitemname.md)|@No__t_0 개체를 식별 하는 항목 이름을 반환 합니다.|  
|[IScriptEntry::GetName](../../winscript/reference/iscriptentry-getname.md)|단일 개체 (예: 함수)를 나타내는 항목의 경우 개체의 이름을 반환 합니다.|  
|[IScriptEntry::GetRange](../../winscript/reference/iscriptentry-getrange.md)|항목의 시작 위치와 길이를 반환 합니다.|  
|[IScriptEntry::GetSignature](../../winscript/reference/iscriptentry-getsignature.md)|@No__t_0 함수 개체에 대 한 형식 정보를 반환 합니다.|  
|[IScriptEntry::GetText](../../winscript/reference/iscriptentry-gettext.md)|@No__t_0 스크립트 블록에 해당 하는 텍스트 또는 `IScriptScriptlet` 이벤트 처리기에 포함 된 소스 코드를 반환 합니다.|  
|[IScriptEntry::SetBody](../../winscript/reference/iscriptentry-setbody.md)|@No__t_0 스크립트 블록 또는 `IScriptScriptlet` scriptlet의 본문에 있는 텍스트를 설정 합니다.|  
|[IScriptEntry::SetItemName](../../winscript/reference/iscriptentry-setitemname.md)|@No__t_0 개체를 식별 하는 항목 이름을 설정 합니다.|  
|[IScriptEntry::SetName](../../winscript/reference/iscriptentry-setname.md)|단일 개체 (예: 함수)를 나타내는 항목의 경우 개체의 이름을 설정 합니다.|  
|[IScriptEntry::SetSignature](../../winscript/reference/iscriptentry-setsignature.md)|@No__t_0 함수 개체에 대 한 형식 정보를 설정 합니다.|  
|[IScriptEntry::SetText](../../winscript/reference/iscriptentry-settext.md)|@No__t_0 스크립트 블록 또는 `IScriptScriptlet` 이벤트 처리기에 포함 된 소스 코드에 해당 하는 텍스트를 설정 합니다.|  
  
## <a name="see-also"></a>참조  
 [액티브 스크립트 작성 인터페이스](../../winscript/reference/active-script-authoring-interfaces.md)