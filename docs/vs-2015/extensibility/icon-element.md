---
title: Icon 요소 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Icon
- Icon element (VSCT XML schema)
ms.assetid: 73c58fe3-d53c-4f4e-b025-29567c6cbb7c
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ca5ced87596b5e40ae70e3faa06e58493da3d8ab
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68203986"
---
# <a name="icon-element"></a>Icon 요소
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

아이콘 태그의 guid 속성에 정의 된 비트맵의 guid입니다.  Id 특성 비트맵 스트립에 슬롯을 선택합니다. 이 요소는 선택적입니다.  이 요소를 생략 하면 변수의 **guidOfficeIcon:msotcidNoIcon** 암시 됩니다.  
  
## <a name="syntax"></a>구문  
  
```  
<Icon guid="guidImages" id="bmpPic1" />  
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  
  
|특성|Description|  
|---------------|-----------------|  
|guid|필수 요소. 정의 된 비트맵의 guid입니다.|  
|id|필수 요소. 비트맵 스트립에 슬롯을 선택합니다.|  
  
### <a name="child-elements"></a>자식 요소  
  
|요소|Description|  
|-------------|-----------------|  
|없음|없음|  
  
### <a name="parent-elements"></a>부모 요소  
  
|요소|Description|  
|-------------|-----------------|  
|[Buttons 요소](../extensibility/buttons-element.md)||  
  
## <a name="see-also"></a>참고 항목  
 [Visual Studio 명령 테이블(.Vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
