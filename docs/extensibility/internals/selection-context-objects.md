---
title: 선택 컨텍스트 개체 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- selection, tracking
- selection, context objects
ms.assetid: 7308ea8f-a42c-47e5-954e-7dee933dce7a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ef76f417fe2b4371c73d78bbb90b0bd48470746a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66318641"
---
# <a name="selection-context-objects"></a>선택 컨텍스트 개체
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 통합된 개발 환경 (IDE) 전역 선택 컨텍스트 개체를 사용 하 여 IDE에서 표시 되어야 할 사항을 결정 합니다. IDE의 각 창 전역 선택 컨텍스트에 푸시된 자체 선택 컨텍스트 개체를 가질 수 있습니다. IDE는 해당 창에 포커스가 있는 경우 창에서 값을 사용 하 여 전역 선택 항목 컨텍스트를 업데이트 합니다. 자세한 내용은 [사용자에 게 피드백](../../extensibility/internals/feedback-to-the-user.md)합니다.

 각 창 프레임 또는 IDE에서 사이트에 라는 서비스 <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>합니다. 창 프레임에 배치 되는 VSPackage로 생성 된 개체를 호출 해야 합니다 `QueryService` 에 대 한 포인터를 가져올 메서드를는 <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> 인터페이스입니다.

 프레임 창 시작 될 때 전역 선택 항목 컨텍스트 전파 되지 않도록 해당 선택 컨텍스트 정보 부분을 유지할 수 있습니다. 이 기능은 빈 선택 영역을 사용 하 여 시작 해야 할 수 있는 도구 창에 유용 합니다.

 Vspackage를 모니터링할 수 있는 전역 선택 컨텍스트 트리거 이벤트를 수정 합니다. Vspackage를 구현 하 여 다음 작업을 수행할 수 있습니다 `IVsTrackSelectionEx` 고 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> 인터페이스:

- 계층에서 현재 활성 파일을 업데이트 합니다.

- 모니터는 특정 유형의 요소를 변경합니다. 예를 들어 VSPackage는 특별 한을 사용 하는 경우 **속성** 창에서 활성에서 변경 내용을 모니터링할 수 있습니다 **속성** 창 고 필요한 경우 사용자를 다시 시작 합니다.

  다음 순서 대로 선택 영역 추적의 일반적인 과정을 보여 줍니다.

1. IDE는 새로 열린된 창에서 선택 항목 컨텍스트를 검색 하 고 전역 선택 컨텍스트에 넣습니다. 선택 항목 컨텍스트 HIERARCHY_DONTPROPAGATE 또는 SELCONTAINER_DONTPROPAGATE을 사용 하는 경우 해당 정보는 전역 컨텍스트를 전파 되지 않습니다. 자세한 내용은 [사용자에 게 피드백](../../extensibility/internals/feedback-to-the-user.md)합니다.

2. 알림 이벤트를 요청한 모든 VSPackage에 브로드캐스트 됩니다.

3. VSPackage는 도구 또는 기타 유사한 작업을 다시 활성화 계층을 업데이트 하는 등의 작업을 수행 하 여 수신한 이벤트에서 작동 합니다.

## <a name="see-also"></a>참고 항목
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>
- [Visual Studio의 계층 구조](../../extensibility/internals/hierarchies-in-visual-studio.md)
- [IDE의 선택 및 통화](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [프로젝트 형식](../../extensibility/internals/project-types.md)