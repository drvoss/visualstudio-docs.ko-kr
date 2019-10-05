---
title: VisibilityItem 요소 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- VisibilityItem element (VSCT XML schema)
- VSCT XML schema elements, VisibilityItem
ms.assetid: 0932f551-972d-4194-84bb-426e3e4375e4
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f6f71e145282d1d6e340060b9798ca54c9af9f4e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62584839"
---
# <a name="visibilityitem-element"></a>VisibilityItem 요소
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`VisibilityItem` 요소 도구 모음 및 명령 정적 표시 여부를 결정 합니다. 모든 항목에는 명령 또는 메뉴 및 연결 된 명령 UI 컨텍스트를 식별합니다. Visual Studio 명령, 메뉴 및 도구 모음 및 표시 여부를 정의 하는 Vspackage를 로드 하지 않고 검색 합니다. IDE를 사용 하 여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> 명령 UI 컨텍스트의 활성 상태 인지 여부를 결정 하는 방법.  
  
 Visual Studio에서는 명령 표시는 VSPackage에서 결정 해야 하는 VSPackage가 로드 한 후 보다는 `VisibilityItem`합니다. 명령의 표시 여부를 확인 하려면 하거나 구현할 수 있습니다 합니다 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> 이벤트 처리기 또는 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 명령을 구현 하는 방법에 따라 메서드.  
  
 명령 또는 있는 메뉴를 `VisibilityItem` 요소가 연결 된 컨텍스트 활성화 되 면에 표시 됩니다. 각 명령 컨텍스트부터 조합에 대 한 진입점을 포함 하 여 하나 이상의 명령 UI 컨텍스트를 사용 하 여 단일 명령, 메뉴 또는 도구 모음을 연결할 수 있습니다. 명령 또는 메뉴와 연결 된 여러 명령 UI 컨텍스트 명령 또는 메뉴 경우 표시 하는 연결 된 명령 UI 컨텍스트 중 하나가 활성화 된 경우.  
  
 `VisibilityItem` 요소 명령, 메뉴 및 도구 모음, 그룹 필요가만 적용 됩니다. 관련 되지 않은 요소 `VisibilityItem` 요소는 부모 메뉴 활성화 될 때마다 표시 됩니다.  
  
## <a name="syntax"></a>구문  
  
```  
<VisibilityItem  
  guid ="="cmdGuidMyProductCommands"  
  id=="cmdidAddWidget"  
  context="guidNotViewSourceMode"/>  
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  
  
|특성|설명|  
|---------------|-----------------|  
|guid|필수 요소. GUID/i D 명령 식별자의 GUID입니다.|  
|ID|필수 요소. ID의 GUID/i D 명령 식별자입니다.|  
|컨텍스트(context)|필수 요소. 이 명령은 표시 되는 UI 컨텍스트.|  
|조건|선택 사항입니다. 참조 [조건부 특성](../extensibility/vsct-xml-schema-conditional-attributes.md)합니다.|  
  
### <a name="child-elements"></a>자식 요소  
 없음  
  
### <a name="parent-elements"></a>부모 요소  
  
|요소|설명|  
|-------------|-----------------|  
|[VisibilityConstraints 요소](../extensibility/visibilityconstraints-element.md)|`VisibilityConstraints` 요소 도구 모음 및 명령 그룹의 정적 표시 여부를 결정 합니다.|  
  
## <a name="remarks"></a>설명  
 에 정의 된 표준 Visual Studio UI 컨텍스트는 *Visual Studio SDK 설치 경로*\VisualStudioIntegration\Common\Inc\vsshlids.h 파일도 에서처럼 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids> 및 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> 클래스입니다. UI 컨텍스트의 전체 집합에 정의 되어는 <xref:Microsoft.VisualStudio.VSConstants> 클래스입니다.  
  
## <a name="example"></a>예제  
  
```  
<VisibilityConstraints>  
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"  
    context="guidNotViewSourceMode"/>  
</VisibilityConstraints>  
```  
  
## <a name="see-also"></a>참고 항목  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>   
 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus>   
 <xref:Microsoft.VisualStudio.VSConstants>   
 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids>   
 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>   
 [VisibilityConstraints 요소](../extensibility/visibilityconstraints-element.md)   
 [Visual Studio 명령 테이블(.Vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
