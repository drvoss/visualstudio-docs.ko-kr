---
title: 프로젝트 하위 형식의 초기화 시퀀스 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, initialization sequence
ms.assetid: f657f8c3-5e68-4308-9971-e81e3099ba29
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5f8b256e25bc9a63093d14eab50d7628c76558b9
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66349848"
---
# <a name="initialization-sequence-of-project-subtypes"></a>프로젝트 하위 형식의 초기화 시퀀스
기본 프로젝트 팩터리 구현을 호출 하 여 프로젝트를 생성 하는 환경 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>합니다. 프로젝트 하위 형식의 생성 환경을 프로젝트 파일의 확장에 대 한 프로젝트 형식 GUID 목록이 비어 있지 않은지 확인 하는 경우 시작 합니다. 프로젝트 파일 확장명과 프로젝트 GUID 프로젝트 인지 여부를 지정 된 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 또는 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 프로젝트 형식. 예를 들어,.vbproj 확장명 및 식별 하는 {F184B08F-C81C-45F6-A57F-5ABD9991F28F}는 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 프로젝트입니다.

## <a name="environments-initialization-of-project-subtypes"></a>프로젝트 하위 형식의 환경 초기화
 다음 절차에는 여러 프로젝트 하위 형식으로 집계 하는 프로젝트 시스템에 대 한 초기화 시퀀스 자세히 설명 합니다.

1. 환경 기본 프로젝트의 호출 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>, 및 해당 프로젝트의 프로젝트 파일을 구문 분석 하는 동안 집계 프로젝트 형식 Guid 목록 아닌지 검색 `null`합니다. 프로젝트에서 프로젝트를 직접 만드는 것을 중단 합니다.

2. 프로젝트를 호출 하 여 `QueryService` 온 <xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject> 환경의 구현을 사용 하 여 프로젝트 하위 형식에 만들려는 서비스는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> 메서드. 이 메서드 내에서 환경에서는 구현에 재귀 함수 호출 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> 및 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A> 프로젝트 목록을 탐색은 그 중에 메서드 가장 바깥쪽 프로젝트 하위 형식부터 Guid를 입력 합니다.

     다음 초기화 단계를 자세히 설명 합니다.

    1. 환경의 구현의 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> 메서드 호출을 `HrCreateInnerProj` 다음 함수 선언과 함께 메서드:

         \<CodeContentPlaceHolder>0</CodeContentPlaceHolder>

         이 함수가 호출 될 때 처음으로 즉, 가장 바깥쪽 프로젝트 하위 형식에 대 한 매개 변수 `pOuter` 하 고 `pOwner` 변수로 전달 됩니다 `null` 함수가 가장 바깥쪽 프로젝트 하위 형식 설정 `IUnknown` 에 `pOuter`합니다.

    2. 다음 호출 환경 `HrCreateInnerProj` 목록의 두 번째 프로젝트 형식 GUID 사용 하 여 함수입니다. 이 GUID는 집계 시퀀스의 기본 프로젝트에서 단계별 실행 두 번째 내부 프로젝트 하위 형식에 해당 합니다.

    3. `pOuter` 이제 가리키는 합니다 `IUnknown` 가장 바깥쪽 프로젝트 하위 형식의 및 `HrCreateInnerProj` 의 구현이 호출 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> 구현에 대 한 호출 뒤에 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A>입니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> 제어를 전달 하는 메서드 `IUnknown` 가장 바깥쪽 프로젝트 하위 형식의 `pOuter`합니다. 여기에 해당 집계 프로젝트 개체를 만들려면 소유 프로젝트 (내부 프로젝트 하위 형식) 해야 합니다. 에 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> 포인터를 전달 하는 메서드 구현을 `IUnknown` 집계 되는 내부 프로젝트의 합니다. 이러한 두 메서드 집계 개체를 만들고 프로젝트 하위 형식 자체에 참조 횟수를 보유 하 끝나지 않습니다 있도록 COM 집계 규칙을 따르도록 구현 해야 합니다.

    4. `HrCreateInnerProj` 구현이 호출 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>합니다. 이 방법에서는 프로젝트 하위 형식 초기화 작업을 수행합니다. 솔루션 이벤트의 예를 들어를 등록할 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A>합니다.

    5. `HrCreateInnerProj` 목록의 마지막 GUID (기본 프로젝트)에 도달할 때까지 재귀적으로 호출 됩니다. 이러한 호출의 각각에 대 한 c ~ d 단계를 반복 됩니다. `pOuter` 가장 바깥쪽 프로젝트 하위 형식 가리키는 `IUnknown` 각 집계 수준에 대 한 합니다.

## <a name="example"></a>예제

다음 예제에서는 대략적으로 표시에서 프로그래밍 방식으로 프로세스를 자세히 설명 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> 메서드 환경에서 구현 됩니다. 코드는 예 일뿐입니다. 컴파일할 수 없습니다 및 명확성을 위해 제거 된 모든 오류를 확인 합니다.

```cpp
HRESULT CreateAggregateProject
(
    LPCOLESTR lpstrGuids,
    LPCOLESTR pszFilename,
    LPCOLESTR pszLocation,
    LPCOLESTR pszName,
    VSCREATEPROJFLAGS grfCreateFlags,
    REFIID iidProject,
    void **ppvProject)
{
    HRESULT hr = NOERROR;
    CComPtr<IUnknown> srpunkProj;
    CComPtr<IVsAggregatableProject> srpAggProject;
    CComBSTR bstrGuids = lpstrGuids;
    BOOL fCanceled = FALSE;
    *ppvProject = NULL;

    HrCreateInnerProj(
         bstrGuids, NULL, NULL, pszFilename, pszLocation,
         pszName, grfCreateFlags, &srpunkProj, &fCanceled);
    srpunkProj->QueryInterface(
        IID_IVsAggregatableProject, (void **)&srpAggProject));
    srpAggProject->OnAggregationComplete();
    srpunkProj->QueryInterface(iidProject, ppvProject);
}

HRESULT HrCreateInnerProj
(
    WCHAR *pwszGuids,
    IUnknown *pOuter,
    IVsAggregatableProject *pOwner,
    LPCOLESTR pszFilename,
    LPCOLESTR pszLocation,
    LPCOLESTR pszName,
    VSCREATEPROJFLAGS grfCreateFlags,
    IUnknown **ppInner,
    BOOL *pfCanceled
)
{
    HRESULT hr = NOERROR;
    CComPtr<IUnknown> srpInner;
    CComPtr<IVsAggregatableProject> srpAggInner;
    CComPtr<IVsProjectFactory> srpProjectFactory;
    CComPtr<IVsAggregatableProjectFactory> srpAggPF;
    GUID guid = GUID_NULL;
    WCHAR *pwszNextGuids = wcschr(pwszGuids, L';');
    WCHAR wszText[_MAX_PATH+150] = L"";

    if (pwszNextGuids)
    {
        *pwszNextGuids++ = 0;
    }

    CLSIDFromString(pwszGuids, &guid);
    GetProjectTypeMgr()->HrGetProjectFactoryOfGuid(
        guid, &srpProjectFactory);
    srpProjectFactory->QueryInterface(
        IID_IVsAggregatableProjectFactory,
        (void **)&srpAggPF);
    srpAggPF->PreCreateForOuter(pOuter, &srpInner);
    srpInner->QueryInterface(
        IID_IVsAggregatableProject, (void **)&srpAggInner);

    if (pOwner)
    {
        IfFailGo(pOwner->SetInnerProject(srpInner));
    }

    if (pwszNextGuids)
    {
        CComPtr<IUnknown> srpNextInner;
        HrCreateInnerProj(
            pwszNextGuids, pOuter ? pOuter : srpInner,
            srpAggInner, pszFilename, pszLocation, pszName,
            grfCreateFlags, &srpNextInner, pfCanceled);
    }

    return srpAggInner->InitializeForOuter(
        pszFilename, pszLocation, pszName, grfCreateFlags,
        IID_IUnknown, (void **)ppInner, pfCanceled);
}
```

## <a name="see-also"></a>참고 항목

- <xref:Microsoft.VisualStudio.Shell.Flavor>
- [프로젝트 하위 형식](../../extensibility/internals/project-subtypes.md)