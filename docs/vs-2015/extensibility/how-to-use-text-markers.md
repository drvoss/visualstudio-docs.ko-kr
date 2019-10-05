---
title: '방법: 텍스트 마커를 사용 하 여 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - using text markers
ms.assetid: 76eed51c-eecb-4579-823e-13df2f0526b9
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 25c3c4f3a3d9a253b9ec671892d0d44ccf9ca3ab
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63430957"
---
# <a name="how-to-use-text-markers"></a>방법: 텍스트 마커를 사용 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

텍스트 마커를 편집 하려면 적용할 수는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> 개체입니다.  
  
## <a name="procedures"></a>절차  
  
#### <a name="to-apply-text-markers"></a>텍스트 마커를 적용 하려면  
  
1. 인스턴스는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> 클래스입니다.  
  
    > [!NOTE]
    > 핵심 편집기를 편집 하는 모든 문서에 표준 텍스트 마커를 자동으로 적용 하 고 표준 텍스트 마커를 명시적으로 적용할 필요는 없습니다.  
  
2. 호출 하 여 관심 있는 표식의 표식 유형 ID를 가져올는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A> 메서드는 `GUID` 사용 하려는 텍스트 마커의 합니다.  
  
    > [!NOTE]
    > 사용 하지 마십시오는 `GUID` VSPackage 또는 텍스트 마커를 제공 하는 서비스입니다.  
  
3. 사용 하 여 호출 하 여 표식 유형 ID를 가져올는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A> 메서드 호출에 매개 변수로 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> 메서드 또는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> 텍스트 마커를 텍스트의 지정된 된 지역에 적용 하는 방법.  
  
#### <a name="to-add-features-to-text-markers"></a>텍스트 표식에 기능을 추가 하려면  
  
1. 특수 한 상황에 대 한 도구 팁, 특별 한 상황에 맞는 메뉴 또는 처리기와 같은 텍스트 표식, 추가 기능을 추가 하는 것이 바람직 수도 있습니다. 이를 수행하려면:  
  
2. 구현 하는 개체 만들기는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> 인터페이스입니다.  
  
3. 추가 기능을 원하는 경우 구현 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx>, 및 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced> 인터페이스를 구현 하는 동일한 개체에는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> 인터페이스.  
  
4. 전달 된 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> 인터페이스에 대 한 호출으로 만든를 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> 메서드 또는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> 텍스트 마커를 텍스트의 지정된 된 지역에 적용 하는 데 사용 되는 메서드.  
  
5. 상황에 맞는 메뉴 지원 텍스트 표식 영역에 추가 하는 경우 메뉴를 만드는 데 필요한 것입니다.  
  
     상황에 맞는 메뉴 참조를 만드는 방법에 대 한 자세한 내용은 [상황에 맞는 메뉴](../extensibility/context-menus.md)합니다.  
  
6. 합니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 환경 같은 제공 된 인터페이스의 메서드를 호출 하는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetTipText%2A> 메서드를 또는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A> 필요에 따라 메서드.  
  
## <a name="see-also"></a>참고 항목  
 [텍스트 마커를 사용 하 여 레거시 API를 사용 하 여](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [방법: 표준 텍스트 마커를 추가 합니다.](../extensibility/how-to-add-standard-text-markers.md)   
 [방법: 사용자 지정 텍스트 표식 만들기](../extensibility/how-to-create-custom-text-markers.md)   
 [방법: 오류 표식 구현](../extensibility/how-to-implement-error-markers.md)
