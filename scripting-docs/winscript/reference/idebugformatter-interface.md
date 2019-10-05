---
title: IDebugFormatter 인터페이스 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugFormatter interface
ms.assetid: 022142d4-c8e1-47ae-b771-3e24953293e5
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f35d1b811a017895ca40f3325bd0ac456070184f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62979229"
---
# <a name="idebugformatter-interface"></a>IDebugFormatter 인터페이스
언어 또는 IDE에서 VARIANT 값 또는 VARTYPE 형식 및 문자열 간의 변환을 사용자 지정할 수 있도록 합니다.  
  
 상속 된 메서드 외에도 `IUnknown`, `IDebugFormatter` 인터페이스는 다음 메서드를 노출 합니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[IDebugFormatter::GetStringForVariant](../../winscript/reference/idebugformatter-getstringforvariant.md)|지정된 된 변형 값을 나타내는 문자열을 반환 합니다.|  
|[IDebugFormatter::GetVariantForString](../../winscript/reference/idebugformatter-getvariantforstring.md)|지정된 된 문자열을 포함 하는 VARIANT를 반환 합니다.|  
|[IDebugFormatter::GetStringForVarType](../../winscript/reference/idebugformatter-getstringforvartype.md)|지정한 VARTYPE 값을 나타내는 문자열을 반환 합니다.|