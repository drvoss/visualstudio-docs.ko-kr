---
title: 기본 프로젝트의 개체 모델 확장 | Microsoft Docs
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- automation object model, extending
- project subtypes, extending automation object model
- automation object model
ms.assetid: 2f95cc53-dff6-476c-bacd-500fb0ff7725
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 607a63dc84db2811a4a2d158be07f158b849e1ad
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66329041"
---
# <a name="extend-the-object-model-of-the-base-project"></a>기본 프로젝트의 개체 모델 확장

프로젝트 하위 형식에는 다음 위치에서 기본 프로젝트의 자동화 개체 모델을 확장 될 수 있습니다.

- Project.Extender("\<ProjectSubtypeName>"): 이렇게 하면 프로젝트 하위 형식에서 사용자 지정 메서드를 사용 하 여 개체를 제공 하는 <xref:EnvDTE.Project> 개체입니다. 프로젝트 하위 형식 Automation Extender를 사용 하 여 노출할 수는 `Project` 개체입니다. <xref:EnvDTE80.IInternalExtenderProvider> 주 프로젝트 하위 형식 aggregator에서 구현 된 인터페이스에 대 한 해당 개체를 제공 해야 합니다 `VSHPROPID_ExtObjectCATID` 에서 <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> (해당 하는 `itemid` 값 [VSITEMID. 루트](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)) CATID입니다.

- ProjectItem.Extender("\<ProjectSubtypeName>"): 이렇게 하면 특정에서 사용자 지정 메서드를 사용 하 여 개체를 제공 하는 프로젝트 하위 형식 <xref:EnvDTE.ProjectItem> 프로젝트 내에서 개체입니다. 프로젝트 하위 형식 automation extender를 사용 하 여이 개체를 노출 하 수 있습니다. 합니다 <xref:EnvDTE80.IInternalExtenderProvider> 주 프로젝트 하위 형식 aggregator에서 구현 된 인터페이스에 대 한 해당 개체를 제공 해야 합니다 `VSHPROPID_ExtObjectCATID` 에서 <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> (에 해당 하는 원하는 <xref:Microsoft.VisualStudio.VSConstants.VSITEMID>) CATID입니다.

- Project.Properties: 이 컬렉션의 구성에 관계 없이 속성을 표시 합니다 `Project` 개체입니다. `Project` 속성에 대한 자세한 내용은 <xref:EnvDTE.Project.Properties%2A>를 참조하세요. 프로젝트 하위 형식 Automation Extender를 사용 하 여이 컬렉션에 해당 속성을 추가할 수 있습니다. <xref:EnvDTE80.IInternalExtenderProvider> 주 프로젝트 하위 형식 aggregator에서 구현 된 인터페이스에 대 한 해당 개체를 제공 해야 합니다 `VSHPROPID_BrowseObjectCATID` 에서 <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> (에 해당 하는 `itemid` 값 [VSITEMID 합니다. 루트](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)) CATID입니다.

- Configuration.Properties: 이 컬렉션 (예: 디버그) 특정 구성에 대 한 프로젝트의 구성에 종속 된 속성을 표시 합니다. 자세한 내용은 <xref:EnvDTE.Configuration>을 참조하세요. 프로젝트 하위 형식 Automation Extender를 사용 하 여이 컬렉션에 해당 속성을 추가할 수 있습니다. 합니다 <xref:EnvDTE80.IInternalExtenderProvider> 주 프로젝트 하위 형식 aggregator에서 구현 된 인터페이스의 CATID를 해당 개체를 제공 `VSHPROPID_CfgBrowseObjectCATID` (해당 하는 `itemid` 값 [VSITEMID 합니다. 루트](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)). <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject> 인터페이스 하나 구성 찾아보기 개체를 구분 하기 위해서 사용 됩니다.

## <a name="see-also"></a>참고자료

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>