---
title: GuidSymbol 요소 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, GuidSymbol
- GuidSymbol element (VSCT XML schema)
ms.assetid: 11fb3545-8974-4776-9a54-6b6e7739ae31
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5f11ed48d9dcf961228957cf15db3815c00d14d7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68204218"
---
# <a name="guidsymbol-element"></a>GuidSymbol 요소
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`GuidSymbol` 요소 메뉴, 그룹 또는 명령을 나타내는 guid: id 쌍의 GUID를 포함 합니다. ID에서 제공 되는 `IDSymbol` 요소에는 `GuidSymbol` 요소입니다. `GuidSymbol` 요소에는 `name` 에 포함 된 GUID 친숙 한 이름을 제공 하는 특성을 `value` 특성.  
  
## <a name="syntax"></a>구문  
  
```  
<GuidSymbol name="guidMyCommandSet" value="{xxxxxxxxxxxxx-xxxx-xxxx-xxxxxxxxxxxx}">  
  <IDSymbol>... </IDSymbol>  
  <IDSymbol>... </IDSymbol>  
</GuidSymbol>  
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  
  
|특성|Description|  
|---------------|-----------------|  
|name|필수 요소. GUID 기호와의 이름입니다.|  
|value|필수 요소. GUID 기호와의 GUID입니다.|  
  
### <a name="child-elements"></a>자식 요소  
  
|요소|Description|  
|-------------|-----------------|  
|[IDSymbol 요소](../extensibility/idsymbol-element.md)|메뉴, 그룹 또는 명령을 나타내는 guid: id 쌍의 ID를 포함 합니다.|  
  
### <a name="parent-elements"></a>부모 요소  
  
|요소|설명|  
|-------------|-----------------|  
|[Symbols 요소](../extensibility/symbols-element.md)|그룹 `GuidSymbol` .vsct 파일의 요소입니다.|  
  
## <a name="remarks"></a>설명  
 일반적으로.vsct 파일 포함 세 `GuidSymbol` 요소에서 해당 `Symbols` 섹션, 패키지 자체에 대해 하나씩, 명령 집합 (메뉴, 그룹 및 명령을 사용할 수 있도록 패키지의 컬렉션)에 대 한 및 제공 하는 비트맵에 대 한 단추 및 기타 시각적 구성 요소에 대 한 아이콘입니다. 모든 `IDSymbol` 요소에는 주어진 `GuidSymbol` 요소는 고유 해야 합니다. `value`합니다. 그러나 `IDSymbol` 으로 부모가 서로 다른 패키지에 동일한 값을 가진 요소가 있을 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [Visual Studio 명령 테이블(.Vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
