---
title: 편집 하며 계속 하기 오류 메시지 대화 상자 | Microsoft 문서
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
ms.openlocfilehash: 0428ecf21da525b8f77334e57547c8f10da7cdf5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62851643"
---
# <a name="edit-and-continue-error-message"></a>편집 하며 계속 하기 오류 메시지

합니다 **편집 하며 계속 하기** 편집 하며 계속 하기를 지 원하는 코드 언어에서 디버깅할 때 오류 메시지 상자 표시 되지만 편집 하며 계속 하기는 코드 변경 내용을 사용할 수 없습니다. 오류 메시지 보다 자세한 설명을 제공합니다. 선택 대화 상자에 응답할 **확인** 대화 상자를 닫고를 편집 하려는 시도 취소 합니다.

이 오류 메시지에 대 한 가능한 원인은 다음과 같습니다.

- SQL Server 코드를 편집 하려고 합니다.
- 최적화 된 코드를 편집 하려고 합니다. 릴리스 빌드에서 디버그 빌드로 전환 해야 합니다.
- 실행 되는 동안 코드를 편집 하는 동안 대신 디버거에서 일시 중지 된 동안. 시도 [중단점 설정](../debugger/using-breakpoints.md), 일시 중지 된 동안 코드를 편집 하 고 있습니다.
- 관리 되지 않는 디버깅만 사용 하는 경우 관리 코드를 편집 하려고 합니다. 편집 하며 계속 하기가 작동 하지 않습니다 [혼합 모드 디버깅](../debugger/how-to-debug-in-mixed-mode.md)합니다.
- 가 코드를 변경 하는 프로그래밍 언어의 편집 하며 계속 하기에서 지원 되지 않습니다. 에 대 한 자세한 내용은 문서를 참조 [에서 코드 변경을 지원 C# ](supported-code-changes-csharp.md)를 [편집 Visual Basic 편집 하며 계속 하기에서 지원 되지 않는](/visualstudio/debugger/supported-code-changes-csharp), 및 [지원 C++ 변경코드](supported-code-changes-cpp.md).
- 디버깅을 시작 하는 대신에 연결 하는 앱에서 코드를 편집 하 여 **디버그** 메뉴.
- Dr을 디버깅 하는 동안 코드를 편집 하려고 합니다. 디버깅
- 처리 되지 않은 예외가 발생 한 후 코드를 편집 하 고 옵션 **처리 되지 않은 예외에 대 한 호출 스택 해제** 선택 하지 않으면.
- 포함 된 런타임 응용 프로그램을 디버깅 하는 동안 코드를 편집 하려고 합니다.
- 4.5.1 이전 64 비트 응용 프로그램 대상을 사용 하 여.NET Framework 버전을 사용 하 여 관리 되는 코드를 편집 하려고 합니다. 편집 하며 계속 하기에 대해 사용 하려면.NET Framework 4.5.1 이전의 대상 **x86** 에  **\<ProjectName >**  > **속성**  >  **컴파일** 탭 **고급 컴파일러** 설정 합니다.
- 디버깅 하는 동안 수정한를 다시 로드 된 어셈블리에서 코드를 편집 하려고 합니다.
- 로드 되지 않았습니다 하는 어셈블리에서 코드를 편집 하려고 합니다.
- 최신 버전에 빌드 오류가 있으므로 이전 버전의 앱을 디버깅 하기 시작 합니다.

자세한 내용은 다음을 참조하세요.
- [C++편집 하며 계속 하기 블로그 게시물](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/)
- [지원되는 코드 변경(C++)](../debugger/supported-code-changes-cpp.md)
- [편집하며 계속하기](../debugger/edit-and-continue.md)