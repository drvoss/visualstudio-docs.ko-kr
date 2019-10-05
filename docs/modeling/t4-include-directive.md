---
title: T4 Include 지시문
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1a3ab6aa4cd116c779cac4367d1eeb9a187edaeb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62964094"
---
# <a name="t4-include-directive"></a>T4 Include 지시문

텍스트 템플릿에서 Visual Studio에서 사용 하 여 다른 파일에서 텍스트를 포함할 수 있습니다는 `<#@include#>` 지시문입니다. 텍스트 템플릿에서 첫 번째 클래스 기능 블록 `include` 앞의 어느 곳에나`<#+ ... #>` 지시문을 둘 수 있습니다. 포함된 파일에는 `include` 지시문 및 다른 지시문도 포함할 수 있습니다. 따라서 템플릿 간에 템플릿 코드와 상용구 텍스트를 공유할 수 있습니다.

## <a name="using-include-directives"></a>include 지시문 사용

```
<#@ include file="filePath" [once="true"] #>
```

- `filePath`는 현재 템플릿 파일에 대해 상대적인 경로이거나 절대 경로일 수 있습니다.

   또한 특정 Visual Studio 확장 include 파일을 검색할 자신의 디렉터리를 지정할 수 있습니다. 다음 폴더가 포함 목록에 추가 됩니다 Visualization and Modeling SDK (DSL 도구)를 설치한 경우에 예를 들어: `Program Files\Microsoft Visual Studio 10.0\Common7\IDE\Extensions\Microsoft\DSL SDK\DSL Designer\11.0\TextTemplates`합니다.

   이러한 추가적인 포함 폴더는 포함 파일의 파일 확장명에 따라 달라질 수 있습니다. 예를 들어 DSL 도구의 포함 폴더에서는 파일 확장명이 `.tt`인 파일이 있는 포함 파일에만 액세스할 수 있습니다.

- `filePath`는 "%"로 구분되는 환경 변수를 포함할 수 있습니다. 예를 들어:

  ```
  <#@ include file="%HOMEPATH%\MyIncludeFile.t4" #>
  ```

- 포함 파일의 이름에 `".tt"` 확장명을 사용할 필요가 없습니다.

   포함 파일에 `".t4"`와 같은 다른 확장명을 사용할 수 있습니다. 이므로 추가 하는 경우는 `.tt` Visual Studio 프로젝트에 파일 자동으로 설정 하는 해당 **사용자 지정 도구** 속성을 `TextTemplatingFileGenerator`입니다. 일반적으로 포함된 파일을 개별적으로 변형하지 않을 수 있습니다.

   반면에 파일 확장명에 따라 포함 파일을 검색할 추가 폴더가 영향을 받는 경우가 있다는 사실에 유의해야 합니다. 이는 다른 파일이 들어 있는 포함된 파일이 있는 경우 중요할 수 있습니다.

- 포함된 내용은 포함하는 텍스트 템플릿의 일부인 것처럼 처리됩니다. 그러나 `<#+...#>` 지시문 뒤에 일반 텍스트와 표준 제어 블록이 있는 경우에도 클래스 기능 블록 `include`이 포함된 파일을 포함할 수 있습니다.

- 사용 하 여 `once="true"` 두 개 이상의 다른 포함 파일에서 호출 되는 경우에 템플릿을 포함 한 번만 인지 확인 합니다.

   쉽게에 포함할 수 있는 재사용 가능한 T4 코드 조각 라이브러리를 구축 하는 걱정 없이이 기능을 사용 하면 다른 코드 조각에 이미 포함 합니다.  예를 들어, 템플릿 처리 및 C# 생성을 처리 하는 매우 세분화 된 코드 조각 라이브러리를 있다고 가정 합니다.  따라서 이러한 값은 모든 더 응용 프로그램별 템플릿에서 사용할 수 있는 예외를 생성 하는 등 일부 작업 관련 유틸리티에서 사용 됩니다. 종속성 그래프를 그리는 경우 일부 코드 조각이 여러 번 포함될 수 있습니다. 그러나 `once` 매개 변수가 이후에 포함되지 않도록 방지합니다.

  **MyTextTemplate.tt:**

```
<#@ output extension=".txt" #>
Output message 1 (from top template).
<#@ include file="TextFile1.t4"#>
Output message 5 (from top template).
<#
   GenerateMessage(6); // defined in TextFile1.t4
   AnotherGenerateMessage(7); // defined in TextFile2.t4
#>
```

 **TextFile1.t4:**

```
   Output Message 2 (from included file).
<#@ include file="TextFile2.t4" #>
   Output Message 4 (from included file).
<#+ // Start of class feature control block.
void GenerateMessage(int n)
{
#>
   Output Message <#= n #> (from GenerateMessage method).
<#+
}
#>
```

 **TextFile2.t4:**

```
        Output Message 3 (from included file 2).
<#+ // Start of class feature control block.
void AnotherGenerateMessage(int n)
{
#>
       Output Message <#= n #> (from AnotherGenerateMessage method).
<#+
}
#>
```

 **결과적으로 생성 된 파일, MyTextTemplate.txt:**

```
Output message 1 (from top template).
   Output Message 2 (from included file).
        Output Message 3 (from included file 2).

   Output Message 4 (from included file).

Output message 5 (from top template).
   Output Message 6 (from GenerateMessage method).
       Output Message 7 (from AnotherGenerateMessage method).
```

## <a name="msbuild"></a> MSBuild 및 Visual Studio에서 프로젝트 속성 사용
 Visual Studio 매크로 $ (solutiondir)와 같은 include 지시문에서 사용할 수 있지만 MSBuild에서 작동 하지 않습니다. 빌드 컴퓨터에서 템플릿을 변형하려는 경우 대신 프로젝트 속성을 사용해야 합니다.

 프로젝트 속성을 정의하기 위해 .csproj 또는 .vbproj 파일을 편집합니다. 이 예제에서는 `myIncludeFolder`라는 속성을 정의합니다.

```xml
<!-- Define a project property, myIncludeFolder: -->
<PropertyGroup>
    <myIncludeFolder>$(MSBuildProjectDirectory)\..\libs</myIncludeFolder>
</PropertyGroup>

<!-- Tell the MSBuild T4 task to make the property available: -->
<ItemGroup>
    <T4ParameterValues Include="myIncludeFolder">
      <Value>$(myIncludeFolder)</Value>
    </T4ParameterValues>
  </ItemGroup>
```

 이제 Visual Studio 및 MSBuild에서 모두 올바르게 변환된 텍스트 템플릿의 프로젝트 속성을 사용할 수 있습니다.

```
<#@ include file="$(myIncludeFolder)\defs.tt" #>
```
