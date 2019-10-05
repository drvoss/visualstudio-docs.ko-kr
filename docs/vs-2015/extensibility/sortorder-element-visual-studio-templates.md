---
title: SortOrder 요소 (Visual Studio 템플릿) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SortOrder
helpviewer_keywords:
- SortOrder element [Visual Studio Templates]
- <SortOrder> element [Visual Studio Templates]
ms.assetid: 151932c1-f08a-4f78-a8d0-bd2f32211a9c
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 825ec785a83cae0aaa8a31ae1375e956228b634e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68205522"
---
# <a name="sortorder-element-visual-studio-templates"></a>SortOrder 요소(Visual Studio 템플릿)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

표시 된 대로 동일한 범주의 다른 템플릿 간에 템플릿을 정렬 하는 데 사용 되는 값을 지정 합니다 **새 프로젝트** 하거나 **새 항목 추가** 대화 상자.  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<SortOrder>  
  
## <a name="syntax"></a>구문  
  
```  
<SortOrder> ... </SortOrder>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|필수적 요소입니다.<br /><br /> 템플릿을 분류하고 **새 프로젝트** 또는 **새 항목 추가** 대화 상자에서 템플릿이 표시되는 방식을 정의합니다.|  
  
## <a name="text-value"></a>텍스트 값  
 텍스트 값은 필수입니다.  
  
 `integer` 정렬 순서 값을 나타내는입니다.  
  
## <a name="remarks"></a>설명  
 `SortOrder`는 선택적 요소입니다. 기본값은 100 및 모든 값에는 10의 배수 여야 합니다.  
  
 `SortOrder` 사용자가 만든 템플릿에 대 한 요소는 무시 됩니다. 모든 사용자가 만든 템플릿 사전순으로 정렬 됩니다.  
  
 낮은 정렬 순서 값이 있는 템플릿 중 하나에 표시 합니다 **새 프로젝트** 하거나 **새 항목 추가** 높은 정렬 순서 값이 있는 템플릿보다 먼저 대화 상자.  
  
## <a name="example"></a>예제  
 다음 예제에서는 표준에 대 한 메타 데이터를 보여 줍니다. [!INCLUDE[csprcs](../includes/csprcs-md.md)] 클래스 템플릿.  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class template.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <SortOrder>290</SortOrder>  
        <DefaultName>MyClass</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem>MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
 이 예제는 `SortOrder` 요소는 상대적으로 높습니다. 가능성이 다른 [!INCLUDE[csprcs](../includes/csprcs-md.md)] 항목 템플릿의 `SortOrder` 보다 낮은 값 `290` 에서이 템플릿을 앞에 표시 되 고 합니다 **새 항목** 대화 상자.  
  
## <a name="see-also"></a>참고 항목  
 [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)   
 [프로젝트 템플릿 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)
