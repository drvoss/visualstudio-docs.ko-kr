---
title: 코드 오류에 대 한 관리 코드 분석 연습 | Microsoft Docs
ms.date: 01/29/2018
ms.topic: conceptual
helpviewer_keywords:
- code analysis [Visual Studio]
- managed code, analyzing
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 4a00fdb2a41a03554113f2ecb626185aab2c74d5
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69548002"
---
# <a name="walkthrough-use-static-code-analysis-to-find-code-defects"></a>연습: 정적 코드 분석을 사용 하 여 코드 오류 찾기

이 연습에서는 레거시 코드 분석을 사용 하 여 코드 오류에 대 한 관리 되는 프로젝트를 분석 합니다.

이 문서에서는 .net 디자인 지침을 준수 하기 위해 레거시 분석을 사용 하 여 .NET 관리 코드 어셈블리를 분석 하는 과정을 단계별로 안내 합니다.

## <a name="create-a-class-library"></a>클래스 라이브러리 만들기

### <a name="to-create-a-class-library"></a>클래스 라이브러리를 만들려면

1. **파일** 메뉴에서 **새로 만들기** > **프로젝트**를 차례로 선택합니다.

1. **새 프로젝트** 대화 상자에서 **설치 된** > **C#시각적 개체**를 확장 한 다음 **Windows 데스크톱**을 선택 합니다.

1. **클래스 라이브러리 (.NET Framework)** 템플릿을 선택 합니다.

1. **이름** 텍스트 상자에 **CodeAnalysisManagedDemo** 를 입력 한 다음 **확인**을 클릭 합니다.

1. 프로젝트를 만든 후 *Class1.cs* 파일을 엽니다.

1. Class1.cs의 기존 텍스트를 다음 코드로 바꿉니다.

   ```csharp
   using System;

   namespace testCode
   {
       public class demo : Exception
       {
           public static void Initialize(int size) { }
           protected static readonly int _item;
           public static int item { get { return _item; } }
       }
   }
   ```

1. Class1.cs 파일을 저장 합니다.

## <a name="analyze-the-project"></a>프로젝트 분석

### <a name="to-analyze-a-managed-project-for-code-defects"></a>코드 오류에 대 한 관리 되는 프로젝트를 분석 하려면

1. **솔루션 탐색기**에서 CodeAnalysisManagedDemo 프로젝트를 선택 합니다.

1. **프로젝트** 메뉴에서 **속성**을 클릭합니다.

     CodeAnalysisManagedDemo 속성 페이지가 표시 됩니다.

1. **코드 분석** 탭을 선택 합니다.

1. **빌드 시 코드 분석 사용** 이 선택 되어 있는지 확인 합니다.

1. **이 규칙 집합 실행** 드롭다운 목록에서 **Microsoft 모든 규칙**을 선택 합니다.

1. **파일** 메뉴에서 **선택한 항목 저장**을 클릭 한 다음 속성 페이지를 닫습니다.

1. **빌드** 메뉴에서 **CodeAnalysisManagedDemo 빌드**를 클릭 합니다.

    CodeAnalysisManagedDemo 프로젝트 빌드 경고는 **오류 목록** 및 **출력** 창에 표시 됩니다.

## <a name="correct-the-code-analysis-issues"></a>코드 분석 문제 해결

### <a name="to-correct-code-analysis-rule-violations"></a>코드 분석 규칙 위반을 수정 하려면

1. **보기** 메뉴에서 **오류 목록**를 선택 합니다.

    선택한 개발자 프로필에 따라 **보기** 메뉴에서 **다른 창** 을 가리킨 다음 **오류 목록**를 선택 해야 할 수 있습니다.

1. **솔루션 탐색기**에서 **모든 파일 표시**를 선택합니다.

1. 속성 노드를 확장 한 다음 *AssemblyInfo.cs* 파일을 엽니다.

1. 다음 팁을 사용 하 여 경고를 수정 하십시오.

   [CA1014: CLSCompliantAttribute](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md)를 사용 하 여 어셈블리 표시: Microsoft. 디자인: ' demo '는 CLSCompliantAttribute로 표시 되어야 하 고 해당 값은 true 여야 합니다.

   1. AssemblyInfo.cs 파일에 `using System;` 코드를 추가 합니다.

   1. 그런 다음 AssemblyInfo.cs 파일의 `[assembly: CLSCompliant(true)]` 끝에 코드를 추가 합니다.

   [CA1032: 표준 예외 생성자](../code-quality/ca1032-implement-standard-exception-constructors.md)를 구현 합니다. Microsoft.Design: 이 클래스에 다음 생성자를 추가 합니다. public demo (String)

   1. `public demo (String s) : base(s) { }` 클래스`demo`에 생성자를 추가 합니다.

   [CA1032: 표준 예외 생성자](../code-quality/ca1032-implement-standard-exception-constructors.md)를 구현 합니다. Microsoft.Design: 이 클래스에 다음 생성자를 추가 합니다. public demo (문자열, 예외)

   1. `public demo (String s, Exception e) : base(s, e) { }` 클래스`demo`에 생성자를 추가 합니다.

   [CA1032: 표준 예외 생성자](../code-quality/ca1032-implement-standard-exception-constructors.md)를 구현 합니다. Microsoft.Design: 이 클래스에 다음 생성자를 추가 합니다. protected demo (SerializationInfo, StreamingContext)

   1. Class1.cs 파일의 `using System.Runtime.Serialization;` 시작 부분에 코드를 추가 합니다.

   1. 다음으로 생성자를 추가 합니다.`protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { } to the class demo.`

   [CA1032: 표준 예외 생성자](../code-quality/ca1032-implement-standard-exception-constructors.md)를 구현 합니다. Microsoft.Design: 이 클래스에 다음 생성자를 추가 합니다. public demo ()

   1. `public demo () : base() { }` 클래스`demo`에 생성자를 추가 **합니다.**

   [CA1709: 식별자의 대/소문자](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)를 올바르게 지정 해야 합니다. Microsoft.Naming: ' Testcode '로 변경 하 여 네임 스페이스 이름 ' testCode '의 대/소문자를 수정 하십시오.

   1. 네임 스페이스 `testCode` 의 대/소문자를 `TestCode`로 변경 합니다.

   [CA1709: 식별자의 대/소문자](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)를 올바르게 지정 해야 합니다. Microsoft.Naming: ' Demo ' 형식으로 변경 하 여 형식 이름 ' demo '의 대/소문자를 수정 하십시오.

   1. 멤버의 이름을로 `Demo`변경 합니다.

   [CA1709: 식별자의 대/소문자](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)를 올바르게 지정 해야 합니다. Microsoft.Naming: ' Item ' 멤버 이름의 대/소문자를 ' 항목 '으로 변경 하 여 수정 하십시오.

   1. 멤버의 이름을로 `Item`변경 합니다.

   [CA1710: 식별자에는 올바른 접미사가](../code-quality/ca1710-identifiers-should-have-correct-suffix.md)있어야 합니다. Microsoft.Naming: ' TestCode. demo '의 이름을 ' Exception '에서 끝으로 바꿉니다.

   1. 클래스 및 생성자의 이름을로 `DemoException`변경 합니다.

   [CA2210: 어셈블리에는 올바른 강력한 이름이](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md)있어야 합니다. 강력한 이름 키를 사용 하 여 ' CodeAnalysisManagedDemo '에 서명 합니다.

   1. **프로젝트** 메뉴에서 **CodeAnalysisManagedDemo 속성**을 선택 합니다.

      프로젝트 속성이 표시 됩니다.

   1. **서명** 탭을 선택합니다.

   1. **어셈블리 서명** 확인란을 선택 합니다.

   1. **문자열 이름 키 파일 선택** 목록에서  **\<새로 만들기 ...를 선택 합니다. >** .

      **강력한 이름 키 만들기** 대화 상자가 나타납니다.

   1. **키 파일 이름**에 testkey를 입력 합니다.

   1. 암호를 입력 한 다음 **확인**을 선택 합니다.

   1. **파일** 메뉴에서 **선택한 항목 저장**을 선택한 다음 속성 페이지를 닫습니다.

   [CA2237: SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)로 ISerializable 형식 표시: Microsoft.Usage: 이 형식이 ISerializable을 구현 하므로 [Serializable] 특성을 ' demo ' 형식에 추가 합니다.

   1. `[Serializable ()]` 클래스`demo`에 특성을 추가 합니다.

   변경을 완료한 후 Class1.cs 파일은 다음과 같습니다.

   ```csharp
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

1. 프로젝트를 다시 빌드합니다.

## <a name="exclude-code-analysis-warnings"></a>코드 분석 경고 제외

1. 나머지 경고 각각에 대해 다음을 수행합니다.

    1. **오류 목록**에서 경고를 선택 합니다.

    1. 오른쪽 클릭 메뉴 (상황에 맞는 메뉴)에서 비 **표시 표시 안 함** > **파일에서**표시 안 함을 선택 합니다.

1. 프로젝트를 다시 빌드합니다.

     프로젝트는 경고 또는 오류 없이 빌드됩니다.

## <a name="see-also"></a>참고자료

[관리 코드에 대 한 코드 분석](../code-quality/code-analysis-for-managed-code-overview.md)