---
title: -Out(devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- errors [Visual Studio], builds
- Devenv, /Out switch
- builds [Visual Studio], logs
- error logs [Visual Studio], command-line build errors
- error logs [Visual Studio]
- /Out Devenv switch
- Out Devenv switch
- builds [Visual Studio], errors
- output files, build errors
ms.assetid: 9002d8c2-36d4-451c-b489-8f01932f31f7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 039456c10993199ec2265042aabc0ed5c475ccd9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62969295"
---
# <a name="out-devenvexe"></a>/Out (devenv.exe)

솔루션을 [실행](run-devenv-exe.md), [실행 및 종료](runexit-devenv-exe.md), [업그레이드](upgrade-devenv-exe.md), [빌드](build-devenv-exe.md), [다시 빌드](rebuild-devenv-exe.md), [정리](clean-devenv-exe.md) 또는 [배포](deploy-devenv-exe.md)하는 경우 오류를 저장하고 표시할 파일을 지정합니다.

## <a name="syntax"></a>구문

```shell
devenv /Out FileName
```

## <a name="arguments"></a>인수

- *FileName*

  필수 요소. 실행 파일을 빌드할 때 출력을 수신할 파일의 경로 및 이름입니다.

## <a name="remarks"></a>주의

존재하지 않는 파일 이름이 지정되면 파일이 자동으로 만들어집니다. 이외의 경우에는 파일이 이미 있고 결과는 파일의 기존 내용에 추가됩니다.

명령줄 빌드 오류는 **명령** 창 및 **출력** 창의 솔루션 작성기 보기에 표시됩니다. 이 스위치는 무인 빌드의 결과를 보는 데 유용합니다.

## <a name="example"></a>예제

이 예제에서는 `MySolution`을 실행하고 `MyErrorLog.txt` 파일에 오류를 기록합니다.

```shell
devenv /run "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /out "C:\MyErrorLog.txt"
```

## <a name="see-also"></a>참고 항목

- [Devenv 명령줄 스위치](../../ide/reference/devenv-command-line-switches.md)
- [/Run(devenv.exe)](../../ide/reference/run-devenv-exe.md)
- [/RunExit(devenv.exe)](runexit-devenv-exe.md)
- [/Upgrade (devenv.exe)](upgrade-devenv-exe.md)
- [/Clean (devenv.exe)](clean-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)