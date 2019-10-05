---
title: '방법: 라이브러리의 기호 식별 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Call Browser tool, identifying symbols in the library
- Call Browser tool
ms.assetid: 8fb0de61-71e7-42d1-8b41-2ad915474384
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 550bd16fec0dde508642a362835cde1e2d1637d5
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66328700"
---
# <a name="how-to-identify-symbols-in-a-library"></a>방법: 라이브러리의 기호 식별
기호 검색 도구는 기호의 계층적 뷰를 표시합니다. 기호는 네임 스페이스, 개체, 클래스, 클래스 멤버 및 다른 언어 요소를 나타냅니다.

 계층의 각 기호를 기호 라이브러리에 의해 전달 된 탐색 정보로 식별할 수 있습니다는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 다음 인터페이스를 통해 개체 관리자:

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfoNode>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes>.

 계층에 있는 기호의 위치 기호를 구분합니다. 기호 검색 도구를 특정 기호로 이동할 수 있습니다. 기호를 고유 하 고 정규화 된 경로 위치를 결정합니다. 경로 있는 각 요소는 노드입니다. 경로 최상위 노드를 사용 하 여 시작한 특정 기호를 사용 하 여 종료 합니다. 예를 들어 M1 방법은 C1 클래스의 멤버 이며 C1 N1 네임 스페이스에 있는 경우 전체 M1 메서드의 경로가 N1. C1 합니다. M1 합니다. 이 경로는 3 개의 노드가 포함 됩니다. N1, C1 및 M1 합니다.

 탐색 정보를 사용 하는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 찾고 선택한 유지 선택한 기호를 계층 구조에서 개체 관리자입니다. 다른 검색 도구에서 이동 수 있습니다. 사용 하는 동안 **개체 브라우저** 에서 기호를 이동할를 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 프로젝트 메서드를 마우스 오른쪽 단추로 클릭 하 고 시작할 수 있습니다 합니다 **호출 브라우저** 메서드 호출 그래프에 표시할 도구입니다.

 두 가지 형식 기호 위치를 설명합니다. 정규 형식 기호 정규화 된 경로 기반으로 합니다. 계층에서 기호의 고유 위치를 나타냅니다. 기호 검색 도구 무관 합니다. 정규 형식 정보를 얻는 합니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] manager 호출은 개체 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> 메서드. 프레젠테이션 폼 특정 기호 검색 도구 내에서 기호의 위치를 설명 합니다. 기호의 위치 계층 구조에서 다른 기호의 위치에 상대적입니다. 지정된 된 기호 하나만 정식 경로 이지만 프레젠테이션 경로가 여러 개 있을 수 있습니다. 예를 들어 C1 클래스 C2 클래스에서 상속 되며 두 클래스 모두 N1 네임 스페이스에는 **개체 브라우저** 다음 계층적 트리를 표시 합니다.

```
N1
    C1
        Bases and Interfaces
            C2
    C2
        Bases and Interfaces
. . . . . . . . . . .

```

 이 예제에서는 C2 클래스의 정식 경로 N1 + C2입니다. C2의 프레젠테이션 경로 C1과 "자료 및 인터페이스" 노드를 포함 합니다. N1 + C1 + 기본 "및" 인터페이스 + C2입니다.

 개체 관리자 호출 프레젠테이션 폼 정보를 얻는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A> 메서드.

## <a name="to-obtain-canonical-and-presentation-forms-information"></a>정식 가져오려고 프레젠테이션 정보 이며

1. <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> 메서드를 구현합니다.

     개체 관리자 기호의 정식 경로에 포함 된 노드의 목록을 가져오려면이 메서드를 호출 합니다.

    ```vb
    Public Function EnumCanonicalNodes(ByRef ppEnum As Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes) As Integer
        Dim EnumNavInfoNodes As CallBrowserEnumNavInfoNodes = _New CallBrowserEnumNavInfoNodes(m_strMethod)
        ppEnum = CType(EnumNavInfoNodes, IVsEnumNavInfoNodes)
        Return 0
    End Function
    ```

    ```csharp
    public int EnumCanonicalNodes(out Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes ppEnum)
    {
        CallBrowserEnumNavInfoNodes EnumNavInfoNodes =
            new CallBrowserEnumNavInfoNodes(m_strMethod);
        ppEnum = (IVsEnumNavInfoNodes)(EnumNavInfoNodes);
        return 0;
    }

    ```

2. <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A> 메서드를 구현합니다.

     개체 관리자 기호의 프레젠테이션 경로에 포함 된 노드의 목록을 가져오려면이 메서드를 호출 합니다.

## <a name="see-also"></a>참고자료
- [기호 검색 도구를 지원 합니다.](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [방법: 개체 관리자를 사용 하 여 라이브러리를 등록 합니다.](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)
- [방법: 개체 관리자에 게 라이브러리에서 제공 하는 기호 목록을 표시 합니다.](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)