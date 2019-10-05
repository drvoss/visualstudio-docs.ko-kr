---
title: 공유 및 버전 관리 Vspackage 중에서 선택 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SxS
- side-by-side installation
- installation [Visual Studio SDK], side-by-side
ms.assetid: e3128ac3-2e92-48e9-87ab-3b6c9d80e8c9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: de7bb2ee0335322e0b089fd2af81026b1f6bd1ca
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/06/2019
ms.locfileid: "66747785"
---
# <a name="choose-between-shared-and-versioned-vspackages"></a>공유 및 버전 관리 Vspackage 중에서 선택
다른 버전의 Visual Studio는 동일한 컴퓨터에 공존할 수 있습니다. Vspackage의 혼합을 지원할 수 있습니다 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 버전입니다.

 두 가지 전략, 공유 전략 또는 버전이 있는 전략 중 하나를 통해 Vspackage의 side-by-side-설치를 사용할 수 있습니다. 여러 버전의 현재 상태를 수용 하는 둘 다 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .NET Framework의 버전을 연결 합니다.

 공유 전략의 여러 버전에서 사용 하기 위해 하나의 VSPackage 등록 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]합니다. 버전 관리 전략의 여러 VSPackage Dll이 설치의 각 버전에 대해 하나씩 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 지원 합니다.

## <a name="shared-vspackages"></a>공유 Vspackage
 공유 VSPackage를 사용 하 여 적합 한 여러 버전의 동일한 VSPackage를 사용 하는 경우 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]합니다. 공유 VSPackage를 구현 하려면 다음 단계를 수행 해야 합니다.

- VSPackage를 여러 버전의 호환 되도록 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]합니다. 따라서 이렇게 두 가지 방법으로 사용할 수 있습니다.

  - 제한의 가장 오래 된 버전의 기능만 사용 하 여 VSPackage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 지원 합니다.

  - VSPackage의 버전에 맞게 프로그램 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 실행 됩니다. 그런 다음 새 서비스에 대 한 쿼리가 실패 하는 경우 VSPackage 제공할 수 있습니다의 이전 버전에서 지원 되는 다른 서비스 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]합니다.

- 적절 하 게 VSPackage를 등록 합니다. 자세한 내용은 [VSPackage 등록](../extensibility/internals/vspackage-registration.md) 하 고 [관리 되는 VSPackage 등록](https://msdn.microsoft.com/library/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)합니다.

- 파일 확장명을 적절 하 게 등록 합니다. 자세한 내용은 [side-by-side-배포에 대 한 파일 이름 확장명 등록](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)합니다.

- 적절 한 버전의 VSPackage를 배포 하는 설치 관리자 만들기 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]합니다. 자세한 내용은 [Windows Installer를 사용 하 여 Vspackage 설치](../extensibility/internals/installing-vspackages-with-windows-installer.md) 하 고 [구성 요소 관리](../extensibility/internals/component-management.md)합니다.

- 등록 충돌 문제를 해결 합니다. 자세한 내용은 [VSPackage 등록](../extensibility/internals/vspackage-registration.md)합니다.

- 공유 및 버전 관리 파일에서 여러 버전의 안전한 설치 및 제거를 허용 하기 위해 참조 가산을 준수 하는지 확인 합니다. 자세한 내용은 [구성 요소 관리](../extensibility/internals/component-management.md)합니다.

## <a name="versioned-vspackages"></a>버전 관리 Vspackage
 버전 관리 VSPackage 전략을 아래 각 버전의 VSPackage를 하나 만들 있습니다 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 지원 합니다. 이 방법은 적절 한 이후 버전의에서 제공 하는 서비스를 활용 하려는 경우 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]이므로 각 VSPackage 다른 영향을 주지 않고 진화 할 수 있습니다. 그럼에도 불구 하 고 여러 독립적인 코드 베이스 또는 단일 코드 베이스에서 여러 이진 파일을 만드는 버전 관리 전략을 공유 전략 보다 더 많은 초기 개발을 수반 될 수 있습니다. 또한 추가 설치 작업 해야 할 수 있습니다 각 버전에 대 한 별도 설치 또는 버전을 검색 하는 단일 설치 프로그램을 만들어야 하기 때문에 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 설치 되어 있고 VSPackage를 지원 합니다.

## <a name="binary-compatibility"></a>이진 호환성
 일반적으로 이진 호환성에는 이전 버전의 Visual Studio의 이후 버전에서 실행 하려면 Visual Studio를 사용 하 여 개발 하는 네이티브 코드로 Vspackage 수 있습니다. 그러나는 세 가지 중요 한 예외가 있습니다.

- VSPackage는 특정 버전의 공용 언어 런타임의 경우의 어떤 버전을 확인 해야 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 실행 됩니다.

- VSPackage 다른 VSPackage 또는 다른 제품의 특정 기능에 대해 종속성이 있을 수 있습니다. 결과적으로 VSPackage 종속성은 충족 하는 위치에 실행할 수 있습니다.

- VSPackage의 보안 수정 영향을 받을 수는 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 서비스 팩 또는 최신 버전의 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]합니다. 이러한 경우 VSPackage의 이전 버전을 사용 하 여 개발 된 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] 버전에서 실행 되지 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 보안 수정이 적용 된 후입니다. 그러나 최신 버전을 사용 하 여 패키지를 다시 작성할 수 있으며 이전 버전에서 실행할 수도 있습니다.

  관리 되는 Vspackage의 버전을 사용 하 여 빌드해야 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 하며 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] 의 대상 버전을 일치 하는 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]합니다.

  VSPackage 이진 파일에 대 한 이진 호환성에 대 한 계획 하는 것 외에도 또한 사항과 고려해 야 솔루션 프로젝트 파일 형식입니다. VSPackage는 새 프로젝트 형식을 만듭니다, 하는 경우 버전을 하나만 또는 여러 버전의 실행할 수 있는지 여부를 결정 해야 합니다 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]합니다. 자세한 내용은 [사용자 지정 프로젝트 업그레이드](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects)합니다.

## <a name="see-also"></a>참고자료
- [Windows Installer를 사용 하 여 Vspackage 설치](../extensibility/internals/installing-vspackages-with-windows-installer.md)
- [구성 요소 관리](../extensibility/internals/component-management.md)