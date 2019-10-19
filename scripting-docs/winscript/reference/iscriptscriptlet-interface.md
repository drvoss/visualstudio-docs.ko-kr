---
title: IScriptScriptlet 인터페이스 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IScriptScriptlet interface
ms.assetid: b9981908-a337-4228-864c-c741f111ab2d
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7b7973aee209695592f022d0e05a770caa1e694c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571878"
---
# <a name="iscriptscriptlet-interface"></a>IScriptScriptlet 인터페이스
@No__t_0 인터페이스를 구현 하는 개체는 이벤트 처리기 스크립트를 나타냅니다.  
  
 @No__t_0에서 상속 된 메서드 외에도 `IScriptScriptlet` 인터페이스는 다음 메서드를 노출 합니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[IScriptScriptlet::GetEventName](../../winscript/reference/iscriptscriptlet-geteventname.md)|Scriptlet와 연결 된 이벤트의 이름을 반환 합니다.|  
|[IScriptScriptlet:: GetSimpleEventName](../../winscript/reference/iscriptscriptlet-getsimpleeventname.md)|Scriptlet와 연결 된 단순 이벤트 이름을 반환 합니다. 공백을 포함 하지 않는 단일 단어 이름입니다.|  
|[IScriptScriptlet::GetSubItemName](../../winscript/reference/iscriptscriptlet-getsubitemname.md)|Scriptlet 개체 호스트의 정규화 된 이름에서 마지막 식별자를 반환 합니다.|  
|[IScriptScriptlet::SetEventName](../../winscript/reference/iscriptscriptlet-seteventname.md)|Scriptlet와 연결 된 이벤트의 이름을 설정 합니다.|  
|[IScriptScriptlet::SetSimpleEventName](../../winscript/reference/iscriptscriptlet-setsimpleeventname.md)|Scriptlet와 연결 된 단순 이벤트 이름을 설정 합니다. 공백을 포함 하지 않는 단일 단어 이름입니다.|  
|[IScriptScriptlet::SetSubItemName](../../winscript/reference/iscriptscriptlet-setsubitemname.md)|Scriptlet 개체 호스트의 정규화 된 이름에서 마지막 식별자를 설정 합니다.|  
  
## <a name="see-also"></a>참조  
 [액티브 스크립트 작성 인터페이스](../../winscript/reference/active-script-authoring-interfaces.md)