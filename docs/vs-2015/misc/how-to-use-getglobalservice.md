---
title: '방법: Getglobalservice | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- services, GetGlobalService
ms.assetid: 4cdf5ab5-9f09-4caf-9011-2dcb2c62f1b7
caps.latest.revision: 14
manager: jillfra
ms.openlocfilehash: 1c1fb48e4bb354ef403b39b0f1320ead92f43967
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62948184"
---
# <a name="how-to-use-getglobalservice"></a>방법: Use GetGlobalService
경우에 따라 도구 창에서 서비스 가져오기 또는 배치 되지 않습니다. 그러지 않으면 요소가 서비스를 알지 못하는 서비스 공급자를 사용 하 여 배치 된 컨테이너를 제어 해야 합니다. 예를 들어, 다음 컨트롤 내에서 활동 로그에 작성 하는 것이 좋습니다. 이러한 및 기타 시나리오에 대 한 자세한 내용은 참조 하세요. [방법: 서비스 문제 해결](../extensibility/how-to-troubleshoot-services.md)합니다.  
  
 대부분의 가져올 수 있습니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 정적 호출 하 여 서비스 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> 메서드.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> 파생 된 모든 VSPackage 처음으로 초기화 되는 캐시 된 서비스 공급자에 의존 <xref:Microsoft.VisualStudio.Shell.Package> 배치 됩니다. 이 조건이 충족 되 면 그렇지 않으면 null 서비스에 대 한 준비를 보장 해야 합니다.  
  
 다행 스럽게도 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> 대부분의 경우 올바르게 작동 합니다.  
  
- 다른 VSPackage에만 알려진 서비스를 제공 하는 VSPackage를 해당 서비스를 요청 하는 VSPackage는 VSPackage 서비스가 로드를 제공 하기 전에 배치 됩니다.  
  
- VSPackage에서 도구 창을 만들어지면 VSPackage는 도구 창이 생성 되기 전에 배치 됩니다.  
  
- 컨트롤 컨테이너는 VSPackage에서 만든 도구 창에서 호스트 되는 경우 VSPackage 컨트롤 컨테이너를 만들기 전에 배치 됩니다.  
  
### <a name="to-get-a-service-from-within-a-tool-window-or-control-container"></a>도구 창 또는 컨트롤 컨테이너 내에서 서비스를 가져오는  
  
- 생성자, 도구 창 또는 컨트롤 컨테이너에이 코드를 삽입 합니다.  
  
     [!code-csharp[UseGetGlobalService#1](../snippets/csharp/VS_Snippets_VSSDK/usegetglobalservice/cs/getglobalservicepackage.cs#1)]
     [!code-vb[UseGetGlobalService#1](../snippets/visualbasic/VS_Snippets_VSSDK/usegetglobalservice/vb/getglobalservicepackage.vb#1)]  
  
     이 코드는 SVsActivityLog 서비스를 가져오고 캐스팅을 <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> 인터페이스를 활동 로그에 쓰는 데 사용할 수 있습니다. 예는 [방법: 활동 로그를 사용 하 여](../extensibility/how-to-use-the-activity-log.md)입니다.  
  
## <a name="see-also"></a>참고 항목  
 [방법: 서비스 문제 해결](../extensibility/how-to-troubleshoot-services.md)   
 [사용 하 고 서비스를 제공 합니다.](../extensibility/using-and-providing-services.md)   
 [서비스 필수 항목](../extensibility/internals/service-essentials.md)