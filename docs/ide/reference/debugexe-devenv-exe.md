---
title: -DebugExe(devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /DebugExe switch
- DebugExe switch
- /DebugExe [devenv.exe]
- debugging executables
ms.assetid: cd700006-1648-418f-924b-4b1e5c1412ab
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bb4eb1eb49cd6b29740fb6d365a98a51cc28387e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661671"
---
# <a name="debugexe-devenvexe"></a>/DebugExe(devenv.exe)

디버깅하도록 지정된 실행 파일을 엽니다.

## <a name="syntax"></a>구문

```shell
devenv /DebugExe ExecutableFile
```

## <a name="arguments"></a>인수

- *ExecutableFile*

  필수 요소. `.exe` 파일의 경로 및 파일 이름. `.exe` 파일을 찾을 수 없거나 파일이 존재하지 않는 경우 경고 또는 오류가 표시되지 않고 Visual Studio가 정상적으로 시작됩니다.

## <a name="remarks"></a>설명

*ExecutableFile* 매개 변수 다음에 나오는 모든 문자열은 해당 파일에 인수로 전달됩니다.

## <a name="example"></a>예

다음 예제는 디버깅을 위해 `MyApplication.exe` 파일을 엽니다.

```shell
devenv /debugexe MyApplication.exe
```

## <a name="see-also"></a>참고 항목

- [Devenv 명령줄 스위치](../../ide/reference/devenv-command-line-switches.md)