---
title: 구성 요소 관리 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], components
- installation [Visual Studio SDK], file management
ms.assetid: 029bffa2-6841-4caa-a41a-442467e1aedc
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 56a110f382d0b182eed0ea1a95cd4dabf2877037
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68191856"
---
# <a name="component-management"></a>구성 요소 관리
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Windows 설치 관리자에서 작업의 단위는 Windows 설치 관리자 구성 요소 (WICs 또는 구성 요소 라고도 함) 라고 합니다. 설치 및 Windows Installer를 사용 하는 설정에 대 한 계산 참조의 기본 단위는 각 WIC를 식별 하는 GUID입니다.  
  
 여러 제품을 사용 하 여 VSPackage 설치 관리자를 만들 수 있습니다, 있지만이 설명에서는 Windows Installer (.msi) 파일의 사용을 가정 합니다. 설치 관리자를 만들 때 발생 하는 모든 시간에 올바른 참조 카운팅 있도록 파일 배포 올바르게 관리 해야 합니다. 따라서 다른 버전의 제품 및 하지 않습니다 방해 또는 서로 다양 한 설치 중단 시나리오를 제거 합니다.  
  
 Windows 설치 관리자에서 구성 요소 수준에서 발생 참조 수를 계산 합니다. 리소스를 신중 하 게 구성 해야 합니다-파일, 레지스트리 항목을 등에-구성 요소에 있습니다. 다른 수준의 조직, 모듈, 기능, 제품 등과 같은-다양 한 시나리오에서 도움이 되는 합니다. 자세한 내용은 [Windows Installer 기본 사항](../../extensibility/internals/windows-installer-basics.md)합니다.  
  
## <a name="guidelines-of-authoring-setup-for-side-by-side-installation"></a>Side-by-side-설치에 대 한 설치 프로그램을 작성 지침  
  
- 작성자 파일 및 레지스트리 키에 고유한 구성 요소 버전 간에 공유 되는 합니다.  
  
     이 옵션을 사용 하면 다음 버전에서 쉽게 사용할 수 있습니다. 예를 들어, 전역으로 등록 된 형식 라이브러리 파일 확장명을 HKEY_CLASSES_ROOT를에 등록 된 다른 항목입니다.  
  
- 공유 구성 요소에 별도 병합 모듈을 그룹화 합니다.  
  
     이 통해-side-by-side 앞에 올바르게 작성할을 수 있습니다.  
  
- 버전 간에 동일한 Windows Installer 구성 요소를 사용 하 여 공유 파일 및 레지스트리 키를 설치 합니다.  
  
     다른 구성 요소를 사용 하는 경우 다른 VSPackage 여전히 설치 되어 있지만 하나의 버전 관리 VSPackage 제거 하는 경우에 파일과 레지스트리 항목이 제거 됩니다.  
  
- 동일한 구성 요소 버전 관리 및 공유 항목을 혼합 하지 마십시오.  
  
     이렇게 하면 격리 된 위치에 버전이 지정 된 항목과 전역 위치에 공유 항목을 설치 하려면 불가능 합니다.  
  
- 버전이 지정 된 파일을 가리키는 공유 레지스트리 키를 갖지 않습니다.  
  
     이렇게 하면 다른 버전 관리 VSPackage를 설치할 때 공유 키를 덮어쓰게 됩니다. 두 번째 버전을 제거한 후에 키가 가리키고 파일은 사라집니다.  
  
## <a name="see-also"></a>참고 항목  
 [공유 및 버전 관리 Vspackage 중에서 선택](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [VSPackage 설치 시나리오](../../extensibility/internals/vspackage-setup-scenarios.md)
