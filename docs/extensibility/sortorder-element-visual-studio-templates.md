---
title: SortOrder 요소 (Visual Studio 템플릿) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SortOrder
helpviewer_keywords:
- SortOrder element [Visual Studio Templates]
- <SortOrder> element [Visual Studio Templates]
ms.assetid: 151932c1-f08a-4f78-a8d0-bd2f32211a9c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2875bcb4583c1d2ec47a935d1a8bb4f0de109a92
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72719920"
---
# <a name="sortorder-element-visual-studio-templates"></a>SortOrder 요소(Visual Studio 템플릿)
**새 프로젝트** 또는 **새 항목 추가** 대화 상자에 표시 된 것 처럼 동일한 범주의 다른 템플릿 간에 템플릿을 정렬 하는 데 사용 되는 값을 지정 합니다.

 \<VSTemplate > \<TemplateData > \<SortOrder >

## <a name="syntax"></a>구문

```
<SortOrder> ... </SortOrder>
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성
 없음.

### <a name="child-elements"></a>자식 요소
 없음.

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|필수적 요소입니다.<br /><br /> 템플릿을 분류하고 **새 프로젝트** 또는 **새 항목 추가** 대화 상자에서 템플릿이 표시되는 방식을 정의합니다.|

## <a name="text-value"></a>텍스트 값
 텍스트 값은 필수입니다.

 정렬 순서 값을 나타내는 `integer`입니다.

## <a name="remarks"></a>주의
 `SortOrder`는 선택적 요소입니다. 기본값은 100이 고 모든 값은 10의 배수 여야 합니다.

 사용자가 만든 템플릿의 `SortOrder` 요소는 무시 됩니다. 사용자가 만든 모든 템플릿은 사전순으로 정렬 됩니다.

 정렬 순서가 낮은 템플릿이 **새 프로젝트** 또는 **새 항목 추가** 대화 상자에서 정렬 순서 값이 높은 템플릿 앞에 표시 됩니다.

## <a name="example"></a>예제
 다음 예제에서는 표준 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 클래스 템플릿에 대 한 메타 데이터를 보여 줍니다.

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

 이 예제에서 `SortOrder` 요소는 상대적으로 높습니다. 다른 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 항목 템플릿의 `SortOrder` 값이 `290` 보다 낮고 **새 항목** 대화 상자에서이 템플릿 앞에 표시 될 수 있습니다.

## <a name="see-also"></a>참조
- [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)
- [프로젝트 템플릿 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)