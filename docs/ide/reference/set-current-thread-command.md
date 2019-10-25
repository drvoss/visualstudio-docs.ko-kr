---
title: 현재 스레드 설정 명령
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.setcurrentthread
helpviewer_keywords:
- Set Current Thread command
- Debug.SetCurrentThread command
ms.assetid: 9917ed1d-6c30-4d94-b2f0-69acce74f1b2
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0d782a507d57e459aa5735cf34717f13e41d4cde
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748610"
---
# <a name="set-current-thread-command"></a>현재 스레드 설정 명령
지정한 스레드를 현재 스레드로 설정합니다.

## <a name="syntax"></a>구문

```
Debug.SetCurrentThread index
```

## <a name="arguments"></a>인수
`index`

필수 요소. 해당 인덱스로 스레드를 선택합니다.

## <a name="example"></a>예

```
>Debug.SetCurrentThread 1
```

## <a name="see-also"></a>참고 항목

- [Visual Studio 명령](../../ide/reference/visual-studio-commands.md)
- [명령 창](../../ide/reference/command-window.md)
- [찾기/명령 상자](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)