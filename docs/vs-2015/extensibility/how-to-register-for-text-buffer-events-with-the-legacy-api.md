---
title: '방법: 레거시 API 사용 하 여 텍스트 버퍼 이벤트에 대 한 등록 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - register for text buffer events
ms.assetid: 5fc00ced-882c-4b48-b46c-1fa5a2469f94
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5f36e8dd780788d241e3c286b1bbbe581311b143
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68204091"
---
# <a name="how-to-register-for-text-buffer-events-with-the-legacy-api"></a>방법: 레거시 API를 사용하여 텍스트 버퍼 이벤트에 등록
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

기존 API를 사용 하 여 텍스트 버퍼를 액세스 하는 경우 다음 절차에 표시 된 대로 텍스트 버퍼 이벤트에 등록 해야 합니다.  
  
### <a name="to-advise-text-buffer-events"></a>텍스트 버퍼 이벤트를 알리기 위해  
  
1. 인터페이스 중 하나에 대 한 포인터에서 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>, 호출 `QueryInterface` 에 대 한 포인터에 대 한 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>합니다.  
  
2. 호출 된 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer.FindConnectionPoint%2A> 메서드를 등록 하려는 이벤트의 인터페이스 ID 전달 합니다.  
  
     예를 들어, 등록 하려는 경우 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>, 다음 인터페이스 ID의 IID_IVsTextLinesEvents을 전달 합니다.  
  
     텍스트 버퍼에 대 한 포인터를 반환 합니다 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> 적절 한 연결 지점 개체에 대 한 인터페이스입니다.  
  
3. 호출이 포인터를 사용 하는 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A> 메서드를 등록 하려면, 예를 들어 이벤트 인터페이스의 구현에 대 한 포인터를 전달 합니다 `IVsTextLinesEvents` 인터페이스.  
  
     환경을 호출 하 여 이벤트를 수신 대기를 중지 한 다음 사용할 수 있는 쿠키도 반환 된 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Unadvise%2A> 메서드.  
  
## <a name="see-also"></a>참고 항목  
 [레거시 API의 텍스트 버퍼 이벤트](../extensibility/text-buffer-events-in-the-legacy-api.md)
