---
title: 텍스트 템플릿에서 Visual Studio 또는 다른 호스트 액세스
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 26845b3878a89ea52a3f77f9a0a8d23363877edd
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68870683"
---
# <a name="access-visual-studio-or-other-hosts-from-a-text-template"></a>텍스트 템플릿에서 Visual Studio 또는 다른 호스트에 액세스

텍스트 템플릿에서 템플릿을 실행 하는 호스트에 의해 노출 되는 메서드 및 속성을 사용할 수 있습니다. Visual Studio는 호스트의 예시입니다.

> [!NOTE]
> 일반 텍스트 템플릿에서 아니라 호스트 메서드 및 속성을 사용할 수 *전처리* 텍스트 템플릿.

## <a name="obtain-access-to-the-host"></a>호스트에 액세스

호스트에 액세스 하려면 설정 `hostspecific="true"` 에 `template` 지시문입니다. 이제 [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)) 형식의 `this.Host`를 사용할 수 있습니다. [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)) 형식에는 파일 이름을 확인 하 고 오류를 기록 하는 데 사용할 수 있는 멤버가 있습니다 (예:).

### <a name="resolve-file-names"></a>파일 이름을 확인합니다

사용 하 여 텍스트 템플릿 기준으로 한 파일의 전체 경로 찾으려면 `this.Host.ResolvePath()`합니다.

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ import namespace="System.IO" #>
<#
 // Find a path within the same project as the text template:
 string myFile = File.ReadAllText(this.Host.ResolvePath("MyFile.txt"));
#>
Content of myFile is:
<#= myFile #>
```

### <a name="display-error-messages"></a>오류 메시지를 표시 합니다.

이 예제에서는 서식 파일을 변환 하는 경우 메시지를 기록 합니다. 오류를 추가할 호스트 Visual Studio 인 경우는 **오류 목록**합니다.

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ import namespace="System.CodeDom.Compiler" #>
<#
  string message = "test message";
  this.Host.LogErrors(new CompilerErrorCollection()
    { new CompilerError(
       this.Host.TemplateFile, // Identify the source of the error.
       0, 0, "0",   // Line, column, error ID.
       message) }); // Message displayed in error window.
#>
```

## <a name="use-the-visual-studio-api"></a>Visual Studio API를 사용 합니다.

텍스트 템플릿에서 Visual Studio에서를 실행 하는 경우 사용할 수 있습니다 `this.Host` Visual Studio 및 패키지 또는 로드 되는 확장에서 제공 서비스에 액세스 합니다.

설정 hostspecific = "true" 및 캐스팅 `this.Host` 에 <xref:System.IServiceProvider>입니다.

이 예제에서는 Visual Studio API를 가져옵니다 <xref:EnvDTE.DTE>, 서비스로:

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ assembly name="EnvDTE" #>
<#@ import namespace="EnvDTE" #>
<#
 IServiceProvider serviceProvider = (IServiceProvider)this.Host;
 DTE dte = serviceProvider.GetService(typeof(DTE)) as DTE;
#>
Number of projects in this solution: <#=  dte.Solution.Projects.Count #>
```

## <a name="use-hostspecific-with-template-inheritance"></a>HostSpecific 템플릿 상속 사용

지정할 `hostspecific="trueFromBase"` 사용 하는 경우는 `inherits` 특성을 지정 하는 서식 파일에서 상속 하는 경우 및 `hostspecific="true"`합니다. 그렇지 않으면 얻게 컴파일러는 경고 속성 `Host` 두 번 선언 되었습니다.