---
title: 소스 제어 패키지 모델 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], model
ms.assetid: 6164b2d3-a622-4de8-bef3-a6de985e9ebd
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 811cdfa2cbae85d6509e7cd883c5675b81639fa0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68198429"
---
# <a name="model-for-source-control-packages"></a>소스 제어 패키지 모델
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

다음 모델은 원본 제어 구현 예를 나타냅니다. 모델에서 구현 해야 하는 인터페이스 및 환경 서비스를 호출 해야 하는 것이 표시 됩니다. 모든 서비스와 마찬가지로 실제로 서비스를 통해 가져와야 하는 특정 인터페이스의 메서드를 호출 합니다. 클래스의 이름은 쉽게 소스 제어를 수행 하는 방법을 확인할 수 있도록 식별 됩니다.  
  
 ![SCC&#95;TUP 예제](../../extensibility/internals/media/scc-tup.gif "SCC_TUP")  
예제에서는 소스 제어 프로젝트  
  
## <a name="interfaces"></a>인터페이스  
 다음 표에 표시 된 인터페이스 목록을 사용 하 여 Visual Studio에서 새 프로젝트 형식에 대 한 소스 제어를 구현할 수 있습니다.  
  
|인터페이스|사용|  
|---------------|---------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|프로젝트 및 변경 (더티) 파일 하거나 저장 하기 전에 편집기에서 호출 됩니다. 이 인터페이스를 사용 하 여 액세스를 <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> 서비스입니다.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|추가, 제거 또는 파일 또는 디렉터리의 이름을 바꿀 수 있는 권한 요청 하는 프로젝트에서 호출 됩니다. 승인 된 추가, 제거 또는 작업의 이름을 바꿀 때 환경은 완료를 알리기 위해 프로젝트에서이 인터페이스를 사용 하는 것이 라고도 합니다. 사용 하 여 액세스 하는 데는 것은 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments> 서비스입니다.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|프로젝트 추가 하거나 이름을 바꾸거나, 파일 또는 디렉터리를 제거 하는 경우 알림을 받으려면 등록 하는 모든 엔터티에 의해 구현 됩니다. 을 이벤트 알림에 등록 하려면 호출 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>합니다.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|소스 제어 패키지를 사용 하 여 등록 하 고 소스 제어 상태에 대 한 정보를 가져오려면 프로젝트에서 호출 됩니다. 이 인터페이스를 사용 하 여 액세스를 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> 서비스입니다.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|소스 제어 설정을 프로젝트 파일에 필요한 가져올 프로젝트 파일에 대 한 정보에 대 한 원본 제어 요청에 응답 하 여 구현 합니다.|  
  
## <a name="see-also"></a>참고 항목  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>   
 [소스 제어 지원](../../extensibility/internals/supporting-source-control.md)
