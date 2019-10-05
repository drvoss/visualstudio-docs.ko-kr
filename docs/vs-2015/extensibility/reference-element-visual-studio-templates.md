---
title: 요소 (Visual Studio 템플릿)를 참조 합니다. | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Reference
helpviewer_keywords:
- Reference element [Visual Studio templates]
- <Reference> element [Visual Studio templates]
ms.assetid: 852772ea-c324-42e9-8c8a-6d565414a109
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c3d67fd19122e160159a6f636516dbca582fe31d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68193837"
---
# <a name="reference-element-visual-studio-templates"></a>Reference 요소(Visual Studio 템플릿)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

항목이 프로젝트에 추가될 때 추가할 어셈블리 참조를 지정합니다.  
  
 \<VSTemplate>  
 \<TemplateContent>  
 \<참조 >  
 \<참조 >  
  
## <a name="syntax"></a>구문  
  
```  
<Reference>  
    <Assembly> ... </Assembly>  
</Reference>  
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  
 없음  
  
### <a name="child-elements"></a>자식 요소  
  
|요소|Description|  
|-------------|-----------------|  
|[어셈블리](../extensibility/assembly-element-visual-studio-templates.md)|필수적 요소입니다.<br /><br /> 서식 파일 프로젝트에 해당 어셈블리 참조를 추가 하는 어셈블리에 대 한 정보를 지정 합니다. 하나는 있어야 `Assembly` 요소에서 모든 `Reference` 요소입니다.|  
  
### <a name="parent-elements"></a>부모 요소  
  
|요소|설명|  
|-------------|-----------------|  
|[참조](../extensibility/references-element-visual-studio-templates.md)|서식 파일 프로젝트에 추가 하는 어셈블리 참조를 그룹화 합니다.|  
  
## <a name="remarks"></a>설명  
 `Reference`은 `References`의 필수 자식 요소입니다.  
  
 `Reference` 하 고 `References` 요소.vstemplate 파일에서 사용할 수 있습니다를 `Type` 특성 값 `Item`합니다.  
  
## <a name="example"></a>예제  
 다음 예제는 `TemplateContent` 항목 템플릿의 요소입니다. 이 XML에는 System.dll 및 System.Data.dll 어셈블리에 대 한 참조를 추가합니다.  
  
```  
<TemplateContent>  
    <References>  
        <Reference>  
            <Assembly>  
                System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
            </Assembly>  
        </Reference>  
        <Reference>  
            <Assembly>  
                System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
            </Assembly>  
        </Reference>  
    </References>  
    ...  
</TemplateContent>  
```  
  
## <a name="see-also"></a>관련 항목  
 [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)   
 [프로젝트 템플릿 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)
