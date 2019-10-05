---
title: 레거시 언어 Service1의 매개 변수 정보 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, method tips
- method tips
- language services, parameter info tooltip
- IVsMethodData interface
- Parameter Info (IntelliSense)
ms.assetid: f367295e-45b6-45d2-9ec8-77481743beef
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 93283854760c4ab8309d3769550beb664c14f41b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66314636"
---
# <a name="parameter-info-in-a-legacy-language-service"></a>레거시 언어 서비스의 매개 변수 정보
IntelliSense 매개 변수 정보 도구 설명이 있는 언어 구문에 대 한 힌트를 사용 하 여 사용자를 제공 합니다.

 레거시 언어 서비스는 VSPackage의 일부로 구현 됩니다 있지만 MEF 확장을 사용 하는 언어 서비스 기능을 구현 하는 최신 방법입니다. 자세한 내용을 참조 하세요 [편집기 및 언어 서비스 확장](../../extensibility/extending-the-editor-and-language-services.md)합니다.

> [!NOTE]
> 편집기를 사용 하 여 새 API 최대한 빨리 시작 하는 것이 좋습니다. 언어 서비스의 성능이 향상 되 고 새 편집기 기능을 활용할 수 있습니다.

## <a name="how-parameter-info-tooltips-work"></a>매개 변수 정보 도구 설명의 작동 방식
 편집기에서 문을 입력할 때 VSPackage에 입력 되는 문의 정의 포함 하는 작은 도구 설명 창이 표시 됩니다. 예를 들어, Microsoft Foundation 클래스 (MFC) 문을 입력 하는 경우 (같은 `pMainFrame ->UpdateWindow`) 메서드 팁의 정의 확인 표시 매개 변수를 나열 하려면 여는 괄호 키를 누릅니다는 `UpdateWindow` 메서드.

 매개 변수 정보 도구 설명 문 완성을 사용 하 여 함께 일반적으로 사용 됩니다. 매개 변수 또는 기타 서식이 지정 된 정보는 메서드 이름 또는 키워드 뒤에 있는 언어에 대 한 가장 유용 합니다.

 매개 변수 정보 도구 설명은 명령 인터 셉 션을 통해 언어 서비스에서 시작 됩니다. 언어 서비스 개체를 가로채 사용자 문자를 구현 해야 합니다는 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 인터페이스 및 텍스트 보기에 대 한 포인터를 전달 하 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 구현을 호출 하 여는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> 에서 메서드를 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 인터페이스입니다. 명령 필터에는 코드 창에 입력 하는 명령을 차단 합니다. 사용자에 게 매개 변수 정보를 표시 하는 경우 알아야 명령 정보를 모니터링 합니다. 문 완성, 오류 표식, 등에 대 한 동일한 명령 필터를 사용할 수 있습니다.

 언어 서비스 힌트를 제공할 수 있는 키워드를 입력 하면 다음 언어 서비스를 만듭니다는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> 개체 및 호출 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> 에서 메서드는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 힌트를 표시 하려면 IDE에 알리는 인터페이스를 합니다. 만들기는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> 를 사용 하 여 개체 `VSLocalCreateInstance` coclass를 지정 하 고 `CLSID_VsMethodTipWindow`입니다. `VsLocalCreateInstance` 호출 하는 헤더 파일 vsdoc.h에 정의 된 함수인 `QueryService` 로컬 레지스트리 및 호출에 대 한 `CreateInstance` 이 개체에 대 한는 `CLSID_VsMethodTipWindow`합니다.

## <a name="providing-a-method-tip"></a>메서드 설명 제공
 메서드 팁을 제공 하려면 호출을 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> 의 메서드를 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> 인터페이스를 구현 전달를 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> 인터페이스.

 경우에 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> 클래스 호출 되 면 해당 메서드를 다음 순서로 호출 됩니다.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetContextStream%2A>

     현재 텍스트 버퍼의 위치 및 관련 데이터의 길이 반환합니다. 이렇게 하면 IDE에 도구 설명 창 사용 하 여 해당 데이터를 가리지 합니다.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetCurMethod%2A>

     처음에 표시 하려는 메서드 수 (인덱스 0부터 시작)를 반환 합니다. 예를 들어 0을 반환 하는 경우 다음 첫 번째 오버 로드 된 메서드는 처음에 표시 됩니다.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetOverloadCount%2A>

     현재 컨텍스트에서 적용할 수 있는 오버 로드 된 메서드를 반환 합니다. 값을이 메서드에 대 한 1 보다 큰 반환 하는 경우 다음 텍스트 뷰에 표시 됩니다 위쪽 및 아래쪽 화살표가 있습니다. 아래쪽 화살표를 클릭 하면 IDE 호출을 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.NextMethod%2A> 메서드. 위쪽 화살표를 클릭 하면 IDE 호출을 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.PrevMethod%2A> 메서드.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A>

     매개 변수 정보 도구 설명의 텍스트를 여러 번 호출 하는 동안 생성 되는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A> 고 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A> 메서드.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterCount%2A>

     메서드를 표시할 매개 변수 개수를 반환 합니다.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A>

     표시 하려는 오버 로드를 사용 하 여 해당 하는 메서드 값을 반환 하는 경우이 메서드는에 대 한 호출 뒤에 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> 메서드.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>

     언어 서비스를 편집기 메서드 팁 표시 되 면 업데이트를 알립니다. 에 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> 메서드를 다음을 호출 합니다.

    ```
    <pTxWin> ->UpdateTipWindow(<pTip>, UTW_CONTENTCHANGED | UTW_CONTEXTCHANGED).
    ```

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>

     에 대 한 호출을 수신 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> 메서드 팁 창의 닫을 때 메서드.