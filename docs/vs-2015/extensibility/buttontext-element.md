---
title: ButtonText 요소 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- ButtonText element (VSCT XML schema)
- VSCT XML schema elements, ButtonText
ms.assetid: 56aba884-0356-4894-ae4e-32d3938f6865
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ef22471d20df5582fec96c8a685029a1d475a4a4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68184569"
---
# <a name="buttontext-element"></a>ButtonText 요소
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 필드를 사용 하면 다양 한 메뉴에 나타나는 텍스트를 지정할 수 있습니다. 기본적으로 `ButtonText` 요소 메뉴 컨트롤러에 표시 됩니다. `ButtonText` 요소 또한 기본값이 다른 텍스트 필드는 비어 있는 경우. `ButtonText` 기타 텍스트 필드에 지정 된 경우에 요소를 비워 둘 수 없습니다.  
  
## <a name="syntax"></a>구문  
  
```  
<ButtonText>My Command</ButtonText>  
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  
 없음  
  
### <a name="child-elements"></a>자식 요소  
 없음  
  
### <a name="parent-elements"></a>부모 요소  
  
|요소|Description|  
|-------------|-----------------|  
|[Strings 요소](../extensibility/strings-element.md)|텍스트 요소와 같은 그룹화 `ButtonText` 고 `CommandName`입니다.|  
  
## <a name="text-value"></a>텍스트 값  
 텍스트 값을 `ButtonText` 요소 메뉴 항목과 combos, 표시 되는 텍스트에 있는 다른 사용자 인터페이스 (UI) 요소에 대 한 표시 되는 텍스트를 제공 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [Visual Studio 명령 테이블(.Vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
