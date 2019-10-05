---
title: Shell (격리 또는 통합) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell
- Visual Studio, Shell
- Shell [Visual Studio]
- Visual Studio shell, shell-based applications
- Shell [Visual Studio], shell-based applications
ms.assetid: c64a9bf0-9bf8-45c3-8fa2-306fa6cab66a
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d570c181125a1f94108624e6f9b1ce23bdcca25a
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63447227"
---
# <a name="shell-isolated-or-integrated"></a>Shell (격리 또는 통합)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

통합 또는 격리 모드에서 사용자 고유의 Visual Studio 기반 응용 프로그램을 만들 수 있습니다. 통합된 모드에서는 여러 Visual Studio 기능을 응용 프로그램 외에도 사용할 수 있습니다. 격리 모드에서 사용자 고유의 확장과 함께 배포 하려는 Visual Studio 기능의 하위 집합을 선택 합니다.  
  
## <a name="integrated-mode"></a>통합된 모드  
 통합된 모드에는 사용자를가 사용자 지정 도구와 함께 표준 Visual Studio 기능을 사용할 수 있습니다. Integrated shell 주로 프로그래밍 언어 및 소프트웨어 개발 도구를 호스트 하기 위한 것입니다.  
  
 Integrated shell에서 자동으로 빌드된 사용자 지정 도구는 동일한 컴퓨터에 설치 된 Visual Studio의 다른 버전을 사용 하 여 병합 합니다. Visual Studio가 이미 설치 되어 있지 않으면 Visual Studio 통합 셸 재배포 가능 패키지 버전을 제공할 수 있습니다.  
  
 Visual Studio 통합 셸 재배포 가능 패키지 버전에서 프로그래밍 언어 및 해당 프로젝트 시스템을 지 원하는 기능을 포함 하지 않습니다.  
  
> [!NOTE]
> Visual Studio shell 통합된 모드의 Visual Studio Express edition 제외한 모든 버전을 함께 설치할 수 있습니다.  
  
 자세한 내용은 [Visual Studio Shell (통합)](../extensibility/visual-studio-shell-integrated.md)합니다.  
  
## <a name="isolated-mode"></a>격리 모드  
 격리 모드를 사용 하면-나란히 실행 하는 사용자 지정 도구를 만들 수 있습니다 다른 버전의 Visual Studio를 사용 하 여 합니다. 기본적으로 모든 표준 Visual Studio 기능에 따라 없이 Visual Studio 서비스에 액세스할 수 있는 도구에 대 한 것입니다. Visual Studio 격리 셸을 기반으로 작성 하는 응용 프로그램의 모양을 사용자 지정할 수 있습니다. 쉽게 기능 및 해당 응용 프로그램과 함께 표시 하지 않을 메뉴 명령 그룹 해제할 수 있습니다.  
  
 자세한 내용은 [Visual Studio Isolated Shell](../extensibility/visual-studio-isolated-shell.md)합니다.  
  
## <a name="distributing-your-integrated-or-isolated-shell-application"></a>통합 또는 격리 셸 응용 프로그램 배포  
 통합 또는 격리 셸 응용 프로그램에 배포 하기 위해 응용 프로그램은 특별 한 통합 또는 격리 된 셸 재배포 가능 패키지 및 설치 프로그램을 포함 해야 합니다. 배포 및 설치 하는 방법에 대 한 자세한 내용은 참조 하세요. [격리 셸 응용 프로그램 배포](../extensibility/distributing-isolated-shell-applications.md)합니다.  
  
> [!IMPORTANT]
> 합니다 [최종 사용자 사용권 계약 (EULA)](https://www.visualstudio.com/support/legal/mt171552) 셸 데이터 수집에 대 한 섹션이 포함 Visual Studio 통합 및 격리에 대 한 (**섹션 3입니다. 데이터**).  사용자의 통합 또는 isolated shell 소프트웨어 응용 프로그램을 작성 하는 Microsoft에서 수집 될 수 있습니다는 고객 사용 데이터를 설명 합니다. 자세한 내용은 [Microsoft Visual Studio 제품 제품군 개인정보취급방침](https://www.visualstudio.com/dn948229)합니다.  
> 
> 응용 프로그램을 통해 고객의 별도 사용 현황 데이터를 수집 하는 경우에 수집 하 여 응용 프로그램의 사용자에 게 적절 한 통지를 제공 해야 합니다.  Visual Studio 소프트웨어 개발 키트 라이선스에 따라 응용 프로그램의 일부로 통합 또는 격리 된 셸 소프트웨어를 배포 하는 경우 다음 중 하나를 포함 해야 합니다.  
> 
> - 응용 프로그램 라이선스의 일부로 최종 사용자 사용권 계약  
> - Visual Studio를 보호 하는 조건에 동의 하도록 고객에 게 필요한 사용자 고유의 EULA 통합 또는 격리 셸은 적어도 shell 소프트웨어에 대 한 Microsoft 최종 사용자 사용 조건으로  
  
## <a name="additional-resources"></a>추가 리소스  
 재배포 가능 패키지에 대 한 자세한 내용은 참조는 [Visual Studio 확장 다운로드](http://go.microsoft.com/fwlink/?LinkID=119298) 웹 사이트입니다.  
  
## <a name="see-also"></a>참고 항목  
 [Visual Studio 확장 전달](../extensibility/shipping-visual-studio-extensions.md)
