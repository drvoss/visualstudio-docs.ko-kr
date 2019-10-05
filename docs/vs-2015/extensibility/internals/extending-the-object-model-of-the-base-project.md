---
title: 기본 프로젝트의 개체 모델 확장 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation object model, extending
- project subtypes, extending automation object model
- automation object model
ms.assetid: 2f95cc53-dff6-476c-bacd-500fb0ff7725
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7723881bce81824b66a936793175077a0ec67666
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68187159"
---
# <a name="extending-the-object-model-of-the-base-project"></a>기본 프로젝트의 개체 모델 확장
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

프로젝트 하위 형식에는 다음 위치에서 기본 프로젝트의 자동화 개체 모델을 확장 될 수 있습니다.  
  
- Project.Extender ("\<ProjectSubtypeName >")-이 통해 프로젝트 하위 형식에서 사용자 지정 메서드를 사용 하 여 개체를 제공 하는 <xref:EnvDTE.Project>합니다. 프로젝트 하위 형식 Automation Extender를 사용 하 여 노출할 수는 `Project` 개체입니다. <xref:EnvDTE80.IInternalExtenderProvider>주 프로젝트 하위 형식 aggregator에서 구현 된 인터페이스에 대 한 해당 개체를 제공 해야 합니다 `VSHPROPID_ExtObjectCATID` 에서 <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> (해당 하는 `itemid` VSITEMID_ROOT의 값에서 `VSITEMID`) CATID입니다.  
  
- ProjectItem.Extender ("\<ProjectSubtypeName >")-이 통해 특정에서 사용자 지정 메서드를 사용 하 여 개체를 제공 하는 프로젝트 하위 형식 <xref:EnvDTE.ProjectItem> 프로젝트 내에서 개체입니다. 프로젝트 하위 형식 Automation Extender를 사용 하 여이 개체를 노출 하 수 있습니다. 합니다 <xref:EnvDTE80.IInternalExtenderProvider> 주 프로젝트 하위 형식 aggregator에서 구현 된 인터페이스에 대 한 해당 개체를 제공 해야 합니다 `VSHPROPID_ExtObjectCATID` 에서 <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> (에 해당 하는 원하는 `VSITEMID`) CATID입니다.  
  
- Project.Properties –이 컬렉션의 구성 독립 속성을 표시 합니다 `Project` 개체입니다. 프로젝트 속성에 대 한 자세한 내용은 참조 하세요. <xref:EnvDTE.Project.Properties%2A>합니다. 프로젝트 하위 형식 Automation Extender를 사용 하 여이 컬렉션에 해당 속성을 추가할 수 있습니다. <xref:EnvDTE80.IInternalExtenderProvider> 주 프로젝트 하위 형식 aggregator에서 구현 된 인터페이스에 대 한 해당 개체를 제공 해야 합니다 `VSHPROPID_BrowseObjectCATID` VSHPROPID2에서 (에 해당 하는 `itemid` VSITEMID_ROOT의 값에서 <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>) CATID입니다.  
  
- Configuration.Properties –이 컬렉션의 프로젝트 (예: 디버그) 특정 구성에 대 한 구성 종속 속성을 노출합니다. 자세한 내용은 <xref:EnvDTE.Configuration>를 참조하세요. 프로젝트 하위 형식 Automation Extender를 사용 하 여이 컬렉션에 해당 속성을 추가할 수 있습니다. 합니다 <xref:EnvDTE80.IInternalExtenderProvider> 주 프로젝트 하위 형식 aggregator에서 구현 된 인터페이스의 CATID를 해당 개체를 제공 `VSHPROPID_CfgBrowseObjectCATID` (해당 하는 `itemid` 의 값 <xref:Microsoft.VisualStudio.VSConstants.VSITEMID>). <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>인터페이스 하나 구성 찾아보기 개체를 구분 하기 위해서 사용 됩니다.  
  
## <a name="see-also"></a>참고 항목  
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>
