---
title: 여러 버전의 Visual Studio 2015 지원 | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, supporting multiple versions
- VSPackages, side-by-side compatibility
ms.assetid: 0047aa90-1ed4-40d3-8772-622b2719a4b1
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8f4393a88a689e2a923291ada37a9b6d85718db5
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63431363"
---
# <a name="supporting-multiple-versions-of-visual-studio"></a>여러 버전의 Visual Studio 지원
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

용어 *side-by-side-* 설치 하 고 동일한 컴퓨터에서 제품의 여러 버전을 유지 관리할 수 있는 것을 의미 합니다. Vspackage, 즉,는 사용자는 동일한 컴퓨터에 설치 하는 몇 가지 Visual Studio 버전을 가질 수 있습니다. 그러나 단일 버전의 Visual Studio에 로드 하 여 Vspackage의 side-by-side-버전 수는 없습니다.

 Side-by-side-버전의 Visual Studio에 로드 되어야 할 VSPackage를 수행 하기 전에 다음 사항을 고려 합니다.

- 수행 하려는 side-by-side-구현 전략을 결정 해야 합니다.

     자세한 내용은 [공유 간의 선택 및 버전 관리 Vspackage](../extensibility/choosing-between-shared-and-versioned-vspackages.md)합니다.

- 솔루션 및 프로젝트 파일 형식을 구현 전략에 맞아야 합니다.

     자세한 내용은 [사용자 지정 프로젝트 업그레이드](../misc/upgrading-custom-projects.md) 하 고 [Side-by-side-배포에 대 한 파일 이름 확장명 등록](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)합니다.

- 설치 관리자 버전 구성 요소 및 모든 버전에서 공유 하는 구성 요소가 올바르게 설치 하 고 등록 구현 전략을 처리 해야 합니다.

     자세한 내용은 [Windows Installer를 사용 하 여 Vspackage 설치](../extensibility/internals/installing-vspackages-with-windows-installer.md) 권한과 [구성 요소 관리](../extensibility/internals/component-management.md)합니다.

    > [!NOTE]
    > 해당 버전의 설치도 Visual Studio의 버전을 설치 합니다 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]합니다. 예를 들어 버전 4.0 및 4.5의 설치도 동일한 컴퓨터에 Visual Studio 2010 및 Visual Studio 2012를 설치 합니다 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], 각각.

## <a name="in-this-section"></a>섹션 내용
 [공유 간의 선택 및 버전 관리 Vspackage](../extensibility/choosing-between-shared-and-versioned-vspackages.md) VSPackage의 side-by-side-문제를 해결 하는 방법에 설명 합니다.

 [Side-by-side-배포에 대 한 파일 이름 확장명을 등록](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md) VSPackage side-by-side-시나리오에서 파일 연결을 등록 하는 방법에 대해 설명 합니다.

## <a name="related-sections"></a>관련 단원
 [Vspackage 설치](../misc/installing-vspackages.md) Vspackage를 빌드 및 설치 하는 방법 및 동시에 여러 버전의 Visual Studio를 실행 하는 사용자를 지 원하는 방법에 설명 합니다.
