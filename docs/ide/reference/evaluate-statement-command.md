---
title: EvaluateStatement
ms.date: 02/25/2019
ms.topic: reference
f1_keywords:
- debug.evaluatestatement
helpviewer_keywords:
- Debug.EvaluateStatement command
- Evaluate Statement command
ms.assetid: 032039bc-9477-4f93-9b9d-66d4be0e90f4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c7eff96d1b413ea10b1274eb7d7938148727acbc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62790878"
---
# <a name="evaluate-statement-command"></a>문 실행 명령

지정된 문을 평가 및 표시합니다.

## <a name="syntax"></a>구문

```cmd
>Debug.EvaluateStatement text
```

## <a name="arguments"></a>인수

`text`

필수 요소. 평가할 문입니다.

## <a name="example"></a>예제

```cmd
>Debug.EvaluateStatement args.Length
```

## <a name="see-also"></a>참고 항목

- [인쇄 명령](../../ide/reference/print-command.md)
- [Visual Studio 명령](../../ide/reference/visual-studio-commands.md)
- [명령 창](../../ide/reference/command-window.md)
- [찾기/명령 상자](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)