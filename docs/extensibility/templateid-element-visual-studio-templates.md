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
ms.openlocfilehash: c0e404921d1ed74db2a1f23117242f49a07206c2
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72718734"
---
# <a name="templateid-element-visual-studio-templates"></a>TemplateID 요소(Visual Studio 템플릿)
템플릿 [groupid](../extensibility/templategroupid-element-visual-studio-templates.md) 요소를 기준으로 항목 템플릿의 그룹으로 분류 되는 항목 템플릿에 대 한 식별자를 지정 합니다.

 \<VSTemplate > \<TemplateData > \<TemplateID >

## <a name="syntax"></a>구문

```
<TemplateID> ... </TemplateID>
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
 @No__t_1 요소를 기준으로 항목 템플릿의 그룹으로 분류 되는 항목 템플릿의 식별자를 나타내는 `string`입니다.

## <a name="remarks"></a>주의
 `TemplateID`는 선택적 요소입니다.

 .Vstemplate 파일에서 `TemplateID` 요소를 생략 하면 [Name](../extensibility/name-element-visual-studio-templates.md) 요소가 템플릿의 식별자로 사용 됩니다.

 @No__t_0 요소 값은 프로젝트 시스템 등록 (HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\Projects \\)과 함께 **새 항목 추가** 대화 상자에 표시 되는 템플릿을 필터링 하는 데 사용 됩니다.

## <a name="see-also"></a>참조
- [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)
- [프로젝트 템플릿 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)