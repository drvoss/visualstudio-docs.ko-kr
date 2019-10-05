---
title: 요소를 포함 합니다. | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- Include
helpviewer_keywords:
- Include element (VSCT XML schema)
- VSCT XML schema elements, Include
ms.assetid: c923dfe6-084a-4105-aec1-f0a3f8399c54
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1bdc56c9d0b488bdbe24a8534ab516cc0fc831df
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68203940"
---
# <a name="include-element"></a>Include 요소
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

찾을 수 있는 파일을 지정 하는 Include 요소에 제공 된 현재 파일에 삽입에 대 한 경로 포함 합니다.  모든 기호 및 형식 정의 컴파일된 결과 포함 됩니다.  
  
## <a name="syntax"></a>구문  
  
```csharp  
<Include href="stdidcmd.h" />  
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  
  
|특성|Description|  
|---------------|-----------------|  
|href|필수 요소. 헤더 파일에 대 한 경로:<br /><br /> href="stdidcmd.h"|  
|조건|선택 사항입니다. 참조 [조건부 특성](../extensibility/vsct-xml-schema-conditional-attributes.md)합니다.|  
  
### <a name="child-elements"></a>자식 요소  
  
|요소|Description|  
|-------------|-----------------|  
|없음|없음|  
  
### <a name="parent-elements"></a>부모 요소  
  
|요소|Description|  
|-------------|-----------------|  
|[CommandTable 요소](../extensibility/commandtable-element.md)|명령을 나타내는 요소를 모두 정의-메뉴 항목, 메뉴, 도구 모음 및 콤보 상자,-VSPackage IDE를 제공 하는 합니다.|  
  
## <a name="example"></a>예제  
  
```  
<Include href="PackagePlacements.vsct"/>  
```  
  
## <a name="see-also"></a>참고 항목  
 [Visual Studio 명령 테이블(.Vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
