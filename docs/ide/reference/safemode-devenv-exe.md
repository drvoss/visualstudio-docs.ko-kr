---
title: -SafeMode(devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: abaeded184db78085a9629da0e763b2f76dbd328
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655508"
---
# <a name="safemode-devenvexe"></a>/SafeMode(devenv.exe)

안전 모드에서 Visual Studio를 시작하고 기본 환경 및 서비스만 로드합니다.

## <a name="syntax"></a>구문

```shell
devenv /SafeMode
```

## <a name="remarks"></a>설명

이 스위치는 Visual Studio가 시작될 때 모든 타사 VSPackages의 로드를 차단하여 안정적으로 실행될 수 있습니다.

## <a name="example"></a>예

다음 예제에서는 안전 모드에서 Visual Studio를 시작합니다.

```shell
devenv /safemode
```

## <a name="see-also"></a>참고 항목

- [Devenv 명령줄 스위치](../../ide/reference/devenv-command-line-switches.md)