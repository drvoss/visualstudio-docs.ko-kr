---
title: TemplateID 요소 (Visual Studio 템플릿) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateID
helpviewer_keywords:
- <TemplateID> element [Visual Studio Templates]
- TemplateID element [Visual Studio Templates]
ms.assetid: 6ca24b4e-0325-4a9e-855e-0cbbe7361d8f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e8207b72d7bb818a5d153abdd56914fd6b2a3f08
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66316549"
---
# <a name="templateid-element-visual-studio-templates"></a>TemplateID 요소(Visual Studio 템플릿)
항목 템플릿의 그룹으로 분류 되는 항목 템플릿에 대 한 식별자를 지정 합니다 [TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md) 요소입니다.

 \<VSTemplate> \<TemplateData> \<TemplateID>

## <a name="syntax"></a>구문

```
<TemplateID> ... </TemplateID>
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성
 없음

### <a name="child-elements"></a>자식 요소
 없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|필수적 요소입니다.<br /><br /> 템플릿을 분류하고 **새 프로젝트** 또는 **새 항목 추가** 대화 상자에서 템플릿이 표시되는 방식을 정의합니다.|

## <a name="text-value"></a>텍스트 값
 A `string` 하 여 항목 템플릿 그룹으로 분류 되는 항목 템플릿에 대 한 식별자를 나타내는 `TemplateGroupID` 요소입니다.

## <a name="remarks"></a>설명
 `TemplateID`는 선택적 요소입니다.

 .Vstemplate 파일을 생략 하는 경우는 `TemplateID` 요소인 경우 [이름](../extensibility/name-element-visual-studio-templates.md) 요소 템플릿에 대 한 식별자로 사용 됩니다.

 값을 `TemplateID` 프로젝트 시스템 등록 함께 사용 하는 요소 (HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\Projects\\)에 표시 되는 템플릿을 필터링 하는 **새 항목 추가** 대화 상자입니다.

## <a name="see-also"></a>참고 항목
- [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)
- [프로젝트 템플릿 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)