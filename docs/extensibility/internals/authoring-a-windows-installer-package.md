---
title: Windows Installer 패키지를 authoring | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .msi files, VSPackages
- msi files, VSPackages
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: da68fa0a6c115a09ba2050f8c84ea6700ee4fc76
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66315783"
---
# <a name="author-a-windows-installer-package"></a>Windows Installer 패키지를 작성 합니다.
데이터 드라이브는 Windows Installer 모델입니다. 레지스트리 항목을 쓰고 파일을 복사 하는 절차 스크립트를 작성 하는 대신 예를 들어 만든 파일 및 레지스트리 데이터를 포함 하는 데이터베이스 테이블의 행과 열입니다.

## <a name="database-entries"></a>데이터베이스 항목
VSPackage를 설치 하려면 Windows Installer 패키지를 다음 작업을 수행할 데이터베이스 항목을 포함 해야 합니다.

- 검색 버전을 찾으려고 시스템 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackage (AppSearch, CompLocator, RegLocator, DrLocator, 및 서명을 포함 하는 Windows Installer 테이블 사용)을 지원 합니다.

- 지원 되는 버전이 없는 경우 설치를 취소 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 되어 VSPackage의 다른 시스템 요구를 충족 되지 않으면 (시작 조건 테이블 사용) 또는 합니다.

- VSPackage 및 종속 파일 (directory, 구성 요소 및 파일 테이블 사용)을 설치 합니다.

- VSPackage에 대 한 적절 한 정보 (레지스트리 테이블 사용)을 레지스트리에 추가 합니다.

- VSPackage를 통합 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 호출한 **devenv.exe /setup** (CustomAction 테이블 사용).

자세한 내용은 [Windows Installer](/windows/desktop/Msi/windows-installer-portal)합니다.

## <a name="setup-tools"></a>도구 설정
다양 한 타사 설치 도구는 Windows Installer 패키지에 대 한 개발 환경을 제공 합니다. 다음 무료 도구를 사용할 수 있습니다.

- InstallShield limited edition

   Visual Studio를 통해 제한 된 버전의 InstallShield 가져올 수 있습니다 **새 프로젝트** 대화 합니다. 확장 **기타 프로젝트 형식** 선택한 후 **설치 및 배포**합니다. InstallShield 템플릿을 선택 합니다.

- Windows Installer XML 도구 집합

   Windows Installer XML (WiX) 도구 집합 XML 소스 파일에서 Windows Installer 패키지를 빌드합니다. WiX 도구 집합 Microsoft 오픈 소스 프로젝트입니다. 소스 코드 및 실행 파일을 다운로드할 수 있습니다 [Wix 도구 집합](http://sourceforge.net/projects/wix)합니다.

   에 통합 하는 상용 제품에 대 한 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 를 사용 하 여는 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]를 참조 하십시오 [Visual Studio Marketplace](https://marketplace.visualstudio.com/)합니다.

## <a name="see-also"></a>참고자료
- [Windows Installer를 사용 하 여 Vspackage 설치](../../extensibility/internals/installing-vspackages-with-windows-installer.md)