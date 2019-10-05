---
title: CreateExpInstance 유틸리티 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- experimental hive
- experimental instance
- createexpinstance
- createexpinst
ms.assetid: 03779774-9401-49ae-997c-0c3ab25ed0d5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ed03833b6c109ca78feb86c1cfe41fa453022c66
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66341911"
---
# <a name="createexpinstance-utility"></a>CreateExpInstance 유틸리티
사용 된 **CreateExpInstance** 유틸리티를 만들거나 다시 설정 하거나 Visual Studio의 실험적 인스턴스를 삭제 합니다. 디버그 하 고 내부 제품을 변경 하지 않고 Visual Studio 확장을 테스트 하는 실험적 인스턴스를 사용할 수 있습니다.

## <a name="syntax"></a>구문

```
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix
```

## <a name="parameters"></a>매개 변수
 **/ 만들기** 실험적 인스턴스를 만듭니다.

 **/ 재설정** 실험적 인스턴스를 삭제 하 고 다음 새로 만듭니다.

 **/ 정리** 실험적 인스턴스를 삭제 합니다.

 **/ VSInstance** 복사할 기본 Visual Studio 인스턴스를 포함 하는 디렉터리의 이름입니다.

 **/ RootSuffix** 실험적 인스턴스 디렉터리의 이름에 추가할 접미사입니다.

## <a name="remarks"></a>설명
 Visual Studio 확장에서 작업 하는 경우 기본 실험적 인스턴스를 열고 현재 확장을 설치 하려면 F5를 눌러 수 있습니다. 실험적 인스턴스를 사용할 수 있는 경우 Visual Studio는 기본 설정을 포함 하는 것을 만듭니다.

 실험적 인스턴스에서의 기본 위치는 Visual Studio 버전 번호에 따라 달라 집니다. 예를 들어, Visual Studio 2015에 대 한 위치가 *%localappdata%\Microsoft\VisualStudio\14.0Exp\\* 합니다. 디렉터리 위치에 있는 모든 파일에는 해당 인스턴스의 일부로 간주 됩니다. 추가 실험적 인스턴스를 기본 위치는 디렉터리 이름을 변경 하지 않으면 Visual Studio에서 로드 되지 않습니다.

 Visual Studio 실험적 인스턴스를 열었을 때 시스템 레지스트리를 액세스 하지 않습니다. 이 레지스트리 하이브의 실험적 버전을 사용 하는 Visual Studio의 이전 버전에서 서로 다릅니다.

 합니다 **CreateExpInstance** 유틸리티를 대체 합니다 **VsRegEx** 유틸리티입니다.

 다음 예제에서는 Visual Studio의 기본 실험적 인스턴스 다시 설정합니다.

 **CreateExpInstance.exe /Reset /VSInstance=14.0 /RootSuffix=Exp**

## <a name="see-also"></a>참고자료
- [VSPackage](../../extensibility/internals/vspackages.md)