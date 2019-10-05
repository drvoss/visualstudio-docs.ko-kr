---
title: ProvideDefaultName 요소 (Visual Studio 템플릿) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProvideDefaultName
helpviewer_keywords:
- ProvideDefaultName element [Visual Studio project templates]
ms.assetid: 7b0e7b20-fd6b-42e2-81d0-e5100cea0528
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a2a19d6a93b709128e8750b6cea82d067b77db98
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66335816"
---
# <a name="providedefaultname-element-visual-studio-templates"></a>ProvideDefaultName 요소 (Visual Studio 템플릿)
지정 여부는 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 프로젝트 시스템의 템플릿에 대 한 기본 이름이 생성 됩니다는 **새 항목 추가** 또는 **새 프로젝트** 대화 상자.

 \<VSTemplate> \<TemplateData> \<ProvideDefaultName>

## <a name="syntax"></a>구문

```xml
<ProvideDefaultName> true/false </ProvideDefaultName>
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성
 없음

### <a name="child-elements"></a>자식 요소
 없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|필수적 요소입니다.<br /><br /> 템플릿을 분류하고 **새 프로젝트** 또는 **새 항목 추가** 대화 상자에서 템플릿이 표시되는 방식을 정의합니다.|

## <a name="text-value"></a>텍스트 값
 텍스트 값은 필수입니다.

 텍스트 여야 `true` 또는 `false`의 템플릿에 대 한 기본 이름을 생성할 것인지 여부를 나타내는 합니다 **새 항목 추가** 또는 **새 프로젝트** 대화 상자.

## <a name="remarks"></a>설명
 `ProvideDefaultName`는 선택적 요소입니다. 기본값은 `true`입니다.

 경우는 `ProvideDefaultName` 요소는 `false`의 **이름** 상자에는 **새 항목 추가** 및 **새 프로젝트** 값을 포함 하는 대화 상자 `<Enter_name>`합니다.

 사용 된 [DefaultName](../extensibility/defaultname-element-visual-studio-templates.md) 항목 또는 프로젝트의 기본 이름을 지정 하는 요소는 **새 항목 추가** 및 **새 프로젝트** 대화 상자. 때 값을 `ProvideDefaultName` 요소는 `true`, 생략은 `DefaultName` 프로젝트에 대 한 요소는 템플릿 이름, 즉, 값을 사용 하 여 대화 상자를 채웁니다를 [이름](../extensibility/name-element-visual-studio-templates.md) 요소.

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

## <a name="see-also"></a>참고자료
- [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)
- [프로젝트 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)
