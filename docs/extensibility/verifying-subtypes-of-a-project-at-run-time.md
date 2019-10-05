---
title: 런타임에 프로젝트의 하위 형식 확인 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes
- check subtypes
ms.assetid: b87780ec-36a3-4e9a-9ee2-7abdc26db739
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 033f2971d0b8acb0390765f240a86a5ff543c353
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66310695"
---
# <a name="verify-subtypes-of-a-project-at-run-time"></a>런타임에 프로젝트의 하위 형식 확인
사용자 지정 프로젝트 하위 형식에 따라 달라 지는 VSPackage를 검색할 하위 형식 없으면 정상적으로 실패 하는 하위 유형을 논리를 포함 해야 합니다. 다음 절차에는 지정 된 하위 있는지 확인 하는 방법을 보여 줍니다.

### <a name="to-verify-the-presence-of-a-subtype"></a>하위 형식이 있는지 확인 하려면

1. 프로젝트 계층 구조는 프로젝트 및 솔루션 개체에서 가져올를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> VSPackage에 다음 코드를 추가 하 여 개체입니다.

    ```csharp
    EnvDTE.DTE dte;
    dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));

    EnvDTE.Project project;
    project = dte.Solution.Projects.Item(1);

    IVsSolution solution;
    solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));

    IVsHierarchy hierarchy;
    hierarchy = solution.GetProjectOfUniqueName(project.UniqueName);

    ```

2. 계층을 캐스팅 합니다 <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected> 인터페이스입니다.

    ```csharp
    IVsAggregatableProjectCorrected AP;
    AP = hierarchy as IVsAggregatableProjectCorrected;

    ```

3. 호출 하 여 프로젝트 형식 Guid의 목록을 가져옵니다는 <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected.GetAggregateProjectTypeGuids%2A>합니다.

    ```csharp
    string projTypeGuids = AP.GetAggregateProjectTypeGuids().ToUpper();

    ```

4. 지정 된 하위의 GUID 목록을 확인 합니다.

    ```csharp
    // Replace the string "MyGUID" with the GUID of the subtype.
    string guidMySubtype = "MyGUID";
    if (projTypeGuids.IndexOf(guidMySubtype) > 0)
    {
        // The specified subtype is present.
    }
    ```

## <a name="see-also"></a>참고자료
- [프로젝트 하위 형식](../extensibility/internals/project-subtypes.md)
- [프로젝트 하위 형식 디자인](../extensibility/internals/project-subtypes-design.md)
- [프로젝트 하위 형식으로 확장 하는 메서드와 속성](../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)