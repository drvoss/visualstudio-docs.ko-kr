---
title: Visual Studio에서 작업 영역 파일 컨텍스트 | Microsoft Docs
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 36f986db6f2c7b483b46060e1f514acc8dd9e758
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62952817"
---
# <a name="workspace-file-contexts"></a>작업 영역 파일 컨텍스트

에 대 한 모든 정보 [폴더 열기](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) 작업 영역 "파일 상황에 맞는" 구현 하는 공급자에서 생성 되는 <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider> 인터페이스입니다. 이러한 확장 패턴 폴더에 대 한 표시 될 수 있습니다 또는 MSBuild 파일 및 메이크파일을 읽을 파일 파일 컨텍스트를 정의 하 게 필요한 정보를 누적 하기 위해 패키지 종속성 등을 검색 합니다. 자체로 파일 컨텍스트 작업을 수행 하지 않지만 대신 다른 확장 한 다음 작업을 수행할 수 있는 데이터를 제공 합니다.

각 <xref:Microsoft.VisualStudio.Workspace.FileContext> 에 `Guid` 연결 된 데이터의 형식을 식별 하 고 전달 합니다. 이 작업 영역을 사용 하 여 `Guid` 를 통해 데이터를 사용 하는 확장을 사용 하 여 일치 하는 나중에 <xref:Microsoft.VisualStudio.Workspace.FileContext.Context> 속성입니다. 파일 컨텍스트 공급자는 파일 컨텍스트를 식별 하는 메타 데이터를 사용 하 여 내보낸 `Guid`의데이터를 생성할 수 있습니다.

정의 되 면 파일 컨텍스트는 임의 개수의 파일 또는 작업 영역에서 폴더를 사용 하 여 연결할 수 있습니다. 지정 된 파일이 나 폴더 개수에 관계 없이 파일 컨텍스트를 사용 하 여 연결할 수 있습니다. 다 대 다 관계입니다.

파일 컨텍스트에 대 한 가장 일반적인 시나리오를 빌드, 디버그 및 언어 서비스 관련 되어 있습니다. 자세한 내용은 이러한 시나리오와 관련 된 다른 항목을 참조 하세요.

## <a name="file-context-lifecycle"></a>파일 컨텍스트 수명 주기

에 대 한 수명 주기를 `FileContext` 명확 하지 않습니다. 언제 든 지 상황에 맞는 형식의 일부 집합에 대 한 구성 요소를 비동기적으로 요청할 수 있습니다. 요청 컨텍스트 형식 중 일부 하위 집합을 지 원하는 공급자를 쿼리할 수 됩니다. 합니다 `IWorkspace` 인스턴스는 소비자 및 공급자를 통해 간의 중재자 역할을 <xref:Microsoft.VisualStudio.Workspace.IWorkspace.GetFileContextsAsync%2A> 메서드. 소비자는 컨텍스트를 요청 하 고 컨텍스트를 기반으로, 다른 컨텍스트를 요청 하 고 장기적인된 참조를 유지 관리 될 수 있습니다 하는 동안 몇 가지 단기 작업을 수행할 수 있습니다.

파일 컨텍스트 구식이를 일으키는 파일에 변경 내용이 발생할 수 있습니다. 공급자에서 이벤트를 발생 시킬 수는 `FileContext` 업데이트의 소비자에 게 알립니다. 예를 들어, 일부 파일에 대 한 제공 되는 빌드 컨텍스트는 해당 컨텍스트를 무효화 하는 디스크에 대 한 변경 하지만 하는 경우 원래 생산자 이벤트를 호출 수입니다. 여전히 참조 하는 소비자 `FileContext` 새 다시 쿼리하여 수 `FileContext`입니다.

>[!NOTE]
>소비자에 게 푸시 모델이 없는 합니다. 소비자는 공급자의 새 알림을 받을지 않습니다 `FileContext` 요청 후 합니다.

## <a name="expensive-file-context-computations"></a>비용이 많이 드는 파일 컨텍스트 계산

디스크에서 읽기 파일 콘텐츠 공급자 파일 간의 관계를 해결 해야 하는 경우에 특히 많은 비용을 들 수 있습니다. 예를 들어, 일부 소스 파일의 파일 컨텍스트를 쿼리할 수 있는 공급자 이지만 파일 컨텍스트 프로젝트 파일에서 메타 데이터에 따라 달라 집니다. 프로젝트 파일을 구문 분석 또는 MSBuild를 사용 하 여 계산 비용이 많이 듭니다. 대신 확장을 내보낼 수는 `IFileScanner` 만들려면 `FileDataValue` 데이터 작업 영역 인덱싱 중입니다. 이제 파일 컨텍스트를 요청 하는 경우는 `IFileContextProvider` 해당 인덱싱된 데이터에 대해 빠르게 쿼리할 수 있습니다. 인덱싱에 대 한 자세한 내용은 참조는 [작업 영역 인덱싱](workspace-indexing.md) 항목입니다.

>[!WARNING]
>다른 방법에 주의 하세요 프로그램 `FileContext` 계산 비용이 많이 들 수 있습니다. 일부 UI 상호 작용은 동기식 이며 많은 양의 의존 `FileContext` 요청 합니다. 편집기 탭을 열고 열을 포함 하는 예제는 **솔루션 탐색기** 상황에 맞는 메뉴입니다. 이러한 작업 요청을 입력 하는 여러 빌드 컨텍스트를 확인 합니다.

## <a name="file-context-related-apis"></a>파일 컨텍스트 관련 Api

- <xref:Microsoft.VisualStudio.Workspace.FileContext> 데이터 및 메타 데이터를 보유합니다.
- <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider> 및 <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider`1> 파일 컨텍스트를 만듭니다.
- <xref:Microsoft.VisualStudio.Workspace.ExportFileContextProviderAttribute> 파일 컨텍스트 공급자를 내보냅니다.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspace.GetFileContextsAsync%2A> 소비자에 대 한 파일 컨텍스트를 가져오는 데 사용 됩니다.
- <xref:Microsoft.VisualStudio.Workspace.Build.BuildContextTypes> 폴더 열기를 사용 하는 빌드 컨텍스트 형식을 정의 합니다.

## <a name="file-context-actions"></a>파일 컨텍스트 작업

하지만 `FileContext` 자체는 일부 파일에 대 한 데이터는 <xref:Microsoft.VisualStudio.Workspace.IFileContextAction> express 및 해당 데이터 작업을 수행 하는 방법. `IFileContextAction` 해당 사용에서 유연 합니다. 빌드 및 디버그 되는 가장 일반적인 사례 2.

## <a name="reporting-progress"></a>진행률 보고

합니다 <xref:Microsoft.VisualStudio.Workspace.IFileContextActionBase.ExecuteAsync%2A> 메서드에 전달 됩니다 `IProgress<IFileContextActionProgressUpdate>`, 하지만 해당 형식으로 인수를 사용할 수 없습니다. `IFileContextActionProgressUpdate` 빈 인터페이스를 호출 하는 방식 `IProgress<IFileContextActionProgressUpdate>.Report(IFileContextActionProgressUpdate)` throw 할 수 있습니다 `NotImplementedException`합니다. 대신는 `IFileContextAction` 인수 시나리오에 대 한 필요에 따라 다른 형식으로 캐스팅 해야 합니다.

Visual Studio에서 제공 하는 형식에 대 한 내용은 각 시나리오의 설명서를 참조 합니다.

## <a name="file-context-action-related-apis"></a>파일 컨텍스트 작업 관련 Api

- <xref:Microsoft.VisualStudio.Workspace.IFileContextAction> 일부 동작에 따라 실행을 `FileContext`입니다.
- <xref:Microsoft.VisualStudio.Workspace.IFileContextActionProvider> 인스턴스를 만듭니다 `IFileContextAction`합니다.
- <xref:Microsoft.VisualStudio.Workspace.ExportFileContextActionProviderAttribute> 형식을 내보냅니다 `IWorkspaceProviderFactory<IFileContextActionProvider>`합니다.

## <a name="file-watching"></a>파일 감시

작업 영역 파일 변경 알림을 수신 대기 하 고 제공 된 <xref:Microsoft.VisualStudio.Workspace.IFileWatcherService> 를 통해 <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetFileWatcherService%2A>합니다. "ExcludedItems" 설정이 일치 하는 파일에는 파일 알림 이벤트를 생성 하지 않습니다. 이벤트 임계값 알림 단순화 하 고 중복 감소에 사용 됩니다. 파일 변경에 반응 해야 할 때이 서비스에 가입 해야 합니다.

>[!TIP]
>작업 영역의 [인덱싱 서비스](workspace-indexing.md) 기본적으로 파일 이벤트를 구독 합니다. 파일 추가 및 수정 관련 하면 `IFileScanner`의이벤트를 해당 파일에 대 한 새 데이터에 대 한 호출 합니다. 파일 삭제에는 인덱싱된 데이터가 제거 됩니다. 구독 하지 않아도 됩니다. 프로그램 `IFileScanner` 파일 감시자 서비스.

## <a name="next-steps"></a>다음 단계

* [인덱싱](workspace-indexing.md) -작업 영역 인덱싱 수집 및 작업 영역에 대 한 정보를 유지 합니다.
* [작업 영역](workspaces.md) -작업 영역 개념 및 저장소 설정 검토 합니다.
