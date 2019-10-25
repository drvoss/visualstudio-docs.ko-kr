---
title: 조사식 명령
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.watch
helpviewer_keywords:
- Watch command
- Debug.Watch command
ms.assetid: aa02e647-d9f5-4905-a651-52a8df595795
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 411452ba0cf8f8625ee67bca51c2f3735f6dc924
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747687"
---
# <a name="watch-command"></a>조사식 명령
**조사식** 창의 지정된 인스턴스를 만들고 엽니다. **조사식** 창을 사용하여 변수, 식 및 레지스터의 값을 계산하고, 이러한 값을 편집하고, 결과를 저장할 수 있습니다.

## <a name="syntax"></a>구문

```cmd
Debug.Watch[index]
```

## <a name="arguments"></a>인수

`index`\
필수 요소. 조사식 창의 인스턴스 번호입니다.

## <a name="remarks"></a>설명

`index`는 정수여야 합니다. 유효한 값은 1, 2, 3 또는 4입니다.

## <a name="example"></a>예

```cmd
>Debug.Watch1
```

## <a name="see-also"></a>참고 항목

- [자동 및 지역 창](../../debugger/autos-and-locals-windows.md)
- [Visual Studio에서 조사식 및 간략한 조사식 창을 사용하여 변수에 대한 조사식 설정](../../debugger/watch-and-quickwatch-windows.md)
- [Visual Studio 명령](../../ide/reference/visual-studio-commands.md)
- [명령 창](../../ide/reference/command-window.md)
- [찾기/명령 상자](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)