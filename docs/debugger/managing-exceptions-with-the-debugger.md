---
title: 디버거를 사용한 예외 관리 | Microsoft Docs
ms.custom: seodec18
ms.date: 10/09/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.exceptions
- vs.debug.exceptions.find
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- run-time errors
- exception handling, during debugging
- errors [debugger]
- debugger, runtime errors
- On Error-style error handlers
- exceptions, Win32
- run-time errors, debugging
- Win32, exceptions
- run time, exceptions
- error handling
- debugging [Visual Studio], exception handling
- common language runtime, exceptions
- native run-time checks
- exceptions, debugging
ms.assetid: 43a77fa8-37d0-4c98-a334-0134dbca4ece
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b83cb026bec6d33490517e5703a042b4a8e2434c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62846583"
---
# <a name="manage-exceptions-with-the-debugger-in-visual-studio"></a>Visual Studio에서 디버거를 사용한 예외 관리

예외는 프로그램이 실행되는 동안 발생하는 오류 상태를 나타냅니다. 예외 또는 집합 예외를 중단 하도록 디버거에 지시할 수 있습니다 및 중단 하도록 디버거를 원하는 시점 (즉, 디버거에서 일시 중지) 합니다. 디버거가 중단 되 면 예외가 throw 된 보여줍니다. 추가 하거나 예외를 삭제할 수도 있습니다. Visual Studio에서 열려 있는 솔루션을 사용 하 여 **디버그 > Windows > 예외 설정** 열려는 합니다 **예외 설정** 창입니다.

가장 중요 한 예외에 응답 하는 처리기를 제공 합니다. 예외에 대 한 처리기를 추가, 참조 하는 방법을 알아야 하는 경우 [잘 작성 하 여 버그를 수정 합니다. C# 코드](../debugger/write-better-code-with-visual-studio.md)합니다. 또한 항상 몇 가지 예외에 대 한 실행을 중단 하도록 디버거를 구성 하는 방법에 알아봅니다.

예외가 발생하면 디버거가 **출력** 창에 예외 메시지를 씁니다. 다음에서 실행을 중단할 수 있으므로 경우 사례:

- 예외가 처리 되지 않은 throw 됩니다.
- 디버거는 처리기가 호출 되기 전에 실행을 중단 하도록 구성 됩니다.
- 설정한 [Just My Code](../debugger/just-my-code.md), 디버거가 사용자 코드에서 처리 되지 않은 모든 예외에서 중단 하도록 구성 되어 있습니다.

> [!NOTE]
> ASP.NET에는 브라우저에 오류 페이지를 표시하는 최상위 예외 처리기가 있습니다. 하지 않는 한 실행을 중단 하지 않습니다 **Just My Code** 켜져 있습니다. 예를 들어 참조 [사용자가 처리 하지 않은 예외에 대해 계속 하도록 디버거에 지시할](#BKMK_UserUnhandled) 아래.

<!-- Two consecutive notes are intentional here...-->

> [!NOTE]
> Visual Basic 애플리케이션에서 디버거는 모든 오류를 예외로 관리합니다. 이는 On Error 스타일의 오류 처리기를 사용하는 경우에도 마찬가지입니다.

## <a name="tell-the-debugger-to-break-when-an-exception-is-thrown"></a>예외가 throw 되 면 중단 하도록 디버거에 지시합니다

처리기가 호출 되기 전에 예외를 검사할 수 있도록 디버거 예외가 throw 되는 지점에서 실행을 중단할 수 있습니다.

에 **예외 설정** 창 (**디버그 > Windows > 예외 설정**), 같은 예외 범주에 대 한 노드를 확장 **Common Language Runtime Exceptions**. 선택한 다음 해당 범주 내의 특정 예외에 대 한 확인란을 같은 **System.AccessViolationException**합니다. 전체 예외 범주를 선택할 수도 있습니다.

![Checked AccessViolationException](../debugger/media/exceptionsettingscheckaccess.png "ExceptionSettingsCheckAccess")

> [!TIP]
> 사용 하 여 특정 예외를 찾을 수 있습니다 합니다 **검색** 창에는 **예외 설정** 도구 모음 또는 검색 특정 네임 스페이스에 대 한 필터링을 사용 (같은 **System.IO**).

예외를 선택 합니다 **예외 설정** 창 처리 되는 여부에 상관 없이 예외가 throw 됩니다 때마다 디버거 실행이 중단 됩니다. 이제 예외는 첫 번째 예외가 호출 됩니다. 예를 들어 다음은 몇 가지 시나리오입니다.

- 다음 C# 콘솔 애플리케이션에서 Main 메서드는 `try/catch` 블록 내부에서 **AccessViolationException**을 발생시킵니다.

  ```csharp
  static void Main(string[] args)
  {
      try
      {
          throw new AccessViolationException();
          Console.WriteLine("here");
      }
      catch (Exception e)
      {
          Console.WriteLine("caught exception");
      }
      Console.WriteLine("goodbye");
  }
  ```

  있다면 **AccessViolationException** 체크 **예외 설정**, 실행 중단 됩니다는 `throw` 디버거에서이 코드를 실행 하면 줄. 그런 다음 실행을 계속할 수 있습니다. 콘솔에 다음 두 줄이 모두 표시됩니다.

  ```cmd
  caught exception
  goodbye
  ```

  하지만 표시 하지 않습니다는 `here` 줄.

- C# 콘솔 응용 프로그램에는 두 개의 메서드가 있는 클래스를 클래스 라이브러리를 참조 합니다. 예외를 throw 하 고 두 번째 방법은 동일한 예외를 throw 하지만 처리 하지 않는 처리 하는 한 가지 방법은 합니다.

  ```csharp
  public class Class1
  {
      public void ThrowHandledException()
      {
          try
          {
              throw new AccessViolationException();
          }
          catch (AccessViolationException ave)
          {
              Console.WriteLine("caught exception" + ave.Message);
          }
      }

      public void ThrowUnhandledException()
      {
          throw new AccessViolationException();
      }
  }
  ```

  콘솔 애플리케이션의 Main() 메서드는 다음과 같습니다.

  ```csharp
  static void Main(string[] args)
  {
      Class1 class1 = new Class1();
      class1.ThrowHandledException();
      class1.ThrowUnhandledException();
  }
  ```

  있는 경우 **AccessViolationException** 체크 **예외 설정**, 실행 중단 됩니다는 `throw` 둘 다에서 줄 **ThrowHandledException()** 및 **ThrowUnhandledException()** 디버거에서이 코드를 실행 하면 됩니다.

예외 설정을 기본값으로 복원 하려면 선택 합니다 **기본 설정으로 목록 복원** 단추:

![예외 설정에서 기본값 복원](../debugger/media/restoredefaultexceptions.png "RestoreDefaultExceptions")

## <a name="BKMK_UserUnhandled"></a>사용자가 처리 하지 않은 예외에 대해 계속 하도록 디버거에 지시합니다

사용 하 여.NET 또는 JavaScript 코드를 디버깅 하는 경우 [Just My Code](../debugger/just-my-code.md), 사용자 코드에서 처리 되지 않았지만 다른 곳에서 처리 된 예외가 중단을 방지 하기 위해 디버거에 지시할 수 있습니다.

1. 에 **예외 설정** 창에서 열 레이블을 마우스 오른쪽 단추로 클릭 하 여 바로 가기 메뉴를 열고 선택 합니다 **표시 열 > 추가 작업**합니다. (하지 않도록 설정한 경우 **Just My Code**,이 명령은 표시 되지 않습니다.) 라는 세 번째 열 **추가 작업** 나타납니다.

   ![추가 작업 열의](../debugger/media/additionalactionscolumn.png "AdditionalActionsColumn")

   예외를 보여 주는 **사용자 코드에서 처리 되지 않은 경우 계속** 이 칼럼에서는 디버거가 계속 해당 예외가 사용자 코드에서 처리 되지 않습니다 하지만 외부적으로 처리 하는 경우.

2. 특정 예외에 대해이 설정을 변경 하려면 예외를 선택 합니다. 마우스 오른쪽 단추로 클릭 바로 가기 메뉴를 표시 하려면 선택 **계속 처리 되지 않은 경우 사용자 코드에서**합니다. 변경할 수 있습니다도 전체 전체 공용 언어 런타임 예외와 같은 예외 범주에 대 한 설정).

   ![* * 사용자 코드 * * 설정에서 처리 되지 않은 경우 계속](../debugger/media/continuewhenunhandledinusercodesetting.png "ContinueWhenUnhandledInUserCodeSetting")

ASP.NET 웹 응용 프로그램을 HTTP 500 상태 코드를 변환 하 여 예외를 처리 하는 예를 들어, ([ASP.NET Web API의 예외 처리](http://www.asp.net/web-api/overview/error-handling/exception-handling)), 예외의 원인을 파악 하는 게 도움이 되지 않을 수 있습니다. 아래 예제에서는 사용자 코드가 `String.Format()` 을 발생시키는 <xref:System.FormatException>을 호출합니다. 다음과 같이 실행이 중단됩니다.

![사용자에서 중단&#45;처리 되지 않은 예외가](../debugger/media/exceptionunhandledbyuser.png "ExceptionUnhandledByUser")

## <a name="add-and-delete-exceptions"></a>예외 추가 및 삭제

예외를 추가하거나 삭제할 수 있습니다. 예외 형식 범주에서를 삭제 하려면 예외를 선택 하 고 선택 합니다 **목록에서 선택한 예외를 삭제** 단추 (빼기 기호)를 **예외 설정** 도구 모음입니다. 예외를 마우스 오른쪽 단추로 클릭 하 고 선택할 수 있습니다 **삭제** 바로 가기 메뉴에서. 예외를 삭제 하는 것과 동일한 효과가 있는 옵션을 선택 취소 하는 예외 throw 되는 디버거가 중단 되지 않습니다는.

예외를 추가 합니다.

1. 에 **예외 설정** 창에서 예외 범주 중 하나를 선택 (예를 들어 **공용 언어 런타임**).

2. 선택 된 **선택한 범주에 예외를 추가** 단추 (+ 기호).

   ![* * 선택한 범주 * * 단추에 예외를 추가 합니다.](../debugger/media/addanexceptiontotheselectedcategorybutton.png "AddAnExceptionToTheSelectedCategoryButton")

3. 예외의 이름을 입력 (예를 들어 **System.UriTemplateMatchException**).

   ![예외 이름을 입력](../debugger/media/typetheexceptionname.png "TypeTheExceptionName")

   예외 (알파벳 순서로) 목록에 추가 되 고 자동으로 선택 합니다.

GPU 메모리 액세스 예외, JavaScript 런타임 예외 또는 Win32 예외 범주에 예외를 추가 하려면 설명 및 오류 코드를 포함 합니다.

> [!TIP]
> 맞춤법 검사를 수행합니다. **예외 설정** 창에서는 추가된 예외가 있는지 검사하지 않습니다. 따라서 **Sytem.UriTemplateMatchException**을 입력하면 해당 예외에 대한 항목( **System.UriTemplateMatchException**에 대한 항목이 아님)을 얻게 됩니다.

예외 설정은 솔루션의 .suo파일에 유지되므로 특정 솔루션에 적용됩니다. 특정 예외 설정을 여러 솔루션에서 다시 사용할 수 없습니다. 이제 추가 된 예외만 유지 됩니다. 삭제 된 예외가 없습니다. 예외를 추가 하 고 솔루션을 다시 열 수 있습니다 및 예외 수 있습니다. 그러나 예외를 삭제한 후 솔루션을 닫았다가 다시 열면 예외가 다시 나타나지 않습니다.

**예외 설정** 창은 C#의 일반적인 예외 형식을 지원하지만 Visual Basic의 일반 예외 형식은 지원하지 않습니다. `MyNamespace.GenericException<T>`와 같은 예외에서 실행을 중단하려면 **MyNamespace.GenericException`1**과 같은 예외를 추가해야 합니다. 즉,이 코드 처럼 예외를 만든 경우:

```csharp
public class GenericException<T> : Exception
{
    public GenericException() : base("This is a generic exception.")
    {
    }
}
```

예외를 추가할 수 있습니다 **예외 설정** 이전 절차를 사용 하 여:

![일반 예외 추가](../debugger/media/addgenericexception.png "AddGenericException")

## <a name="add-conditions-to-an-exception"></a>예외에 조건 추가

사용 된 **예외 설정** 예외에 조건을 설정 하는 창입니다. 현재 지원 되는 조건을 포함 하거나 제외할 예외에 대 한 모듈 이름을 포함 합니다. 모듈 이름 조건으로로 설정 하면 특정 코드 모듈에만 예외에 대 한 중단 하도록 선택할 수 있습니다. 특정 모듈에서 분리를 방지할 수도 있습니다.

> [!NOTE]
> 부터 지원 되는 예외에 조건 추가 [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]합니다.

조건부 예외를 추가 합니다.

1. 선택 된 **조건 편집** 예외 설정 창에서 단추 및 예외를 마우스 오른쪽 단추로 클릭 한 다음 선택 **조건 편집**합니다.

   ![예외에 대 한 조건을](../debugger/media/dbg-conditional-exception.png "DbgConditionalException")

2. 추가 필수 조건에는 예외를 추가 하려면 선택 **조건 추가** 각 새 조건에 대 한 합니다. 추가 조건 선이 표시 됩니다.

   ![예외에 대 한 추가 조건을](../debugger/media/extraconditionsforanexception.png "ExtraConditionsForAnException")

3. 각 상태 줄에 대 한 모듈의 이름을 입력 하 고 비교 연산자 목록 변경 **Equals** 또는 **Not Equals**합니다. 와일드 카드를 지정할 수 있습니다 (**\\\***) 모듈을 둘 이상 지정 하려면 이름에 있습니다.

4. 조건을 삭제 해야 할 경우 선택 합니다 **X** 조건 줄의 끝입니다.

## <a name="see-also"></a>참고자료

- [예외 후 실행 계속](../debugger/continuing-execution-after-an-exception.md)<br/>
- [방법: 예외 발생 후 시스템 코드 검사](../debugger/how-to-examine-system-code-after-an-exception.md)<br/>
- [방법: 네이티브 런타임 검사 사용](../debugger/how-to-use-native-run-time-checks.md)<br/>
- [C 런타임 라이브러리 없이 런타임 검사 사용](../debugger/using-run-time-checks-without-the-c-run-time-library.md)<br/>
- [디버거 소개](../debugger/debugger-feature-tour.md)
