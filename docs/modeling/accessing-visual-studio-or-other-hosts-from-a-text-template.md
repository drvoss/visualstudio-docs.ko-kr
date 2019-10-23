---
title: 텍스트 템플릿에서 Visual Studio 또는 다른 호스트 액세스
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 752b9d9e69eee26f267927f03c4b83c68740100b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652368"
---
# <a name="access-visual-studio-or-other-hosts-from-a-text-template"></a>텍스트 템플릿에서 Visual Studio 또는 다른 호스트에 액세스

텍스트 템플릿에서 템플릿을 실행 하는 호스트에 의해 노출 되는 메서드 및 속성을 사용할 수 있습니다. Visual Studio는 호스트의 한 예입니다.

> [!NOTE]
> 일반 텍스트 템플릿에서 호스트 메서드 및 속성을 사용할 수 있지만 *전처리* 텍스트 템플릿에서는 사용할 수 없습니다.

## <a name="obtain-access-to-the-host"></a>호스트에 대 한 액세스 권한 얻기

호스트에 액세스 하려면 설정 `hostspecific="true"` 에 `template` 지시문입니다. 이제 [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)) 형식의 `this.Host`를 사용할 수 있습니다. [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)) 형식에는 파일 이름을 확인 하 고 오류를 기록 하는 데 사용할 수 있는 멤버가 있습니다 (예:).

### <a name="resolve-file-names"></a>파일 이름을 확인합니다

텍스트 템플릿에 상대적인 파일의 전체 경로를 찾으려면 `this.Host.ResolvePath()`를 사용 합니다.

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

### <a name="display-error-messages"></a>오류 메시지 표시

이 예에서는 템플릿을 변환할 때 메시지를 기록 합니다. 호스트가 Visual Studio 인 경우 오류는 **오류 목록**에 추가 됩니다.

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

## <a name="use-the-visual-studio-api"></a>Visual Studio API 사용

Visual Studio에서 텍스트 템플릿을 실행 하는 경우 `this.Host`를 사용 하 여 Visual Studio에서 제공 하는 서비스 및 로드 된 패키지 또는 확장에 액세스할 수 있습니다.

Hostspecific = "true"를 설정 하 고 `this.Host`를 <xref:System.IServiceProvider>로 캐스팅 합니다.

이 예제에서는 <xref:EnvDTE.DTE> Visual Studio API를 서비스로 가져옵니다.

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

## <a name="use-hostspecific-with-template-inheritance"></a>템플릿 상속과 함께 hostSpecific 사용

@No__t_1 특성도 사용 하 고 `hostspecific="true"`를 지정 하는 템플릿에서 상속 하는 경우 `hostspecific="trueFromBase"`를 지정 합니다. 그렇지 않으면 `Host` 속성이 두 번 선언 되었다는 컴파일러 경고가 나타날 수 있습니다.