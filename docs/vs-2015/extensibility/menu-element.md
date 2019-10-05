---
title: Menu 요소 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Menus
- Menus element (VSCT XML schema)
ms.assetid: ce0560f3-b4c9-4ab2-a99c-d4e10f37b9e0
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 79a8fafc748274015dac7f8f0938bba37ba5a8bc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68194346"
---
# <a name="menu-element"></a>Menu 요소
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

하나의 메뉴 항목을 정의합니다. 다음은 6 유형의 메뉴입니다. 상황에 맞는, 메뉴, MenuController, MenuControllerLatched, 도구 모음 및 ToolWindowToolbar 합니다.  
  
## <a name="syntax"></a>구문  
  
```  
<Menu guid=”guidMyCommandSet” id=”MyCommand” priority=”0x100” type=”button”>  
  <Parent>... </Parent>  
  <CommandFlag>... </CommandFlag>  
  <Strings>... </Strings>  
</Menu>  
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  
  
|특성|Description|  
|---------------|-----------------|  
|guid|필수 요소. GUID/i D 명령 식별자의 GUID입니다.|  
|id|필수 요소. GUID/i D 명령 식별자의 ID입니다.|  
|priority|선택 사항입니다. 그룹 메뉴의 메뉴의 상대 위치를 지정 하는 숫자 값입니다.|  
|ToolbarPriorityInBand|선택 사항입니다. 창 도킹 되 면 밴드에서 도구 모음의 상대 위치를 지정 하는 숫자 값입니다.|  
|type|선택 사항입니다. 요소의 종류를 지정 하는 열거형된 값입니다.<br /><br /> 없는 경우 기본 형식은 메뉴입니다.<br /><br /> 컨텍스트<br /> 클릭할 때 창이 표시 되는 바로 가기 메뉴입니다. 바로 가기 메뉴에는 다음과 같은 특징이 있습니다.<br /><br /> -메뉴 바로 가기 메뉴로 표시 될 때 부모 및 우선 순위 필드를 사용 하지 않습니다.<br />-하위 메뉴 및 바로 가기 메뉴도 사용할 수 있습니다. 이 경우 그룹 ID와 우선 순위 필드 적용 됩니다.<br />-항상 사용할 수 없습니다.<br /><br /> 바로 가기 메뉴에는 다음 조건이 true 인 경우에 표시 됩니다.<br /><br /> 호스팅하는-창이 표시 됩니다.<br />VSPackage에서-마우스 처리기 검색 창에서를 마우스 오른쪽 단추로 클릭 하 고 명령을 처리 하는 메서드를 호출 합니다.<br />-바로 가기 메뉴를 호출 하 여 표시 되는 <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager.ShowContextMenu%2A> 메서드 (권장) 또는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A> 메서드.<br /><br /> 메뉴<br /> 드롭다운 메뉴를 제공합니다. 드롭다운 메뉴에는 다음과 같은 특징이 있습니다.<br /><br /> -해당 정의에서 부모를 따릅니다.<br />-부모 그룹 또는 그룹에 CommandPlacement 있어야 합니다.<br />-메뉴의 다른 모든 종류의 하위 메뉴 수 있습니다.<br />-부모 메뉴에 표시 될 때마다 자동으로 표시 됩니다.<br />-하지 않아도 표시 되도록 하는 코드를 VSPackage 구현 됩니다.<br /><br /> MenuController<br /> 도구 모음에서 일반적으로 사용 되는 분할 단추 드롭다운 메뉴를 제공 합니다. MenuController 메뉴에는 다음과 같은 특징이 있습니다.<br /><br /> -부모 또는 CommandPlacement를 통해 다른 메뉴에 포함 되어야 합니다.<br />-해당 정의에서 부모를 따릅니다.<br />-있습니다 어떤 유형의 메뉴 부모로.<br />-자동으로 제공 될 때마다 수행 부모 메뉴에 표시 됩니다.<br />-하지 않아도 표시 되는 메뉴 수 있도록 프로그래밍 방식으로 지원 됩니다.<br /><br /> 분할 단추 메뉴에서 명령은 메뉴 단추에 표시 됩니다. 표시 된 명령에 다음 특성 중 하나:<br /><br /> 마지막 명령은 명령을 계속 표시 되 고 사용 하도록 설정 하는 경우 사용 된 경우-<br />-표시 된 첫 번째 명령은 것입니다.<br /><br /> MenuControllerLatched<br /> 명령을 지정할 수 있습니다 기본으로 선택 래치으로 명령을 표시 하 여 분할 단추 드롭다운 메뉴를 제공 합니다.<br /><br /> 래치 명령에 확인 표시를 표시 하 여 일반적으로 선택으로 메뉴에 표시 된 명령이입니다. 명령이 래치는 OLECMDF_LATCHED 있을 경우 처럼 표시 될 수 있습니다 플래그의 구현에서이 설정에는 `QueryStatus` 메서드를 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 인터페이스. MenuControllerLatched 메뉴에는 다음과 같은 특징이 있습니다.<br /><br /> -부모 그룹 또는 CommandPlacement를 통해 다른 메뉴에 포함 되어야 합니다.<br />-해당 정의에서 부모를 따릅니다.<br />-있습니다 어떤 유형의 메뉴 부모로.<br />-부모 메뉴에 표시 될 때마다 가능 합니다.<br />-하지 않아도 표시 되는 메뉴 수 있도록 프로그래밍 방식으로 지원 됩니다.<br /><br /> 분할 단추 메뉴에서 명령은 메뉴 단추에 표시 됩니다. 표시 된 명령에 다음 특성 중 하나:<br /><br /> -됩니다는 첫 번째 명령에 표시 된 것입니다.<br />-표시 된 첫 번째 명령은 것입니다.<br /><br /> 도구 모음<br /> 도구 모음을 제공 합니다. 도구 모음에는 다음과 같은 특징이 있습니다.<br /><br /> -해당 정의에서 부모를 무시합니다.<br />-CommandPlacement를 사용 하 여도 모든 그룹의 하위를 만들 수 없습니다.<br />-를 항상를 클릭 하 여 표시할 **도구 모음** 에 **보기** 메뉴.<br />-를 사용 하 여 표시할를 [VisibilityItem](../extensibility/visibilityitem-element.md)합니다.<br />-모든 코드를 만들 필요가 없습니다. 도구 모음을 만드는 방법에 대 한 예제를 보려면 [도구 모음 추가](../extensibility/adding-a-toolbar.md)합니다.<br /><br /> ToolWindowToolbar<br /> 도구 모음 개발 환경에 연결 된 것 처럼 특정 도구 창에 연결 된 도구 모음을 제공 합니다.<br /><br /> -해당 정의에서 부모를 무시합니다.<br />-CommandPlacement를 사용 하 여도 모든 그룹의 하위를 만들 수 없습니다.<br />-도구 창 도구 모음을 호스팅하는 표시 되 고 VSPackage에서 도구 창으로이 도구 모음을 명시적으로 추가 하는 경우에 표시 합니다. 도구 모음 호스트 속성을 확보 하 여 도구 창을 만들 때 일반적으로 이루어집니다 (나타낸 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost> 인터페이스) 도구 창 프레임에서 호출을 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost.AddToolbar%2A> 메서드.|  
|조건|선택 사항입니다. 참조 [조건부 특성](../extensibility/vsct-xml-schema-conditional-attributes.md)합니다.|  
  
### <a name="child-elements"></a>자식 요소  
  
|요소|Description|  
|-------------|-----------------|  
|부모|선택 사항입니다. 메뉴 항목의 부모 요소입니다.|  
|CommandFlag|필수 요소. 참조 [Flag 요소 명령을](../extensibility/command-flag-element.md)합니다. 메뉴에 대해 유효한 CommandFlag 값은 다음과 같습니다.<br /><br /> -   **AlwaysCreate**<br />-   **DefaultDocked**<br />-   **DefaultInvisible** -이 플래그는 도구 모음 표시에 영향을 주지 않습니다.<br />-   **DontCache**<br />-   **DynamicVisibility** -이 플래그는 도구 모음 표시에 영향을 주지 않습니다.<br />-   **IconAndText**<br />-   **NoCustomize**<br />-   **NotInTBList**<br />-   **NoToolbarClose**<br />-   **TextChanges**<br />-   **TextIsAnchorCommand**|  
|문자열|필수 요소. 참조 [요소를 문자열](../extensibility/strings-element.md)합니다. 자식 `ButtonText` 요소를 정의 해야 합니다.|  
|Annotation|선택적 설명입니다.|  
  
### <a name="parent-elements"></a>부모 요소  
  
|요소|Description|  
|-------------|-----------------|  
|[Menus 요소](../extensibility/menus-element.md)|VSPackage를 구현 하는 모든 메뉴를 정의 합니다.|  
  
## <a name="example"></a>예제  
  
```  
<Menu guid="cmdGuidWidgetCommands" id="menuIDEditWidget"  
  priority="0x0002" type="Menu">  
  <Parent guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit">  
    <CommandFlag>AlwaysCreate</CommandFlag>  
    <Strings>  
      <ButtonText>Edit Widget</ButtonText>  
    </Strings>  
    </Parent>  
</Menu>  
```  
  
## <a name="see-also"></a>관련 항목  
 [Visual Studio 명령 테이블(.Vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)