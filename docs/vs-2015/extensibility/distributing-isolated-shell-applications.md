---
title: 격리 셸 응용 프로그램 배포 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: c503a985-d67a-4ef8-9123-7744a78f2f17
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bf0d8a4cab8d30a56e84d1a6869c2c842b982aea
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68204673"
---
# <a name="distributing-isolated-shell-applications"></a>격리 셸 애플리케이션 배포
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

격리 셸 응용 프로그램을 만들기 위해 Visual Studio 및 Visual Studio SDK를 설치 해야 합니다. 다른 사용자 또는 고객의 컴퓨터에 응용 프로그램을 배포 하려면 격리 셸에 대 한 특별 한 재배포 가능 패키지를 포함 해야 합니다.  
  
## <a name="prerequisites-for-distributing-isolated-shell-applications"></a>격리 셸 응용 프로그램을 배포 하기 위한 필수 구성 요소  
  
|이름|Description|  
|----------|-----------------|  
|Visual Studio SDK|개발 및 테스트를 확장 해야 하는 SDK [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]합니다. 또한 Visual Studio 격리 셸의 고유한 인스턴스를 만드는 SDK를 사용할 수 있습니다.<br /><br /> Visual Studio SDK에 대 한 필수 구성 요소입니다.|  
|Microsoft Visual Studio 격리 셸 재배포 가능 패키지|Shell 재배포 가능 패키지 포함 하는 설치 프로그램에서 Visual studio는 도구 환경을 빌드할 때 격리 합니다. Isolated Shell 재배포 가능 패키지는.NET Framework 4.5를 포함합니다.|  
  
## <a name="creating-an-installation-program-for-the-application"></a>응용 프로그램에 대 한 설치 프로그램 만들기  
 통합 또는 격리 셸 응용 프로그램에 대 한 특별 한 설치 프로그램을 만들어야 합니다. 자세한 내용은 [격리 셸 응용 프로그램을 설치](../extensibility/installing-an-isolated-shell-application.md)합니다.  
  
## <a name="allowing-for-updates-to-your-application"></a>응용 프로그램에 대 한 업데이트 허용  
 설치 프로그램에는 응용 프로그램을 업데이트할 Microsoft 업데이트 또는 회사 업데이트 가능성에 대 한 허용 해야 합니다. 업데이트에 대 한 자세한 내용은 참조 하세요. [격리 셸 응용 프로그램에 대 한 서비스 지침](../extensibility/servicing-guidelines-for-isolated-shell-applications.md)합니다.
