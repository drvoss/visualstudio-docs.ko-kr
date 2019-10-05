---
title: 새로운&#39;Visual Studio 2017 SDK의 새로운 | Microsoft Docs
ms.date: 10/31/2017
ms.topic: conceptual
ms.assetid: 9efcf0a3-dbde-4cab-8ed3-425826a48b2e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 434a04aaa8389b4b09f32778d5de63bd2a7d687f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350789"
---
# <a name="what39s-new-in-the-visual-studio-2017-sdk"></a>새로운&#39;Visual Studio 2017 SDK의 새로운

Visual Studio SDK는 Visual Studio 2017에 대 한 다음 새로운 및 업데이트 된 기능.

## <a name="vsix-v3-format"></a>VSIX v3 형식

Visual Studio 2017의 새로운 경량 설치를 지원 하려면 VSIX 확장 매니페스트 형식 버전 3 (VSIX v3)으로 업데이트 되었습니다.

새 형식에 대 한 지원에 있습니다.

* 검색 하 고는 VSIXInstaller에서 설치 필수 구성 요소를 명시적으로 선언 합니다.
* 확장 설치에서 어셈블리를 Ngen 합니다.
* 일반적인 확장 루트 밖에 자산을 설치 합니다.

이러한 변경에 대 한 자세한 내용은 다음 항목을 참조 합니다.

* [Visual Studio 2017에 대 한 확장성 변경](breaking-changes-2017.md)
* [VSIX v3의 Ngen 지원](ngen-support.md)
* [확장 폴더 외부에 설치](set-install-root.md)
* [Visual Studio 2017 확장성에 대 한 질문과 대답](faq-2017.md)

## <a name="migrate-extensibility-project-to-visual-studio-2017"></a>Visual Studio 2017로 확장성 프로젝트 마이그레이션

Visual Studio 2017로 확장성 프로젝트 및 해당 VSIX 매니페스트를 업데이트 하는 방법에 알아보려면 참조 [방법: Visual Studio 2017로 확장성 프로젝트 마이그레이션](how-to-migrate-extensibility-projects-to-visual-studio-2017.md)합니다.

## <a name="custom-project-and-item-templates"></a>사용자 지정 프로젝트 및 항목 템플릿

Visual Studio 2017부터 사용자 지정 프로젝트 및 항목 템플릿에 대 한 검사는 더 이상 수행 됩니다. 대신 확장 이러한 서식 파일의 설치 위치를 설명 하는 템플릿 매니페스트 파일을 제공 해야 합니다. VSIX 확장을 업데이트 하려면 Visual Studio 2017을 사용할 수 있습니다. MSI를 사용 하 여 확장을 배포 하는 경우 손으로 템플릿 매니페스트 파일을 생성 해야 합니다. 자세한 내용은 [Visual Studio 2017에 대 한 사용자 지정 프로젝트 및 항목 템플릿 업그레이드](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md)합니다. 템플릿 매니페스트 스키마에 설명 되어 있습니다 [Visual Studio 템플릿 매니페스트 스키마 참조](../extensibility/visual-studio-template-manifest-schema-reference.md)합니다.

## <a name="updated-extension-performance-guidelines"></a>업데이트 된 확장 성능 지침

새로운 [방법: 확장 성능 진단](how-to-diagnose-extension-performance.md) 에서 문서 [관리 Vspackage](managing-vspackages.md) 시작 및 솔루션 로드 시간을 검색 하 여 Visual Studio에 대 한 확장 영향을 분석 하는 방법을 보여 줍니다.
