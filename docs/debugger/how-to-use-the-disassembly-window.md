---
title: 디버거의 디스어셈블리 코드 보기 | Microsoft Docs
ms.custom: seodec18
ms.date: 10/30/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.disassembly
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- assembly language, debugging inline assembly code
- breakpoints, Disassembly window
- Disassembly window
- machine code
ms.assetid: eaf84dd0-c82d-481b-af51-690b74e7794c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 43214ee122b3aa5c3907b9176631f2dc22c9178e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62846392"
---
# <a name="view-disassembly-code-in-the-visual-studio-debugger-c-c-visual-basic-f"></a>Visual Studio 디버거의 디스어셈블리 코드 보기 (C#, C++, Visual Basic의 경우 F#)

**디스어셈블리** 창에는 컴파일러에서 만든 명령에 따라 어셈블리 코드가 표시됩니다. 관리 되는 코드를 디버깅 하는 경우 이러한 어셈블리 명령은 없습니다 Microsoft intermediate language (MSIL) Visual Studio 컴파일러에서 생성 시간 하기만 하면 됩니다 (JIT) 컴파일러에서 생성 하는 네이티브 코드에 해당 합니다.

> [!NOTE]
> 완전히 활용 하는 **디스어셈블리** 창 이해 하거나 기본 사항 알아보기 [어셈블리 언어 프로그래밍](https://wikipedia.org/wiki/Assembly_language)합니다.

이 기능은 주소 수준 디버깅을 설정한 경우에 사용할 수만 있습니다. 스크립트나 SQL 디버깅에 사용할 수 없습니다.

**디스어셈블리** 창에는 어셈블리 지침뿐 아니라 다음과 같은 선택적 정보도 표시할 수 있습니다.

- 각 명령이 있는 메모리 주소, 네이티브 응용 프로그램에 대 한 실제 메모리 주소입니다. Visual basic 또는 C#를 함수 시작 부분 으로부터의 오프셋입니다.

- 어셈블리 코드가 파생된 소스 코드

- 코드 바이트, 즉, 실제 컴퓨터 또는 MSIL 명령의 바이트 표시 합니다.

- 메모리 주소의 기호 이름

- 소스 코드에 해당하는 줄 번호

어셈블리 언어 명령을 이루어진 *니모닉*, 명령 이름에 대 한 약어는 및 *기호* 변수, 레지스터 및 상수에 대 한 합니다. 각 컴퓨터 언어 명령은 하나 이상의 기호 뒤에 선택적으로 하나의 어셈블리 언어 니모닉으로 표시 됩니다.

어셈블리 코드는 프로세서 레지스터에 크게 의존 또는 공용 언어 런타임에서 관리 코드에 대해 등록 합니다. 사용할 수는 **디스어셈블리** 함께 창 합니다 **등록** 창 레지스터의 내용을 검사할 수 있습니다.

어셈블리 언어 아닌 원시 숫자 형식으로 컴퓨터 코드 명령을 보려면 사용 하 여 합니다 **메모리** 창이 나 선택 **코드 바이트** 의 바로 가기 메뉴에서를 **디스어셈블리**  창입니다.

## <a name="use-the-disassembly-window"></a>디스어셈블리 창 사용

사용 하도록 설정 합니다 **디스어셈블리** 창 아래에 있는 **도구** > **옵션** (또는 **도구**  >  **옵션**) > **디버깅**을 선택 **주소 수준 디버깅 사용**합니다.

열려는 합니다 **디스어셈블리** 선택 디버그 하는 동안 창 **Windows** > **디스어셈블리** 누르거나 **Alt** + **8**합니다.

> [!NOTE]
> 표시되는 대화 상자와 메뉴 명령은 활성 설정이나 버전에 따라 도움말에서 설명하는 것과 다를 수 있습니다. 설정을 변경하려면 **도구** 메뉴에서 **설정 가져오기 및 내보내기** 를 선택합니다. 자세한 내용은 [재설정 설정](../ide/environment-settings.md#reset-settings)을 참조하세요.

선택적 정보를 설정 하거나 해제 하려면 마우스 오른쪽 단추로 클릭 합니다 **디스어셈블리** 창 고을 선택 하거나 바로 가기 메뉴에서 원하는 옵션의 선택을 취소 합니다.

왼쪽된 여백의 노란색 화살표는 현재 실행 위치를 표시합니다. 네이티브 코드에 대해 실행 지점을 CPU의 프로그램 카운터에 해당합니다. 이 위치는 프로그램에서 다음에 실행될 명령을 나타냅니다.

## <a name="see-also"></a>참고자료

* [메모리에서 페이지 위나 아래로 이동](../debugger/how-to-page-up-or-down-in-memory.md)
* [디버거에서 데이터 보기](../debugger/viewing-data-in-the-debugger.md)
* [방법: 레지스터 창 사용](../debugger/how-to-use-the-registers-window.md)