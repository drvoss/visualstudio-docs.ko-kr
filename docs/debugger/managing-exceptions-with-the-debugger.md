---
title: 디버거를 사용 하 여 예외 관리 | Microsoft Docs
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
ms.openlocfilehash: 00ad5b41dd0a11661d281f24474b7673ea0a342c
ms.sourcegitcommit: 257fc60eb01fefafa9185fca28727ded81b8bca9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72911506"
---
# <a name="manage-exceptions-with-the-debugger-in-visual-studio"></a>Visual Studio에서 디버거를 사용 하 여 예외 관리

예외는 프로그램이 실행되는 동안 발생하는 오류 상태를 나타냅니다. 중단할 예외 또는 예외 집합을 디버거에 알리고 디버거를 중단할 지점 (즉, 디버거에서 일시 중지)을 지정할 수 있습니다. 디버거가 중단 되 면 예외가 throw 된 위치를 표시 합니다. 예외를 추가 하거나 삭제할 수도 있습니다. Visual Studio에서 솔루션을 열고 **디버그 > Windows > 예외 설정** 을 사용 하 여 **예외 설정** 창을 엽니다.

가장 중요 한 예외에 응답 하는 처리기를 제공 합니다. 예외에 대 한 처리기를 추가 하는 방법을 알고 있어야 하는 경우 [더 나은 C# 코드를 작성 하 여 버그 수정](../debugger/write-better-code-with-visual-studio.md)을 참조 하세요. 또한 일부 예외에 대해 항상 실행을 중단 하도록 디버거를 구성 하는 방법에 대해 알아봅니다.

예외가 발생하면 디버거가 **출력** 창에 예외 메시지를 씁니다. 다음과 같은 경우에 실행이 중단 될 수 있습니다.

- 처리 되지 않은 예외가 throw 됩니다.
- 디버거는 처리기가 호출 되기 전에 실행을 중단 하도록 구성 됩니다.
- [내 코드만](../debugger/just-my-code.md)를 설정 했으며, 사용자 코드에서 처리 되지 않은 예외에서 중단 하도록 디버거가 구성 되어 있습니다.

> [!NOTE]
> ASP.NET에는 브라우저에 오류 페이지를 표시하는 최상위 예외 처리기가 있습니다. **내 코드만** 를 설정 하지 않으면 실행이 중단 되지 않습니다. 예를 들어 아래에서 [사용자가 처리 하지 않은 예외에 대 한 작업을 계속 하도록 디버거에 지시](#BKMK_UserUnhandled) 를 참조 하세요.

<!-- Two consecutive notes are intentional here...-->

> [!NOTE]
> Visual Basic 애플리케이션에서 디버거는 모든 오류를 예외로 관리합니다. 이는 On Error 스타일의 오류 처리기를 사용하는 경우에도 마찬가지입니다.

## <a name="tell-the-debugger-to-break-when-an-exception-is-thrown"></a>예외가 throw 될 때 중단 하도록 디버거에 지시 합니다.

디버거는 예외가 발생 한 지점에서 실행을 중단 하 여 처리기가 호출 되기 전에 예외를 검사할 수 있습니다.

**예외 설정** 창 (**디버그 > Windows > 예외 설정**)에서 **공용 언어 런타임 예외**와 같은 예외 범주에 대 한 노드를 확장 합니다. 그런 다음 해당 범주 내의 특정 예외 (예: **AccessViolationException**)에 대 한 확인란을 선택 합니다. 전체 예외 범주를 선택할 수도 있습니다.

![선택 된 AccessViolationException](../debugger/media/exceptionsettingscheckaccess.png "ExceptionSettingsCheckAccess")

> [!TIP]
> **예외 설정** 도구 모음에 있는 **검색** 창을 사용 하 여 특정 예외를 찾거나 검색을 사용 하 여 특정 네임 스페이스 (예: **System.IO**)를 필터링 할 수 있습니다.

예외 **설정** 창에서 예외를 선택 하면 처리 여부에 관계 없이 예외가 throw 될 때마다 디버거 실행이 중단 됩니다. 이제 예외를 첫째 예외 라고 합니다. 예를 들어 다음은 몇 가지 시나리오입니다.

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

  **AccessViolationException** 를 체크 인 한 **예외 설정이**있는 경우 디버거에서이 코드를 실행할 때 `throw` 줄에서 실행이 중단 됩니다. 그런 다음 실행을 계속할 수 있습니다. 콘솔에 다음 두 줄이 모두 표시됩니다.

  ```cmd
  caught exception
  goodbye
  ```

  그러나 `here` 줄은 표시 되지 않습니다.

- 콘솔 C# 응용 프로그램은 두 개의 메서드가 있는 클래스를 사용 하 여 클래스 라이브러리를 참조 합니다. 한 메서드는 예외를 throw 하 고 처리 하지만, 두 번째 메서드는 동일한 예외를 throw 하지만 처리 하지는 않습니다.

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

  **AccessViolationException** 를 체크 인 한 **예외 설정이**있는 경우 디버거에서이 코드를 실행할 때 **ThrowHandledException ()** 및 **ThrowUnhandledException ()** 의 `throw` 줄에서 실행이 중단 됩니다.

예외 설정을 기본값으로 복원 하려면 **기본 설정으로 목록 복원 단추를** 선택 합니다.

![예외 설정의 기본값 복원](../debugger/media/restoredefaultexceptions.png "RestoreDefaultExceptions")

## <a name="BKMK_UserUnhandled"></a>사용자가 처리 하지 않은 예외에 대해 계속 하려면 디버거에 지시 합니다.

[내 코드만](../debugger/just-my-code.md)를 사용 하 여 .Net 또는 JavaScript 코드를 디버그 하는 경우 사용자 코드에서 처리 되지 않았지만 다른 위치에서 처리 되는 예외를 방지 하도록 디버거에 지시할 수 있습니다.

1. **예외 설정** 창에서 열 레이블을 마우스 오른쪽 단추로 클릭 하 여 바로 가기 메뉴를 열고 **추가 작업 > 열 표시**를 선택 합니다. **내 코드만**해제 한 경우에는이 명령이 표시 되지 않습니다. **추가 동작** 이라는 세 번째 열이 나타납니다.

   ![추가 작업 열](../debugger/media/additionalactionscolumn.png "Additional의 열")

   이 열에 있는 **사용자 코드에서 처리 되지 않은 경우 Continue** 를 표시 하는 예외는 예외가 사용자 코드에서 처리 되지 않았지만 외부에서 처리 되는 경우 디버거를 계속 합니다.

2. 특정 예외에 대 한이 설정을 변경 하려면 예외를 선택 하 고 마우스 오른쪽 단추를 클릭 하 여 바로 가기 메뉴를 표시 하 고 **사용자 코드에서 처리 되지 않은 경우 계속**을 선택 합니다. 전체 공용 언어 런타임 예외와 같은 전체 예외 범주에 대 한 설정을 변경할 수도 있습니다.

   ![* * 사용자 코드에서 처리 되지 않은 경우 계속 * * 설정](../debugger/media/continuewhenunhandledinusercodesetting.png "ContinueWhenUnhandledInUserCodeSetting")

예를 들어, ASP.NET 웹 응용 프로그램은 예외를 HTTP 500 상태 코드 ([ASP.NET Web API의 예외 처리](/aspnet/web-api/overview/error-handling/exception-handling))로 변환 하 여 예외를 처리 하며,이는 예외 원인을 확인 하는 데 도움이 되지 않을 수 있습니다. 아래 예제에서는 사용자 코드가 `String.Format()` 을 발생시키는 <xref:System.FormatException>을 호출합니다. 다음과 같이 실행이 중단됩니다.

![사용자가&#45;처리 하지 않은 예외에서 중단](../debugger/media/exceptionunhandledbyuser.png "ExceptionUnhandledByUser")

## <a name="add-and-delete-exceptions"></a>예외 추가 및 삭제

예외를 추가하거나 삭제할 수 있습니다. 범주에서 예외 유형을 삭제 하려면 예외를 선택 하 고 **예외 설정** 도구 모음에 있는 **목록에서 선택한 예외 삭제** 단추 (빼기 기호)를 선택 합니다. 또는 예외를 마우스 오른쪽 단추로 클릭 하 고 바로 가기 메뉴에서 **삭제** 를 선택할 수도 있습니다. 예외를 삭제 하는 것은 예외를 선택 취소 하는 것과 동일한 효과가 있습니다. 즉, 디버거가 throw 될 때 중단 되지 않습니다.

예외를 추가 하려면:

1. **예외 설정** 창에서 예외 범주 중 하나 (예: **공용 언어 런타임**)를 선택 합니다.

2. **선택한 범주에 예외 추가** 단추 (더하기 기호)를 선택 합니다.

   ![* * 선택한 범주에 예외를 추가 합니다. * * 단추](../debugger/media/addanexceptiontotheselectedcategorybutton.png "AddAnExceptionToTheSelectedCategoryButton")

3. 예외의 이름을 입력 합니다 (예: **system.uritemplatematchexception**).

   ![예외 이름 입력](../debugger/media/typetheexceptionname.png "유형-Exceptionname")

   예외는 목록 (사전순)에 추가 되 고 자동으로 확인 됩니다.

GPU 메모리 액세스 예외, JavaScript 런타임 예외 또는 Win32 예외 범주에 예외를 추가 하려면 오류 코드 및 설명을 포함 합니다.

> [!TIP]
> 맞춤법 검사를 수행합니다. **예외 설정** 창에서는 추가된 예외가 있는지 검사하지 않습니다. 따라서 **Sytem.UriTemplateMatchException**을 입력하면 해당 예외에 대한 항목( **System.UriTemplateMatchException**에 대한 항목이 아님)을 얻게 됩니다.

예외 설정은 솔루션의 .suo파일에 유지되므로 특정 솔루션에 적용됩니다. 특정 예외 설정을 여러 솔루션에서 다시 사용할 수 없습니다. 이제 추가 된 예외만 유지 됩니다. 삭제 된 예외는 그렇지 않습니다. 예외를 추가 하 고 솔루션을 닫았다가 다시 열 수 있으며 예외는 계속 표시 됩니다. 그러나 예외를 삭제한 후 솔루션을 닫았다가 다시 열면 예외가 다시 나타나지 않습니다.

**예외 설정** 창은 C#의 일반적인 예외 형식을 지원하지만 Visual Basic의 일반 예외 형식은 지원하지 않습니다. `MyNamespace.GenericException<T>`와 같은 예외에서 실행을 중단하려면 **MyNamespace.GenericException`1**과 같은 예외를 추가해야 합니다. 즉, 다음 코드와 같은 예외를 만든 경우

```csharp
public class GenericException<T> : Exception
{
    public GenericException() : base("This is a generic exception.")
    {
    }
}
```

이전 절차를 사용 하 여 예외 **설정** 에 예외를 추가할 수 있습니다.

![일반 예외 추가](../debugger/media/addgenericexception.png "AddGenericException")

## <a name="add-conditions-to-an-exception"></a>예외에 조건 추가

**예외 설정** 창을 사용 하 여 예외에 대 한 조건을 설정할 수 있습니다. 현재 지원 되는 조건에는 예외에 포함 하거나 제외할 모듈 이름이 포함 됩니다. 모듈 이름을 조건으로 설정 하면 특정 코드 모듈 에서만 예외를 중단 하도록 선택할 수 있습니다. 특정 모듈을 중단 하지 않도록 선택할 수도 있습니다.

> [!NOTE]
> 예외에 조건을 추가 하는 것은 [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]부터 지원 됩니다.

조건부 예외를 추가 하려면:

1. 예외 설정 창에서 **조건 편집** 단추를 선택 하거나 예외를 마우스 오른쪽 단추로 클릭 하 고 **조건 편집**을 선택 합니다.

   ![예외에 대 한 조건](../debugger/media/dbg-conditional-exception.png "DbgConditionalException")

2. 예외에 필요한 조건을 더 추가 하려면 각 새 조건에 대해 **조건 추가** 를 선택 합니다. 추가 조건 줄이 표시 됩니다.

   ![예외에 대 한 추가 조건](../debugger/media/extraconditionsforanexception.png "ExtraConditionsForAnException")

3. 각 조건 줄에 모듈의 이름을 입력 하 고 비교 연산자 목록을 **같음** 또는 같지 **않음**으로 변경 합니다. 이름에 와일드 카드 ( **\\\*** )를 지정 하 여 둘 이상의 모듈을 지정할 수 있습니다.

4. 조건을 삭제 해야 하는 경우 조건 줄의 끝에 있는 **X** 를 선택 합니다.

## <a name="see-also"></a>참조

- [예외 후 실행 계속](../debugger/continuing-execution-after-an-exception.md)<br/>
- [방법: 예외 발생 후 시스템 코드 검사](../debugger/how-to-examine-system-code-after-an-exception.md)<br/>
- [방법: 네이티브 런타임 검사 기능 사용](../debugger/how-to-use-native-run-time-checks.md)<br/>
- [C 런타임 라이브러리 없이 런타임 검사 사용](../debugger/using-run-time-checks-without-the-c-run-time-library.md)<br/>
- [디버거 소개](../debugger/debugger-feature-tour.md)
