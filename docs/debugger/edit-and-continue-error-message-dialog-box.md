---
title: 편집 하며 계속 하기 오류 메시지 대화 상자 | Microsoft Docs
ms.date: 10/15/2018
ms.topic: reference
f1_keywords:
- vs.debug.ENC.SupportedButNotAvailable
- vs.debug.ENC.CannotEditWhileException
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue Error Message dialog box
ms.assetid: f98c91c0-447a-4533-85b6-87170a0dc4c3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7df95eae689f7c3abbb0d75a7557ce749bdceee5
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73188226"
---
# <a name="edit-and-continue-error-message"></a>편집 하며 계속 하기 오류 메시지

편집 **하며 계속 하기 오류 메시지** 상자는 편집 하며 계속 하기를 지 원하는 코드 언어로 디버그할 때 표시 되지만 편집 하며 계속 하기는 코드 변경 내용에 사용할 수 없습니다. 오류 메시지에 자세한 설명이 나와 있습니다. 대화 상자에 응답 하려면 **확인** 을 선택 하 여 대화 상자를 닫고 편집 시도를 취소 합니다.

이 오류 메시지의 가능한 원인은 다음과 같습니다.

- SQL Server 코드를 편집 하려고 합니다.
- 최적화 된 코드를 편집 하려고 합니다. 릴리스 빌드에서 디버그 빌드로 전환 해야 할 수도 있습니다.
- 디버거에서 일시 중지 되지 않고 실행 되는 동안 코드를 편집 하려고 합니다. [중단점을 설정](../debugger/using-breakpoints.md)하 고 일시 중지 된 상태에서 코드를 편집 해 보세요.
- 관리 되지 않는 디버깅만 사용 하도록 설정 된 경우 관리 코드를 편집 하려고 합니다. 편집 하며 계속 하기는 [혼합 모드 디버깅](../debugger/how-to-debug-in-mixed-mode.md)에서 작동 하지 않습니다.
- 프로그래밍 언어에서 편집 하며 계속 하기에서 지원 되지 않는 코드 변경을 수행 합니다. 자세한 내용은 [에서 C#지원 되는 코드 변경 내용 ](supported-code-changes-csharp.md), [편집 하며 계속 하기 Visual Basic에서 지원 되지 않는 편집](supported-code-changes-csharp.md), [지원 C++ 되는 코드 변경](supported-code-changes-cpp.md)에 대 한 문서를 참조 하세요.
- **디버그** 메뉴에서 디버깅을 시작 하는 대신 연결 된 앱의 코드를 편집 하려고 합니다.
- Dr. Watson 덤프를 디버깅 하는 동안 코드를 편집 하려고 합니다.
- 처리 되지 않은 예외가 발생 한 후 코드를 편집 하려고 했지만 **처리 되지 않은 예외에 대 한 호출 스택 해제** 옵션이 선택 되어 있지 않습니다.
- 포함 된 런타임 응용 프로그램을 디버깅 하는 동안 코드를 편집 하려고 합니다.
- 64 비트 앱 대상으로 4.5.1 이전 .NET Framework 버전을 사용 하 여 관리 코드를 편집 하려고 합니다. 4\.5.1 이전 .NET Framework에 대해 편집 하며 계속 하기를 사용 하려면 **\<ProjectName >**  > **속성** > **컴파일** 탭, **고급 컴파일러** 설정에서 대상을 **x 86** 으로 설정 합니다.
- 디버깅 하는 동안 수정 되었으며 다시 로드 된 어셈블리의 코드를 편집 하려고 합니다.
- 로드 되지 않은 어셈블리의 코드를 편집 하려고 합니다.
- 최신 버전에 빌드 오류가 있기 때문에 이전 버전의 앱 디버깅을 시작 합니다.

자세한 내용은 다음을 참조하십시오.
- [C++편집 하며 계속 하기 블로그 게시물](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/)
- [지원되는 코드 변경(C++)](../debugger/supported-code-changes-cpp.md)
- [편집하며 계속하기](../debugger/edit-and-continue.md)