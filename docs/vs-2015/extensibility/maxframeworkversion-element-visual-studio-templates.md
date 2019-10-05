---
title: MaxFrameworkVersion 요소 (Visual Studio 템플릿) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <MaxFrameworkVersion> Element (Visual Studio Templates)
- MaxFrameworkVersion Element (Visual Studio Templates)
ms.assetid: f732a9d3-fc29-405b-9298-01ea83fc58b8
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4a1c27e42574429dbb6b2eaeb140db484bf29db5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68194324"
---
# <a name="maxframeworkversion-element-visual-studio-templates"></a>MaxFrameworkVersion 요소(Visual Studio 템플릿)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

서식 파일에 필요한.NET Framework의 최대 버전을 지정 합니다. 템플릿이 표시 되는지 여부를 결정 합니다 **템플릿** 부분을 **새 프로젝트 추가** 대화 상자에서 선택한 값을 기반으로 **대상 프레임 워크 버전** 상자는 **새 프로젝트 추가** 대화 상자.  
  
 \<VSTemplate>  
 \<MaxFrameworkVersion>  
  
## <a name="syntax"></a>구문  
  
```  
<MaxFrameworkVersion> ... </MaxFrameworkVersion>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|필수적 요소입니다.<br /><br /> 템플릿을 분류 하 고에서 표시 되는 방식을 정의 합니다 **새 프로젝트** 또는 **새 항목 추가** 대화 상자.|  
  
## <a name="text-value"></a>텍스트 값  
 텍스트 값은 필수입니다.  
  
 텍스트는 템플릿에 의해 허용 되는.NET Framework의 가장 높은 버전 번호 여야 합니다.  
  
## <a name="remarks"></a>설명  
 `MaxFrameworkVersion`는 선택적 요소입니다. 요소는 `TemplateData` .vstemplate 파일의 섹션에 대 한 필터로 작동 합니다 **템플릿** 의 섹션을 **새 프로젝트 추가** 대화 상자. 해당.NET Framework 요구 사항은 템플릿만 미만 `MaxFrameworkVersion` 요소 값이 표시 됩니다에서 선택한 값을 기반으로 합니다 **대상 프레임 워크 버전** 상자는 **새 프로젝트 추가**대화 상자. `MaxFrameworkVersion` 를 하지 못하도록 실수로 최신 버전의.NET Framework를 사용 하 여 사용할 때 표시 되지 않도록 템플릿을 일으킬 필요 하지 않은 요소를 생략 해야 합니다.  
  
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
        <MaxFrameworkVersion>3.5</MaxFrameworkVersion>  
        <DefaultName>MyClass</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem>MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
 이 예제에서는 서식 파일을 여는 데 필요한.NET Framework의 최대 버전 표시 `MaxFrameworkVersion`은 3.5입니다. 위의 템플릿을 선택 3.0 또는 3.5에서 하는 경우에 표시 됩니다는 **대상 프레임 워크 버전** 상자에 **새 프로젝트 추가** 대화 상자.  
  
## <a name="see-also"></a>관련 항목  
 [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)   
 [프로젝트 템플릿 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)
