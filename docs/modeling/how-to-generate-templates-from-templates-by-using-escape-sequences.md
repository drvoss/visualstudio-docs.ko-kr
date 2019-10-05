---
title: 이스케이프 시퀀스를 사용 하 여 템플릿에서 템플릿 생성
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, generating templates from templates
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7872b9bf55ad5d712ac01edf10c4b9df2a82feea
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/28/2019
ms.locfileid: "66263678"
---
# <a name="how-to-generate-templates-from-templates-by-using-escape-sequences"></a>방법: 이스케이프 시퀀스를 사용하여 템플릿에서 템플릿 생성
생성 된 텍스트 출력으로 다른 텍스트 템플릿을 작성 하는 텍스트 템플릿을 만들 수 있습니다. 이렇게 하려면 텍스트 템플릿 태그를 설명 하려면 이스케이프 시퀀스를 사용 해야 합니다. 이스케이프 시퀀스를 사용 하지 않는 경우 생성 된 텍스트 템플릿을 미리 정의 된 의미를 갖습니다. 텍스트 템플릿에서 이스케이프 시퀀스를 사용 하는 방법에 대 한 자세한 내용은 참조 하십시오 [텍스트 템플릿에서 이스케이프 시퀀스를 사용 하 여](../modeling/using-escape-sequences-in-text-templates.md)입니다.

### <a name="to-generate-a-text-template-from-within-a-text-template"></a>텍스트 템플릿 내에서 텍스트 템플릿을 생성 하려면

- 백슬래시를 사용 하 여 (\\) 지시문, 문, 식에 대 한 텍스트 템플릿 내에서 필요한 태그를 생성 하 고 기능을 별도 텍스트 템플릿 파일에서 클래스를 이스케이프 문자로 합니다.

    ```
    \<#@ directive \#>
    \<# statement \#>
    \<#= expression \#>
    \<#+ classfeature \#>
    ```

## <a name="example"></a>예제
 다음 예제에서는 이스케이프 문자를 사용 하 여 텍스트 템플릿에서 텍스트 템플릿을 생성 합니다. `output` 지시문 텍스트 템플릿 파일 형식 (.tt) 대상 파일 형식으로 설정 합니다.

```csharp
\<#@ output extension=".tt" \#>
\<#@ assembly name="System.Xml.dll" \#>
\<#@ import namespace="System.Xml" \#>
\<#
XmlDocument xDoc = new XmlDocument();
//System.Diagnostics.Debugger.Break();
    xDoc.Load(@"E:\CSharp\Overview.xml");
    XmlAttributeCollection attributes = xDoc.Attributes;
    if (attributes != null)
    {
       foreach (XmlAttribute attr in attributes)
       {\#>
           \<#= attr.Name \#>
       \<#}
     }
\#>
```

 생성된 된 텍스트 출력은 텍스트 템플릿입니다.

```
<#@ output extension=".tt" #>
<#@ assembly name="System.Xml.dll" #>
<#@ import namespace="System.Xml" #>
<#
XmlDocument xDoc = new XmlDocument();
//System.Diagnostics.Debugger.Break();
    xDoc.Load(@"E:\CSharp\Overview.xml");
    XmlAttributeCollection attributes = xDoc.Attributes;
    if (attributes != null)
    {
       foreach (XmlAttribute attr in attributes)
       {#>
           <#= attr.Name #>
       <#}
     }
#>
```