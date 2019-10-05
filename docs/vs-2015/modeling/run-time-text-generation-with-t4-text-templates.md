---
title: T4 텍스트 템플릿 사용 하 여 런타임 텍스트 생성 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Preprocessed Text Template project item
- TextTemplatingFilePreprocessor custom tool
- text templates, TransformText() method
- text templates, generating files at run time
ms.assetid: 79b4b3c6-a9a7-4446-b6fd-e2388fc6b05f
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 586ad1d68ce1d0310b30b8bdac8aa2fb55acdeb5
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63411870"
---
# <a name="run-time-text-generation-with-t4-text-templates"></a>T4 텍스트 템플릿을 사용하여 런타임 텍스트 생성
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

사용 하 여 런타임 시 응용 프로그램에서 텍스트 문자열을 생성할 수 있습니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 런타임 텍스트 템플릿. 응용 프로그램을 실행 하는 컴퓨터 필요가 없는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]합니다. 런타임 템플릿 때때로 이라고 "전처리 된 텍스트 템플릿을" 템플릿은 컴파일 시간에 런타임 시 실행 되는 코드를 생성 합니다.  
  
 각 템플릿은 생성 된 문자열 및 프로그램 코드 조각에 표시 될 텍스트의 혼합입니다. 프로그램 조각은 변수 부분 문자열에 대 한 값을 제공 하며 조건부로 / 반복 부분을 제어할 수도 있습니다.  
  
 예를 들어 다음 템플릿은 HTML 보고서를 작성 하는 응용 프로그램에서 사용할 수 있습니다.  
  
```  
<#@ template language="C#" #>  
<html><body>  
<h1>Sales for Previous Month</h2>  
<table>  
    <# for (int i = 1; i <= 10; i++)  
       { #>  
         <tr><td>Test name <#= i #> </td>  
             <td>Test value <#= i * i #> </td> </tr>  
    <# } #>  
 </table>  
This report is Company Confidential.  
</body></html>  
```  
  
 템플릿에 있는 변수 부분 바뀌었습니다 프로그램 코드를 사용 하 여 HTML 페이지 인지 확인 합니다. HTML 페이지의 정적 프로토타입을 작성 하 여 이러한 페이지의 디자인을 시작할 수 있습니다. 그런 다음 각각의 경우 다음 달라 지는 콘텐츠를 생성 하는 프로그램 코드를 사용 하 여 테이블 및 기타 변수 부분을 바꿀 수 있습니다.  
  
 응용 프로그램에서 템플릿을 사용 하 여 할 수 있습니다. 예를 들어 일련의 긴 쓰기 문에서는 보다 출력의 마지막 양식을 보려면 쉽습니다. 출력의 형식을 변경 하기 더 쉽고 안정 됩니다.  
  
## <a name="creating-a-run-time-text-template-in-any-application"></a>모든 응용 프로그램에서 런타임 텍스트 템플릿 만들기  
  
#### <a name="to-create-a-run-time-text-template"></a>런타임 텍스트 템플릿을 만들려면  
  
1. 솔루션 탐색기에서 프로젝트의 바로 가기 메뉴 선택 **추가**하십시오 **새 항목**합니다.  
  
2. 에 **새 항목 추가** 대화 상자에서 **런타임 텍스트 템플릿**합니다. (에 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 아래에서 확인 **일반적인 Items\General**.)  
  
3. 템플릿 파일의 이름을 입력 합니다.  
  
    > [!NOTE]
    > 템플릿 파일 이름이 생성된 된 코드에서 클래스 이름으로 사용 됩니다. 따라서 공백이 나 문장 부호가 것이 없어야 합니다.  
  
4. **추가**를 선택합니다.  
  
     새 파일 확장명을 가진 만들어집니다 **.tt**합니다. 해당 **사용자 지정 도구** 속성이 **TextTemplatingFilePreprocessor**합니다. 다음 줄을 포함합니다.  
  
    ```  
    <#@ template language="C#" #>  
    <#@ assembly name="System.Core" #>  
    <#@ import namespace="System.Linq" #>  
    <#@ import namespace="System.Text" #>  
    <#@ import namespace="System.Collections.Generic" #>  
    ```  
  
## <a name="converting-an-existing-file-to-a-run-time-template"></a>기존 파일을 런타임에 템플릿으로 변환  
 템플릿을 만들려면 기존 예가 출력을 변환 하는 것이 좋습니다. 예를 들어, 응용 프로그램 HTML 파일을 생성 하는 경우 일반 HTML 파일을 만들어 시작할 수 있습니다. 올바르게 작동 하는지, 그리고 모양을 올바른지 있는지 확인 합니다. 다음에 포함 프로그램 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 프로젝트를 템플릿으로 변환 합니다.  
  
#### <a name="to-convert-an-existing-text-file-to-a-run-time-template"></a>기존 텍스트 파일을 런타임에 템플릿으로 변환 하려면  
  
1. 로 파일을 포함 하면 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 프로젝트입니다. 솔루션 탐색기에서 프로젝트의 바로 가기 메뉴 선택 **추가**하십시오 **기존 항목**합니다.  
  
2. 파일의 설정 **사용자 지정 도구** 속성을 **TextTemplatingFilePreprocessor**합니다. 솔루션 탐색기에서 파일의 바로 가기 메뉴 선택 **속성**합니다.  
  
    > [!NOTE]
    > 속성이 이미 있는지 확인 하십시오 **TextTemplatingFilePreprocessor** 아니라 **TextTemplatingFileGenerator**합니다. 이 확장에 이미 있는 파일을 포함 하는 경우 발생할 수 있습니다 **.tt**합니다.  
  
3. 파일 이름 확장명을 변경 **.tt**합니다. 이 단계는 선택 사항, 있지만 잘못 된 편집기에서 파일을 열고 않을 수 있습니다.  
  
4. 파일 이름의 주요 부분에서 공백 또는 문장 부호를 제거 합니다. 예를 들어 "내 웹 Page.tt"의 잘못 되지 것 이지만 "MyWebPage.tt" 올바른 있습니다. 파일 이름은 생성된 된 코드에서 클래스 이름으로 사용 됩니다.  
  
5. 파일의 시작 부분에 다음 줄을 삽입 합니다. Visual Basic 프로젝트에서 작업 하는 경우 대체 "C#" "VB"를 사용 하 여 합니다.  
  
     `<#@ template language="C#" #>`  
  
## <a name="the-content-of-the-run-time-template"></a>런타임 서식 파일의 콘텐츠  
  
### <a name="template-directive"></a>템플릿 지시문  
 파일을 만들 때 처럼 템플릿의 첫 번째 줄을 유지 합니다.  
  
 `<#@ template language="C#" #>`  
  
 Language 매개 변수는 프로젝트의 언어에 따라 달라 집니다.  
  
### <a name="plain-content"></a>일반 콘텐츠  
 편집 된 **.tt** 응용 프로그램을 생성 하려는 텍스트를 포함 하는 파일입니다. 예를 들어:  
  
```  
<html><body>  
<h1>Sales for January</h2>  
<!-- table to be inserted here -->  
This report is Company Confidential.  
</body></html>  
```  
  
### <a name="embedded-program-code"></a>포함 된 프로그램 코드  
 사이 프로그램 코드를 삽입할 수 있습니다 `<#` 고 `#>`입니다. 예를 들어:  
  
```csharp  
<table>  
    <# for (int i = 1; i <= 10; i++)  
       { #>  
         <tr><td>Test name <#= i #> </td>  
             <td>Test value <#= i * i #> </td> </tr>  
    <# } #>  
 </table>  
```  
  
```vb  
<table>  
<#  
    For i As Integer = 1 To 10  
#>  
    <tr><td>Test name <#= i #> </td>  
      <td>Test value <#= i*i #> </td></tr>  
<#  
    Next  
#>  
</table>  
  
```  
  
 문 사이 삽입 되는 알 수 있습니다 `<# ... #>` 식 사이 삽입 되 고 `<#= ... #>`입니다. 자세한 내용은 [T4 텍스트 템플릿 쓰기](../modeling/writing-a-t4-text-template.md)합니다.  
  
## <a name="using-the-template"></a>템플릿 사용  
  
### <a name="the-code-built-from-the-template"></a>템플릿에서 코드  
 저장할 때마다 합니다 **.tt** 파일을 자회사 **.cs** 또는 **.vb** 파일이 생성 됩니다. 솔루션 탐색기에서이 파일을 보려면 확장 합니다 **.tt** 파일 노드. Visual Basic 프로젝트에서는 클릭 한 후 노드를 확장 하는 일을 할 됩니다 **모든 파일 표시** 솔루션 탐색기 도구 모음에서입니다.  
  
 이 보조 파일이 들어 라는 메서드를 포함 하는 부분 클래스 `TransformText()`합니다. 응용 프로그램에서이 메서드를 호출할 수 있습니다.  
  
### <a name="generating-text-at-run-time"></a>런타임에 텍스트를 생성합니다.  
 응용 프로그램 코드에서 다음과 같은 호출을 사용 하 여 서식 파일의 콘텐츠를 생성할 수 있습니다.  
  
```csharp  
MyWebPage page = new MyWebPage();  
String pageContent = page.TransformText();  
System.IO.File.WriteAllText("outputPage.html", pageContent);  
  
```  
  
```vb  
Dim page = New My.Templates.MyWebPage  
Dim pageContent = page.TransformText()  
System.IO.File.WriteAllText("outputPage.html", pageContent)  
  
```  
  
 특정 네임 스페이스에 생성된 된 클래스에 배치 하려면 설정 합니다 **사용자 지정 도구 Namespace** 텍스트 템플릿 파일의 속성입니다.  
  
### <a name="debugging-runtime-text-templates"></a>런타임 텍스트 템플릿 디버깅  
 디버그 및 런타임 텍스트 템플릿 일반 코드와 동일한 방식으로 테스트 합니다.  
  
 텍스트 템플릿에서 중단점을 설정할 수 있습니다. Visual Studio에서 디버깅 모드로 응용 프로그램을 시작 하는 경우 코드를 단계별로 실행 하 고 일반적인 방법으로 조사식을 평가할 수 있습니다.  
  
### <a name="passing-parameters-in-the-constructor"></a>생성자에 매개 변수 전달  
 일반적으로 템플릿을 응용 프로그램의 다른 부분에서 일부 데이터를 가져와야 합니다. 이렇게 하면 간편 하 게 템플릿에서 코드를 partial 클래스입니다. 프로젝트에서 다른 파일에서 동일한 클래스의 다른 부분을 만들 수 있습니다. 파일 매개 변수, 속성 및 템플릿에 포함 된 코드를 응용 프로그램의 나머지 부분에서 모두 액세스할 수 있는 함수를 사용 하 여 생성자를 포함할 수 있습니다.  
  
 예를 들어, 별도 파일을 만들 수 있습니다 **MyWebPageCode.cs**:  
  
```csharp  
partial class MyWebPage  
{  
    private MyData m_data;  
    public MyWebPage(MyData data) { this.m_data = data; }}  
```  
  
 템플릿 파일에 **MyWebPage.tt**를 작성할 수 있습니다.  
  
```csharp  
<h2>Sales figures</h2>  
<table>  
<# foreach (MyDataItem item in m_data.Items)   
   // m_data is declared in MyWebPageCode.cs  
   { #>  
      <tr><td> <#= item.Name #> </td>  
          <td> <#= item.Value #> </td></tr>  
<# } // end of foreach  
#>  
</table>  
```  
  
 에 응용 프로그램에서이 템플릿을 사용 합니다.  
  
```csharp  
MyData data = ...;  
MyWebPage page = new MyWebPage(data);  
String pageContent = page.TransformText();  
System.IO.File.WriteAllText("outputPage.html", pageContent);  
```  
  
#### <a name="constructor-parameters-in-visual-basic"></a>Visual Basic의 생성자 매개 변수  
 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], 별도 파일 **MyWebPageCode.vb** 포함 되어 있습니다.  
  
```vb  
Namespace My.Templates  
  Partial Public Class MyWebPage  
    Private m_data As MyData  
    Public Sub New(ByVal data As MyData)  
      m_data = data  
    End Sub  
  End Class  
End Namespace  
```  
  
 템플릿 파일을 포함할 수 있습니다.  
  
```vb  
<#@ template language="VB" #>  
<html><body>  
<h1>Sales for January</h2>  
<table>  
<#  
    For Each item In m_data.Items  
#>  
    <tr><td>Test name <#= item.Name #> </td>  
      <td>Test value <#= item.Value #> </td></tr>  
<#  
    Next  
#>  
</table>  
This report is Company Confidential.  
</body></html>  
  
```  
  
 및 템플릿 생성자에서 매개 변수를 전달 하 여 호출 됩니다.  
  
```vb  
Dim data = New My.Templates.MyData  
    ' Add data values here ....  
Dim page = New My.Templates.MyWebPage(data)  
Dim pageContent = page.TransformText()  
System.IO.File.WriteAllText("outputPage.html", pageContent)  
  
```  
  
#### <a name="passing-data-in-template-properties"></a>템플릿 속성의 데이터를 전달합니다.  
 템플릿에 데이터를 전달 하는 다른 방법은 템플릿 클래스는 partial 클래스 정의에 공용 속성을 추가 하는 것입니다. 응용 프로그램을 호출 하기 전에 속성을 설정할 수 `TransformText()`입니다.  
  
 부분 정의에서 템플릿 클래스에 필드를 추가할 수도 있습니다. 이렇게 하면 템플릿의 연속 실행 간에 데이터를 전달할 수 있습니다.  
  
### <a name="use-partial-classes-for-code"></a>코드에 대 한 partial 클래스를 사용 합니다.  
 템플릿에서 큰 코드 본문을 작성 하지 않는 많은 개발자 들을 선호 합니다. 대신 템플릿 파일과 이름이 같은 partial 클래스에서 메서드를 정의 합니다. 템플릿에서 이러한 메서드를 호출 합니다. 이러한 방식으로 보다 명확 하 게 어떤 대상 출력 문자열 모양은 템플릿을 보여줍니다. 결과의 모양에 대 한 토론을 표시 하는 데이터를 만드는 논리에서 분리할 수 있습니다.  
  
### <a name="assemblies-and-references"></a>어셈블리 및 참조  
 템플릿 코드와 같은.NET 또는 다른 어셈블리를 참조 하려는 경우 **System.Xml.dll**, 프로젝트에 추가 해야 **참조** 일반적인 방식입니다.  
  
 동일한 방식으로 네임 스페이스를 가져오려는 경우는 `using` 문을 이렇게 사용 하 여는 `import` 지시문:  
  
```  
<#@ import namespace="System.Xml" #>  
```  
  
 이러한 지시문에 위치 하는 파일의 시작 부분 바로 뒤의 `<#@template` 지시문입니다.  
  
### <a name="shared-content"></a>공유 콘텐츠  
 여러 템플릿 간에 공유 되는 텍스트에 있는 경우에 별도 파일에 배치 하 고 표시 해야 하는 각 파일에 포함 수 있습니다.  
  
```  
<#@include file="CommonHeader.txt" #>  
```  
  
 포함 된 콘텐츠는 프로그램 코드와 일반 텍스트를 혼합을 포함할 수 있으며 다른 포함할 수 있습니다 지시문 및 다른 지시문을 포함 합니다.  
  
 Include 지시문의 템플릿 파일 또는 파일을 포함된 텍스트 내에서 아무 곳 이나 수입니다.  
  
### <a name="inheritance-between-run-time-text-templates"></a>런타임 텍스트 템플릿 간에 상속  
 해당 되는 추상 기본 클래스 템플릿을 작성 하 여 런타임 템플릿 사이의 콘텐츠를 공유할 수 있습니다. 사용 합니다 `inherits` 의 매개 변수는 `<@#template#>` 지시문 다른 런타임 템플릿 클래스를 참조 합니다.  
  
#### <a name="inheritance-pattern-fragments-in-base-methods"></a>상속 패턴: 기본 메서드에서 조각  
 패턴의 예제에 사용 되는 경우 다음 사항에 유의 합니다.  
  
- 기본 클래스 `SharedFragments` 메서드를 클래스 기능 블록 내에서 정의 `<#+ ... #>`합니다.  
  
- 기본 클래스 없음 자유 텍스트를 포함합니다. 대신, 모든 텍스트 블록 클래스 기능 메서드 내에서 발생합니다.  
  
- 파생된 클래스에 정의 된 메서드를 호출 `SharedFragments`합니다.  
  
- 응용 프로그램이 호출 된 `TextTransform()` 파생된 클래스 메서드의 기본 클래스를 변환 하지 않습니다 하지만 `SharedFragments`합니다.  
  
- 기본 및 파생 클래스는 런타임 텍스트 템플릿: 즉, 합니다 **사용자 지정 도구** 속성이 **TextTemplatingFilePreprocessor**합니다.  
  
  **SharedFragments.tt:**  
  
```csharp  
<#@ template language="C#" #>  
<#+  
protected void SharedText(int n)  
{  
#>  
   Shared Text <#= n #>  
<#+  
}  
// Insert more methods here if required.  
#>  
  
```  
  
 **MyTextTemplate1.tt:**  
  
```csharp  
<#@ template language="C#" inherits="SharedFragments" #>  
begin 1  
   <# SharedText(2); #>  
end 1  
  
```  
  
 **MyProgram.cs:**  
  
```csharp  
...   
MyTextTemplate1 t1  = new MyTextTemplate1();  
string result = t1.TransformText();  
Console.WriteLine(result);  
```  
  
 **결과 출력:**  
  
```  
begin 1  
    Shared Text 2  
end 1  
```  
  
#### <a name="inheritance-pattern-text-in-base-body"></a>상속 패턴: 기본 본문 텍스트  
 템플릿 상속을 사용 하 여이 대체 접근 방법에서는 텍스트의 기본 템플릿에서 정의 됩니다. 데이터를 제공 하는 파생된 템플릿의 텍스트 조각 기본 내용에 적합 하며  
  
 **AbstractBaseTemplate1.tt:**  
  
```csharp  
<#@ template language="C#" #>  
  
Here is the description for this derived template:  
  <#= this.Description #>  
  
Here is the fragment specific to this derived template:  
<#   
  this.PushIndent("  ");  
  SpecificFragment(42);   
  this.PopIndent();  
#>  
End of common template.  
<#+   
  // State set by derived class before calling TextTransform:  
  protected string Description = "";  
  // 'abstract' method to be defined in derived classes:  
  protected virtual void SpecificFragment(int n) { }  
#>  
  
```  
  
 **DerivedTemplate1.tt:**  
  
```csharp  
<#@ template language="C#" inherits="AbstractBaseTemplate1" #>  
<#   
  // Set the base template properties:  
  base.Description = "Description for this derived class";   
  
  // Run the base template:  
  base.TransformText();  
  
#>  
End material for DerivedTemplate1.  
  
<#+  
// Provide a fragment specific to this derived template:  
  
protected override void SpecificFragment(int n)  
{  
#>  
   Specific to DerivedTemplate1 : <#= n #>  
<#+  
}  
#>  
  
```  
  
 **응용 프로그램 코드:**  
  
```csharp  
...   
DerivedTemplate1 t1 = new DerivedTemplate1();  
string result = t1.TransformText();  
Console.WriteLine(result);  
```  
  
 **결과 출력:**  
  
```  
Here is the description for this derived template:  
  Description for this derived class  
  
Here is the fragment specific to this derived template:  
     Specific to DerivedTemplate1 : 42  
End of common template.  
End material for DerivedTemplate1.  
```  
  
## <a name="related-topics"></a>관련 항목  
 디자인 타임 템플릿: 응용 프로그램의 일부가 됩니다 하는 템플릿을 사용 하 여 코드를 생성 하려는 경우, 참조 [T4 텍스트 템플릿을 사용 하 여 디자인 타임 코드 생성](../modeling/design-time-code-generation-by-using-t4-text-templates.md)합니다.  
  
 런타임 템플릿은 컴파일 타임에 템플릿과 그 내용이 결정 됩니다 모든 응용 프로그램에서 사용할 수 있습니다. 그러나 작성 하려는 경우는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 런타임 시 변경, 참조 되는 템플릿에서 텍스트를 생성 하는 확장 [VS 확장에서 텍스트 변환 호출](../modeling/invoking-text-transformation-in-a-vs-extension.md)합니다.  
  
## <a name="see-also"></a>참고 항목  
 [코드 생성 및 T4 텍스트 템플릿](../modeling/code-generation-and-t4-text-templates.md)   
 [T4 텍스트 템플릿 쓰기](../modeling/writing-a-t4-text-template.md)   
 [T4 이해: Oleg 동기화 하 여 전처리 된 텍스트 템플릿](https://github.com/olegsych/T4Toolbox)
