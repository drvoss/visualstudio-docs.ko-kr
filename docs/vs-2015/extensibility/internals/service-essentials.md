---
title: Essentials 서비스 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- services, essentials
ms.assetid: fbe84ad9-efe1-48b1-aba3-b50b90424d47
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 407dda2f203b7be20b19c0e296caa9ce1c95b32c
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65696075"
---
# <a name="service-essentials"></a>서비스 필수 항목
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

서비스는 두 Vspackage 간의 계약입니다. 하나의 VSPackage를 사용 하는 다른 VSPackage에 대 한 인터페이스의 특정 집합을 제공 합니다. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 다른 Vspackage에 서비스를 제공 하는 Vspackage의 컬렉션인 됩니다.  
  
 예를 들어 활동 로그에 작성 하는 데 사용할 수 있는 IVsActivityLog 인터페이스를 가져올 SVsActivityLog 서비스를 사용할 수 있습니다. 자세한 내용은 [방법: 활동 로그를 사용 하 여](../../extensibility/how-to-use-the-activity-log.md)입니다.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 또한 등록 되지 않은 몇 가지 기본 제공 서비스를 제공 합니다. Vspackage는 서비스 재정의 제공 하 여 기본 제공 또는 다른 서비스를 바꿀 수 있습니다. 모든 서비스에 대 한 하나의 서비스 재정의 허용 됩니다.  
  
 서비스에 검색 되지 않습니다. 따라서 서비스를 사용 하려는 서비스 식별자 (SID)를 알고 있어야 하 고 제공 하는 인터페이스를 알고 있어야 합니다. 서비스에 대 한 참조 설명서는이 정보를 제공합니다.  
  
- 서비스를 제공 하는 Vspackage는 서비스 공급자 라고 합니다.  
  
- 다른 Vspackage에 제공 되는 서비스는 글로벌 서비스 라고 합니다.  
  
- 구현 하는 VSPackage 또는 만드는 모든 개체에만 사용할 수 있는 서비스에는 로컬 서비스 라고 합니다.  
  
- 기본 제공 서비스 또는 다른 패키지에서 제공 하는 서비스를 대체 하는 서비스는 서비스 재정의 호출 됩니다.  
  
- 서비스 또는 서비스 재정의 주문형 로르, 다른 VSPackage에서 제공 하는 서비스 요청 되 면 서비스 공급자가 로드 하는, 합니다.  
  
- 요청 시 로드를 지원 하려면 서비스 공급자를 등록가 글로벌 서비스를 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]입니다. 자세한 내용은 [서비스 등록](../../misc/registering-services.md)합니다.  
  
- 사용 하 여 서비스를 가져온 후 [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) (비관리 코드) 또는 예를 들어 원하는 인터페이스를 가져오려면 캐스팅 (관리 코드):  
  
    ```vb  
    TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)  
    ```  
  
    ```csharp  
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
  
    ```  
  
- 관리 코드는 비관리 코드 GUID 사용 하 여 서비스를 참조 하는 반면 해당 형식 사용 하 여 서비스를 가리킵니다.  
  
- 때 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] VSPackage 로드, 서비스 공급자에 전달 VSPackage 글로벌 서비스를 VSPackage 액세스를 제공 합니다. VSPackage "사이 팅" 이라고 합니다.  
  
- Vspackage는 자신이 만든 개체에 대 한 서비스 공급자 수 있습니다. 예를 들어 폼 색 서비스에 대 한 요청을 요청을 전달할 수는 해당 프레임에 보낼 수 있습니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]합니다.  
  
- 깊게 중첩 되거나 전혀 배치 하지 되는 관리 되는 개체를 호출할 수 있습니다 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> 글로벌 서비스에 대 한 직접 액세스에 대 한 합니다. 자세한 내용은 [방법: Getglobalservice](../../misc/how-to-use-getglobalservice.md)합니다.  
  
## <a name="see-also"></a>참고 항목  
 [사용 가능한 서비스 목록](../../extensibility/internals/list-of-available-services.md)   
 [사용 하 고 서비스를 제공 합니다.](../../extensibility/using-and-providing-services.md)   
 [캐스팅 및 형식 변환](https://msdn.microsoft.com/library/568df58a-d292-4b55-93ba-601578722878)   
 [캐스팅](https://msdn.microsoft.com/library/3dbeb06e-2f4b-4693-832d-624bc8ec95de)
