---
title: 출력 창에 메시지 보내기 | Microsoft Docs
ms.date: 11/08/2018
ms.topic: conceptual
helpviewer_keywords:
- diagnostic messages [C#]
- System.Diagnostics.Debug class, Output window
- messages, diagnostic
- Debug.Print replacements
- diagnosis
- Output window, diagnostic messages
- System.Diagnostics.Trace class, Output window
- Trace class, diagnostic messages
- diagnostics
- debugger, Output window
- debugging [Visual Studio], diagnostic messages in Output window
- Debug class
ms.assetid: 386e9524-be17-4573-83fb-4f7c5cae0be0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 47b563f58d08a732ec224bb8bbf47ad807c4e81d
ms.sourcegitcommit: ce1ab8a25c66a83e60eab80ed8e1596fe66dd85c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/29/2019
ms.locfileid: "68605383"
---
# <a name="send-messages-to-the-output-window"></a>출력 창으로 메시지 보내기

클래스 또는 <xref:System.Diagnostics.Debug> <xref:System.Diagnostics>  클래스를사용하여출력창에런타임메시지를작성할수있습니다.클래스는클래스라이브러리의일부<xref:System.Diagnostics.Trace> 입니다. 프로그램의 <xref:System.Diagnostics.Debug> *디버그* 버전에만 출력을 사용 하려면 클래스를 사용 합니다. 디버그 버전과 <xref:System.Diagnostics.Trace> *릴리스* 버전 모두에서 출력을 원하는 경우  클래스를 사용 합니다.

## <a name="output-methods"></a>출력 메서드
 <xref:System.Diagnostics.Trace> 클래스와 <xref:System.Diagnostics.Debug> 클래스에는 다음과 같은 출력 메서드가 있습니다.

- 실행을 중단하지 않고 정보를 출력하는 여러 가지 `Write` 메서드. 이 메서드는 이전 Visual Basic 버전의 `Debug.Print` 메서드 대신 사용됩니다.

- <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>지정 <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> 된 조건이 실패할 경우 실행을 중단 하 고 정보를 출력 하는 및 메서드. 기본적으로 `Assert` 메서드는 해당 정보를 대화 상자에 표시합니다. 자세한 내용은 [관리 코드의 어설션](../debugger/assertions-in-managed-code.md)을 참조하세요.

- 항상 실행 <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=fullName> 을 중단 하 고 정보를 출력 하는 및메서드.<xref:System.Diagnostics.Debug.Fail%2A?displayProperty=fullName> 기본적으로 `Fail` 메서드는 정보를 대화 상자에 표시합니다.

**출력** 창에는 다음에 대 한 정보를 표시할 수도 있습니다.

- 디버거에서 로드하거나 언로드한 모듈 정보

- throw된 예외 정보

- 종료되는 프로세스 정보

- 종료되는 스레드 정보

## <a name="see-also"></a>참고자료
- [디버거 보안](../debugger/debugger-security.md)
- [출력 창](../ide/reference/output-window.md)
- [응용 프로그램 추적 및 계측](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications)
- [C#, F# 및 Visual Basic 프로젝트 형식](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [관리 코드 디버깅](../debugger/debugging-managed-code.md)
