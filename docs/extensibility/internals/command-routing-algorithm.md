---
title: 명령 라우팅 알고리즘 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, routing
- command routing
ms.assetid: 998b616b-bd08-45cb-845f-808efb8c33bc
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c98e145961f8d98c7ea939bd051a94ee68cd93f4
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66342106"
---
# <a name="command-routing-algorithm"></a>명령 라우팅 알고리즘
Visual Studio에서 명령은 다양 한 다른 구성 요소에서 처리 됩니다. 명령 (라고도 전역)은 가장 바깥쪽 컨텍스트를 현재 선택 영역을 기반으로 하는 가장 안쪽의 컨텍스트에서 라우팅됩니다. 자세한 내용은 [가용성 명령을](../../extensibility/internals/command-availability.md)합니다.

## <a name="order-of-command-resolution"></a>명령 확인 순서
 명령에서는 다음과 같은 수준의 명령 컨텍스트를 통해 전달 됩니다.

1. 추가 기능: 환경에는 먼저 모든 추가 기능에 존재 하는 명령을 제공 합니다.

2. 명령 우선 순위: 다음이 명령을 사용 하 여 등록 된 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterPriorityCommandTarget>합니다. Visual Studio에서 모든 명령에 대 한 라고 하며 등록 된 순서 대로 호출 됩니다.

3. 상황에 맞는 메뉴 명령: 상황에 맞는 메뉴에 있는 명령은 먼저 일반적인 라우팅으로 그 후 상황에 맞는 메뉴를 제공 하는 명령 대상에 제공 됩니다.

4. 도구 모음 명령 대상 설정: 이러한 명령 대상을 호출 하는 경우 등록 된 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell4.SetupToolbar2%2A>합니다. 합니다 `pCmdTarget` 매개 변수 수 `null`입니다. 없는 경우 `null`를이 명령 대상 업데이트 설정 하는 도구 모음에 있는 모든 명령에 사용 됩니다. 셸 도구 모음을 설정 하는 경우 창 프레임으로 전달 합니다 `pCmdTarget` 창 프레임을 통해 도구 모음 흐름에서 명령에 모든 업데이트에도 있도록 때 포커스가 있습니다.

5. 도구 창: 일반적으로 구현 하는 windows 도구를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> 인터페이스를 구현 해야 합니다 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 도구 창이 활성 창인지 때 Visual Studio 명령 대상을 받을 수 있도록 인터페이스입니다. 그러나 도구 창이 있는 경우 포커스가 합니다 **프로젝트** 창에서 다음 명령으로 라우팅됩니다는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> 선택한 항목의 공통 부모가 되는 인터페이스입니다. 명령이 라우팅되는이 선택에 여러 프로젝트에 걸쳐 있는 경우는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> 계층입니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> 인터페이스를 포함 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> 및 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> 에서 해당 명령에 유사한 메서드를 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 인터페이스.

6. 문서 창: 명령에 있는 경우는 `RouteToDocs` 에 플래그를 설정 해당 *.vsct* 파일을 Visual Studio 찾습니다 이거나 문서 보기 개체에 대 한 명령 대상의 인스턴스는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> 인터페이스 또는 문서의 인스턴스 개체 ( 일반적으로 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> 인터페이스 또는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> 인터페이스). Visual Studio 명령을 라우팅합니다 문서 뷰 개체는 명령을 지원 하지 않으면는 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 반환 되는 인터페이스입니다. (문서 데이터 개체에 대 한 선택적 인터페이스입니다.)

7. 현재 계층: 현재 계층에서 활성 문서 창이 나에서 선택한 계층을 소유 하는 프로젝트를 수 있습니다 **솔루션 탐색기**합니다. Visual Studio를 찾습니다는 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 현재 또는 활성 계층 구조에서 구현 되는 인터페이스입니다. 계층에는 프로젝트 항목의 문서 창에 포커스가 있을 경우에 계층 활성화 될 때마다 사용할 수 있는 명령을 지원 해야 합니다. 그러나 경우에만 적용 되는 명령 **솔루션 탐색기** 에 포커스를 사용 하 여 지원 해야 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> 인터페이스 및 해당 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> 및 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> 메서드.

     **잘라내기**, **복사**를 **붙여넣기**를 **삭제**를 **이름 바꾸기**를 **입력**, 및 **DoubleClick** 명령에는 특별 한 처리가 필요 합니다. 처리 하는 방법에 대 한 자세한 **삭제** 하 고 **제거** 계층에 대 한 명령 참조는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler> 인터페이스.

8. 전역: Visual Studio를 구현 하는 명령을 소유 하는 VSPackage에 라우팅할 하려고 앞에서 언급 한 컨텍스트에서 명령을 처리 하지 않은, 경우를 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 인터페이스입니다. VSPackage 이미 로드 되지 않은, 경우 로드 되지 않습니다 Visual Studio에서 호출 하는 경우는 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 메서드. VSPackage는 경우에만 로드 되는 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> 메서드가 호출 됩니다.

## <a name="see-also"></a>참고자료
- [명령 디자인](../../extensibility/internals/command-design.md)