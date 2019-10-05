---
title: 사용자 지정 속성 창 제공 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- property browsers, providing
- Properties window, providing your own
ms.assetid: 408dcdef-8ef9-4644-97d2-f311cd35824f
caps.latest.revision: 12
manager: jillfra
ms.openlocfilehash: a244463832ff5620efa74a2c7fd20d6d47d79e76
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62810706"
---
# <a name="providing-a-custom-properties-window"></a>사용자 지정 속성 창 제공
직접 제공할 수 있기 **속성** 창을 확장 하는 대신 지정 된 프로젝트 시스템에 대 한 합니다 **속성** 에서 제공 하는 창은 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 통합된 개발 환경 (IDE)입니다. 가장 자주 발생 한 시나리오에는 구현 하는 경우 직접 창 프레임에 배치 하는 개체입니다.  
  
 다양 한 방법으로 액세스 하는 이벤트에 창 프레임에 배치 하는 개체를 구현 하지 않는 해도 다른 방법에 대 한 액세스 권한이 여전히는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> 이 페이지의 마지막 절차에 나열 된 인터페이스입니다.  
  
### <a name="to-provide-your-properties-window"></a>속성 창 제공  
  
1. 나타내는 GUID를 정의 하 **속성** 창 구현 합니다.  
  
2. 프로그램 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> 구현을 사용 하 여를 <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> 서비스를 제공 하 **속성** 서비스로 Visual Studio 환경에는 창.  
  
### <a name="to-call-your-properties-window"></a>속성 창에 호출  
  
1. <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane.SetSite%2A> 메서드를 호출합니다.  
  
2. `QueryService` 에 대 한 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> 에서 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> 에 전달 된 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane.SetSite%2A> 메서드.  
  
3. 가져올 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> 에서 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> 서비스입니다.  
  
4. 호출 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A> 로 설정 하는 첫 번째 매개 변수를 사용 하 여 `SEID_PropertyBrowserSID` (에서 가져온 합니다 <xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID> 열거형), 및 세 번째 매개 변수를 `varValue`를 나타내는 GUID의 문자열 형식 나타내는 **속성** 창입니다. 첫 번째 생성 시이 호출을 한 번만 수행 하 **속성** 창 문서 창입니다. 호출 후 이렇게 **속성** 창은 창 프레임을 사용 하 여 연결 합니다.  
  
### <a name="to-obtain-the-window-frame-object-when-you-are-not-the-implementer"></a>구현 자가 없는 경우 창 프레임 개체를 가져오려면  
  
- 할 수 있습니다 `QueryService` 에 대 한 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> 서비스 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> 매개 변수를 사용 하 여 `propid` 로 <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>합니다.  
  
- 호출 하 여 활성 문서 창이 가져올 수 있습니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A> SVsMonitorSelection 서비스를 통해. 매개 변수를 설정 `elementid` 하 `SEID_WindowFrame`에서 가져온는 <xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID> 열거형입니다.  
  
## <a name="see-also"></a>참고 항목  
 [확장 속성](../extensibility/internals/extending-properties.md)   
 [속성 창 필드 및 인터페이스](../extensibility/internals/properties-window-fields-and-interfaces.md)