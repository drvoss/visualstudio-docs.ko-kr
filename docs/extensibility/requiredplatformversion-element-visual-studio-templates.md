---
title: RequiredPlatformVersion 요소 (Visual Studio 템플릿) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 6f0e4986-3157-4bba-aed3-c28413ebe976
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cd166e41588ee440d9e0a1e90494aaa8f5091909
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66334149"
---
# <a name="requiredplatformversion-element-visual-studio-templates"></a>RequiredPlatformVersion 요소 (Visual Studio 템플릿)
프로젝트 템플릿이 제대로 작동 하는 데 필요한 운영 체제의 최소 버전을 지정 합니다. 이 요소는 프로젝트 템플릿을 만드는 데 [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] 앱.

 `RequiredPlatformVersion` 운영 체제의 버전을 사용 하 여 직접 값과 비교 됩니다. 경우는 `RequiredPlatformVersion` 운영 체제 버전 보다 높은 템플릿이 표시 되지 않습니다 합니다 **새 프로젝트** 대화 상자. 에 대 한 템플릿을 지정 하려면 [!INCLUDE[win8](../debugger/includes/win8_md.md)] 더 높고, 설정 또는 `RequiredPlatformVersion` 6.2.0 하 합니다. 에 대 한 템플릿을 지정 하려면 [!INCLUDE[win81](../debugger/includes/win81_md.md)] 더 높고, 설정 또는 `RequiredPlatformVersion` 를 6.3.0으로 합니다.

 지정 하는 템플릿 `RequiredPlatformVersion`= 8 이전 고객와 호환 되는 [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] 템플릿.

 VSTemplate TemplateData... TargetPlatformName RequiredPlatformVersion

## <a name="syntax"></a>구문

```xml
<RequiredPlatformVersion> OperatingSystem </RequiredPlatformVersion>
```

## <a name="attributes-and-elements"></a>특성 및 요소
 없음

### <a name="attributes"></a>특성
 없음

### <a name="child-elements"></a>자식 요소
 없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[TemplatePlatformName](../extensibility/templatedata-element-visual-studio-templates.md)|프로젝트 템플릿의 대상 플랫폼을 지정합니다.|

## <a name="text-value"></a>텍스트 값
 텍스트 값은 필수입니다.

## <a name="remarks"></a>설명
 이 텍스트 템플릿에 필요한 최소 운영 체제 버전을 지정 합니다.

## <a name="example"></a>예제
 이 예제에서는 프로젝트 템플릿이 [!INCLUDE[win8](../debugger/includes/win8_md.md)] 이상을 대상으로 하도록 지정합니다.

```xml
<VSTemplate Type="Project" Version="3.0.0"    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <TargetPlatformName>Windows</TargetPlatformName>
            <RequiredPlatformVersion>6.3.0</RequiredPlatformVersion>

    </TemplateData>
    <TemplateContent>

    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>참고자료
- [TargetPlatformName 요소 (Visual Studio 템플릿)](../extensibility/targetplatformname-element-visual-studio-templates.md)
- [프로젝트 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)
- [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)