---
title: 요소 (Visual Studio 템플릿)를 참조 | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#References
helpviewer_keywords:
- <References> element [Visual Studio Templates]
- References element [Visual Studio Templates]
ms.assetid: 1969146d-46bf-422d-8d46-0e9493925003
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e2ab5c3decc201958bd939a0a9d66dd65a5ef1c6
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66334416"
---
# <a name="references-element-visual-studio-templates"></a>References 요소 (Visual Studio 템플릿)
서식 파일 프로젝트에 추가 하는 어셈블리 참조를 그룹화 합니다.

 \<VSTemplate> \<TemplateContent> \<References>

## <a name="syntax"></a>구문

```xml
<References>
    <Reference>... </Reference>
    <Reference>... </Reference>
    ...
</References>
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성
 없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[참조](../extensibility/reference-element-visual-studio-templates.md)|필수적 요소입니다.<br /><br /> 항목이 프로젝트에 추가될 때 추가할 어셈블리 참조를 지정합니다. 하나 이상 이어야 `Reference` 의 요소를 `References` 요소입니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|서식 파일의 내용을 지정합니다.|

## <a name="remarks"></a>설명
 `References`은 `TemplateContent`의 선택적 자식 요소입니다.

 `Reference` 및 `References` 요소에만 사용할 수 있습니다 *.vstemplate* 파일을 `Type` 특성의 값 `Item`합니다.

## <a name="example"></a>예제
 다음 예제는 `TemplateContent` 항목 템플릿의 요소입니다. 이 XML에 대 한 참조를 추가 합니다 *System.dll* 하 고 *System.Data.dll* 어셈블리입니다.

```xml
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

## <a name="see-also"></a>참고자료
- [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)
- [프로젝트 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)
