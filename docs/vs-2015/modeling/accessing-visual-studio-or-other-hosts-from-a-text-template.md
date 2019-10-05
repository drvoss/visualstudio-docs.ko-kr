---
title: 텍스트 템플릿에서 Visual Studio 2015 또는 기타 호스트 액세스 | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: a68886da-7416-4785-8145-3796bb382cba
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 053e8b09fd2b52683238f1ffe008e5e7d38b3962
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68872012"
---
# <a name="accessing-visual-studio-or-other-hosts-from-a-text-template"></a>텍스트 템플릿에서 Visual Studio 또는 다른 호스트 액세스
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

텍스트 템플릿에서는와 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]같이 템플릿을 실행 하는 호스트에서 노출 하는 메서드 및 속성을 사용할 수 있습니다.

 이는 전처리 텍스트 템플릿이 아닌 일반 텍스트 템플릿에 적용 됩니다.

## <a name="obtaining-access-to-the-host"></a>호스트에 대 한 액세스 권한 얻기

지시문에를 설정 `hostspecific="true"`합니다. `template` 이를 통해 `this.Host` [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110))형식의를 사용할 수 있습니다. 예를 들어이 형식에는 파일 이름을 확인 하 고 오류를 기록 하는 데 사용할 수 있는 멤버가 있습니다.

### <a name="resolving-file-names"></a>파일 이름 확인
 텍스트 템플릿에 상대적인 파일의 전체 경로를 찾으려면이를 사용 합니다. ResolvePath ().

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

### <a name="displaying-error-messages"></a>오류 메시지 표시
 이 예제에서는 서식 파일을 변환 하는 경우 메시지를 기록 합니다. 호스트가 인 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]경우 오류 창에 추가 됩니다.

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

## <a name="using-the-visual-studio-api"></a>Visual Studio API 사용
 에서 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]텍스트 템플릿을 실행 하는 경우를 사용 `this.Host` 하 여 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 에서 제공 하는 서비스 및 로드 된 패키지 또는 확장에 액세스할 수 있습니다.

 설정 hostspecific = "true" 및 캐스팅 `this.Host` 에 <xref:System.IServiceProvider>입니다.

 이 예제에서는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] <xref:EnvDTE.DTE>API를 서비스로 가져옵니다.

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

## <a name="using-hostspecific-with-template-inheritance"></a>템플릿 상속과 함께 hostSpecific 사용
 지정할 `hostspecific="trueFromBase"` 사용 하는 경우는 `inherits` 특성을 지정 하는 서식 파일에서 상속 하는 경우 및 `hostspecific="true"`합니다. 이렇게 하면 속성이 `Host` 두 번 선언 된 결과에 대 한 컴파일러 경고가 방지 됩니다.
