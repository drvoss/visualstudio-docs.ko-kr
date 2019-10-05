---
title: 파일 열기 명령을 사용 하 여 파일을 표시 합니다. | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open File command
- Open File command
- persistence, supporting Open File command
ms.assetid: 4fff0576-b2f3-4f17-9769-930f926f273c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 19fda87f0e2692d30b9a99777ca11edd7b3906f0
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66324335"
---
# <a name="display-files-by-using-the-open-file-command"></a>파일 열기 명령을 사용 하 여 파일을 표시 합니다.
다음 단계는 IDE가 처리 하는 방법을 설명 합니다 **열려 있는 파일** 명령에서 사용할 수 있는 **파일** 메뉴에서 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]합니다. 또한 단계는 프로젝트가이 명령에서 발생 하는 호출에 응답 해야 하는 방법을 설명 합니다.

 클릭할 경우는 **파일 열기** 명령을 **파일** 메뉴에서 파일을 선택 하 고는 **파일 열기** 대화 상자에서 다음 프로세스가 발생:

1. 문서 테이블 실행을 사용 하 여 IDE 파일이 프로젝트에서 열려 이미 있는지 여부를 결정 합니다.

    - 파일이 열려 있으면 IDE 창 자신에 게 합니다.

    - IDE를 호출 하는 파일이 열려 있지 않으면 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> 각 프로젝트는 프로젝트 파일을 열 수를 확인 하려면을 쿼리 합니다.

        > [!NOTE]
        > 프로젝트 구현의 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>에는 프로젝트 파일을 엽니다 수준을 나타내는 우선 순위 값을 제공 합니다. 우선 순위 값을 제공 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> 열거형입니다.

2. 각 프로젝트는 중요도 나타내는 우선 순위를 사용 하 여 응답 파일을 열고 프로젝트에 배치 합니다.

3. IDE는 다음 조건을 사용 하 여 프로젝트 파일을 엽니다 결정 합니다.

    - 가장 높은 우선 순위를 사용 하 여 응답 하는 프로젝트 (`DP_Intrinsic`) 파일을 엽니다. 둘 이상의 프로젝트에이 우선 순위를 사용 하 여 응답 응답할 첫 번째 프로젝트 파일을 엽니다.

    - 프로젝트가 없습니다. 가장 높은 우선 순위를 사용 하 여 응답 하는 경우 (`DP_Intrinsic`), 활성 프로젝트 파일을 열고 모든 프로젝트 동일 하 고 낮은 우선 순위를 사용 하 여 응답 합니다. 프로젝트가 활성 상태인 경우 응답할 첫 번째 프로젝트 파일을 엽니다.

    - 프로젝트가 없습니다. 파일의 소유권을 요구 하는 경우 (`DP_Unsupported`), 기타 파일 프로젝트 파일을 엽니다.

         프로젝트 값을 사용 하 여 항상 응답 기타 파일 프로젝트의 인스턴스를 만든 경우 `DP_CanAddAsExternal`합니다. 이 값은 프로젝트 파일을 열 수를 나타냅니다. 이 프로젝트는 다른 프로젝트에 있지 않은 열려 있는 파일을 보관 하는 데 사용 됩니다. 이 프로젝트의 항목 목록을 유지 되지 않습니다. 이 프로젝트에 표시 됩니다 **솔루션 탐색기** 만 사용 하는 경우 파일을 열려고 합니다.

         기타 파일 프로젝트 파일을 열 수를 나타내지 않는 경우 프로젝트의 인스턴스는 만들어지지 않습니다. 이 경우 IDE 기타 파일 프로젝트의 인스턴스를 만듭니다 및 프로젝트 파일을 열고를 알려 줍니다.

4. IDE는 프로젝트 파일을 엽니다 결정을 하는 즉시 호출한는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> 해당 프로젝트는 메서드.

5. 프로젝트에는 다음 프로젝트별 편집기 또는 표준 편집기를 사용 하 여 파일을 여는 옵션을 있습니다. 자세한 내용은 [방법: 프로젝트별 편집기 열기](../../extensibility/how-to-open-project-specific-editors.md) 고 [방법: 표준 편집기 열기](../../extensibility/how-to-open-standard-editors.md), 각각.

## <a name="see-also"></a>참고자료
- [연결 프로그램 명령을 사용 하 여 파일을 표시 합니다.](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)
- [열기 및 프로젝트 항목 저장](../../extensibility/internals/opening-and-saving-project-items.md)
- [방법: 프로젝트별 편집기 열기](../../extensibility/how-to-open-project-specific-editors.md)
- [방법: 표준 편집기 열기](../../extensibility/how-to-open-standard-editors.md)