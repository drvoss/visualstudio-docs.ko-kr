---
title: -SafeMode(devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 14b2ac3a80a9e17e0c554f56ae8e31ac32450c5e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62945481"
---
# <a name="safemode-devenvexe"></a>/SafeMode(devenv.exe)

안전 모드에서 Visual Studio를 시작하고 기본 환경 및 서비스만 로드합니다.

## <a name="syntax"></a>구문

```shell
devenv /SafeMode
```

## <a name="remarks"></a>주의

이 스위치는 Visual Studio가 시작될 때 모든 타사 VSPackages의 로드를 차단하여 안정적으로 실행될 수 있습니다.

## <a name="example"></a>예제

다음 예제에서는 안전 모드에서 Visual Studio를 시작합니다.

```shell
devenv /safemode
```

## <a name="see-also"></a>참고 항목

- [Devenv 명령줄 스위치](../../ide/reference/devenv-command-line-switches.md)