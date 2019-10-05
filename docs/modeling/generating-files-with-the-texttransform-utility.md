---
title: TextTransform 유틸리티 사용하여 파일 생성
ms.date: 07/26/2019
ms.topic: conceptual
helpviewer_keywords:
- text templates, TextTransform utility
- TextTransform.exe
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f224419cd92b760d71045859a13887a83115b987
ms.sourcegitcommit: ce1ab8a25c66a83e60eab80ed8e1596fe66dd85c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/29/2019
ms.locfileid: "68606100"
---
# <a name="generate-files-with-the-texttransform-utility"></a>TextTransform 유틸리티를 사용 하 여 파일 생성

TextTransform.exe는 텍스트 템플릿을 변환 하는 데 사용할 수 있는 명령줄 도구입니다. TextTransform.exe를 호출할 때 인수로 텍스트 템플릿 파일의 이름을 지정 합니다. TextTransform.exe는 텍스트 변형 엔진을 호출 하 고 텍스트 템플릿을 처리 합니다. 일반적으로 TextTransform.exe 스크립트에서 호출 됩니다. 그러나이 아니므로 일반적으로 필요한 Visual Studio 또는 빌드 프로세스에서 텍스트 변환 작업을 수행할 수 있습니다.

> [!NOTE]
> 빌드 프로세스의 일부로 텍스트 변환을 수행 하려는 경우에 MSBuild 텍스트 변환 작업을 사용 하는 것이 좋습니다. 자세한 내용은 [빌드 프로세스에서 코드 생성](../modeling/code-generation-in-a-build-process.md)합니다. Visual Studio가 설치 된 컴퓨터에서 응용 프로그램 또는 텍스트 템플릿을 변형할 수 있는 Visual Studio 확장을 작성할 수 있습니다. 자세한 내용은 [사용자 지정 호스트를 사용 하 여 텍스트 템플릿 처리](../modeling/processing-text-templates-by-using-a-custom-host.md)합니다.

TextTransform.exe은 다음 디렉터리에 있습니다.
 
::: moniker range=">=vs-2019"

**Filefiles (x86) \Microsoft Visual Studio\2019\Professional\Common7\IDE**

Professional edition의 경우 또는

**Filefiles (x86) \Microsoft Visual Studio\2019\Enterprise\Common7\IDE**

Enterprise edition의 경우.

::: moniker-end
 
::: moniker range="vs-2017"

**\Program Files (x86)\Microsoft Visual Studio\2017\Professional\Common7\IDE**

Professional edition의 경우 또는

**\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE**

Enterprise edition의 경우.

Visual Studio의 이전 버전에서는 파일은 다음 위치에 있습니다.

**\Program Files (x86)\Common Files\Microsoft Shared\TextTemplating\{version}**

여기서 {version} 설치 된 이전 버전에 따라 달라 집니다.

::: moniker-end

## <a name="syntax"></a>구문

```
TextTransform [<options>] <templateName>
```

### <a name="parameters"></a>매개 변수

|**인수**|**설명**|
|-|-|
|`templateName`|변환 하려는 템플릿 파일의 이름을 식별 합니다.|

|**옵션**|**설명**|
|-|-|
|**-out** \<filename>|변환의 출력을 쓸 파일입니다.|
|**-r** \<assembly>|컴파일 및 텍스트 템플릿을 실행에 사용 되는 어셈블리입니다.|
|**-u** \<namespace>|서식 파일을 컴파일하는 데 사용 되는 네임 스페이스입니다.|
|**-I** \<includedirectory>|지정 된 텍스트 템플릿에 포함 된 텍스트 템플릿을 포함 하는 디렉터리입니다.|
|**-P** \<referencepath>|또는 사용 하 여 텍스트 템플릿 내에서 지정 된 어셈블리에 대 한 검색할 디렉터리를 **-r** 옵션입니다.<br /><br /> 예를 들어, Visual Studio API를 사용 하는 어셈블리를 포함 하려면 사용<br /><br /> `-P "%VSSHELLFOLDER%\Common7\IDE\PublicAssemblies"`|
|**-dp** \<processorName>!\<className>!\<assemblyName&#124;codeBase>|이름, 전체 형식 이름 및 텍스트 템플릿 내에서 사용자 지정 지시문을 처리 하는 데 사용할 수 있는 지시문 프로세서의 어셈블리입니다.|
|**-a** [processorName]![directiveName]!\<parameterName>!\<parameterValue>|지시문 프로세서에 대 한 매개 변수 값을 지정 합니다. 매개 변수 이름 및 값을 지정 하면 매개 변수가 모든 지시문 프로세서에 제공 됩니다. 지시문 프로세서를 지정 하는 매개 변수는 지정 된 프로세서 에서만 사용할 수 있습니다. 지시문 이름을 지정 하는 경우 지정된 된 지시문을 처리 되는 경우에 매개 변수는 사용할 수 있습니다.<br /><br /> 지시문 프로세서 또는 텍스트 템플릿에서 매개 변수 값에 액세스 하려면 사용 하 여 [ITextTemplatingEngineHost.ResolveParameterValue](/previous-versions/visualstudio/visual-studio-2012/bb126369\(v\=vs.110\))합니다. 텍스트 템플릿을 포함 `hostspecific` 템플릿 지시문에서에서 메시지를 호출 하 고 `this.Host`입니다. 예를 들어 다음과 같습니다.<br /><br /> `<#@template language="c#" hostspecific="true"#> [<#= this.Host.ResolveParameterValue("", "", "parameterName") #>]`.<br /><br /> 항상 입력의 '!' 옵션 프로세서와 지시문 이름이 생략 한 경우에 표시 합니다. 예를 들어 다음과 같습니다.<br /><br /> `-a !!param!value`|
|**-h**|도움말을 제공 합니다.|

## <a name="related-topics"></a>관련 항목

|작업|항목|
|-|-|
|Visual Studio 솔루션에서 파일을 생성 합니다.|[T4 텍스트 템플릿을 사용하여 디자인 타임 코드 생성](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|
|고유한 데이터 소스를 변형하는 지시문 프로세서를 작성합니다.|[T4 텍스트 변환 사용자 지정](../modeling/customizing-t4-text-transformation.md)|
|텍스트 템플릿을 사용자 고유의 응용 프로그램에서 호출할 수 있는 텍스트 템플릿 호스트를 작성 합니다.|[사용자 지정 호스트를 사용하여 텍스트 템플릿 처리](../modeling/processing-text-templates-by-using-a-custom-host.md)|
