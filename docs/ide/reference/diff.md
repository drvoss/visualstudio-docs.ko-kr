---
title: -Diff(devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /Diff switch
- /Diff Devenv switch
- Diff Devenv switch
ms.assetid: 5377fedb-632a-4e86-a947-7c11c86451e7
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 26d438e9cea35cbf178658d8def78e264804240c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654506"
---
# <a name="diff-devenvexe"></a>/Diff(devenv.exe)

두 파일을 비교합니다. 차이점은 특별한 Visual Studio 창에 표시됩니다.

## <a name="syntax"></a>구문

```shell
devenv /Diff SourceFile TargetFile [SourceDisplayName [TargetDisplayName]]
```

## <a name="arguments"></a>인수

- *SourceFile*

  필수 요소. 비교할 첫 번째 파일의 전체 경로와 이름입니다.

- *TargetFile*

  필수 요소. 비교할 두 번째 파일의 전체 경로와 이름입니다.

- *SourceDisplayName*

  선택 사항입니다. 첫 번째 파일의 표시 이름입니다.

- *TargetDisplayName*

  선택 사항입니다. 두 번째 파일의 표시 이름입니다.

## <a name="remarks"></a>설명

IDE의 인스턴스가 이미 열려 있는 경우 현재 IDE의 탭에 파일 비교가 나타납니다.

## <a name="example"></a>예

첫 번째 예제에서는 표시 이름을 변경하지 않고 두 파일을 비교합니다. 두 번째 예제에서는 표시 이름을 둘 다 변경하면서 파일을 비교합니다. 세 번째 및 네 번째 예제에서는 두 파일을 비교하지만 첫 번째 파일 또는 두 번째 파일에만 별칭을 적용합니다.

```shell
devenv /diff File1.txt File2.txt

devenv /diff File1.txt File2.txt FirstAlias "Second Alias"

devenv /diff File1.txt File2.txt "File One"

devenv /diff File1.txt File2.txt "" FileTwo
```

## <a name="see-also"></a>참고 항목

- [Devenv 명령줄 스위치](../../ide/reference/devenv-command-line-switches.md)
