---
title: 실험적 인스턴스에서 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- VSPackages, experimental builds
- VSIP, experimental builds
ms.assetid: ead0df4e-6f88-4b42-9297-581b7902f050
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 773581e7cf9e0f12f507dcd3c768d88724da9f80
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66316426"
---
# <a name="the-experimental-instance"></a>실험적 인스턴스
Visual Studio 개발 환경에서 변경할 수는 테스트 되지 않은 응용 프로그램을 보호 하려면 VSSDK 실험 하는 데 사용할 수 있는 실험적 공간을 제공 합니다. 일반적으로 Visual Studio를 사용 하 여 새 응용 프로그램을 개발 하지만이 실험적 인스턴스를 사용 하 여 실행할 수 있습니다.

 VSIX 패키지에 있는 모든 응용 프로그램 디버그 모드에서 Visual Studio 실험적 인스턴스를 시작 합니다.

 특정 솔루션 외부 Visual Studio의 실험적 인스턴스를 시작 하려면 명령 창에서 다음 명령을 실행 합니다.

 " *\<Visual studio installation path>* \Common7\IDE\devenv.exe" /RootSuffix Exp

> [!NOTE]
> 실험적 인스턴스를 레지스트리에 쓸 합니다 `<version number>Exp` 고 `<version number>Exp_Config` 노드. 예를 들어 Visual Studio 2015 실험적 레지스트리 영역에는
>
> `HKCU\Software\Microsoft\VisualStudio\14.0Exp` 및 `HKCU\Software\Microsoft\VisualStudio\14.0Exp_Config`

 이 개발 하는 동안 실험적 인스턴스에서 확장을 실행 하는 것이 좋습니다. 확장을 배포 하는 경우 개발 인스턴스에서 실행 됩니다. 응용 프로그램을 등록 하는 방법에 대 한 자세한 내용은 참조 하세요. [Vspackage 등록](../extensibility/internals/registering-vspackages.md)합니다.