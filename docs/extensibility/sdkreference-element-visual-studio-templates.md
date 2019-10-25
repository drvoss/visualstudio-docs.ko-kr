---
title: SDKReference 요소 (Visual Studio 템플릿) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 72c8b352-0b7a-42b3-ba5d-2a2d1e90c34b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3cf1b3bed942894e20132ecd7b06c1884caa9a93
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720087"
---
# <a name="sdkreference-element-visual-studio-templates"></a>SDKReference 요소(Visual Studio 템플릿)
항목 템플릿에서 SDK 참조를 사용하도록 지정합니다.

## <a name="syntax"></a>구문

```xml
<VSTemplate>
    <TemplateContent>
        <References>
            <Reference>
                <SDKReference>SDKname</SDKReference>
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
|[참조](../extensibility/reference-element-visual-studio-templates.md)|항목이 프로젝트에 추가될 때 추가할 어셈블리 참조를 지정합니다.|

## <a name="text-value"></a>텍스트 값
 텍스트 값은 필수입니다.

## <a name="remarks"></a>주의
 이 텍스트는 항목 템플릿이 인스턴스화될 때 프로젝트에 추가할 SDK 참조를 지정합니다.

```xml
<VSTemplate Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">
    <TemplateData> . . . </TemplateData>
    <TemplateContent>
        <References>
            <Reference>
                <SDKReference>Microsoft Visual C++ Runtime Package, Version=11.0.0.0</SDKReference>
...
```

## <a name="see-also"></a>참조
- [References 요소(Visual Studio 템플릿)](../extensibility/references-element-visual-studio-templates.md)
- [Reference 요소(Visual Studio 템플릿)](../extensibility/reference-element-visual-studio-templates.md)
- [프로젝트 템플릿 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)
- [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)