---
title: 디버깅 기술 및 도구
description: 예외 문제를 수정 하 고 오류를 수정 하 여 코드 개선에 Visual Studio를 사용 하 여 버그가 줄어들었습니다를 사용 하 여 더 나은 코드를 작성 합니다.
ms.custom:
- debug-experiment
- seodec18
ms.date: 01/24/2019
ms.topic: conceptual
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8b34e23b1bc7972563d6d8d014ba0728dc637b34
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/28/2019
ms.locfileid: "66262138"
---
# <a name="debugging-techniques-and-tools-to-help-you-write-better-code"></a>디버깅 기술 및 더 나은 코드를 작성할 수 있도록 도구

코드에서 버그 및 오류를 수정 하는 걸리는-수 고 때로는 이유도 바로-작업. 효과적으로 디버깅 하는 방법을 배울 시간이 걸리지만 Visual Studio와 같은 강력한 IDE를 훨씬 더 쉽게 작업을 수행할 수 있습니다. IDE 오류를 수정 하 고 코드를 보다 신속 하 게 디버그 뿐 아니라 하 고, 하지만 버그가 줄어 드를 사용 하 여 더 나은 코드를 작성 하는 도움말 수도 수 있습니다. 이 문서의 목적은 코드 분석기를 사용 하는 경우 이해 하 게 되므로 "버그 수정" 프로세스의 전체적인 보기를 제공 하는 디버거를 사용 하는 경우 예외를 해결 하는 방법 및 의도 대 한 코딩 하는 방법입니다. 알고 있는 경우 디버거를 사용 해야 [디버거 소개](../debugger/debugger-feature-tour.md)합니다.

이 문서에서는 생산성 코딩 세션을 확인 하기 위해 IDE를 활용 하는 방법에 대 한 이야기입니다. 에서는 터치 여러 작업을 같은:

* IDE의 코드 분석기를 활용 하 여 디버깅 하는 코드를 준비

* 예외 (런타임 오류) 문제를 수정 하는 방법

* 의도 (assert 사용)에 대 한 코딩 하 여 버그를 최소화 하는 방법

* 디버거를 사용 하는 경우

이러한 작업을 보여 주기 위해 오류 및 앱을 디버깅 하려고 할 때 발생 하는 버그의 가장 일반적인 종류 중 일부를 살펴보겠습니다. 샘플 코드는 있지만 C#, 개념 정보는 일반적으로 적용할 C++, Visual Basic, JavaScript 및 Visual Studio (언급 한 위치 제외) 지 원하는 다른 언어입니다. 스크린샷은 C#에 있습니다.

## <a name="create-a-sample-app-with-some-bugs-and-errors-in-it"></a>일부 버그와 오류에 샘플 앱 만들기

다음 코드에 몇 가지 버그를 Visual Studio IDE를 사용 하 여 해결할 수 있습니다. 여기에 앱은 가져오는 JSON 데이터로 작업을 데이터 개체를 역직렬화 하 고 새 데이터를 사용 하 여 간단한 목록을 업데이트를 시뮬레이션 하는 간단한 앱.

앱을 만들려면:

1. Visual Studio를 열고 **파일** > **새로 만들기** > **프로젝트**합니다. 아래 **Visual C#** , 선택 **Windows Desktop** 또는 **.NET Core**를 선택한 다음 가운데 창에서을 **콘솔 앱**.

    > [!NOTE]
    > **콘솔 애플리케이션** 프로젝트 템플릿이 표시되지 않으면 **새 프로젝트** 대화 상자의 왼쪽 창에서 **Visual Studio 설치 관리자 열기** 링크를 클릭합니다. Visual Studio 설치 관리자가 시작됩니다. .**NET 데스크톱 개발** 또는 **.NET Core 플랫폼 간 개발** 워크로드를 선택한 다음, **수정**을 선택합니다.

2. 에 **이름을** 필드에 입력 **Console_Parse_JSON** 클릭 **확인**합니다. Visual Studio가 프로젝트를 만듭니다.

3. 프로젝트의 기본 코드 바꿉니다 *Program.cs* 아래 샘플 코드를 사용 하 여 파일입니다.

```csharp
using System;
using System.Collections.Generic;
using System.Runtime.Serialization.Json;
using System.Runtime.Serialization;
using System.IO;

namespace Console_Parse_JSON
{
    class Program
    {
        static void Main(string[] args)
        {
            var localDB = LoadRecords();
            string data = GetJsonData();

            User[] users = ReadToObject(data);

            UpdateRecords(localDB, users);

            for (int i = 0; i < users.Length; i++)
            {
                List<User> result = localDB.FindAll(delegate (User u) {
                    return u.lastname == users[i].lastname;
                    });
                foreach (var item in result)
                {
                    Console.WriteLine($"Matching Record, got name={item.firstname}, lastname={item.lastname}, age={item.totalpoints}");
                }
            }

            Console.ReadKey();
        }

        // Deserialize a JSON stream to a User object.
        public static User[] ReadToObject(string json)
        {
            User deserializedUser = new User();
            User[] users = { };
            MemoryStream ms = new MemoryStream(Encoding.UTF8.GetBytes(json));
            DataContractJsonSerializer ser = new DataContractJsonSerializer(users.GetType());

            users = ser.ReadObject(ms) as User[];

            ms.Close();
            return users;
        }

        // Simulated operation that returns JSON data.
        public static string GetJsonData()
        {
            string str = "[{ \"points\":4o,\"firstname\":\"Fred\",\"lastname\":\"Smith\"},{\"lastName\":\"Jackson\"}]";
            return str;
        }

        public static List<User> LoadRecords()
        {
            var db = new List<User> { };
            User user1 = new User();
            user1.firstname = "Joe";
            user1.lastname = "Smith";
            user1.totalpoints = 41;

            db.Add(user1);

            User user2 = new User();
            user2.firstname = "Pete";
            user2.lastname = "Peterson";
            user2.totalpoints = 30;

            db.Add(user2);

            return db;
        }
        public static void UpdateRecords(List<User> db, User[] users)
        {
            bool existingUser = false;

            for (int i = 0; i < users.Length; i++)
            {
                foreach (var item in db)
                {
                    if (item.lastname == users[i].lastname && item.firstname == users[i].firstname)
                    {
                        existingUser = true;
                        item.totalpoints += users[i].points;

                    }
                }
                if (existingUser == false)
                {
                    User user = new User();
                    user.firstname = users[i].firstname;
                    user.lastname = users[i].lastname;
                    user.totalpoints = users[i].points;

                    db.Add(user);
                }
            }
        }
    }

    [DataContract]
    internal class User
    {
        [DataMember]
        internal string firstname;

        [DataMember]
        internal string lastname;

        [DataMember]
        // internal double points;
        internal string points;

        [DataMember]
        internal int totalpoints;
    }
}
```

## <a name="find-the-red-and-green-squiggles"></a>빨간색 및 녹색 오류 표시선을 찾습니다.

샘플 앱을 시작 하 고 디버거를 실행 하기 전에, 빨강 및 녹색 오류 표시선 코드 편집기에서 코드를 확인 합니다. 이러한 오류 및 IDE의 코드 분석기에 의해 식별 되는 경고를 나타냅니다. 빨간색 물결선은 컴파일 타임 오류를 먼저 수정 해야 하는 코드를 실행할 수 있습니다. 녹색 물결선은 경고입니다. 종종 경고를 수정 하지 않고 앱을 실행할 수 있습니다, 있지만 버그의 원인이 될 수 있습니다 하 고 자주 저장 하면 직접 시간과 노력을 조사 하 여 합니다. 이러한 경고 및 오류에도 표시 합니다 **오류 목록** 창에서 목록 뷰를 선호 하는 경우.

샘플 앱을 해결 해야 하는 여러 빨간색 물결선 및 하나의 녹색 것 살펴보겠습니다 볼 수 있습니다. 첫 번째 오류는 다음과 같습니다.

![빨간색 물결선으로 표시 하는 오류](../debugger/media/write-better-code-red-squiggle.png)

이 오류를 해결 하려면 전구 아이콘으로 표시, IDE의 다른 기능을 살펴 보겠습니다.

## <a name="check-the-light-bulb"></a>전구를 확인 하세요.

첫 번째 빨간색 구부러진 곡선은 컴파일 타임 오류를 나타냅니다. 위로 마우스를 메시지가 표시 ```The name `Encoding` does not exist in the current context```합니다.

이 오류 전구 아이콘 왼쪽 아래에 표시 되는지 확인 합니다. 스크루 드라이버 아이콘을와 함께 ![스크루 드라이버 아이콘](../ide/media/screwdriver-icon.png), 전구 아이콘 ![전구 아이콘](../ide/media/light-bulb-icon.png) 나타냅니다 도움이 될 수 있는 빠른 작업 수정 또는 리팩터링 코드 인라인 합니다. 전구 나타내는 문제 *해야* 수정 합니다. 드라이버 문제를 해결 하려면 선택할 수 있는 문제입니다. 첫 번째 제안 된 수정을 클릭 하 여이 오류를 해결 하는 데 **System.Text를 사용 하 여** 왼쪽입니다.

![전구를 사용 하 여 코드 수정](../debugger/media/write-better-code-missing-include.png)

이 항목을 클릭 하면 Visual Studio 추가 합니다 `using System.Text` 맨 위에 있는 문을 합니다 *Program.cs* 파일과 빨간색 구부러진 곡선은 사라집니다. (제안 된 수정 사항을 어떻게 되는지 확실 하지 않은 경우 선택 합니다 **변경 내용 미리 보기** 수정을 적용 하기 전에 오른쪽의 링크입니다.)

이전 오류는 일반적으로 새로 추가 하 여 수정 하는 일반적인 단일 `using` 문을 코드에 있습니다. 여러 가지 일반적인 마찬가지로 오류가 있습니다이 같은 ```The type or namespace `Name` cannot be found.``` 이러한 종류의 오류는 누락 된 어셈블리 참조를 나타낼 수 있습니다 (선택, 프로젝트를 마우스 오른쪽 단추로 클릭 **추가** > **참조**)에 철자가 잘못 된 이름 또는 추가 해야 하는 누락 된 라이브러리 (에 대 한 C#프로젝트를 마우스 오른쪽 단추로 클릭 하 고 선택 **NuGet 패키지 관리**).

## <a name="fix-the-remaining-errors-and-warnings"></a>나머지 오류 및 경고 해결

이 코드에서 살펴볼 자세한 오류 표시선 몇 가지가 있습니다. 여기서 일반적인 유형 변환 오류가 표시 됩니다. 오류 표시선 위로 마우스를 가져가면 string을 int로 변환할 변환을 수행 하는 명시적 코드를 추가 하지 않는 경우 지원 되지 않는 코드를 시도 하는 것이 표시 됩니다.

![유형 변환 오류](../debugger/media/write-better-code-conversion-error.png)

코드 분석기 의도인 추측할 수 없습니다, 없습니다 전구이 이번 도와줄 수 있습니다. 이 오류를 해결 하려면 코드의 의도 알 필요가 있습니다. 이 예제에서는 너무 어렵지 않습니다에서 볼 수 있듯이 `points` 여야 합니다. 숫자 (정수)를 추가 하려고 하므로 `points` 에 `totalpoints`입니다.

이 오류를 해결 하려면 변경 된 `points` 의 멤버는 `User` 클래스에서:

```csharp
[DataMember]
internal string points;
```

아래와 같이 변환합니다.

```csharp
[DataMember]
internal int points;
```

코드 편집기에서 빨간색의 구불구불한 선 사라집니다.

다음으로, 녹색의 선언에 구불구불한 마우스로 `points` 데이터 멤버입니다. 변수에 값 할당 되지 않으므로 코드 분석기에서 알 수 있습니다.

![할당 되지 않은 변수에 대 한 경고 메시지](../debugger/media/write-better-code-warning-message.png)

일반적으로이 해결 해야 하는 문제를 나타냅니다. 그러나 샘플 앱에서 실제로 저장 하는 데이터에는 `points` deserialization 프로세스 및 해당 값을 추가 하는 동안 변수를 `totalpoints` 데이터 멤버입니다. 이 예제에서는 코드의 의도 지식과 경고를 무시 해도 됩니다. 그러나 경고 제거 하려는 경우에 다음 코드를 대체할 수 있습니다.

```csharp
item.totalpoints = users[i].points;
```

다음 코드로 바꿉니다.

```csharp
item.points = users[i].points;
item.totalpoints += users[i].points;
```

녹색 오류 표시선이 사라집니다.

## <a name="fix-an-exception"></a>예외를 해결 합니다.

빨간색 물결선 모든 고정 및-해결 하거나 최소 조사-때 녹색 물결선 모든 준비가 디버거를 시작 하 고 앱을 실행 합니다.

디버그 도구 모음에서 **F5**(**디버그 > 디버깅 시작**) 또는 **디버깅 시작** 단추 ![디버깅 시작](../debugger/media/dbg-tour-start-debugging.png "디버깅 시작")를 누릅니다.

이 시점에서 샘플 앱 throw를 `SerializationException` 예외 (런타임 오류). 즉, 앱 데이터를 직렬화 하는 것에 대해 제한 합니다. 디버그 모드 (디버거 연결)에서 앱을 시작 했기 때문에 디버거의 예외 도우미 예외가 발생 한 및 유용한 오류 메시지를 제공 하는 코드에 바로 이동 합니다.

![SerializationException을 발생](../debugger/media/write-better-code-serialization-exception.png)

오류 메시지를 지시 하는 값 `4o` 정수로 구문 분석할 수 없습니다. 따라서이 예제에서는 알고 데이터가 잘못 된: `4o` 있어야 `40`합니다. 그러나 실제 시나리오 (예: 웹 서비스에서 발생 하는) 데이터를 제어 하지 경우에 대 한 할까요? 어떻게 해결할 수행 하 시겠습니까?

예외에 도달 하면 몇 가지 질문을 요청 (및 답변) 해야 합니다.

* 이 예외는 버그를 해결할 수 있습니다만 인지 확인 합니다. 또는,

* 사용자에 게 발생할 수 있는 것이 예외는?

이전의 경우 버그를 수정 합니다. (샘플 앱에서 즉, 잘못 된 데이터를 수정 합니다.) 사용 하 여 코드에서 예외를 처리 해야 두 번째 경우는 `try/catch` 블록 (살펴봅니다 다음 섹션의 다른 가능한 전략). 샘플 앱에서 다음 코드를 바꿉니다.

```csharp
users = ser.ReadObject(ms) as User[];
```

이 코드로 바꿉니다.

```csharp
try
{
    users = ser.ReadObject(ms) as User[];
}
catch (SerializationException)
{
    Console.WriteLine("Give user some info or instructions, if necessary");
    // Take appropriate action for your app
}
```

`try/catch` 블록에 일부 성능 비용으로 사용할 실제로 필요할 때, 즉, (a)는 발생할 수 있는 앱의 릴리스 버전에서에 하려는 경우 고 (b) 설명서를 확인 해야 하는 메서드를 나타냅니다는 예외 (가정: 문서가 완료!). 대부분의 경우에서 예외를 적절 하 게 처리할 수 있습니다 하 고 사용자가 알고 필요가 없습니다.

예외 처리를 위한 주요 팁 가지는 다음과 같습니다.

* 예: 빈 catch 블록은 사용 하지 않도록 `catch (Exception) {}`, 적절 한 조치를 노출 하거나 오류 처리를 사용 하지 않는 합니다. 비어 있거나 정보 catch 블록은 예외를 숨길 수 있습니다 및 코드 대신 쉽게 디버깅을 더 어렵게 만들 수 있습니다.

* 사용 합니다 `try/catch` 예외를 throw 하는 특정 함수 주위에 블록 (`ReadObject`, 샘플 앱에서). 코드의 큰 청크의 주위를 사용 하면 오류의 위치를 숨기기 될 있습니다. 예를 들어, 사용 하지 않는 합니다 `try/catch` 부모 함수에 대 한 호출 주위에 블록 `ReadToObject`, 여기에 표시 된 또는 예외 발생 한 위치을 정확 하 게 알 수 없습니다.

    ```csharp
    // Don't do this
    try
    {
        User[] users = ReadToObject(data);
    }
    catch (SerializationException)
    {
    }
    ```

* 알 수 없는 포함할 수 있는 함수 앱에서 특히 외부 데이터 (예: 웹 요청)와 상호 작용, 예외에 대해 함수는 throw 가능성이 확인 하려면 설명서를 참조 합니다. 이 응용 프로그램을 디버깅 및 적절 한 오류 처리에 대 한 중요 한 정보를 수 있습니다.

샘플 앱에 대 한 해결 합니다 `SerializationException` 에 `GetJsonData` 메서드를 변경 하 여 `4o` 에 `40`.

## <a name="clarify-your-code-intent-by-using-assert"></a>Assert를 사용 하 여 사용자 코드 의도 명확히 합니다.

디버그 도구 모음에서 **다시 시작** ![앱 다시 시작](../debugger/media/dbg-tour-restart.png "RestartApp") 단추를 클릭합니다(**Ctrl** + **Shift** + **F5**). 이 앱을 더 적은 단계로 다시 시작 합니다. 콘솔 창에 다음 출력이 표시 됩니다.

![출력에 null 값](../debugger/media/write-better-code-using-assert-null-output.png)

정확 하지 않은 출력을 확인할 수 있습니다. **이름을** 하 고 **lastname** 세 번째 레코드는 빈!

이 사용 하는 좋은 때 종종 제대로 활용 하는 유용한 코딩 사례에 설명 `assert` 함수에는 문입니다. 확인에 런타임 검사를 포함 하는 다음 코드를 추가 하면 `firstname` 하 고 `lastname` 되지 `null`합니다. 다음 코드는 `UpdateRecords` 메서드:

```csharp
if (existingUser == false)
{
    User user = new User();
    user.firstname = users[i].firstname;
    user.lastname = users[i].lastname;
```

다음 코드로 바꿉니다.

```csharp
// Also, add a using statement for System.Diagnostics at the start of the file.
Debug.Assert(users[i].firstname != null);
Debug.Assert(users[i].lastname != null);
if (existingUser == false)
{
    User user = new User();
    user.firstname = users[i].firstname;
    user.lastname = users[i].lastname;
```

추가 하 여 `assert` 문을 다음과 같은 함수를 개발 프로세스 중에 코드의 의도 지정을 할 수 있습니다. 앞의 예제에서 다음을 지정합니다.

* 유효한 문자열 이름에 필요
* 마지막 이름에는 유효한 문자열 필요

의도 이러한 방식으로 지정 하 여 요구 사항을 적용할 수 있습니다. 이 개발 하는 동안 화면 버그에 사용할 수 있는 간단 하 고 편리한 메서드입니다. (`assert` 문은 단위 테스트의 주요 요소로 사용 됩니다.)

디버그 도구 모음에서 **다시 시작** ![앱 다시 시작](../debugger/media/dbg-tour-restart.png "RestartApp") 단추를 클릭합니다(**Ctrl** + **Shift** + **F5**).

> [!NOTE]
> `assert` 코드가 디버그 빌드에만 활성화 되어 있습니다.

를 다시 시작 하면 디버거가 일시 중지 합니다 `assert` 문 때문에 식 `users[i].firstname != null` 로 계산 되 `false` 대신 `true`합니다.

![False로 확인 되 면 어설션](../debugger/media/write-better-code-using-assert.png)

`assert` 오류 알려 조사 해야 하는 문제가 있는 것입니다. `assert` 예외를 반드시 표시 되지 않으면 대부분의 시나리오를 처리할 수 있습니다. 이 예제에서는 사용자에는 예외가 표시 되지 않습니다 및 `null` 값으로 추가 `firstname` 레코드 목록에 있습니다. 이 문제가 있을 수 있습니다 나중에 (예: 콘솔 출력에 표시) 및 디버깅에 매우 어려울 수 있습니다.

> [!NOTE]
> 시나리오에서 메서드를 호출 하는 위치에 `null` 값을 `NullReferenceException` 결과입니다. 일반적으로 사용 하지 않도록 하려는 `try/catch` 즉, 특정 라이브러리 함수에 연결 되지 않은 예외는 일반 예외에 대 한 차단 합니다. 모든 개체를 throw 할 수는 `NullReferenceException`합니다. 확실 하지 않은 경우에 라이브러리 함수에 대 한 설명서를 확인 합니다.

디버깅 프로세스 중 것이 좋지만 특정 `assert` 문을 수정 하는 실제 코드를 사용 하 여 교체 해야 알 때까지 합니다. 사용자가 앱의 릴리스 빌드에 예외를 발생할 수 하려는 경우를 가정해 봅니다. 이 경우 앱 심각한 예외를 throw 하지 않습니다 또는 일부 다른 오류로 인해 않은지 확인 하는 코드를 리팩터링 해야 합니다. 따라서이 코드를 수정 하려면 다음 코드를 바꿉니다.

```csharp
if (existingUser == false)
{
    User user = new User();
```

이 코드로 바꿉니다.

```csharp
if (existingUser == false && users[i].firstname != null && users[i].lastname != null)
{
    User user = new User();
```

이 코드를 사용 하 여 코드 요구 사항을 충족 하 고이 확인 레코드를 `firstname` 하거나 `lastname` 의 값 `null` 데이터에 추가 되지 않습니다.

이 예제에서는 두 개의 추가 `assert` 루프 내의 문. 일반적으로 사용 하는 경우 `assert`를 추가 하는 것이 좋습니다 `assert` 함수 또는 메서드의 진입점 (시작)에 문의 합니다. 현재 살펴보고는 `UpdateRecords` 샘플 앱에서 메서드. 메서드 인수 중 하나에 해당 하는 경우 문제가 된다고 생각이 메서드에서 `null`, 모두를 사용 하 여 확인는 `assert` 함수의 진입점에 문의 합니다.

```csharp
public static void UpdateRecords(List<User> db, User[] users)
{
    Debug.Assert(db != null);
    Debug.Assert(users != null);
```

위의 문에서 의도 기존 데이터를 로드 함을 (`db`) 새 데이터를 검색 하 고 (`users`) 항목을 업데이트 하기 전에 합니다.

사용할 수 있습니다 `assert` 로 확인 되는 식의 모든 종류 `true` 또는 `false`합니다. 따라서 예를 들어, 추가할 수 있습니다는 `assert` 문을 다음과 같이 합니다.

```csharp
Debug.Assert(users[0].points > 0);
```

위의 코드에서는 다음 의도 지정 하려는 경우 유용 합니다: 영 (0) 사용자의 레코드를 업데이트 하는 데 필요한 것 보다 큰 새 지점 값입니다.

## <a name="inspect-your-code-in-the-debugger"></a>디버거에서 코드를 검사 합니다.

그렇다면 샘플 앱을 사용 하 여 잘못 된 모든 중요 한 수정 했다면, 이제는 다른 중요 한 부분으로 이동할 수 있습니다.

앞서 소개한 디버거의 예외 도우미, 이지만 디버거도 해당 변수를 검사 및 코드를 단계별로 같은 다른 작업을 수행할 수 있는 훨씬 더 강력한 도구입니다. 이러한 더 강력한 기능은 다음 특히 많은 시나리오에서 유용 합니다.

* 코드에서 런타임 버그를 격리 하려는 해도 방법과 앞에서 설명한 도구를 사용 하 여 작업을 수행 하지 못합니다.

* 예상 대로 동작 하 고 원하는를 수행 하는 실행 되는 동안 보기, 즉 코드의 유효성을 검사 하려고 합니다.

    이 실행 되는 동안 코드를 살펴보면 도움이 됩니다. 자세한 코드에 대 한이 이런을 하기 전에 확실 한 증상이 종종 버그를 확인할 수 있습니다.

디버거의 필수 기능을 사용 하는 방법에 알아보려면 참조 [초보자를 위한 디버깅](../debugger/debugging-absolute-beginners.md)합니다.

## <a name="fix-performance-issues"></a>성능 문제 해결

다른 종류의 버그 이면 앱이 느리게 실행 또는 너무 많은 메모리를 사용 하는 비효율적인 코드를 포함 합니다. 일반적으로 성능 최적화 응용 프로그램 개발의 뒷부분에 나오는 할 것입니다. 그러나 실행할 수 있습니다 성능 문제를 초기 (예를 들어 표시 앱의 일부 느리게 실행 되 고 있는지), 초기에 프로 파일링 도구를 사용 하 여 앱을 테스트 해야 할 수 있습니다. CPU 사용량 도구 및 메모리 분석기와 같은 도구를 프로 파일링 하는 방법에 대 한 자세한 내용은 참조 하세요. [프로 파일링 도구 살펴보기](../profiling/profiling-feature-tour.md)합니다.

## <a name="next-steps"></a>다음 단계

이 문서에서는 디버거를 사용 하는 경우 및 방지 하 고 코드에서 일반적인 많은 버그를 수정 하는 방법을 알아보았습니다. Visual Studio 디버거를 사용 하 여 버그를 수정 하는 방법에 대 한 자세한 내용은 다음을 알아봅니다.

> [!div class="nextstepaction"]
> [완전 초보자를 위한 디버깅](../debugger/debugging-absolute-beginners.md)
