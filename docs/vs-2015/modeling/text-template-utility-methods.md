---
title: 텍스트 템플릿 유틸리티 메서드 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, utility methods
ms.assetid: 8c11f9f7-678b-4f0c-b634-dc78fda699d1
caps.latest.revision: 52
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e69bd59782c2caa1dcb878df4e5316df798b0f21
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65680981"
---
# <a name="text-template-utility-methods"></a>텍스트 템플릿 유틸리티 메서드
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

코드를 작성할 때 항상를 사용할 수 있는 여러 가지가 있습니다를 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 텍스트 템플릿. 에 정의 된 이러한 메서드가 <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>합니다.  
  
> [!TIP]
> 또한 다른 메서드 및 일반 하지 전처리 된 텍스트 템플릿에서 호스트 환경에서 제공 하는 서비스를 사용할 수 있습니다. 예를 들어, 파일 경로 확인, 오류 로그를 가져올 수에서 제공 하는 서비스 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 모든 패키지를 로드 합니다.  자세한 내용은 [텍스트 템플릿에서 Visual Studio 액세스](https://msdn.microsoft.com/0556f20c-fef4-41a9-9597-53afab4ab9e4)합니다.  
  
## <a name="write-methods"></a>메서드를 작성 합니다.  
 사용할 수는 `Write()` 고 `WriteLine()` 식 코드 블록을 사용 하는 대신 표준 코드 블록 내에 텍스트를 추가 하는 방법입니다. 다음 두 코드 블록 기능적으로 동일합니다.  
  
##### <a name="code-block-with-an-expression-block"></a>식 블록을 사용 하 여 코드 블록  
  
```  
<#  
int i = 10;  
while (i-- > 0)  
    { #>  
        <#= i #>  
    <# }  
#>  
```  
  
##### <a name="code-block-using-writeline"></a>WriteLine()를 사용 하 여 코드 블록  
  
```  
<#   
    int i = 10;  
    while (i-- > 0)  
    {   
        WriteLine((i.ToString()));  
    }  
#>  
```  
  
 중첩된 제어 구조를 사용 하 여 긴 코드 블록 내부의 식 블록 대신 이러한 유틸리티 메서드 중 하나를 사용 하는 것이 유용할 수 있습니다.  
  
 `Write()` 하 고 `WriteLine()` 메서드는 두 개의 오버 로드를 갖고, 합성 서식 문자열 및 문자열에 포함할 개체의 배열을 사용 하는 단일 문자열 매개 변수 및 1을 사용 하는 (같은 `Console.WriteLine()` 메서드). 다음 두 가지 용도 `WriteLine()` 기능적으로 동일 합니다.  
  
```  
<#  
    string msg = "Say: {0}, {1}, {2}";  
    string s1 = "hello";  
    string s2 = "goodbye";  
    string s3 = "farewell";  
  
    WriteLine(msg, s1, s2, s3);  
    WriteLine("Say: hello, goodbye, farewell");  
#>   
```  
  
## <a name="indentation-methods"></a>들여쓰기 메서드  
 텍스트 템플릿의 출력 형식을 들여쓰기 메서드를 사용할 수 있습니다. <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> 클래스에는 `CurrentIndent` 문자열 텍스트 템플릿의 현재 들여쓰기를 보여 주는 속성 및 `indentLengths` 필드 추가 된 들여쓰기의 목록입니다. 사용 하 여 들여쓰기를 추가할 수 있습니다 합니다 `PushIndent()` 메서드를 사용 하 여 들여쓰기를 뺍니다는 `PopIndent()` 메서드. 사용 하 여 모든 들여쓰기를 제거 하려는 경우는 `ClearIndent()` 메서드. 다음 코드 블록에서는 이러한 메서드를 사용을 보여 줍니다.  
  
```  
<#  
    WriteLine(CurrentIndent + "Hello");  
    PushIndent("    ");  
    WriteLine(CurrentIndent + "Hello");  
    PushIndent("    ");  
    WriteLine(CurrentIndent + "Hello");  
    ClearIndent();  
    WriteLine(CurrentIndent + "Hello");  
    PushIndent("    ");  
    WriteLine(CurrentIndent + "Hello");  
#>  
```  
  
 이 코드 블록의 출력은 다음과 같습니다.  
  
```  
Hello  
        Hello  
                Hello  
Hello  
        Hello  
```  
  
## <a name="error-and-warning-methods"></a>오류 및 경고 메서드  
 오류 및 경고 유틸리티 메서드를 사용 하 여 메시지를 추가 하 여 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 오류 목록입니다. 예를 들어, 다음 코드는 오류 목록에는 오류 메시지를 추가 합니다.  
  
```  
<#  
  try  
  {  
    string str = null;  
    Write(str.Length.ToString());  
  }  
  catch (Exception e)  
  {  
    Error(e.Message);  
  }  
#>    
```  
  
## <a name="access-to-host-and-service-provider"></a>호스트와 서비스 공급자에 대 한 액세스  
 속성 `this.Host` 서식 파일을 실행 하는 호스트에 의해 노출 되는 속성에 대 한 액세스를 제공할 수 있습니다. 사용 하도록 `this.Host`를 설정 해야 합니다 `hostspecific` 특성을 `<@template#>` 지시문:  
  
 `<#@template ... hostspecific="true" #>`  
  
 형식의 `this.Host` 템플릿이 실행 되는 호스트의 형식에 따라 달라 집니다. 실행 되는 템플릿에서 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]를 캐스팅할 수 있습니다 `this.Host` 에 `IServiceProvider` IDE와 같은 서비스에 액세스할 수 있습니다. 예를 들어:  
  
```  
EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)  
                       .GetService(typeof(EnvDTE.DTE));  
```  
  
## <a name="using-a-different-set-of-utility-methods"></a>다양 한 유틸리티 메서드를 사용 하 여  
 라고 하는 클래스로 변환 하는 템플릿 파일 텍스트 생성 프로세스의 일부로 `GeneratedTextTransformation`에서 상속 되 고 <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>입니다. 다른 사용 하려는 경우 메서드 집합을 대신, 고유한 클래스를 작성 하 template 지시문에 지정 합니다. 클래스에서 상속 해야 <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>합니다.  
  
```  
<#@ template inherits="MyUtilityClass" #>  
```  
  
 사용 된 `assembly` 컴파일된 클래스를 찾을 수 있는 어셈블리를 참조 하는 지시문입니다.
