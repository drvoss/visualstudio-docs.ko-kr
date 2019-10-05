---
title: VSPackage 상태 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- state, VSPackages
- VSPackages, managing application state
- state persistence
ms.assetid: 6056a9ea-e7a8-481c-9fc8-340229fa12d9
caps.latest.revision: 25
manager: jillfra
ms.openlocfilehash: f3140b527673f87b1d7c552e99584232494aed7f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62979997"
---
# <a name="vspackage-state"></a>VSPackage 상태
다양 한 요인의 지속형된 값 또는 상태 집합을 결정 한 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 응용 프로그램입니다.  
  
- 프로젝트 구성과 프로젝트 속성을가지고 있습니다.  
  
- 솔루션에는 속성이 있습니다.  
  
- 사용자 설정은 문서 창과 도구 창, 도킹 상태 바로 가기 키의 위치와 크기를 결정합니다.  
  
- 응용 프로그램 사용자 설정 하는 옵션이 있을 수 있습니다.  
  
- 응용 프로그램을 만드는 개체는 자체 속성에 있을 수 있습니다.  
  
  다음은 몇 가지는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 응용 프로그램 상태를 관리할 수 있습니다.  
  
- 프로젝트 및 솔루션 속성 페이지를 통해.  
  
- 통해 합니다 **설정 가져오기 및 내보내기 마법사**, 사용자 설정을 컴퓨터에서 간에 이동할 수 있습니다.  
  
- 통해 합니다 **옵션** 응용 프로그램과 관련 된 옵션을 포함 하는 대화 상자.  
  
- 통해 합니다 **속성** 창 개체의 속성을 표시 합니다.  
  
- 자동화 합니다. 응용 프로그램 자동화에 노출 되는 VSPackage 및 개체 속성에 액세스할 수 있습니다.  
  
  응용 프로그램 상태를 기본 가지 응용 프로그램 상태를 저장 하 고 복원할 수 있도록 하는 다양 한 지 속성 메커니즘이 있습니다.  
  
## <a name="in-this-section"></a>섹션 내용  
 [상태 지속성 지원](../misc/support-for-state-persistence.md)  
 VSPackage 상태의 저장, 복원, 재설정 등에 대한 일반적인 전략이 표시됩니다.  
  
 [옵션 및 옵션 페이지](../extensibility/internals/options-and-options-pages.md)  
 일반 및 사용자 지정 옵션 페이지를 소개 하 고 구현 하는 방법에 설명 합니다.  
  
 [옵션 페이지 만들기](../extensibility/creating-an-options-page.md)  
 두 옵션 페이지, 간단한 페이지 및 사용자 지정 페이지를 만드는 방법을 설명 합니다.  
  
 [설정 범주에 대한 지원](../misc/support-for-settings-categories.md)  
 사용자 설정 및 생성 및 유지 하는 방법을 설명 합니다.  
  
 [설정 범주 만들기](../extensibility/creating-a-settings-category.md)  
 만드는 방법에 설명 된 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 설정 범주 값을 저장 하 고 설정 파일에서 값을 복원 하는 데 사용할 합니다.  
  
 [속성 및 속성 창 확장](../extensibility/extending-properties-and-the-property-window.md)  
 표시에 있는 개체의 값을 변경 하는 방법을 설명 합니다 **속성** 창입니다.  
  
 [속성 창에 속성 노출](../extensibility/exposing-properties-to-the-properties-window.md)  
 개체의 공용 속성을 노출 하는 방법에 설명 합니다 **속성** 창입니다.  
  
 [프로젝트 및 구성 속성 지원](../extensibility/internals/support-for-project-and-configuration-properties.md)  
 표시 속성을 변경 하려면 프로젝트 및 구성 하는 방법을 설명 합니다.  
  
 [프로젝트 속성 가져오기](../extensibility/getting-project-properties.md)  
 도구 창에서 프로젝트 속성을 표시 하는 관리 되는 VSPackage를 만드는 단계를 안내 합니다.  
  
 [설정 저장소 사용](../extensibility/using-the-settings-store.md)  
 설정 저장소 지 속성 메커니즘을 사용 하는 방법을 설명 합니다.  
  
## <a name="related-sections"></a>관련 단원  
 [VSPackage](../extensibility/internals/vspackages.md)  
 만들고 Vspackage를 사용 하는 방법을 설명 하는 일반적인 방향을 제공 합니다.