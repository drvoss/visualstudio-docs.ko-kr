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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6c38b15a3b819ce561c098c3b9810ee6884e526b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658532"
---
# <a name="text-template-utility-methods"></a>텍스트 템플릿 유틸리티 메서드
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

@No__t_0 텍스트 템플릿에서 코드를 작성할 때 항상 사용할 수 있는 몇 가지 방법이 있습니다. 이러한 메서드는 <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>에서 정의 됩니다.

> [!TIP]
> 또한 일반 (전처리 되지 않은) 텍스트 템플릿에서 호스트 환경에서 제공 하는 다른 메서드 및 서비스를 사용할 수 있습니다. 예를 들어 파일 경로를 확인 하 고, 오류를 기록 하 고, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 및 로드 된 모든 패키지에서 제공 하는 서비스를 가져올 수 있습니다.  자세한 내용은 [텍스트 템플릿에서 Visual Studio에 액세스](https://msdn.microsoft.com/0556f20c-fef4-41a9-9597-53afab4ab9e4)를 참조 하세요.

## <a name="write-methods"></a>Write 메서드
 @No__t_0 및 `WriteLine()` 메서드를 사용 하 여 식 코드 블록을 사용 하는 대신 표준 코드 블록 내에 텍스트를 추가할 수 있습니다. 다음 두 코드 블록은 기능적으로 동일 합니다.

##### <a name="code-block-with-an-expression-block"></a>식 블록이 포함 된 코드 블록

```
<#
int i = 10;
while (i-- > 0)
    { #>
        <#= i #>
    <# }
#>
```

##### <a name="code-block-using-writeline"></a>WriteLine ()을 사용 하는 코드 블록

```
<#
    int i = 10;
    while (i-- > 0)
    {
        WriteLine((i.ToString()));
    }
#>
```

 중첩 된 컨트롤 구조의 긴 코드 블록 내에서 식 블록 대신 이러한 유틸리티 메서드 중 하나를 사용 하는 것이 유용할 수 있습니다.

 @No__t_0 및 `WriteLine()` 메서드에는 두 개의 오버 로드가 있습니다. 하나는 단일 문자열 매개 변수를 사용 하 고 다른 하나는 복합 서식 문자열과 문자열에 포함할 개체의 배열을 사용 합니다 (예: `Console.WriteLine()` 메서드). 다음 두 가지 `WriteLine()` 사용은 기능적으로 동일 합니다.

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
 들여쓰기 메서드를 사용 하 여 텍스트 템플릿의 출력 형식을 지정할 수 있습니다. @No__t_0 클래스에는 텍스트 템플릿의 현재 들여쓰기를 표시 하는 `CurrentIndent` string 속성과 추가 된 들여쓰기 목록 `indentLengths` 필드가 있습니다. @No__t_0 메서드를 사용 하 여 들여쓰기를 추가 하 고 `PopIndent()` 메서드를 사용 하 여 들여쓰기를 뺄 수 있습니다. 모든 들여쓰기를 제거 하려면 `ClearIndent()` 메서드를 사용 합니다. 다음 코드 블록에서는 이러한 메서드를 사용 하는 방법을 보여 줍니다.

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

 이 코드 블록은 다음과 같은 출력을 생성 합니다.

```
Hello
        Hello
                Hello
Hello
        Hello
```

## <a name="error-and-warning-methods"></a>Error 및 warning 메서드
 오류 및 경고 유틸리티 메서드를 사용 하 여 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 오류 목록에 메시지를 추가할 수 있습니다. 예를 들어 다음 코드는 오류 목록에 오류 메시지를 추가 합니다.

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

## <a name="access-to-host-and-service-provider"></a>호스트 및 서비스 공급자에 대 한 액세스
 @No__t_0 속성은 템플릿을 실행 하는 호스트에서 노출 하는 속성에 대 한 액세스를 제공할 수 있습니다. @No__t_0를 사용 하려면 `<@template#>` 지시문에서 `hostspecific` 특성을 설정 해야 합니다.

 `<#@template ... hostspecific="true" #>`

 @No__t_0 유형은 템플릿이 실행 되는 호스트의 유형에 따라 달라 집니다. @No__t_0에서 실행 되는 템플릿에서 IDE와 같은 서비스에 대 한 액세스 권한을 얻기 위해 `this.Host`를 `IServiceProvider`으로 캐스팅할 수 있습니다. 예:

```
EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)
                       .GetService(typeof(EnvDTE.DTE));
```

## <a name="using-a-different-set-of-utility-methods"></a>다른 유틸리티 메서드 집합 사용
 텍스트 생성 프로세스의 일부로 템플릿 파일은 클래스로 변환 됩니다 .이 클래스는 항상 이름 `GeneratedTextTransformation`and <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>에서 상속 됩니다. 대신 다른 메서드 집합을 사용 하려는 경우 고유한 클래스를 작성 하 고 템플릿 지시문에서 지정할 수 있습니다. 클래스는 <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>에서 상속 해야 합니다.

```
<#@ template inherits="MyUtilityClass" #>
```

 @No__t_0 지시어를 사용 하 여 컴파일된 클래스를 찾을 수 있는 어셈블리를 참조할 수 있습니다.
