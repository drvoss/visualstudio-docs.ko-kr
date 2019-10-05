---
title: 레거시 언어 서비스에서 숨겨진된 텍스트 지원 제공
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- hidden text, supporting
- editors [Visual Studio SDK], hidden text
- language services, implementing hidden text regions
ms.assetid: 1c1dce9f-bbe2-4fc3-a736-5f78a237f4cc
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c3d1088399256a4d5b16fa269ce022800ed645b1
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351024"
---
# <a name="how-to-provide-hidden-text-support-in-a-legacy-language-service"></a>방법: 레거시 언어 서비스의 숨겨진된 텍스트 지원 제공
개요 영역 외에도 숨겨진된 텍스트 영역을 만들 수 있습니다. 클라이언트에서 제어 되 나 편집기 제어 숨겨진된 텍스트 영역 수 및 텍스트 영역을 완전히 숨기는 데 사용 됩니다. 편집기는 가로선으로 숨겨진된 영역을 표시합니다. 이러한 예로 **스크립트만** HTML 편집기에서 보기.

## <a name="to-implement-a-hidden-text-region"></a>숨겨진된 텍스트 영역을 구현 하려면

1. 호출 `QueryService` 에 대 한 <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>합니다.

     에 대 한 포인터를 반환 하는이 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>합니다.

2. 호출 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>지정된 텍스트 버퍼에 대 한 포인터에 전달 합니다. 버퍼에 대 한 숨겨진된 텍스트 세션이 이미 있는지 여부를 결정 합니다.

3. 이미 있는 경우 및 기존에 대 한 포인터를 만들 필요가 없습니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> 개체가 반환 됩니다. 이 포인터를 사용 하 여 숨겨진된 텍스트 영역을 만들고 열거 합니다. 그렇지 않으면 호출 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> 버퍼에 대 한 숨겨진된 텍스트 세션을 만듭니다.

     에 대 한 포인터를 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> 개체가 반환 됩니다.

    > [!NOTE]
    > 호출 하는 경우 `CreateHiddenTextSession`, 숨겨진된 텍스트 클라이언트를 지정할 수 있습니다 (즉, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient>). 숨겨진된 텍스트 클라이언트 숨겨진된 텍스트 또는 개요 확장 또는 사용자가 축소 하는 경우이 알려 줍니다.

4. 호출 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> 을 추가 하거나 더 많은 새로운 개요 영역 번에서 다음 정보를 지정 하는 `reHidReg` (<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>) 매개 변수:

    1. 값을 지정 `hrtConcealed` 에 `iType` 의 멤버는 <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> 개요 영역 보다는 숨겨진된 영역을 만드는 것을 나타내기 위해 구조입니다.

        > [!NOTE]
        > 숨겨진된 영역 숨겨지면 편집기가 있는지 표시 하려면 숨겨진된 영역 주위에 선을 자동으로 표시 합니다.

    2. 클라이언트에서 제어 되 나 편집기 제어에서 지역 인지 지정 합니다 `dwBehavior` 의 멤버는 <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> 구조. 스마트 개요 구현에는 다양 한 편집기 및 클라이언트 제어 개요 및 숨겨진된 텍스트 영역을 포함할 수 있습니다.