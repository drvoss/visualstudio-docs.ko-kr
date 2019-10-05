---
title: ProvideDefaultName 요소 (Visual Studio 템플릿) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProvideDefaultName
helpviewer_keywords:
- ProvideDefaultName element [Visual Studio project templates]
ms.assetid: 7b0e7b20-fd6b-42e2-81d0-e5100cea0528
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0bd18dd979436b02cc12a4dab5439bdb5f371e2d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68193882"
---
# <a name="providedefaultname-element-visual-studio-templates"></a>ProvideDefaultName 요소(Visual Studio 템플릿)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

지정 여부는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 프로젝트 시스템의 템플릿에 대 한 기본 이름이 생성 됩니다는 **새 항목 추가** 또는 **새 프로젝트** 대화 상자.  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<ProvideDefaultName>  
  
## <a name="syntax"></a>구문  
  
```  
<ProvideDefaultName> true/false </ProvideDefaultName>  
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
  
 텍스트 여야 `true` 또는 `false`의 템플릿에 대 한 기본 이름을 생성할 것인지 여부를 나타내는 합니다 **새 항목 추가** 또는 **새 프로젝트** 대화 상자.  
  
## <a name="remarks"></a>설명  
 `ProvideDefaultName`는 선택적 요소입니다. 기본값은 `true`입니다.  
  
 경우는 `ProvideDefaultName` 요소는 `false`의 **이름** 상자에는 **새 항목 추가** 및 **새 프로젝트** 값을 포함 하는 대화 상자 `<Enter_name>`합니다.  
  
 사용 된 [DefaultName](../extensibility/defaultname-element-visual-studio-templates.md) 항목 또는 프로젝트의 기본 이름을 지정 하는 요소는 **새 항목 추가** 및 **새 프로젝트** 대화 상자.  
  
## <a name="example"></a>예제  
 다음 코드 예제에서는 합니다 `ProvideDefaultName` 요소를 `false`입니다.  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <ProvideDefaultName>false</ProvideDefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem>MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>관련 항목  
 [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)   
 [프로젝트 템플릿 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)
