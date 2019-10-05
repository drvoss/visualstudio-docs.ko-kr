---
title: Vspackage 관리 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, delayed loading
- delay loading
- VSPackages, loading
ms.assetid: 386e0ce5-4107-4164-b0cd-1cf43eb5e7cf
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b622901ce90187ff8230a8e23a11110e0795b0b5
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66340494"
---
# <a name="manage-vspackages"></a>VSPackage 관리
대부분의 프로젝트 및 항목 템플릿을 등록 하 고 패키지를 자동으로 로드 되므로 Vspackage, 관리에 대해 걱정할 필요가 없습니다. 그러나 일부 경우에 패키지를 관리 하기 위해 좀 더 자세한 내용을 알아보려면 해야 할 수 있습니다.

## <a name="use-the-experimental-instance"></a>실험적 인스턴스 사용
 실험적 인스턴스에 대 한 자세한 내용을 참조 하세요 [실험적 인스턴스에서](../extensibility/the-experimental-instance.md)합니다.

## <a name="register-and-unregister-vspackages"></a>등록 하 고 Vspackage 등록 취소
 등록 및 Vspackage 및 다른 유형의 확장을 등록 취소 하는 방법을 알아보려면 참조 [등록 하 고 Vspackage 등록 취소](../extensibility/registering-and-unregistering-vspackages.md)합니다.

## <a name="load-a-vspackage"></a>VSPackage를 로드 합니다.
 Vspackage는 CMDUICONTEXT GUID 켜져 특정 autoload를 설정할 수 있습니다. 자세한 내용은 [부하 Vspackage](../extensibility/loading-vspackages.md)합니다.

## <a name="use-asyncpackage-to-load-vspackages-in-the-background"></a>AsyncPackage를 사용 하 여 백그라운드에서 Vspackage를 로드 합니다.
 `AsyncPackage` 클래스를 사용 하면 Visual Studio에서 UI 응답성 향상에 대 한 백그라운드 스레드에서 패키지 로드 합니다. 자세한 내용은 [방법: AsyncPackage를 사용 하 여 백그라운드에서 Vspackage를 로드](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md)합니다.

## <a name="rule-based-ui-context-for-extensions"></a>확장에 대 한 규칙 기반 UI 컨텍스트
 규칙 기반 UI 컨텍스트 확장 작성자를는 UI 컨텍스트의 활성화 되 고 연결된 Vspackage 로드 정확한 조건을 정의할 수 있습니다. 자세한 내용은 [방법: Visual Studio 확장에 대 한 규칙 기반 UI 컨텍스트를 사용 하 여](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md)입니다.

## <a name="diagnose-extension-performance"></a>확장 성능 진단
확장 시작 및 솔루션 로드 성능에 영향을 줄 수 있습니다. Visual Studio 확장 impact는 어떻게 계산 및 방식을 분석할 수 있습니다 로컬로 확장인 확장에 영향을 주는 성능으로 표시 될 수 있으며 테스트에 대해 알아봅니다. 자세한 내용은 [방법: 확장 성능 진단](how-to-diagnose-extension-performance.md)합니다.

## <a name="troubleshoot-vspackages"></a>Vspackage 문제 해결
 Vspackage 로드 안 함 또는 오류가 발생 하는 문제 해결을 위한 기술을 확인 합니다. [Vspackage 문제 해결](../extensibility/troubleshooting-vspackages.md)

## <a name="see-also"></a>참고자료
- [VSPackage](../extensibility/internals/vspackages.md)