---
title: 여러 버전의 Visual Studio 지원 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, supporting multiple versions
- VSPackages, side-by-side compatibility
ms.assetid: 0047aa90-1ed4-40d3-8772-622b2719a4b1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f7212445cd507a0d7d185bbd73fa2292e5b783f4
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/06/2019
ms.locfileid: "66746000"
---
# <a name="supporting-multiple-versions-of-visual-studio"></a>여러 버전의 Visual Studio 지원
용어 *side-by-side-* 설치 하 고 동일한 컴퓨터에서 제품의 여러 버전을 유지 관리할 수 있는 것을 의미 합니다. Vspackage, 즉,는 사용자는 동일한 컴퓨터에 설치 하는 몇 가지 Visual Studio 버전을 가질 수 있습니다. 그러나 단일 버전의 Visual Studio에 로드 하 여 Vspackage의 side-by-side-버전 수는 없습니다.

 Side-by-side-버전의 Visual Studio에 로드 되어야 할 VSPackage를 수행 하기 전에 다음 사항을 고려 합니다.

- 수행 하려는 side-by-side-구현 전략을 결정 해야 합니다.

   자세한 내용은 [공유 간의 선택 및 버전 관리 Vspackage](../extensibility/choosing-between-shared-and-versioned-vspackages.md)합니다.

- 솔루션 및 프로젝트 파일 형식을 구현 전략에 맞아야 합니다.

   자세한 내용은 [사용자 지정 프로젝트 업그레이드](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects) 하 고 [Side-by-side-배포에 대 한 파일 이름 확장명 등록](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)합니다.

- 설치 관리자 버전 구성 요소 및 모든 버전에서 공유 하는 구성 요소가 올바르게 설치 하 고 등록 구현 전략을 처리 해야 합니다.

   자세한 내용은 [Windows Installer를 사용 하 여 Vspackage 설치](../extensibility/internals/installing-vspackages-with-windows-installer.md) 권한과 [구성 요소 관리](../extensibility/internals/component-management.md)합니다.

  > [!NOTE]
  > 해당 버전의.NET Framework 설치도 Visual Studio의 버전을 설치 합니다. 예를 들어, 동일한 컴퓨터에 Visual Studio 2010 및 Visual Studio 2012를 설치 설치 버전 4.0 및.NET Framework 4.5 각각.

## <a name="in-this-section"></a>섹션 내용
- [공유 간의 선택 및 버전 관리 Vspackage](../extensibility/choosing-between-shared-and-versioned-vspackages.md) VSPackage의 side-by-side-문제를 해결 하는 방법에 설명 합니다.

- [Side-by-side-배포에 대 한 파일 이름 확장명을 등록](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md) VSPackage side-by-side-시나리오에서 파일 연결을 등록 하는 방법에 대해 설명 합니다.

## <a name="related-sections"></a>관련 단원
- [Windows Installer를 사용하여 VSPackage 설치](../extensibility/internals/installing-vspackages-with-windows-installer.md)
