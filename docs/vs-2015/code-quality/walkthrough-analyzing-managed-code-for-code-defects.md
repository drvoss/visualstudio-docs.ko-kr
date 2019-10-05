---
title: '연습: 관리 되는 코드의 코드 오류 분석 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, walkthroughs
- managed code, analyzing
- code analysis tool, walkthroughs
ms.assetid: 22b99f49-1924-4fb5-a421-c8b23e5d5cd4
caps.latest.revision: 47
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 26d8412318efd2292fd0f5a0f0ef52fe36c7d06c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68201142"
---
# <a name="walkthrough-analyzing-managed-code-for-code-defects"></a>연습: 코드 오류에 대한 관리 코드 분석
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 연습에서는 코드 분석 도구를 사용 하 여 코드 오류에 대 한 관리 되는 프로젝트를 분석 합니다.  
  
 이 연습에서는 Microsoft.NET Framework 디자인 지침을 사용 하 여 규칙에 대 한.NET 관리 코드 어셈블리를 분석 하려면 코드 분석을 사용 하는 프로세스 안내 합니다.  
  
 이 연습에서는 있습니다.  
  
- 분석 하 고 코드 오류 경고를 수정 합니다.  
  
## <a name="prerequisites"></a>필수 구성 요소  
  
- [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)].  
  
## <a name="create-a-class-library"></a>클래스 라이브러리 만들기  
  
#### <a name="to-create-a-class-library"></a>클래스 라이브러리를 만들려면  
  
1. 에 **파일** 메뉴 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], 클릭 **새로 만들기** 클릭 하 고 **프로젝트**합니다.  
  
2. 에 **새 프로젝트** 대화 상자의 **프로젝트 형식**, 클릭 **Visual C#** 합니다.  
  
3. 아래 **템플릿을**를 선택 **클래스 라이브러리**합니다.  
  
4. 에 **이름** 텍스트 상자에서 **CodeAnalysisManagedDemo** 을 클릭 한 다음 **확인**합니다.  
  
5. 프로젝트를 만든 후 Class1.cs 파일을 엽니다.  
  
6. Class1.cs에서 기존 텍스트를 다음 코드로 바꿉니다.  
  
     `//CodeAnalysisManagedDemo //Class1.cs using System;  namespace testCode {          public class demo : Exception     {                  public static void Initialize(int size) { }         protected static readonly int _item;         public static int item { get { return _item; } }     } }`  
  
7. Class1.cs 파일을 저장 합니다.  
  
## <a name="analyze-the-project"></a>프로젝트를 분석 합니다.  
  
#### <a name="to-analyze-a-managed-project-for-code-defects"></a>코드 오류에 대 한 관리 되는 프로젝트를 분석 하려면  
  
1. CodeAnalysisManagedDemo 프로젝트에서 선택 **솔루션 탐색기**합니다.  
  
2. **프로젝트** 메뉴에서 **속성**을 클릭합니다.  
  
     CodeAnalysisManagedDemo 속성 페이지가 표시 됩니다.  
  
3. 클릭 **CodeAnalysis**합니다.  
  
4. 했는지 **빌드에 코드 분석 사용 (CODE_ANALYSIS 상수 정의**) 확인란이 선택 되어 있습니다.  
  
5. **이 규칙 집합 실행** 드롭 다운 목록에서 **Microsoft 모든 규칙**합니다.  
  
6. 에 **파일** 메뉴에서 클릭 **선택한 항목 저장**, ManagedDemo 속성 페이지를 닫습니다.  
  
7. 에 **빌드** 메뉴에서 클릭 **빌드 ManagedDemo**합니다.  
  
     CodeAnalysisManagedDemo 프로젝트 빌드 경고에 보고 되는 **코드 분석** 하 고 **출력** windows.  
  
     경우는 **코드 분석** 창이 표시 되지 않는는 **분석** 메뉴에서 선택 **Windows** 차례로 **코드 분석**합니다.  
  
## <a name="correct-the-code-analysis-issues"></a>코드 분석 문제 해결  
  
#### <a name="to-correct-code-analysis-rule-violations"></a>코드 분석 규칙 위반을 수정 하려면  
  
1. 에 **뷰** 메뉴에서 클릭 **오류 목록**합니다.  
  
     가리키도록 해야 선택한 개발자 프로필에 따라 **다른 Windows** 에 **뷰** 메뉴를 클릭 한 다음 **오류 목록**합니다.  
  
2. **솔루션 탐색기**, 클릭 **모든 파일 표시**합니다.  
  
3. 다음으로 속성 노드를 확장 한 다음 AssemblyInfo.cs 파일을 엽니다.  
  
4. 경고를 해결 하려면 다음을 사용 합니다.  
  
- [CA1014: CLSCompliantAttribute로 어셈블리 표시](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md): Microsoft.Design: '데모'를 CLSCompliantAttribute로 표시 되어야 합니다 하 고 해당 값은 true 여야 합니다.  
  
  - 코드를 추가 `using``System;` AssemblyInfo.cs 파일에 있습니다.  
  
       다음으로 코드를 추가 `[assembly: CLSCompliant(true)]` AssemblyInfo.cs 파일의 끝에 있습니다.  
  
       프로젝트를 다시 빌드합니다.  
  
- [CA1032: 표준 예외 생성자를 구현](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: 이 클래스에 다음 생성자를 추가 합니다: 공용 demo(String)  
  
  - 생성자를 추가 합니다 `public demo (String s) : base(s) { }` 클래스에 `demo`입니다.  
  
- [CA1032: 표준 예외 생성자를 구현](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: 이 클래스에 다음 생성자를 추가 합니다: 공용 데모 (String, 예외)  
  
  - 생성자를 추가 합니다 `public demo (String s, Exception e) : base(s, e) { }` 클래스에 `demo`입니다.  
  
- [CA1032: 표준 예외 생성자를 구현](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: 이 클래스에 다음 생성자를 추가 합니다: 데모 (SerializationInfo, StreamingContext) 보호  
  
  - 코드를 추가 `using System.Runtime.Serialization;` Class1.cs 파일의 시작 부분에 있습니다.  
  
       그런 다음 생성자를 추가 `protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { } to the class demo.`  
  
       프로젝트를 다시 빌드합니다.  
  
- [CA1032: 표준 예외 생성자를 구현](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: 이 클래스에 다음 생성자를 추가 합니다: 공용 demo()  
  
  - 생성자를 추가 합니다 `public demo () : base() { }` 클래스에 `demo` **합니다.**  
  
       프로젝트를 다시 빌드합니다.  
  
- [CA1709: 식별자에는 올바르게 표기를 사용 해야](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: 'TestCode'로 변경 하 여 네임 스페이스 이름 'testCode'의 대/소문자를 수정 합니다.  
  
  - 네임 스페이스의 대/소문자를 변경 `testCode` 에 `TestCode`입니다.  
  
- [CA1709: 식별자에는 올바르게 표기를 사용 해야](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: 형식 이름 '데모'의 대/소문자를 '데모'로 변경 하 여 수정 합니다.  
  
  - 멤버의 이름을 변경 `Demo`합니다.  
  
- [CA1709: 식별자에는 올바르게 표기를 사용 해야](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: 'Item'로 변경 하 여 멤버 이름 'item'의 대/소문자를 수정 합니다.  
  
  - 멤버의 이름을 변경 `Item`합니다.  
  
- [CA1710: 식별자에는 올바른 접미사를 사용 해야 합니다.](../code-quality/ca1710-identifiers-should-have-correct-suffix.md): Microsoft.Naming: 'Exception'에서 end 'testCode.demo를'의 이름을 바꿉니다.  
  
  - 클래스 및 해당 생성자의 이름을 변경 `DemoException`합니다.  
  
- [CA2210: 어셈블리에는 올바른 강력한 이름을 사용 해야 합니다.](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md): 'ManagedDemo' 강력한 이름 키를 사용 하 여 로그인 합니다.  
  
  - 에 **프로젝트** 메뉴에서 클릭 **ManagedDemo 속성**합니다.  
  
       프로젝트 속성이 표시 됩니다.  
  
       클릭 **서명**합니다.  
  
       선택 된 **어셈블리에 서명할** 확인란 합니다.  
  
       에 **강력한 이름 키 파일 선택** 목록에서  **\<새로 만들기... >** 합니다.  
  
       합니다 **강력한 이름 키 만들기** 대화 상자가 나타납니다.  
  
       에 **키 파일 이름**, TestKey를 입력 합니다.  
  
       암호를 입력 한 다음 클릭 **확인**합니다.  
  
       에 **파일** 메뉴에서 클릭 **선택한 항목 저장**, 한 다음 속성 페이지를 닫습니다.  
  
       프로젝트를 다시 빌드합니다.  
  
- [CA2237: SerializableAttribute로 ISerializable 형식 표시](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md): Microsoft.Usage: 이 형식이 ISerializable을 구현 하는 대로 '데모'를 입력 [Serializable] 특성을 추가 합니다.  
  
  - 추가 된 `[Serializable ()]` 특성을 클래스 `demo`합니다.  
  
       프로젝트를 다시 빌드합니다.  
  
  변경을 완료한 후 Class1.cs 파일은 다음과 같습니다.  
  
```  
//CodeAnalysisManagedDemo  
//Class1.cs  
using System;  
using System.Runtime.Serialization;  
  
namespace TestCode  
{  
  
    [Serializable()]   
    public class DemoException : Exception  
    {  
        public DemoException () : base() { }  
        public DemoException(String s) : base(s) { }  
        public DemoException(String s, Exception e) : base(s, e) { }  
        protected DemoException(SerializationInfo info, StreamingContext context) : base(info, context) { }  
  
        public static void Initialize(int size) { }  
        protected static readonly int _item;  
        public static int Item { get { return _item; } }  
    }  
}  
```  
  
## <a name="exclude-code-analysis-warnings"></a>코드 분석 경고를 제외 합니다.  
  
#### <a name="to-exclude-code-defect-warnings"></a>코드 오류 경고를 제외 하려면  
  
1. 나머지 경고 각각에 대해 다음을 수행합니다.  
  
   1. 코드 분석 창에서 경고를 선택합니다.  
  
   2. 선택 **동작**, 선택한 **메시지 표시 안 함**를 선택한 후 **프로젝트 비 표시 오류 파일의**합니다.  
  
      자세한 내용은 [방법: 메뉴 항목을 사용 하 여 경고 표시 안 함](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md)  
  
2. 프로젝트를 다시 빌드합니다.  
  
    프로젝트 경고 또는 오류 없이 빌드됩니다.
