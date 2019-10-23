---
title: 프로젝트 모델링 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], implementing project objects
- project models, automation
ms.assetid: c8db8fdb-88c1-4b12-86fe-f3c30a18f9ee
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 42e810a36478e49a578c6713d20f1bfc6be98309
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725568"
---
# <a name="project-modeling"></a>프로젝트 모델링
프로젝트에 대 한 자동화를 제공 하는 다음 단계는 표준 프로젝트 개체 (<xref:EnvDTE.Projects> 및 `ProjectItems` 컬렉션)를 구현 하는 것입니다. `Project` 및 <xref:EnvDTE.ProjectItem> 개체 및 구현에 고유한 나머지 개체입니다. 이러한 표준 개체는 Dteinternal .h 파일에 정의 되어 있습니다. 표준 개체의 구현은 BscPrj 샘플에서 제공 됩니다. 이러한 클래스를 모델로 사용 하 여 다른 프로젝트 형식의 project 개체와 나란히 있는 고유한 표준 프로젝트 개체를 만들 수 있습니다.

 Automation 소비자는 <xref:EnvDTE.Solution> ("`<UniqueProjName>")` 및 <xref:EnvDTE.ProjectItems> (`n`)를 호출할 수 있다고 가정 합니다. 여기서 n은 솔루션에서 특정 프로젝트를 가져오기 위한 인덱스 번호입니다. 이 자동화 호출로 인해 환경에서 적절 한 프로젝트 계층 구조에 대 한 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A>를 호출 하 고 VSITEMID_ROOT를 ItemID 매개 변수로 전달 하 고 VSHPROPID_ExtObject를 VSHPROPID 매개 변수로 전달 합니다. `IVsHierarchy::GetProperty`는 구현한 핵심 `Project` 인터페이스를 제공 하는 자동화 개체에 대 한 `IDispatch` 포인터를 반환 합니다.

 다음은 `IVsHierarchy::GetProperty` 구문입니다.

 `HRESULT GetProperty (`

 `VSITEMID` `itemid`

 `VSHPROPID` `propid`

 `VARIANT` `*pvar`

 `);`

 프로젝트는 중첩을 수용 하 고 컬렉션을 사용 하 여 프로젝트 항목 그룹을 만듭니다. 계층 구조는 다음과 같습니다.

```
Projects
  |- Project
      |- ProjectItems (a collection of ProjectItem)
          |- ProjectItem (single object) or ProjectItems (another collection)
```

 중첩은 `ProjectItems` 컬렉션이 중첩 된 개체를 포함할 수 있기 때문에 <xref:EnvDTE.ProjectItem> 개체를 동시에 <xref:EnvDTE.ProjectItems> 수집할 수 있음을 의미 합니다. 기본 프로젝트 샘플에서는 이러한 중첩을 보여 주지 않습니다. @No__t_0 개체를 구현 하 여 전체 자동화 모델의 디자인에 대 한 특징을 나타내는 트리 형식의 구조에 참여 합니다.

 프로젝트 자동화는 다음 다이어그램의 경로를 따릅니다.

 ![Visual Studio 프로젝트 개체](../../extensibility/internals/media/projectobjects.gif "ProjectObjects") 프로젝트 자동화

 @No__t_0 개체를 구현 하지 않으면 환경에서 프로젝트 이름만 포함 하는 제네릭 `Project` 개체를 반환 합니다.

## <a name="see-also"></a>참조
- <xref:EnvDTE.Projects>
- <xref:EnvDTE.ProjectItem>
- <xref:EnvDTE.ProjectItems>