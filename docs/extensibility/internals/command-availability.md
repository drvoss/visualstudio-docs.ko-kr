---
title: 명령 가용성 | Microsoft Docs
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- commands, context
- menu items, visibility contexts
ms.assetid: c74e3ccf-d771-48c8-a2f9-df323b166784
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5087e5f7958f9abe46e0caeb2eb03e21285e4da7
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66338599"
---
# <a name="command-availability"></a>명령 가용성

Visual Studio 컨텍스트에 사용할 수 있는 명령을 결정 합니다. 컨텍스트는 현재 프로젝트, 현재 편집기, 로드 되는 Vspackage 및 통합된 개발 환경 (IDE)의 다른 측면에 따라 변경할 수 있습니다.

## <a name="command-contexts"></a>명령이 컨텍스트

다음 명령은 컨텍스트는 가장 일반적인 이유:

- IDE: IDE에서 제공 하는 명령과 항상 사용할 수 있습니다.

- VSPackage. Vspackage는 명령을 표시 하거나 숨길 때 정의할 수 있습니다.

- 프로젝트: 프로젝트 명령은 현재 선택한 프로젝트에 대해서만 표시 됩니다.

- 편집기: 한 번에 하나만 편집기를 활성화할 수 있습니다. 활성 편집기에서 명령을 사용할 수 있습니다. 편집기는 언어 서비스와 긴밀 하 게 작동합니다. 언어 서비스에 연결된 된 편집기의 컨텍스트에서 해당 명령을 처리 해야 합니다.

- 파일 형식: 편집기에는 둘 이상의 파일 형식을 로드할 수 있습니다. 사용 가능한 명령 파일 형식에 따라 변경할 수 있습니다.

- 활성 창: 마지막 활성 문서 창이 키 바인딩에 대 한 사용자 인터페이스 (UI) 컨텍스트를 설정합니다. 그러나 내부 웹 브라우저를 유사한 키 바인딩 테이블이 있는 도구 창 UI 컨텍스트를 설정할 수도 없습니다. HTML 편집기와 같은 다중 탭 문서 창에 대 한 모든 탭에는 다른 명령을 컨텍스트가 GUID입니다. 도구 창을 등록 되 면 항상 사용할 수 있기에 **보기** 메뉴.

- UI 컨텍스트: UI 컨텍스트 변수의 값으로 식별 됩니다 합니다 <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> 클래스, 예를 들어 <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid> 솔루션을 빌드할 때 또는 <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid> 디버거가 활성 상태일 때. 여러 UI 컨텍스트는 동시에 활성화할 수 있습니다.

## <a name="define-custom-context-guids"></a>사용자 지정 컨텍스트 Guid를 정의 합니다.

경우 GUID는 아직 정의 되지 않은 적절 한 명령 컨텍스트를 VSPackage의 하나를 정의 하 고 활성 또는 비활성 명령의 표시 유형을 제어 하려면 필요에 따라 수를 프로그래밍할 수 있습니다.:

1. 컨텍스트 Guid를 호출 하 여 등록 된 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> 메서드.

2. 호출 하 여 GUID 컨텍스트의 상태를 가져오기는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> 메서드.

3. 호출 하 여 상황에 맞는 Guid 설정 및 해제를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> 메서드.

> [!CAUTION]
> VSPackage 영향을 주지 않습니다 모든 기존 컨텍스트 Guid에 따라 달라질 수 있습니다 다른 Vspackage 때문에 있는지 확인 합니다.

## <a name="see-also"></a>참고자료

- [선택 컨텍스트 개체](../../extensibility/internals/selection-context-objects.md)
- [Vspackage에서 사용자 인터페이스 요소를 추가 하는 방법](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)