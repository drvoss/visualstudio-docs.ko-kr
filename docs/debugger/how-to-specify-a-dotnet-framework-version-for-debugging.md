---
title: 디버그할 .NET Framework 버전 지정 | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- .NET Framework, specifying version for debugging
- debugging [Visual Studio], specifying .NET Framework version
ms.assetid: 7a4893ba-4620-4774-893f-378d4ca28893
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 1f6107d6396c6228be1d511e81003fbe7faf06c9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72732631"
---
# <a name="specify-an-older-net-framework-version-for-debugging-c-visual-basic-f"></a>디버깅에 사용할 이전 .NET Framework 버전을 지정C#합니다 (, F#Visual Basic,).

Visual Studio 디버거는 이전 버전의 Microsoft .NET 프레임 워크 및 현재 버전의 디버깅을 지원 합니다. Visual Studio에서 응용 프로그램을 시작 하는 경우 디버거는 디버깅 중인 응용 프로그램에 대 한 올바른 .NET Framework 버전을 항상 식별할 수 있습니다. 그러나 응용 프로그램이 이미 실행 중이 고 **에 연결을**사용 하 여 디버깅을 시작 하는 경우 디버거는 .NET Framework의 이전 버전을 항상 식별 하지 못할 수 있습니다. 이러한 문제가 발생하면 다음과 같은 오류 메시지가 표시됩니다.

``` cmd
The debugger has made an incorrect assumption about the .NET Framework version your application is going to use.
```

드문 경우 지만이 오류가 표시 되는 경우 디버거를 사용 하 여 사용할 버전을 나타내도록 레지스트리 키를 설정할 수 있습니다.

### <a name="to-specify-a-net-framework-version-for-debugging"></a>디버깅을 위한 .NET Framework 버전을 지정하려면

1. Windows\Microsoft.NET\Framework 디렉터리에서 컴퓨터에 설치되어 있는 .NET Framework의 버전을 확인합니다. 버전 번호는 다음과 비슷합니다.

    `V1.1.4322`

    올바른 버전 번호를 확인하여 기록해 둡니다.

2. **레지스트리 편집기**(regedit)를 시작합니다.

3. **레지스트리 편집기**에서 HKEY_LOCAL_MACHINE 폴더를 엽니다.

4. HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine\\{449EC4CC-30D2-4032-9256-EE18EB41B62B}로 이동

    이 키가 없으면 마우스 오른쪽 단추로 HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine을 클릭하고 **새 키**를 클릭합니다. 새 키의 이름을 `{449EC4CC-30D2-4032-9256-EE18EB41B62B}` 합니다.

5. {449EC4CC-30D2-4032-9256-EE18EB41B62B}로 이동한 후 **이름** 열에서 CLRVersionForDebugging 키를 찾습니다.

   1. 해당하는 키가 없으면 {449EC4CC-30D2-4032-9256-EE18EB41B62B}를 마우스 오른쪽 단추로 클릭하고 **새 문자열 값**을 클릭합니다. 그런 다음 새 문자열 값을 마우스 오른쪽 단추로 클릭 하 고 **이름 바꾸기**를 클릭 한 다음 `CLRVersionForDebugging`를 입력 합니다.

6. **CLRVersionForDebugging**을 두 번 클릭합니다.

7. **문자열 편집** 상자에서 **값** 상자에 .NET Framework 버전 번호를 입력합니다. 예를 들어 V1.1.4322 같은 형식입니다.

8. **확인**을 클릭합니다.

9. **레지스트리 편집기**를 닫습니다.

     디버깅을 시작할 때 여전히 오류 메시지가 표시되면 레지스트리에 버전 번호를 올바르게 입력했는지 확인합니다. 또한 Visual Studio에서 지 원하는 .NET Framework 버전을 사용 중인지 확인 합니다. 현재 디버거는 .NET Framework 버전 및 이전 버전과 호환되지만 이후 버전과는 호환되지 않을 수 있습니다.

## <a name="see-also"></a>참조
- [디버거 설정 및 준비](../debugger/debugger-settings-and-preparation.md)