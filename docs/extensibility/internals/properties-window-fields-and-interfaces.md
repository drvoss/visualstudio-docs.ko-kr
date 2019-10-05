---
title: 속성 Window Fields and Interfaces | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, fields and interfaces
ms.assetid: 0328f0e5-2380-4a7a-a872-b547cb775050
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 379eaa6e154b77d10463514a63978708bf2b89d0
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66347875"
---
# <a name="properties-window-fields-and-interfaces"></a>Properties Window Fields and Interfaces
모델에 표시 되는 정보를 확인 하려면 선택 합니다 **속성** IDE에서 포커스가 있는 창에서 창 기반 합니다. 모든 창 및 선택된 된 창 내에서 개체에 전역 선택 컨텍스트에 푸시된 해당 선택 컨텍스트 개체를 가질 수 있습니다. 해당 창에 포커스가 있는 경우 창 프레임의 값을 사용 하 여 전역 선택 컨텍스트를 업데이트 하는 환경입니다. 포커스 변경 되 면 선택 항목 컨텍스트를 그렇습니다.

## <a name="tracking-selection-in-the-ide"></a>IDE에서 추적 선택
 창 프레임 또는 IDE를 소유한 사이트에 라는 서비스 <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>합니다. 다음 단계에서는 다른 열린 창으로 포커스를 변경 하거나에서 다른 프로젝트 항목을 선택 하는 사용자가 발생 한 항목을 변경 하는 방법 설명 **솔루션 탐색기**를 에서표시되는내용을변경하기위해구현됩니다 **속성** 창입니다.

1. 선택한 창 호출에 배치 되는 VSPackage로 생성 된 개체 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> 필요가 <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> 호출 <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>합니다.

2. 선택한 기간에 제공한 선택 컨테이너 자체 만듭니다 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 개체입니다. VSPackage 호출 하는 선택 항목이 변경 하면 <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> 환경에서 모든 수신기에 알리기 위해 포함 하는 **속성** 변경의 창. 또한 계층 구조 및 항목 관련 정보를 새 선택 영역에 대 한 액세스를 제공 합니다.

3. 호출 <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> 선택한 계층 항목에 전달 하는 `VSHPROPID_BrowseObject` 매개 변수를 채웁니다는 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 개체입니다.

4. 파생 된 개체를 [IDispatch 인터페이스](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) 에 대해 반환 됩니다 [__VSHPROPID 합니다. VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>) 항목을 요청 하 고 환경에 래핑되어는 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> (다음 단계 참조). 환경에 대 한 두 번째 호출에서는 호출에 실패 하는 경우 `IVsHierarchy::GetProperty`, 선택 컨테이너 전달 [__VSHPROPID 합니다. VSHPROPID_SelContainer](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_SelContainer>) 항목 계층 구조를 제공 합니다.

    VSPackage를 만들지 않습니다 프로젝트가 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 구현 하는 VSPackage의 환경에서 제공한 창 (예를 들어 **솔루션 탐색기**) 생성 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 을 대신 합니다.

5. 메서드를 호출 하는 환경 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 기준으로 개체를 가져오는 데는 `IDispatch` 인터페이스를 작성 하는 **속성** 창.

   값을 **속성** 창이 변경 될, Vspackage 구현 `IVsTrackSelectionEx::OnElementValueChangeEx` 및 `IVsTrackSelectionEx::OnSelectionChangeEx` 요소 값에 변경 내용을 보고할 합니다. 환경을 다음 호출 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> 또는 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> 표시 되는 정보를 유지 하는 **속성** 창이 속성 값과 동기화 합니다. 자세한 내용은 [속성 창에서 속성 값 업데이트](#updating-property-values-in-the-properties-window)합니다.

   다른 선택 하는 것 외에도 프로젝트 항목 **솔루션 탐색기** 해당 항목과 관련 된 속성을 표시 하려면 선택할 수도 있습니다에서 사용할 수 있는 드롭다운 목록을 사용 하 여 폼 이나 문서 창 내에서 다른 개체는 **속성** 창입니다. 자세한 내용은 [속성 창 개요 목록](../../extensibility/internals/properties-window-object-list.md)합니다.

   정보에 표시 되는 방식을 변경할 수 있습니다 합니다 **속성** 범주를 알파벳에서 창 그리드의 는에서해당단추를클릭하여선택한개체에대한속성페이지를도열수,사용가능한경우 **속성** 창입니다. 자세한 내용은 [속성 창 단추](../../extensibility/internals/properties-window-buttons.md) 하 고 [속성 페이지](../../extensibility/internals/property-pages.md)합니다.

   맨 마지막으로 **속성** 창에서 선택한 필드에 대 한 설명을 포함 합니다 **속성** 창 그리드입니다. 자세한 내용은 [속성 창에서 필드 설명 가져오기](#getting-field-descriptions-from-the-properties-window)합니다.

## <a name="updating-property-values-in-the-properties-window"></a> 속성 창에서 속성 값 업데이트
**속성** 창이 속성 값 변경과 동기화 상태를 유지하도록 하는 방법에는 두 가지가 있습니다. 첫 번째는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> 인터페이스를 호출하는 방법입니다. 이 인터페이스는 환경에서 제공하는 도구 및 문서 창의 생성 및 액세스를 포함한 기본적인 창 관리 기능에 대한 액세스를 제공합니다. 다음 단계에서 이 동기화 프로세스를 설명합니다.

### <a name="updating-property-values-using-ivsuishell"></a>IVsUIShell을 사용하여 속성 값 업데이트

#### <a name="to-update-property-values-using-the-ivsuishell-interface"></a>IVsUIShell 인터페이스를 사용하여 속성 값을 업데이트하려면

1. VSPackages, 프로젝트 또는 편집기가 도구 또는 문서 창을 만들거나 열거해야 할 때 언제라도 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>을 호출합니다(<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> 서비스를 통해).

2. 구현 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.RefreshPropertyBrowser%2A> 유지 하는 **속성** 프로젝트에 대 한 속성 변경과 동기화 창 (또는 된 다른 개체에서 검색 되는 **속성** 창) 구현하지않고<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> 발생 하 고 <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink.OnChanged%2A> 이벤트입니다.

3. <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 메서드 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.AdviseHierarchyEvents%2A> 및 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.UnadviseHierarchyEvents%2A>를 구현하여 계층이 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>를 구현할 필요 없이 계층  이벤트의 클라이언트 알림을 설정 및 비활성화합니다.

### <a name="updating-property-values-using-iconnection"></a>IConnection을 사용하여 속성 값 업데이트
 **속성** 창과 속성 값 변경의 동기화를 유지하는 두 번째 방법은 연결 가능 개체에 `IConnection` 를 구현하여 송신 인터페이스가 있음을 나타내는 것입니다. 속성 이름을 지역화하려는 경우에는 <xref:System.ComponentModel.ICustomTypeDescriptor>에서 개체를 파생하세요. <xref:System.ComponentModel.ICustomTypeDescriptor> 구현은 반환되는 속성 설명자를 수정하고 속성의 이름을 변경할 수 있습니다. 설명을 지역화하려면 <xref:System.ComponentModel.DescriptionAttribute>에서 파생되는 특성을 만들고 설명 속성을 재정의하세요.

#### <a name="considerations-in-implementing-the-iconnection-interface"></a>IConnection 인터페이스 구현 시 고려 사항

1. `IConnection`는 <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> 인터페이스를 통해 열거자 하위 개체에 대한 액세스를 제공합니다. 또한 각각 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> 인터페이스를 구현하는 모든 연결점 하위 개체에 대한 액세스도 제공합니다.

2. 모든 찾아보기 개체가 <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink> 이벤트 구현을 담당합니다. **속성** 창은 `IConnection`를 통해 설정된 이벤트에 대해 통지합니다.

3. 연결점은 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A>의 구현에서 허용되는 연결 수(하나 또는 그 이상)를 제어합니다. 하나의 인터페이스만 허용하는 연결점은 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.EnumConnections%2A> 메서드에서 <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>을 반환할 수 있습니다.

4. 클라이언트는 `IConnection` 인터페이스를 호출하여 <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> 인터페이스를 통해 열거자 하위 개체에 대한 액세스를 얻습니다. 그러면 <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> 인터페이스를 호출하여 각 송신 인터페이스 ID(IID)에 대한 연결점을 열거할 수 있습니다.

5. 또한 `IConnection`를 호출하여 각 송신 IID에 대한 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> 인터페이스를 통해 연결점 하위 개체에 대한 액세스를 얻을 수도 있습니다. 클라이언트는 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> 인터페이스를 통해 연결 가능 개체 및 클라이언트 자체 동기화로 통지 루프를 시작하거나 종료합니다. 또한 클라이언트는 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> 인터페이스를 호출하여 <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnections> 인터페이스로 열거자 개체를 가져오고 인식 가능한 연결을 열거할 수도 있습니다.

## <a name="getting-field-descriptions-from-the-properties-window"></a> 속성 창에서 필드 설명 가져오기
**속성** 창 맨 아래 설명 영역에는 선택한 속성 필드와 관련된 정보가 표시됩니다. 이 기능은 기본적으로 켜져 있습니다. 설명 필드를 숨기려면 **속성** 창을 오른쪽 단추로 클릭하고 **설명**을 클릭합니다. 그러면 메뉴 창에서 **설명** 제목 옆의 확인 표시가 사라집니다. 같은 방법으로 **설명** 을 다시 토글하면 필드가 표시됩니다.

 설명 필드의 정보는 <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>에서 가져옵니다. 각 메서드, 인터페이스, coclass 등은 형식 라이브러리에 지역화되지 않은 `helpstring` 특성을 가질 수 있습니다. 합니다 **속성** 창에서 문자열을 검색 <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo.GetDocumentation%2A>합니다.

### <a name="to-specify-localized-help-strings"></a>지역화된 도움말 문자열을 지정하려면

1. 형식 라이브러리( `helpstringdll` )의 라이브러리 문에`typelib`특성을 추가합니다.

   > [!NOTE]
   > 형식 라이브러리가 개체 라이브러리 (.olb) 파일인 경우 이 단계는 선택 사항입니다.

2. 문자열에 대한 지정 `helpstringcontext` 특성을 지정합니다. `helpstring` 특성을 지정할 수도 있습니다.

    이러한 특성은 실제 .chm 파일 도움말 항목에 포함된 `helpfile` 및 `helpcontext` 특성과 별개입니다.

   강조 표시 된 속성 이름에 대해 표시할 설명 정보를 검색 하는 **속성** 창 호출 <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetDocumentation2%2A> 선택 되어 있는 속성에 대 한 원하는 지정 `lcid` 특성는 출력 문자열입니다. 내부적으로 <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2>이(가) `helpstringdll` 특성에 지정된 .dll 파일을 찾아서 지정된 컨텍스트 및 `lcid` 특성으로 이 .dll 파일에 대해 `DLLGetDocumentation`을(를) 호출합니다.

   `DLLGetDocumentation` 의 서명 및 구현:

```cpp
STDAPI DLLGetDocumentation
(
   ITypeLib * /* ptlib */,
   ITypeInfo * /* ptinfo */,
   LCID /* lcid */,
   DWORD dwCtx,
   BSTR * pbstrHelpString
);
```

 `DLLGetDocumentation` 함수는 DLL에 대한.def 파일에 정의된 내보내기여야 합니다.

 내부적으로 .olb 파일이 생성되는데 실제로 이것은 DLL입니다. 이 DLL에는 형식 라이브러리(.tlb) 파일 리소스 하나와 내보내기 함수 `DLLGetDocumentation`하나가 있습니다.

 .olb 파일의 경우 .tlb 파일 자체를 포함하는 것과 같은 파일이므로 `helpstringdll` 특성은 선택 사항입니다.

 따라서 **설명** 창에 문자열이 나타나도록 하려면 최소한 형식 라이브러리에서 `helpstring` 특성을 지정해야 합니다. 이러한 문자열을 지역화하려면 `helpstringdll` (선택 사항) 특성 및 `helpstringcontext` (필수) 특성을 지정하고 `DLLGetDocumentation`을(를) 구현해야 합니다.

 idl의 `helpstringcontext` 특성 및 `DLLGetDocumentation`을(를) 통해 지역화된 정보를 가져올 경우 추가 인터페이스를 구현할 필요가 없습니다.

 속성의 지역화된 이름 및 설명을 가져오는 또 하나의 방법은 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.GetLocalizedPropertyInfo%2A> 구현입니다. 이 방법으로 구현하는 자세한 내용은 [Properties Window Fields and Interfaces](../../extensibility/internals/properties-window-fields-and-interfaces.md)에서 참조하세요.

## <a name="see-also"></a>참고자료

- [속성 확장](../../extensibility/internals/extending-properties.md)