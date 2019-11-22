---
title: Writing a T4 Text Template | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, syntax
- text templates, guide
- text templates, functions that generate text
ms.assetid: 94328da7-953b-4e92-9587-648543d1f732
caps.latest.revision: 45
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bcd5a4996db4a5e374baabe4f52d5fd1dbac2e5e
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301117"
---
# <a name="writing-a-t4-text-template"></a>T4 텍스트 템플릿 쓰기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

텍스트 템플릿은 해당 템플릿에서 생성될 텍스트를 포함합니다. For example, a template that creates a web page will contain "\<html>…" and all the other standard parts of an HTML page. Inserted into the template are *control blocks*, which are fragments of program code. 제어 블록은 경우에 따라 다른 값을 제공하여 텍스트 부분을 조건부로/반복 적용할 수 있도록 합니다.

 이 구조에서는 템플릿을 쉽게 개발할 수 있습니다. 생성된 파일의 프로토타입으로 시작한 다음 상황에 따라 다른 결과를 생성하는 제어 블록을 증분 방식으로 삽입할 수 있기 때문입니다.

 텍스트 템플릿은 다음 부분으로 구성됩니다.

- **Directives** - elements that control how the template is processed.

- **Text blocks** - content that is copied directly to the output.

- **Control blocks** - program code that inserts variable values into the text, and controls conditional or repeated parts of the text.

  To try the examples in this topic, copy them into a template file as described in [Design-Time Code Generation by using T4 Text Templates](../modeling/design-time-code-generation-by-using-t4-text-templates.md). After editing the template file, save it, and then inspect the output **.txt** file.

## <a name="directives"></a>지시문
 텍스트 템플릿 지시문은 변환 코드 및 출력 파일 생성 방법에 대한 일반 명령을 텍스트 템플릿 생성 엔진에 제공합니다.

 예를 들어 다음 지시문은 출력 파일의 확장명이 .txt여야 하도록 지정합니다.

```

<#@ output extension=".txt" #>
```

 For more information about directives, see [T4 Text Template Directives](../modeling/t4-text-template-directives.md).

## <a name="text-blocks"></a>텍스트 블록
 텍스트 블록은 출력 파일에 텍스트를 직접 삽입합니다. 텍스트 블록에는 특수한 서식이 없습니다. 예를 들어 다음 텍스트 템플릿은 "Hello"라는 단어가 포함된 텍스트 파일을 생성합니다.

```
<#@ output extension=".txt" #>
Hello
```

## <a name="control-blocks"></a>제어 블록
 제어 블록은 템플릿을 변환하는 데 사용되는 프로그램 코드 섹션입니다. 기본 언어는 C#이지만 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]을 사용하려는 경우 파일 시작 부분에 다음 지시문을 작성하면 됩니다.

```
<#@ template language="VB" #>
```

 제어 블록에서 코드를 작성하는 언어는 생성되는 텍스트의 언어와는 관계가 없습니다.

### <a name="standard-control-blocks"></a>표준 제어 블록
 표준 제어 블록은 출력 파일 부분을 생성하는 프로그램 코드 섹션입니다.

 템플릿 파일에서는 텍스트 블록과 표준 제어 블록을 원하는 수만큼 혼합하여 사용할 수 있습니다. 그러나 제어 블록 내에 제어 블록을 배치할 수는 없습니다. 각 표준 제어 블록은 `<# ... #>` 기호로 구분됩니다.

 예를 들어 다음 제어 블록 및 텍스트 블록을 사용하면 출력 파일에 "0, 1, 2, 3, 4 Hello!" 줄이 포함됩니다.

```

      <#
    for(int i = 0; i < 4; i++)
    {
        Write(i + ", ");
    }
    Write("4");
#> Hello!
```

 명시적인 `Write()` 문을 사용하는 대신 텍스트와 코드를 인터리빙할 수 있습니다. The following example prints "Hello!" four times:

```
<#
    for(int i = 0; i < 4; i++)
    {
#>
Hello!
<#
    }
#>
```

 코드에서 `Write();` 문이 허용되는 모든 위치에 텍스트 블록을 삽입할 수 있습니다.

> [!NOTE]
> When you embed a text block within a compound statement such as a loop or conditional, always use braces {...} to contain the text block.

### <a name="expression-control-blocks"></a>식 제어 블록
 식 제어 블록은 식을 평가한 다음 문자열로 변환합니다. 이 문이 출력 파일에 삽입됩니다.

 식 제어 블록은 `<#= ... #>` 기호로 구분됩니다.

 예를 들어 다음 제어 블록은 출력 파일에 "5"가 포함되도록 지정합니다.

```
<#= 2 + 3 #>
```

 Notice that the opening symbol has three characters "<#=".

 식은 범위 내의 모든 변수를 포함할 수 있습니다. 예를 들어 다음 블록은 숫자가 포함된 줄을 출력합니다.

```
<#@ output extension=".txt" #>
<#
    for(int i = 0; i < 4; i++)
    {
#>
This is hello number <#= i+1 #>: Hello!
<#
    }
#>
```

### <a name="class-feature-control-blocks"></a>클래스 기능 제어 블록
 클래스 기능 제어 블록은 주 변환에 포함되지 않아야 할 속성, 메서드 또는 기타 코드를 정의합니다. 클래스 기능 블록은 대개 도우미 함수에 사용되며,  Typically, class feature blocks are placed in separate files so that they can be [included](#Include) by more than one text template.

 클래스 기능 제어 블록은 `<#+ ... #>` 기호로 구분됩니다.

 예를 들어 다음 템플릿 파일은 메서드를 선언 및 사용합니다.

```
<#@ output extension=".txt" #>
Squares:
<#
    for(int i = 0; i < 4; i++)
    {
#>
    The square of <#= i #> is <#= Square(i+1) #>.
<#
    }
#>
That is the end of the list.
<#+   // Start of class feature block
private int Square(int i)
{
    return i*i;
}
#>
```

 클래스 기능은 작성되는 파일 끝에 배치해야 합니다. 그러나 `<#@include#>` 지시문 뒤에 표준 블록과 텍스트가 있어도 클래스 기능을 포함하는 파일을 `include`할 수 있습니다.

 For more information about control blocks, see [Text Template Control Blocks](../modeling/text-template-control-blocks.md).

### <a name="class-feature-blocks-can-contain-text-blocks"></a>텍스트 블록을 포함할 수 있는 클래스 기능 블록
 텍스트를 생성하는 메서드를 작성할 수 있습니다. 예를 들어 다음과 같은 가치를 제공해야 합니다.

```
List of Squares:
<#
   for(int i = 0; i < 4; i++)
   {  WriteSquareLine(i); }
#>
End of list.
<#+   // Class feature block
private void WriteSquareLine(int i)
{
#>
   The square of <#= i #> is <#= i*i #>.
<#+
}
#>
```

 따라서 둘 이상의 템플릿에 포함될 수 있는 텍스트를 별도의 파일에 생성하는 메서드를 배치하는 경우 특히 유용합니다.

## <a name="using-external-definitions"></a>외부 정의 사용

### <a name="assemblies"></a>어셈블리
 템플릿의 코드 블록은 System.dll 등 가장 흔히 사용되는 .NET 어셈블리에 대해 정의되는 형식을 사용할 수 있습니다. 또한 기타 .NET 어셈블리나 고유한 어셈블리를 참조할 수도 있습니다. 다음과 같이 어셈블리의 경로 이름 또는 강력한 이름을 제공할 수 있습니다.

```
<#@ assembly name="System.Xml" #>
```

 절대 경로 이름을 사용하거나 경로 이름에 표준 매크로 이름을 사용해야 합니다. 예를 들어 다음과 같은 가치를 제공해야 합니다.

```
<#@ assembly name="$(SolutionDir)library\MyAssembly.dll" #>
```

 For a list of macros, see [Common Macros for Build Commands and Properties](https://msdn.microsoft.com/library/239bd708-2ea9-4687-b264-043f1febf98b).

 The assembly directive has no effect in a [preprocessed text template](../modeling/run-time-text-generation-with-t4-text-templates.md).

 For more information, see [T4 Assembly Directive](../modeling/t4-assembly-directive.md).

### <a name="namespaces"></a>네임스페이스
 import 지시문은 C#의 경우 `using` 절, Visual Basic의 경우 `imports` 절과 같습니다. 이 지시문을 사용하면 정규화된 이름을 사용하지 않고도 코드에서 형식을 참조할 수 있습니다.

```
<#@ import namespace="System.Xml" #>
```

 지시문 `assembly` 및 `import`은 원하는 수만큼 사용할 수 있습니다. 이러한 지시문은 텍스트 및 제어 블록 앞에 배치해야 합니다.

 For more information, see [T4 Import Directive](../modeling/t4-import-directive.md).

### <a name="Include"></a> Including code and text
 `include` 지시문은 다른 템플릿 파일의 텍스트를 삽입합니다. 예를 들어 다음 지시문은 `test.txt`의 내용을 삽입합니다.

 `<#@ include file="c:\test.txt" #>`

 포함된 내용은 포함하는 텍스트 템플릿의 일부인 것처럼 처리됩니다. 그러나 include 지시문 뒤에 일반 텍스트와 표준 제어 블록이 있어도 클래스 기능 블록 `<#+...#>`이 포함된 파일을 포함할 수 있습니다.

 For more information, see [T4 Include Directive](../modeling/t4-include-directive.md).

### <a name="utility-methods"></a>유틸리티 메서드
 제어 블록에서 항상 사용할 수 있는 `Write()` 등의 여러 메서드가 있습니다. 여기에는 출력 들여쓰기, 오류 보고 등을 위한 메서드가 포함됩니다.

 원하는 유틸리티 메서드 집합을 직접 작성할 수도 있습니다.

 For more information, see [Text Template Utility Methods](../modeling/text-template-utility-methods.md).

## <a name="transforming-data-and-models"></a>데이터 및 모델 변환
 텍스트 템플릿의 가장 유용한 적용 사례는 모델, 데이터베이스 또는 데이터 파일과 같은 소스의 내용에 따라 자료를 생성하는 것입니다. 템플릿은 데이터를 추출한 다음 서식을 다시 지정합니다. 템플릿 컬렉션은 이러한 소스를 여러 파일로 변환할 수 있습니다.

 소스 파일을 읽는 방식은 다양합니다.

 **Read a file in the text template**. 이는 데이터를 템플릿으로 가져오는 가장 단순한 방법입니다.

```
<#@ import namespace="System.IO" #>
<# string fileContent = File.ReadAllText(@"C:\myData.txt"); ...
```

 **Load a file as a navigable model**. 즉, 텍스트 템플릿 코드가 탐색할 수 있는 모델로 데이터를 읽는 보다 효율적인 방식을 사용할 수 있습니다. 예를 들어 XML 파일을 로드한 다음 XPath 식을 사용하여 탐색할 수 있습니다. You could also use [xsd.exe](https://go.microsoft.com/fwlink/?LinkId=178765) to create a set of classes with which you can read the XML data.

 **Edit the model file in a diagram or form.** [!INCLUDE[dsl](../includes/dsl-md.md)] provides tools that let you edit a model as a diagram or Windows form. 그러면 생성된 애플리케이션의 사용자와 모델에 대해 보다 쉽게 논의할 수 있습니다. [!INCLUDE[dsl](../includes/dsl-md.md)]에서는 모델 구조를 반영하는 강력한 형식의 클래스 집합도 만듭니다. For more information, see [Generating Code from a Domain-Specific Language](../modeling/generating-code-from-a-domain-specific-language.md).

 **Use a UML model**. UML 모델에서 코드를 생성할 수 있습니다. 이 경우 익숙한 표기법을 사용해 모델을 다이어그램으로 편집할 수 있다는 이점이 있습니다. 또한 다이어그램을 디자인하지 않아도 됩니다. For more information, see [Generate files from a UML model](../modeling/generate-files-from-a-uml-model.md).

### <a name="relative-file-paths-in-design-time-templates"></a>디자인 타임 템플릿의 상대 파일 경로
 In a [design-time text template](../modeling/design-time-code-generation-by-using-t4-text-templates.md), if you want to reference a file in a location relative to the text template, use `this.Host.ResolvePath()`. 또한 `hostspecific="true"` 지시문에서 `template`도 설정해야 합니다.

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ import namespace="System.IO" #>
<#
 // Find a path within the same project as the text template:
 string myFile = File.ReadAllText(this.Host.ResolvePath("MyFile.txt"));
#>
Content of MyFile.txt is:
<#= myFile #>

```

 호스트가 제공하는 다른 서비스도 가져올 수 있습니다. For more information, see [Accessing Visual Studio or other Hosts from a Template](https://msdn.microsoft.com/0556f20c-fef4-41a9-9597-53afab4ab9e4).

### <a name="design-time-text-templates-run-in-a-separate-appdomain"></a>별도의 AppDomain에서 실행되는 디자인 타임 텍스트 템플릿
 You should be aware that a [design-time text template](../modeling/design-time-code-generation-by-using-t4-text-templates.md) runs in an AppDomain that is separate from the main application. 이러한 방식은 대부분의 경우 중요하지 않지만 복잡한 코드를 사용하는 특정 사례에서는 제한이 적용될 수 있습니다. 예를 들어 별도의 서비스에서 템플릿 내부나 외부로 데이터를 전달하려는 경우 해당 서비스가 serializable API를 제공해야 합니다.

 (This isn’t true of a [run-time text template](../modeling/run-time-text-generation-with-t4-text-templates.md), which provides code that is compiled along with the rest of your code.)

## <a name="editing-templates"></a>템플릿 편집
 확장 관리자 온라인 갤러리에서 특수한 텍스트 템플릿 편집기를 다운로드할 수 있습니다. On the **Tools** menu, click **Extension Manager**. Click **Online Gallery**, and then use the search tool.

## <a name="related-topics"></a>관련 항목

|작업|항목|
|----------|-----------|
|템플릿을 작성합니다.|[T4 텍스트 템플릿 작성 지침](../modeling/guidelines-for-writing-t4-text-templates.md)|
|프로그램 코드를 사용하여 텍스트를 생성합니다.|[Text Template Structure](../modeling/writing-a-t4-text-template.md)|
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 솔루션에서 파일을 생성합니다.|[T4 텍스트 템플릿을 사용하여 디자인 타임 코드 생성](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 외부에서 텍스트 생성을 실행합니다.|[TextTransform 유틸리티 사용하여 파일 생성](../modeling/generating-files-with-the-texttransform-utility.md)|
|DSL(Domain-Specific Language) 형식으로 데이터를 변형합니다.|[도메인별 언어에서 코드 생성](../modeling/generating-code-from-a-domain-specific-language.md)|
|고유한 데이터 소스를 변형하는 지시문 프로세서를 작성합니다.|[T4 텍스트 변환 사용자 지정](../modeling/customizing-t4-text-transformation.md)|
