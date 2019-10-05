---
title: 프로젝트 시스템에 웹 서비스 추가 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- project systems, adding Web services
- Web services, adding to VSPackage project systems
ms.assetid: 8efa078b-68b2-45a2-9be2-44f807bc0d7f
caps.latest.revision: 8
manager: jillfra
ms.openlocfilehash: f5b192be8e5f68ad9314fe08fff963c032013cb0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63002659"
---
# <a name="adding-web-services-to-project-systems"></a>프로젝트 시스템에 웹 서비스 추가
XML Web services는 일반적으로 SOAP (Simple Object Access Protocol) 프로토콜을 사용 하 여 프로젝트 시스템에 프로그래밍 방식으로 정보를 반환 하는 URL 주소 지정 가능 리소스입니다. 웹 서비스를 사용 하 여 VSPackage 프로젝트 시스템에 통합할 수 있습니다는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddProjectItemDlg2> 인터페이스입니다.  
  
### <a name="to-add-a-web-service-to-your-project-system"></a>프로젝트 시스템에 웹 서비스를 추가 하려면  
  
1. 호출 `QueryService` 에 대 한 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddProjectItemDlg2> 인터페이스를 통해 <xref:Microsoft.VisualStudio.Shell.Interop.SVsAddWebReferenceDlg> 서비스입니다.  
  
2. <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2.AddWebReferenceDlg%2A> 메서드를 호출합니다. 에 전달 하는 경우 `pDiscoverySession` 매개 변수에 `NULL`, 검색 세션을 생성 되 고 후속 사용에 사용할 수 있도록 세션 캐시 되는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2> 인터페이스입니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2.AddWebReferenceDlg%2A> 에 대 한 포인터를 반환 하는 메서드 <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult2>합니다.  
  
3. <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult.AddWebReference%2A> 메서드를 호출합니다. 웹 서비스 참조 폴더에 대 한 자동화 개체를 전달 합니다 `pUnkWebReferenceFolder` 매개 변수입니다. Visual Studio 환경 이미 웹 서비스가 있는지 확인 합니다. 웹 서비스가 없으면 환경 다운로드 하 고 웹 서비스 폴더 및 폴더의 자식 노드로 추가 파일 (예:.wsdl 파일)를 추가 합니다.  
  
## <a name="see-also"></a>참고 항목  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoverySession>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDiscoveryService>