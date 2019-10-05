---
title: 프로젝트 하위 형식 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], subtypes
- project subtypes [Visual Studio SDK]
ms.assetid: d235b47b-cf11-4d47-a63f-e33d9d16105d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aede76a39506f74c39d9ec63ed4bb4a410d1013c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66328111"
---
# <a name="project-subtypes"></a>프로젝트 하위 형식
프로젝트 하위 형식을 사용 하면 사용자 지정 하거나의 프로젝트 시스템의 동작을 flavor [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]합니다. 사용자 지정 포함 프로젝트 파일을 추가 하거나 항목을 필터링의 추가 데이터를 저장 합니다 **새 항목 추가** 어셈블리는 디버깅 및 배포 하는 방법을 제어 하 고 대화 상자에서 프로젝트를 확장 하 고 **속성 페이지** 대화 상자. Vspackage는 프로젝트 하위 형식 COM 집계를 사용 하 여 구현 합니다.

> [!NOTE]
> 시각적 개체 C++ 프로젝트 시스템이 프로젝트 하위 형식을 지원 하지 않습니다. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 자체 프로젝트 하위 형식을 사용 하 여 SQL Server 및 스마트 장치 프로젝트를 구현 합니다.

## <a name="in-this-section"></a>섹션 내용
- [프로젝트 하위 형식 디자인](../../extensibility/internals/project-subtypes-design.md)

 프로젝트 하위 형식의 개념을 설명합니다.

- [프로젝트 하위 형식의 초기화 시퀀스](../../extensibility/internals/initialization-sequence-of-project-subtypes.md)

 프로그래밍 방식으로 프로젝트 하위 형식 초기화 시퀀스를 설명 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 환경입니다.

- [프로젝트 하위 형식에 의해 확장된 속성 및 메서드](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)

 자세한 설명은 기능과 프로젝트 하위 형식을 사용 하 여 가장 자주 확장 메서드를 제공 합니다.

- [MSBuild 프로젝트 파일의 데이터 유지](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)

 프로젝트 파일에서 데이터를 유지 하는 방법 및 사용 하는 방법에 설명 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> 프로젝트 하위 형식 집계 수준에서 프로젝트 파일에서 데이터를 유지 합니다.

- [프로젝트 속성 사용자 인터페이스](../../extensibility/internals/project-property-user-interface.md)

 프로젝트 하위 형식에서 프로젝트를 수정할 수는 방법에 대해 설명 합니다 **속성 페이지** 대화 상자.

- [기본 프로젝트의 개체 모델 확장](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)

 프로젝트 하위 형식 Automation Extender을 사용 하 여 자동화 개체 모델을 확장 하는 방법에 대 한 정보를 제공 합니다.

- [새 항목 추가 대화 상자에 적용](../../extensibility/internals/contributing-to-the-add-new-item-dialog-box.md)

 항목을 추가 하는 방법에 설명 합니다 **새 항목 추가** 대화 상자.

- [프로젝트 파일에 데이터 저장](../../extensibility/saving-data-in-project-files.md)

 프로젝트 하위 형식 수 저장 및 관리 패키지 프레임 워크 (MPF)를 사용 하 여 프로젝트 파일에서 하위 형식의 특정 데이터를 검색 하는 방법을 설명 합니다.

- [특수 배포 처리](../../extensibility/internals/handling-specialized-deployment.md)

 프로젝트 하위 형식이 구현 하 여 특수 한 배포 동작을 제공할 수는 방법에 대해 설명 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> 인터페이스입니다.

- [속성 페이지 추가 및 제거](../../extensibility/adding-and-removing-property-pages.md)

 프로젝트 디자이너의 속성 페이지를 제거 하 고 추가 설명 합니다.

## <a name="related-sections"></a>관련 단원
- [프로젝트 형식](../../extensibility/internals/project-types.md)

 자세히 설명 하는 항목 링크를 제공 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 프로젝트입니다.