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
ms.openlocfilehash: cc4f0aad4dd3f28f28259d0ca439a0cda1a520d9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723909"
---
# <a name="selection-context-objects"></a>선택 컨텍스트 개체
@No__t_0 IDE (통합 개발 환경)는 전역 선택 컨텍스트 개체를 사용 하 여 IDE에 표시 되는 항목을 결정 합니다. IDE의 각 창에는 전역 선택 컨텍스트에 푸시되는 자체 선택 컨텍스트 개체가 있을 수 있습니다. IDE는 창에 포커스가 있을 때 창의 값을 사용 하 여 전역 선택 컨텍스트를 업데이트 합니다. 자세한 내용은 [사용자에 대 한 피드백](../../extensibility/internals/feedback-to-the-user.md)을 참조 하세요.

 IDE의 각 창 프레임이 나 사이트에는 <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> 라는 서비스가 있습니다. 창 프레임에 있는 VSPackage에서 만든 개체는 <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> 인터페이스에 대 한 포인터를 가져오기 위해 `QueryService` 메서드를 호출 해야 합니다.

 프레임 창은 선택 컨텍스트 정보의 일부가 시작 될 때 전역 선택 컨텍스트로 전파 되지 않도록 유지할 수 있습니다. 이 기능은 빈 선택 항목으로 시작 해야 할 수 있는 도구 창에 유용 합니다.

 전역 선택 컨텍스트를 수정 하면 Vspackage에서 모니터링할 수 있는 이벤트가 트리거됩니다. Vspackage는 `IVsTrackSelectionEx` 및 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> 인터페이스를 구현 하 여 다음 작업을 수행할 수 있습니다.

- 계층의 현재 활성 파일을 업데이트 합니다.

- 특정 형식의 요소에 대 한 변경 내용을 모니터링 합니다. 예를 들어 VSPackage 특수 **속성** 창을 사용 하는 경우 활성 **속성** 창에서 변경 내용을 모니터링 하 고 필요한 경우 다시 시작할 수 있습니다.

  다음 시퀀스에서는 일반적인 선택 추적 과정을 보여 줍니다.

1. IDE는 새로 열린 창에서 선택 컨텍스트를 검색 하 여 전역 선택 컨텍스트에 넣습니다. 선택 컨텍스트가 HIERARCHY_DONTPROPAGATE 또는 SELCONTAINER_DONTPROPAGATE를 사용 하는 경우 해당 정보는 전역 컨텍스트에 전파 되지 않습니다. 자세한 내용은 [사용자에 대 한 피드백](../../extensibility/internals/feedback-to-the-user.md)을 참조 하세요.

2. 알림 이벤트는 요청 된 모든 VSPackage에 브로드캐스트 됩니다.

3. VSPackage는 계층 업데이트, 도구 다시 활성화 또는 기타 유사한 작업과 같은 작업을 수행 하 여 수신 하는 이벤트에 대해 작동 합니다.

## <a name="see-also"></a>참조
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>
- [Visual Studio의 계층 구조](../../extensibility/internals/hierarchies-in-visual-studio.md)
- [IDE의 선택 및 통화](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [프로젝트 형식](../../extensibility/internals/project-types.md)