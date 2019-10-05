---
title: Vspackage에 대 한 자동화 제공 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, automation [Visual Studio SDK]
- automation [Visual Studio SDK], VSPackages
ms.assetid: 104c4c55-78b8-42f4-b6b0-9a334101aaea
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c6eb76eba76567f2966323d4058c9e752cb6fb69
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68200976"
---
# <a name="providing-automation-for-vspackages"></a>VSPackage에 대한 자동화 제공
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

에 Vspackage에 대 한 자동화를 제공 하는 방법에 두 가지가: 표준 automation 개체를 구현 하 고 VSPackage 관련 개체를 구현 하 여 합니다. 일반적으로 이러한 하는 데 함께 환경의 자동화 모델을 확장 합니다.  
  
## <a name="vspackage-specific-objects"></a>VSPackage 관련 개체  
 자동화 모델 내의 특정 위치를 사용 하는 VSPackage에 고유한 자동화 개체를 제공 해야 합니다. 예를 들어, 새 프로젝트만 VSPackage를 제공 하는 고유한 개체를 해야 합니다. 이러한 개체의 이름을 레지스트리에 입력 되어 환경에 대 한 호출을 통해 얻은 `DTE` 개체입니다.  
  
 Automation 소비자를 표준 개체의 개체 속성을 통해 제공 되는 개체를 사용 하는 경우 VSPackage 관련 개체도 가져올 수 있습니다. 예를 들어 표준 `Window` 개체에는 `Object` 속성을 일반적으로 라고는 `Windows.Object` 속성입니다. 소비자가 호출 되는 경우는 `Window.Object` VSPackage에서 구현 되는 창에 전달 하면 고유한 디자인의 특정 automation 개체를 사용 하 여 합니다.  
  
#### <a name="projects"></a>프로젝트  
 Vspackage는 자체 VSPackage 관련 개체를 통해 새 프로젝트 형식에 대 한 자동화 모델을 확장할 수 있습니다. 고유한 프로젝트를 구분 하는 VSPackage에 대 한 새 자동화 개체를 제공 하는의 주 목적은 개체를 <xref:Microsoft.VisualStudio.VCProjectEngine.VCProject> 또는 <xref:VSLangProj80.VSProject2> 개체입니다. Side-by-side-표시 되는 single 또는 기타 프로젝트 형식 외에도 프로젝트 유형에 반복 하는 방법을 제공 하려는 경우 이러한 구분이 유용한 솔루션에서입니다. 자세한 내용은 [프로젝트 개체 노출](../../extensibility/internals/exposing-project-objects.md)합니다.  
  
#### <a name="events"></a>이벤트  
 환경의 이벤트 아키텍처는 사용자 고유의 VSPackage 관련 개체를 추가할 수에 대 한 다른 위치를 제공 합니다. 예를 들어 자신의 고유한 이벤트 개체를 만들어 프로젝트에 대 한 환경의 이벤트 모델을 확장할 수 있습니다. 사용자 고유의 프로젝트 형식에 새 항목이 추가 될 때 사용자 고유의 이벤트를 제공 해야 할 수 있습니다. 자세한 내용은 [이벤트를 노출](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)합니다.  
  
#### <a name="window-objects"></a>창 개체  
 Windows 다시 전달할 수 있습니다 VSPackage 관련 자동화 개체를 호출 하는 경우 환경으로 다시 합니다. 파생 된 개체를 구현 <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>, <xref:EnvDTE.IExtensibleObject> 또는 `IDispatch` 는 사이 팅 하는 창 개체 확장 속성을 다시 전달 합니다. 예를 들어, 자동화 된 창 프레임에 배치할 컨트롤에 대 한이 접근 방식을 사용할 수 있습니다. 이 개체 및 확장 하는 다른 모든 개체의 의미 체계 디자인 하도록 설정할 경우 자세한 내용은 [방법: Windows에 대 한 자동화 제공](../../extensibility/internals/how-to-provide-automation-for-windows.md)합니다.  
  
#### <a name="options-pages-on-the-tools-menu"></a>도구 메뉴의 옵션 페이지  
 도구를 통해 페이지를 구현 하 고 고유한 옵션을 만들려면 레지스트리 정보를 추가 하는 옵션 자동화 모델을 확장 하는 페이지를 만들 수 있습니다. 페이지에 다른 옵션 페이지와 같은 환경 개체 모델을 통해 호출할 수 있습니다. Vspackage 통해 환경에 추가 하는 기능의 설계 옵션 페이지에 필요한 경우에 자동화 지원을 추가 해야 합니다. 자세한 내용은 [옵션 페이지에 대 한 자동화 지원을](../../extensibility/internals/automation-support-for-options-pages.md)합니다.  
  
## <a name="standard-automation-objects"></a>표준 자동화 개체  
 프로젝트에 대 한 자동화를 확장 하려면 또한 표준 automation 개체가 구현 (에서 파생 된 `IDispatch`) 옆에 있는 다른 프로젝트 개체를 구축 하 고 표준 메서드 및 속성을 구현 합니다. 표준 개체의 예로 같은 솔루션 계층에 삽입 되는 프로젝트 개체 `Projects`, `Project`를 `ProjectItem`, 및 `ProjectItems`합니다. 이러한 개체 및 가능한 경우 다른 조건은 의미 체계에 따라 프로젝트의 모든 새 프로젝트 형식을 구현 해야 합니다.  
  
 어떤 의미에서 이러한 개체는 반대 장점이 VSPackage 관련 프로젝트 개체를 제공합니다. 표준 automation 개체는 프로젝트가 동일한 개체를 지 원하는 다른 프로젝트와 마찬가지로 일반화 된 방식으로 사용할 수 있습니다. 따라서 추가 기능에서 일반에 대해 작성 된 `Project` 고 `ProjectItem` 개체 형식의 프로젝트에 대해 작동할 수 있습니다. 자세한 내용은 [프로젝트 모델링](../../extensibility/internals/project-modeling.md)합니다.
