---
title: DefaultName 요소 (Visual Studio 템플릿) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#DefaultName
helpviewer_keywords:
- DefaultName element [Visual Studio project templates]
ms.assetid: 0ff056c8-b9d2-4747-9308-92adf1811491
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0bc3a18c47b78a312f3bca3762cc4ff3d658a70e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68185294"
---
# <a name="defaultname-element-visual-studio-templates"></a>DefaultName 요소(Visual Studio 템플릿)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

만들 때 프로젝트 또는 항목에 대 한 Visual Studio 프로젝트 시스템에서 생성 하는 이름을 지정 합니다.  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<DefaultName>  
  
## <a name="syntax"></a>구문  
  
```  
<DefaultName>  
    Default Project Name  
</DefaultName>  
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
  
 이 텍스트는 프로젝트 또는 항목의 기본 이름을 지정합니다.  
  
## <a name="remarks"></a>설명  
 `DefaultName`는 선택적 요소입니다.  
  
 이 요소는 프로젝트의 경우 디스크에서 프로젝트를 저장 하는 디렉터리의 이름을 지정 합니다. 항목에 대 한 소스 파일의 파일 이름을 지정 합니다.  
  
 프로젝트 또는 항목을 만들 때 사용 하 여 기본 이름을 수정할 수 있습니다는 **이름을** 에서 사용할 수 있는 옵션을 **새 프로젝트** 대화 상자 또는 **새 항목 추가** 대화 상자입니다.  
  
 프로젝트 시스템에서 프로젝트 또는 항목에 대 한 기본 이름을 생성 하지 않으려면 설정한 합니다 [ProvideDefaultName](../extensibility/providedefaultname-element-visual-studio-templates.md) 요소를 `False`입니다.  
  
## <a name="example"></a>예제  
 다음 예제에 대 한 표준 항목 템플릿에 대 한 메타 데이터를 [!INCLUDE[csprcs](../includes/csprcs-md.md)] 클래스입니다.  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <DefaultName>MyClass.cs</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem ReplaceParameters="true">MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>참고 항목  
 [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)   
 [프로젝트 템플릿 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)
