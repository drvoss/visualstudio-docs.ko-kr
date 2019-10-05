---
title: 텍스트 마커를 사용 하 여 레거시 API를 사용 하 여 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text markers
ms.assetid: 937a0b19-1216-45d5-a7ad-4fe1d6f73097
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3dff5e6ecf60d389730841e99b87db584465e020
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65695471"
---
# <a name="using-text-markers-with-the-legacy-api"></a>텍스트 마커를 사용 하 여 레거시 API를 사용 하 여
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

텍스트 마커 부동 표시에 영향을 줄 수 있는 버퍼의 텍스트 범위 및 텍스트 영역의 동작은 합니다. 표식은 중단점, 책갈피, 물결 무늬 밑줄 및 읽기 전용 영역을 포함 합니다. 텍스트 마커 구문 색 지정 기본적으로 다릅니다. 구문 색 지정은 텍스트 영역을 사용 하 여 연결 된 언어 구문의 통신 하는 빠른 방법은 합니다. 속도가 중요 한 Windows 화면에는 연결 하는 경우에 일반적으로 구문 색 지정 요청 됩니다. 구문 색 지정만 텍스트의 색을 변경합니다. 텍스트 마커는 다른 여러 텍스트 속성을 변경할 수 있습니다. 텍스트 마커 "float"를 업데이트 하 고 특별 한 동작을 적용할 수의 색을 지정 합니다.  
  
 텍스트 마커를 사용 하 여 연결 된 성능 오버 헤드 때문에 텍스트 버퍼에 대 한 많은 표식을 만들지 마십시오. 각 표식에는 사용자 편집 하는 버퍼의 내용이 될 때마다 업데이트 됩니다.  
  
> [!NOTE]
> 사용자 표시 표식 유형을 하지만 하지 해당 모양과 스타일의 색을 변경할 수 있습니다. 자세한 내용은 [글꼴 및 색, 환경, 옵션 대화 상자](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)합니다.  
  
## <a name="related-topics"></a>관련 항목  
  
|제목|설명|  
|-----------|-----------------|  
|[방법: 표준 텍스트 표식 추가](../extensibility/how-to-add-standard-text-markers.md)|제공한 표준 텍스트 표식 유형을 추가 하는 방법에 설명 합니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 코어 편집기 텍스트 뷰를 합니다.|  
|[방법: 오류 표식 구현](../extensibility/how-to-implement-error-markers.md)|인스턴스를 구현 하는 방법에 설명 합니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 빨간색 물결 무늬 밑줄을 사용 하 여 오류를 나타내는 데 사용 되는 표식입니다.|  
|[방법: 사용자 지정 텍스트 표식 만들기](../extensibility/how-to-create-custom-text-markers.md)|만들고 텍스트 보기에 사용자 지정 텍스트 표식 유형을 추가 하는 방법을 설명 합니다.|  
|[방법: 텍스트 표식 사용](../extensibility/how-to-use-text-markers.md)|텍스트 마커를 추가 하는 방법에 설명 합니다.|  
|[핵심 편집기 내부](../extensibility/inside-the-core-editor.md)|핵심 편집기의 기능을 설명 하 고 핵심 편집기 사용자 지정 하는 방법에 대 한 세부 정보를 제공 합니다.|  
|[편집기 기능](https://msdn.microsoft.com/bdac940d-1f14-4019-a01f-fd0bb3dc7198)|사용할 수 있는 기능에 설명 합니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 핵심 편집기입니다.|  
  
## <a name="reference"></a>참조  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>  
 편집기에서 미리 정의 된 vspackage 등록 되어 있는지 여부는 특정 텍스트 표식 유형에 대 한 정보를 얻기 위한 균일 한 메커니즘을 제공 합니다.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLineMarker>  
 에 대 한 액세스를 제공 하 고 2 차원 좌표를 사용 하 여 텍스트 마커를 텍스트 버퍼의 위치를 조정 합니다.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker>  
 텍스트 마커를 관리 하기 위한 메서드를 제공 합니다.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>  
 에 대 한 콜백을 제공 된 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE 및 텍스트 마커를 조정 하는 데 사용 되는 다른 프로세스입니다.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced>  
 통해 사용할 수 있는 기능을 확장 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> 추가 콜백을 제공 하 여 인터페이스입니다.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx>  
 통해 사용할 수 있는 기능을 확장 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> 추가 콜백을 제공 하 여 인터페이스입니다.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerColorSet>  
 표식 유형을 다른 표식 유형을 색의 동일한 집합을 공유 하는지 여부를 결정할 수 있습니다.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>  
 핵심 편집기에서 텍스트 표식에 대 한 컨텍스트를 제공합니다. 핵심 편집기에 있는 각 텍스트 표식 유형에 대해 IDE는 별도 만듭니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> 개체입니다.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerGlyphDropHandler>  
 해당 문자 모양 끌어서 놓기 편집이 지원 되는 표식에 대 한 제공 되는 처리기입니다. 문자 모양 아이콘 표식 위치를 나타내는 경우  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>  
 반환 된 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType> 텍스트 마커 다른 Vspackage 제공 하는 서비스에서 인터페이스.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamMarker>  
 에 대 한 액세스를 제공 하 고 1 차원 좌표를 사용 하 여 텍스트 마커를 텍스트 버퍼의 위치를 조정 합니다. 가능한 경우에이 인터페이스를 사용 하지 마십시오.
