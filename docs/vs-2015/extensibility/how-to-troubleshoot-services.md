---
title: '방법: 서비스 문제 해결 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: troubleshooting
helpviewer_keywords:
- services, troubleshooting
ms.assetid: 001551da-4847-4f59-a0b2-fcd327d7f5ca
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5311aa3ff390611942aa91cb1f2a53ca5a76258d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68204061"
---
# <a name="how-to-troubleshoot-services"></a>방법: 서비스 문제 해결
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

서비스를 가져오려고 할 때 발생할 수 있는 몇 가지 일반적인 문제는  
  
- 서비스에 등록 되지 않았습니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]합니다.  
  
- 서비스 유형별이 아닌 인터페이스 형식에서 서비스 요청 됩니다.  
  
- 해당 서비스를 요청 하는 VSPackage에 배치 된 했습니다.  
  
- 잘못 된 서비스 공급자가 사용 됩니다.  
  
  하는 경우 요청된 된 서비스를 가져올 수 없으며 호출 <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> null을 반환 합니다. 서비스 요청 후 항상 null에 대 한 테스트 해야 합니다.  
  
```csharp  
IVsActivityLog log =   
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
if (log == null) return;  
```  
  
### <a name="to-troubleshoot-a-service"></a>서비스 문제를 해결 하려면  
  
1. 서비스가 올바르게 등록 되었는지 여부를 확인 하려면 시스템 레지스트리를 검사 합니다. 자세한 내용은 [서비스 등록](../misc/registering-services.md)합니다.  
  
     다음.reg 파일 조각은 SVsTextManager 서비스를 등록 하는 방법을 보여 줍니다.  
  
    ```  
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}]  
    @="{F5E7E720-1401-11d1-883B-0000F87579D2}"  
    "Name"="SVsTextManager"  
    ```  
  
     위의 예에서 버전 번호는 버전의 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]등 12.0 또는 14.0을 {F5E7E71D-1401-11d1-883B-0000F87579D2} 키가 기본 값 {, SVsTextManager 서비스의 서비스 식별자 (SID) F5e7e720-1401-11d1-883b-0000f87579d2}는 텍스트 관리자 서비스를 제공 하는 VSPackage의 패키지 GUID입니다.  
  
2. GetService를 호출할 때 서비스 형식 및 인터페이스 형식이 아닌을 사용 합니다. 서비스를 요청할 때 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], <xref:Microsoft.VisualStudio.Shell.Package> 형식에서 GUID를 추출 합니다. 다음 조건에 해당 하는 경우 서비스를 찾을 수 없습니다.  
  
    1. 인터페이스 형식 대신 서비스 유형을 GetService에 전달 됩니다.  
  
    2. GUID가 없는 인터페이스를 명시적으로 할당 됩니다. 따라서 시스템 필요에 따라 개체에 대 한 기본 GUID를 생성 합니다.  
  
3. 서비스 요청 VSPackage 배치 되었는지 확인 해야 합니다. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 생성 후 호출 하기 전에 VSPackage 사이트 <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>합니다.  
  
     서비스는 VSPackage 생성자의 코드가 있으면 Initialize 메서드를 이동 합니다.  
  
4. 올바른 서비스 공급자를 사용 하 고 있는지 확인 해야 합니다.  
  
     모든 서비스 공급자는 유사 합니다. 서비스 공급자는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] VSPackage에 전달 하는 것에서 다른 도구 창에 전달 합니다. 도구 창 서비스 공급자가 인식 <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>, 알 수 없습니다 있지만 <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>합니다. 호출할 수 있습니다 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> 도구 창 내에서 VSPackage 서비스 공급자를 가져오려고 합니다.  
  
     사용자 정의 컨트롤 또는 기타 컨트롤 컨테이너를 호스트 하는 도구 창, 컨테이너 Windows 구성 요소 모델에 의해 위치할 고에 액세스할 수 없습니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 서비스입니다. 호출할 수 있습니다 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> 컨트롤 컨테이너에서 VSPackage 서비스 공급자를 가져오려고 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [사용 가능한 서비스 목록](../extensibility/internals/list-of-available-services.md)   
 [사용 하 고 서비스를 제공 합니다.](../extensibility/using-and-providing-services.md)   
 [서비스 필수 항목](../extensibility/internals/service-essentials.md)
