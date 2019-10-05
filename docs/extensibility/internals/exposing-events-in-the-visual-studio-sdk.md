---
title: Visual Studio SDK의에서 이벤트 노출 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- events [Visual Studio], exposing
- automation [Visual Studio SDK], exposing events
ms.assetid: 70bbc258-c221-44f8-b0d7-94087d83b8fe
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 29fd9df90f58807ab3d48e077dcfa02d75eff837
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352598"
---
# <a name="expose-events-in-the-visual-studio-sdk"></a>Visual Studio SDK에는 이벤트를 노출 합니다.
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 있습니다 자동화를 사용 하 여 이벤트의 소스가 있습니다. 프로젝트 및 프로젝트 항목에 대 한 이벤트 소싱 하는 것이 좋습니다.

 자동화 소비자가 이벤트를 검색 합니다 <xref:EnvDTE.DTEClass.Events%2A> 개체 또는 <xref:EnvDTE.DTEClass.GetObject%2A> (예를 들어 `GetObject("EventObjectName")`). 환경 `IDispatch::Invoke` 를 사용 하 여 합니다 `DISPATCH_METHOD` 또는 `DISPATCH_PROPERTYGET` 이벤트를 반환 하는 플래그입니다.

 다음 프로세스에서는 VSPackage 관련 이벤트가 반환 되는 방법을 설명 합니다.

1. 환경을 시작합니다.

2. 아래에 있는 모든 값 이름이 레지스트리에서 읽고 합니다 **Automation**를 **AutomationEvents**, 및 **AutomationProperties** 모든 Vspackage, 및의 이름은 해당 하는 저장소 키를 테이블입니다.

3. 이 예제에서는 automation 소비자를 호출 `DTE.Events.AutomationProjectsEvents` 또는 `DTE.Events.AutomationProjectItemsEvents`합니다.

4. 환경은 테이블에서 문자열 매개 변수를 찾아서 해당 VSPackage를 로드 합니다.

5. 환경 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> 메서드 호출에이 예제에서는 전달 된 이름을 사용 하 여 `AutomationProjectsEvents` 또는 `AutomationProjectItemsEvents`합니다.

6. VSPackage와 같은 메서드를가지고 있는 루트 개체를 만듭니다 `get_AutomationProjectsEvents` 고 `get_AutomationProjectItemEvents` 다음 개체에 IDispatch 포인터를 반환 합니다.

7. Automation 호출에 전달 된 이름을 기반으로 적절 한 메서드를 호출 하는 환경.

8. `get_` 메서드 둘 다 구현 하는 다른 IDispatch 기반 이벤트 개체를 만듭니다를 `IConnectionPointContainer` 인터페이스 및 `IConnectionPoint` 인터페이스 및 반환은 `IDispatchpointer` 개체입니다.

   Automation을 사용 하 여 이벤트를 노출 하려면에 응답 해야 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> 및 조사식 레지스트리에 추가 하는 문자열입니다. 문자열에 기본 프로젝트 샘플 *BscProjectsEvents* 하 고 *BscProjectItemsEvents*합니다.

## <a name="registry-entries-from-the-basic-project-sample"></a>기본 프로젝트 샘플에서 레지스트리 항목
 이 섹션에서는 레지스트리에 자동화 이벤트 값을 추가 하는 위치를 보여 줍니다.

 **[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Packages\\<PkgGUID\>\AutomationEvents]**

 **AutomationProjectEvents** = 반환 된 `AutomationProjectEvents` 개체입니다.

 **AutomationProjectItemEvents** = 반환 된 `AutomationProjectItemsEvents` 개체입니다.

|이름|형식|범위|설명|
|----------|----------|-----------|-----------------|
|기본 (@)|REG_SZ|사용 되지 않는|사용되지 않습니다. 설명서에 대 한 데이터 필드를 사용할 수 있습니다.|
|*AutomationProjectsEvents*|REG_SZ|이벤트 개체의 이름입니다.|키 이름에만 관련이 있습니다. 설명서에 대 한 데이터 필드를 사용할 수 있습니다.<br /><br /> 이 예제에서는 기본 프로젝트 샘플에서 제공 됩니다.|
|*AutomationProjectItemEvents*|REG_SZ|이벤트 개체의 이름|키 이름에만 관련이 있습니다. 설명서에 대 한 데이터 필드를 사용할 수 있습니다.<br /><br /> 이 예제에서는 기본 프로젝트 샘플에서 제공 됩니다.|

 Automation 소비자 요청은 이벤트 개체의 경우 VSPackage에서 지 원하는 모든 이벤트에 대 한 메서드가 포함 된 루트 개체를 만듭니다. 환경에 적절 한 호출 `get_` 이 개체에서 메서드. 예를 들어 경우 `DTE.Events.AutomationProjectsEvents` 호출 되는 `get_AutomationProjectsEvents` 루트 개체에는 메서드가 호출 됩니다.

 ![Visual Studio 프로젝트 이벤트](../../extensibility/internals/media/projectevents.gif "ProjectEvents") 이벤트에 대 한 자동화 모델

 클래스 `CProjectEventsContainer` 에 대 한 소스 개체를 나타내는 *BscProjectsEvents*, 및 `CProjectItemsEventsContainer` 에 대 한 소스 개체를 나타내는 *BscProjectItemsEvents*합니다.

 대부분의 경우에서 대부분의 이벤트 개체를 필터 개체를 사용 하기 때문에 모든 이벤트 요청에 대해 새 개체를 반환 해야 합니다. 이벤트를 발생 하는 경우 이벤트 처리기가 호출 되 고 있는지 확인 하려면이 필터를 확인 합니다.

 *AutomationEvents.h* 하 고 *AutomationEvents.cpp* 선언 및 다음 표에 클래스의 구현을 포함 합니다.

|클래스|설명|
|-----------|-----------------|
|`CAutomationEvents`|검색 된 이벤트 루트 개체를 구현 하는 `DTE.Events` 개체입니다.|
|`CProjectsEventsContainer` 및 `CProjectItemsEventsContainer`|해당 이벤트를 발생 시키는 이벤트 소스 개체를 구현 합니다.|

 다음 코드 예제에서는 이벤트 개체에 대 한 요청에 응답 하는 방법을 보여 줍니다.

```cpp
STDMETHODIMP CVsPackage::GetAutomationObject(
    /* [in]  */ LPCOLESTR       pszPropName,
    /* [out] */ IDispatch **    ppIDispatch)
{
    ExpectedPtrRet(ppIDispatch);
    *ppIDispatch = NULL;

    if (_wcsicmp(pszPropName, g_wszAutomationProjects) == 0)
        //Is the requested name our Projects object?
    {
        return GetAutomationProjects(ppIDispatch);
        // Gets our Projects object.
    }
    else if (_wcsicmp(pszPropName, g_wszAutomationProjectsEvents) == 0)
        //Is the requested name our ProjectsEvents object?
    {
        return CAutomationEvents::GetAutomationEvents(ppIDispatch);
          // Gets our ProjectEvents object.
    }
    else if (_wcsicmp(pszPropName, g_wszAutomationProjectItemsEvents) == 0)  //Is the requested name our ProjectsItemsEvents object?
    {
        return CAutomationEvents::GetAutomationEvents(ppIDispatch);
          // Gets our ProjectItemsEvents object.
    }
    return E_INVALIDARG;
}
```

 위의 코드에서 `g_wszAutomationProjects` 프로젝트 컬렉션의 이름입니다 (*FigProjects*), `g_wszAutomationProjectsEvents` (*FigProjectsEvents*) 및 `g_wszAutomationProjectItemsEvents` (*FigProjectItemEvents* )은 프로젝트 이벤트의 이름 및 프로젝트 항목은 VSPackage 구현에서 제공 하는 이벤트입니다.

 이벤트 개체는 같은 중앙 위치에서 검색 된 `DTE.Events` 개체입니다. 이러한 방식으로 모든 이벤트 개체 있도록 그룹화 되어 함께 최종 사용자는 특정 이벤트를 찾으려면 전체 개체 모델을 탐색할 필요가 없습니다. 이 수 있습니다 시스템 전체 이벤트에 대 한 사용자 고유의 코드를 구현 하도록 요구 하는 대신 특정 VSPackage 개체를 제공 합니다. 그러나 최종 사용자에 대 한 사용자를 찾아야에 대 한 이벤트에 `ProjectItem` 인터페이스 명확 하지 않기 즉시 해당 이벤트 개체가 검색 됩니다.

## <a name="see-also"></a>참고자료
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>
