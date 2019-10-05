---
title: 지원 언어 서비스의 개요를 제공 합니다. | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], outlining support
- language services, supporting outlining
- outlining, supporting
ms.assetid: df759e89-8193-418c-8038-6626304d387b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 13bfa8abacbd8f9bd4b604c5a2389981c192b86e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66312129"
---
# <a name="how-to-provide-expanded-outlining-support-in-a-legacy-language-service"></a>방법: 레거시 언어 서비스의 확장된 개요 표시 지원 제공
초과 지 원하는 언어에 대 한 개요 표시 지원 확장을 위한 두 가지는 **정의 부분만 보이기** 명령입니다. 편집기 제어 개요 영역을 추가 하 고 클라이언트 제어 개요 영역을 추가할 수 있습니다.

## <a name="adding-editor-controlled-outline-regions"></a>추가 편집기 제어 개요 영역
 이 방법을 사용 하 여 개요 영역을 만들고 편집기에 지역 확장 되었는지 여부를 처리 될 수 있도록 축소 및 등입니다. 개요 표시 지원 제공 하기 위한 두 가지 옵션을이 옵션은 가장 약한. 이 옵션을 사용 하 여 텍스트의 지정 된 기간 동안 새 개요 영역을 만들 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>합니다. 이 영역을 만든 후 해당 동작은 편집기에서 제어 됩니다. 다음 절차를 사용 하 여 편집기 제어 개요 영역을 구현 합니다.

### <a name="to-implement-an-editor-controlled-outline-region"></a>편집기 제어 개요 영역을 구현 하려면

1. 호출 `QueryService` 에 대 한 <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>

     에 대 한 포인터를 반환 하는이 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>합니다.

2. 호출 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>지정된 텍스트 버퍼에 대 한 포인터에 전달 합니다. 이에 대 한 포인터를 반환 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> 버퍼에 대 한 개체입니다.

3. 호출 <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> 대 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> 에 대 한 포인터에 대 한 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession>합니다.

4. 호출 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> 을 추가 하거나 더 많은 새로운 시간에 영역을 간략하게 설명 합니다.

     이 메서드를 사용 하면 개요, 기존 개요 영역 제거 되었거나 유지 여부 및 여부 개요 영역 확장 또는 기본적으로 축소 된 텍스트의 범위를 지정할 수 있습니다.

## <a name="add-client-controlled-outline-regions"></a>클라이언트 제어 개요 영역 추가
 사용 하 여가이 방법은 클라이언트 제어 (또는 스마트) 구현 개요 등에서 사용 하는 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 및 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 언어 서비스입니다. 자체 개요를 관리 하는 언어 서비스 무효화 될 때 기존 개요 영역을 삭제 하 고 필요에 따라 새 개요 영역을 만드는 데 텍스트 버퍼 콘텐츠를 모니터링 합니다.

### <a name="to-implement-a-client-controlled-outline-region"></a>클라이언트 제어 개요 영역을 구현 하려면

1. 호출 `QueryService` 에 대 한 <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>합니다. 에 대 한 포인터를 반환 하는이 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>합니다.

2. 호출 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>지정된 텍스트 버퍼에 대 한 포인터에 전달 합니다. 버퍼에 대 한 숨겨진된 텍스트 세션이 이미 있는지 여부를 결정 합니다.

3. 텍스트 세션이 이미 있는 경우 1 및 기존에 대 한 포인터를 만들 필요가 없습니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> 개체가 반환 됩니다. 이 포인터를 사용 하 여 열거 하 고 개요 영역을 만듭니다. 그렇지 않으면 호출 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> 버퍼에 대 한 숨겨진된 텍스트 세션을 만듭니다. 에 대 한 포인터를 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> 개체가 반환 됩니다.

    > [!NOTE]
    > 호출 하는 경우 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>, 숨겨진된 텍스트 클라이언트를 지정할 수 있습니다 (즉,는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient> 개체). 이 클라이언트를에 알립니다 때 숨겨진된 텍스트 또는 개요 영역 확장 또는 사용자가 축소 합니다.

4. 호출 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> 구조) 매개 변수: 값을 지정 <xref:Microsoft.VisualStudio.TextManager.Interop.HIDDEN_REGION_TYPE> 에 `iType` 의 멤버는 <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> 숨겨진된 영역 보다는 개요 영역을 만드는 것을 나타내기 위해 구조입니다. 지역 인지 클라이언트 제어 또는 편집기 제어에 지정 합니다 `dwBehavior` 의 멤버는 <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> 구조입니다. 스마트 개요 구현에는 다양 한 편집기 및 클라이언트 제어 개요 영역을 포함할 수 있습니다. 개요 지역을 축소 하면 "..." 등의 표시 되는 배너 텍스트를 지정 합니다 `pszBanner` 의 멤버는 <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> 구조입니다. 숨겨진된 영역에 대 한 편집기의 기본 배너 텍스트는 "..."입니다.