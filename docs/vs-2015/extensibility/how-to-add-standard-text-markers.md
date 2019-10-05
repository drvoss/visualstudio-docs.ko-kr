---
title: '방법: 표준 텍스트 마커를 추가 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - standard text markers
ms.assetid: a39fca69-0014-474c-933f-51f0e9b9617e
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 912d5d7a225520fc825d832bf73f5cfc733a9486
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436014"
---
# <a name="how-to-add-standard-text-markers"></a>방법: 표준 텍스트 마커를 추가 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

와 함께 제공 되는 기본 텍스트 표식 유형 중 하나를 만들려면 다음 절차는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 핵심 편집기입니다.  
  
### <a name="to-create-a-text-marker"></a>텍스트 마커를 만들려면  
  
1. 하나 또는 두-차원 좌표계, 호출을 사용 중인지 여부에 따라 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> 메서드 또는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> 새 텍스트 마커를 만드는 방법.  
  
     이 메서드 호출에서 표식 유형을, 표식, 만들려는 텍스트 범위를 지정 및 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> 인터페이스입니다. 그런 다음이 메서드는 새로 만든된 텍스트 표식에 대 한 포인터를 반환합니다. 가져온 표식 유형에 <xref:Microsoft.VisualStudio.TextManager.Interop.MARKERTYPE> 열거형입니다. 지정 된 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> 표식 이벤트를 수신 하려면 인터페이스입니다.  
  
    > [!NOTE]
    > 주 스레드에서 UI만 텍스트 마커를 만듭니다. 텍스트 마커를 만들려면 텍스트 버퍼의 내용을 의존 하는 핵심 편집기 및 텍스트 버퍼를 스레드로부터 안전 하지 않습니다.  
  
## <a name="adding-a-custom-command"></a>사용자 지정 명령 추가  
 구현 된 `IVsTextMarkerClient` 인터페이스에 포인터를 표식에서 제공 하 고 여러 가지 방법으로 표식 동작을 향상 시킵니다. 첫째, 따라서 사용자 표식에 대 한 팁을 제공 하 고 명령을 실행할 수 있습니다. 또한 따라서 개별 표식에 대 한 이벤트 알림을 수신 하 고 표식을 통해 사용자 지정 상황에 맞는 메뉴를 만들 수 있습니다. 마커 상황에 맞는 메뉴에는 사용자 지정 명령을 추가 하려면 다음 절차를 따르십시오.  
  
#### <a name="to-add-a-custom-command-to-the-context-menu"></a>상황에 맞는 메뉴에는 사용자 지정 명령을 추가 하려면  
  
1. 환경을 호출 하는 상황에 맞는 메뉴 표시 되기 전에 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetMarkerCommandInfo%2A> 메서드 및 전달 하면 텍스트 표식에 대 한 포인터에 영향을 받는 상황에 맞는 메뉴에서 명령 항목의 수입니다.  
  
     상황에 맞는 메뉴의 중단점 별 명령을 포함 하는 예를 들어 **중단점 제거** 를 통해 **새 중단점**다음 스크린샷에 표시 된 대로 합니다.  
  
     ![마커 상황에 맞는 메뉴](../extensibility/media/vsmarkercontextmenu.gif "vsMarkercontextmenu")  
  
2. 사용자 지정 명령 이름을 식별 하는 일부 텍스트를 다시 전달 합니다. 예를 들어 **중단점 제거** 환경을 제공 하지 않았습니다 이미 해당 하는 경우에 사용자 지정 명령을 수 있습니다. 또한 전달 하면 지원 되는, 사용 가능한 및 활성화 되 면 명령 인지 및/또는 켜기 / 끄기 전환 합니다. 이 정보를 사용 하 여 올바른 방법으로 사용자 지정 명령 상황에 맞는 메뉴에 표시할 환경입니다.  
  
3. 환경에서 명령을 실행할 수는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A> 메서드를 텍스트 마커 및 상황에 맞는 메뉴에서 선택한 명령 수에 대 한 포인터를 전달 합니다.  
  
     이 호출에서이 정보를 사용 하 여 사용자 지정 명령을 결정 하는 텍스트 마커의 모든 작업을 실행 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [텍스트 마커를 사용 하 여 레거시 API를 사용 하 여](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [방법: 오류 마커를 구현 합니다.](../extensibility/how-to-implement-error-markers.md)   
 [방법: 사용자 지정 텍스트 표식 만들기](../extensibility/how-to-create-custom-text-markers.md)   
 [방법: 텍스트 표식 사용](../extensibility/how-to-use-text-markers.md)
