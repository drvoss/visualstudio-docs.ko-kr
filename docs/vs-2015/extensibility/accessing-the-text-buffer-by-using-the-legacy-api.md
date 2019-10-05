---
title: 레거시 API를 사용 하 여 텍스트 버퍼에 액세스 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text buffers
ms.assetid: cd6cf4ae-fff5-4e23-b293-7cbafdb8aed2
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f2cfbd84bc4f9298358a2a2d1ba87f76d6e5303c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68184990"
---
# <a name="accessing-the-text-buffer-by-using-the-legacy-api"></a>레거시 API를 사용하여 텍스트 버퍼에 액세스
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

텍스트는 텍스트 스트림 및 파일 유지 관리 하는 일을 담당 합니다. 버퍼 수를 읽거나 쓰려면 다른 형식이 있지만 버퍼를 사용 하 여 모든 일반 통신 유니코드를 사용 하 여 수행 됩니다. 레거시 Api에서 텍스트 버퍼 1 개 또는 2 차원 좌표 시스템을 하 여 버퍼의 문자 위치를 식별 합니다.  
  
## <a name="one--and-two-dimension-coordinate-systems"></a>1 및 2 차원 좌표 시스템  
 1 차원 좌표 위치 147 같은 버퍼의 첫 번째 문자에서는 문자 위치를 기반으로 합니다. 사용 된 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> 버퍼에서 1 차원 위치에 액세스 하는 인터페이스입니다. 2 차원 좌표계 선과 인덱스 쌍을 기반으로 합니다. 예를 들어 43 버퍼의 문자를 5 것 줄 43 줄에서 첫 번째 문자의 오른쪽에 다섯 개의 문자입니다. 사용 하 여 버퍼에서 2 차원 위치에 액세스 하는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> 인터페이스입니다. 모두를 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> 하며 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> 인터페이스 텍스트 버퍼 개체에 의해 구현 됩니다 (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>)를 사용 하 여 서로 액세스할 수 있습니다 `QueryInterface`합니다. 다음 다이어그램에서 이러한 및 기타 핵심 인터페이스에서는 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>합니다.  
  
 ![텍스트 버퍼 개체](../extensibility/media/vstextbuffer.gif "vsTextBuffer")  
텍스트 버퍼 개체  
  
 좌표계 중 하나는 작동 하지만 텍스트 버퍼에서 2 차원 좌표를 사용 하도록 최적화 되었습니다. 1 차원 좌표계 성능 오버 헤드를 만들 수 있습니다. 따라서 가능한 한 2 차원 좌표 시스템을 사용 합니다.  
  
 텍스트 버퍼의 두 번째 책임에는 파일 지 속성입니다. 이렇게 하려면 텍스트 버퍼 개체는 다음과 같이 구현 됩니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> 및 프로젝트 항목에 대 한 문서 데이터 개체 구성 요소 및 기타 환경 구성 요소를 지 속성에 관련 된 역할을 합니다. 자세한 내용은 [열기 및 프로젝트 항목 저장](../extensibility/internals/opening-and-saving-project-items.md)합니다.  
  
## <a name="in-this-section"></a>섹션 내용  
 [레거시 API를 사용하여 보기 설정 변경](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 기존 API를 사용 하 여 보기 설정을 변경 하는 방법에 설명 합니다.  
  
 [텍스트 관리자를 사용하여 글로벌 설정 모니터링](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 전역 설정을 모니터링 하는 텍스트 관리자를 사용 하는 방법에 설명...  
  
## <a name="see-also"></a>관련 항목  
 [핵심 편집기 내부](../extensibility/inside-the-core-editor.md)
