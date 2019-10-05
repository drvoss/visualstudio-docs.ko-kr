---
title: Visual Studio에서 작업 영역 | Microsoft 문서
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 011781b434c4d005e473c5f97c60a9269dc5d034
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62952765"
---
# <a name="workspaces"></a>작업 영역

작업 영역은 Visual Studio에서 파일의 컬렉션을 표시 하는 방법 [폴더 열기](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md), 고으로 표시 되는 <xref:Microsoft.VisualStudio.Workspace.IWorkspace> 형식입니다. 자체적으로 작업 영역 콘텐츠나 폴더 내의 파일과 관련 된 기능 이해 하지 않습니다. 대신 일반 생성 하 고 다른 사용자가 취할 수 있는 데이터를 사용할 기능 및 확장에 대 한 Api 집합을 제공 합니다. 생산자를 통해 구성 됩니다. 합니다 [Managed Extensibility Framework](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (MEF)를 사용 하 여 다양 한 특성을 내보냅니다.

## <a name="workspace-providers-and-services"></a>작업 영역 공급자 및 서비스

작업 영역 공급자 및 서비스 데이터 및 작업 영역 내용에 대응 하는 기능을 제공 합니다. 상황에 맞는 파일 정보를 소스 파일의에서 기호를 제공할 수도 기능을 작성 합니다.

두 개념 사용를 [팩터리 패턴](https://en.wikipedia.org/wiki/Factory_method_pattern) 및 작업 영역에서 MEF를 통해 가져옵니다. 내보내기 특성을 모두 구현할 `IProviderMetadataBase` 또는 `IWorkspaceServiceFactoryMetadata`, 되지만 확장 내보낸된 형식에 대 한 사용 해야 하는 구체적인 형식.

공급자 및 서비스 간의 차이점 중 하나는 작업 영역에 해당 관계입니다. 작업 영역을 특정 형식으로 대부분의 공급자 수 있지만 작업 영역당 특정 형식의 서비스가 하나만 생성 됩니다. 예를 들어 작업 영역에는 많은 파일 스캐너 공급자가 있지만 작업 영역 작업 영역당 하나의 인덱싱 서비스에 있습니다.

또 다른 주요 차이점은 데이터 공급자 및 서비스를 사용 합니다. 작업 영역은 몇 가지 이유로 공급자에서 데이터 가져오기에 대 한 진입점입니다. 먼저 공급자는 일반적으로 일부 좁은 자신이 만든 데이터 집합을 가집니다. 데이터에 대 한 기호를 수 있습니다는 C# 에 대 한 파일 컨텍스트를 빌드하거나 소스 파일을 _CMakeLists.txt_ 파일입니다. 작업 영역에는 해당 메타 데이터 요청을 사용 하 여 정렬 공급자는 소비자의 요청을 일치 합니다. 일부 시나리오 대부분에 대 한 허용 하는 두 번째 시나리오는 동안 다른 요청에 참여 하는 공급자가 가장 높은 우선 순위를 사용 하 여 공급자를 사용 합니다.

반면, 확장의 인스턴스 하 고 작업 영역 서비스와 직접 상호 작용할 수 있습니다. 확장 메서드 `IWorkspace` 와 같은 Visual Studio에서 제공 하는 서비스에 사용할 수 있는 <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetFileWatcherService%2A>합니다. 확장 프로그램 사용 하는 다른 확장 또는 확장 내에서 구성 요소에 대 한 작업 공간 서비스를 제공할 수 있습니다. 소비자가 사용 해야 <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetServiceAsync%2A> 또는 확장 메서드를 제공 하는 `IWorkspace` 형식입니다.

>[!WARNING]
> Visual Studio를 사용 하 여 충돌 하는 서비스를 작성 하지 않습니다. 예기치 않은 문제가 발생할 수 있습니다.

## <a name="disposal-on-workspace-closure"></a>작업 영역 닫기 전 삭제

작업 영역 닫기 전, extender 삭제 하지만 비동기 호출을 해야 코드입니다. <xref:Microsoft.VisualStudio.Threading.IAsyncDisposable> 인터페이스를 쉽게이 코드를 작성 하기는 사용할 수 있습니다.

## <a name="related-types"></a>관련된 형식

- <xref:Microsoft.VisualStudio.Workspace.IWorkspace> 열려 있는 폴더와 같은 작업 영역을 열된에 대 한 중앙 엔터티입니다.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspaceProviderFactory`1> 인스턴스화할 작업 영역당 공급자를 만듭니다.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspaceServiceFactory> 인스턴스화할 작업 영역당 서비스를 만듭니다.
- <xref:Microsoft.VisualStudio.Threading.IAsyncDisposable> 공급자 및 삭제 하는 동안 비동기 코드를 실행 해야 하는 서비스에서 구현 되어야 합니다.
- <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper> 잘 알려진 서비스 또는 임의 서비스에 액세스 하기 위한 도우미 메서드를 제공 합니다.

## <a name="workspace-settings"></a>작업 영역 설정

작업 영역을 <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager> 으로 간단 하지만 강력한 작업 영역을 제어 하는 서비스입니다. 설정의 기본적인 개요를 참조 하세요 [빌드를 사용자 지정 및 디버그 작업](../ide/customize-build-and-debug-tasks-in-visual-studio.md)합니다.

가장에 대 한 설정을 `SettingsType` 유형은 _.json_ 파일을 같은 _VSWorkspaceSettings.json_ 하 고 _tasks.vs.json_합니다.

작업 영역 내에서 단순히 경로 "범위"를 중심으로 작업 영역 설정 활용 합니다. 소비자가 호출 하는 경우 <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager.GetAggregatedSettings%2A>, 요청 된 경로 및 설정 유형을 포함 하는 모든 범위 집계 됩니다. 범위 집계 우선 순위는 다음과 같습니다.

1. "로컬 설정"는 일반적으로 작업 영역 루트의 `.vs` 디렉터리입니다.
1. 자체 요청된 경로입니다.
1. 요청 경로의 부모 디렉터리입니다.
1. 모든 디렉터리 및 작업 영역 루트까지 추가 부모입니다.
1. "전역 설정"에서 사용자 디렉터리에 있는 합니다.

결과의 인스턴스가 <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings>합니다. 이 개체를 특정 형식에 대 한 설정을 보유 하 고 설정 키 이름으로 저장 쿼리할 수 있습니다 `string`합니다. 합니다 <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings.GetProperty%2A> 메서드 및 <xref:Microsoft.VisualStudio.Workspace.Settings.WorkspaceSettingsExtensions> 확장 메서드는 호출자가 요청 된 설정 값의 형식을 알 수를 예상 합니다. 대부분의 설정 파일으로 유지 됩니다 _.json_ 파일을 여러 호출 사용할지 `string`, `bool`, `int`, 및 해당 형식의 배열입니다. 개체 형식도 지원 됩니다. 이러한 경우에 사용할 수 있습니다 `IWorkspaceSettings` 형식 인수로 자체입니다. 예를 들어:

```json
{
  "intValue": 1,
  "stringValue": "s",
  "boolValue": true,
  "stringArray": [
    "s1",
    "s2"
  ],
  "nestedIWorkspaceSettings": {
    "nestedString": "ns"
  }
}
```

사용자의 에서처럼 이러한 설정 가정 _VSWorkspaceSettings.json_로 데이터를 액세스할 수 있습니다.

```csharp
using System.Collections.Generic;
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Settings;

private static void ReadSettings(IWorkspace workspace)
{
    IWorkspaceSettingsManager settingsManager = workspace.GetSettingsManager();
    IWorkspaceSettings settings = settingsManager.GetAggregatedSettings(SettingsTypes.Generic);

    // result == WorkspaceSettingsResult.Success
    WorkspaceSettingsResult result = settings.GetProperty("intValue", out int intValue);
    result = settings.GetProperty("stringValue", out string stringValue);
    result = settings.GetProperty("boolValue", out bool boolValue);
    result = settings.GetProperty("stringArray", out string[] stringArray);
    result = settings.GetProperty("nestedIWorkspaceSettings", out IWorkspaceSettings nestedIWorkspaceSettings);
    result = nestedIWorkspaceSettings.GetProperty("nestedString", out string nestedString);

    // Extension method alternative using default values.
    int intValueOrDefault = settings.Property("intValue", /* default */ 42);

    // Missing key. result == WorkspaceSettingsResult.Undefined
    result = settings.GetProperty("missing", out string missing);

    // Wrong type for a key. result == WorkspaceSettingsResult.Error
    result = settings.GetProperty("intValue", out IWorkspaceSettings notSettings);

    // Special ability to union "stringArray" across all scopes.
    IEnumerable<string> allStringArray = settings.UnionPropertyArray<string>("stringArray");
}
```

>[!NOTE]
>이러한 설정은 Api에서 사용 가능한 Api 관련 되지 않습니다.는 `Microsoft.VisualStudio.Settings` 네임 스페이스입니다. 작업 영역 설정을 호스트의 영향을 받지 않습니다 하 고 작업 영역 설정 파일 또는 동적 설정 공급자를 사용 합니다.

### <a name="providing-dynamic-settings"></a>동적 설정 제공

확장을 제공할 수 있습니다 <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsProvider>s입니다. 이러한 메모리 내 공급자 설정을 추가 하거나 다른 재정의에 대 한 확장을 허용 합니다.

내보내기는 `IWorkspaceSettingsProvider` 다른 작업 영역 공급자와 다릅니다. 팩터리 아닙니다 `IWorkspaceProviderFactory` 이며 특수 특성 유형이 없습니다. 대신, 구현 <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsProviderFactory> 사용 하 여 `[Export(typeof(IWorkspaceSettingsProviderFactory))]`입니다.

```csharp
// Common workspace provider factory pattern
[ExportFeatureProvider(some, args, to, export)]
internal class MyProviderFactory : IWorkspaceProviderFactory<IFeatureProvider>
{
     IFeatureProvider CreateProvider(IWorkspace workspace) => new Provider(workspace);
}

// IWorkspaceSettingsProvider pattern
[Export(typeof(IWorkspaceSettingsProviderFactory))]
internal class MySettingsProviderFactory : IWorkspaceSettingsProviderFactory
{
    // 100 is typically the value used by built-in settings providers. Lower value is higher priority.
    int Priority => 100;

    IWorkspaceSettingsProvider CreateSettingsProvider(IWorkspace workspace) => new MySettingsProvider(workspace);
}
```

>[!TIP]
>반환 하는 메서드를 구현 하는 경우 `IWorkspaceSettingsSource` (같은 `IWorkspaceSettingsProvider.GetSingleSettings`), 인스턴스를 반환 `IWorkspaceSettings` 대신 `IWorkspaceSettingsSource`합니다. `IWorkspaceSettings` 일부 설정 집계 하는 동안 유용할 수 있는 자세한 정보를 제공 합니다.

### <a name="settings-related-apis"></a>설정 관련 Api

- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager> 작업 영역에 대 한 읽기 및 집계 설정입니다.
- <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetSettingsManager%2A> 가져옵니다는 `IWorkspaceSettingsManager` 작업 영역에 대 한 합니다.
- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager.GetAggregatedSettings%2A> 전체 겹치는 범위에 걸쳐 집계 된 지정된 된 범위에 대 한 설정을 가져옵니다.
- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings> 특정 범위에 대 한 설정을 포함합니다.

## <a name="workspace-suggested-practices"></a>작업 영역 권장 사례

- 개체를 반환 `IWorkspaceProviderFactory.CreateProvider` 또는 이와 유사한 Api 기억를 해당 `Workspace` 컨텍스트를 만들 때. 공급자 인터페이스는이 개체 만들기에 보관 되어 필요한 기록 됩니다.
- 작업 영역 관련 캐시 또는 설정 작업 영역의 "로컬 설정" 경로 내에서 저장 합니다. 사용 하 여 파일에 대 한 경로 만들기 `Microsoft.VisualStudio.Workspace.WorkspaceHelper.MakeRootedUnderWorkingFolder` Visual Studio 2017 버전 15.6 이상. 버전 15.6 이전 버전에서는 다음 코드 조각을 사용 합니다.

```csharp
using System.IO;
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Settings;

private static string MakeRootedUnderWorkingFolder(IWorkspace workspace, string relativePath)
{
    string workingFolder = workspace.GetSettingsManager().GetAggregatedSettings(SettingsTypes.WorkspaceControlSettings).Property<string>("WorkingFolder");
    return Path.Combine(workingFolder, relativePath);
}
```

## <a name="solution-events-and-package-auto-load"></a>솔루션 이벤트 및 패키지 자동 로드

로드 된 패키지를 구현할 수 있습니다 `IVsSolutionEvents7` 호출 `IVsSolution.AdviseSolutionEvents`합니다. 열기 및 닫기 Visual Studio에서 폴더에서 이벤트를 포함 합니다.

UI 컨텍스트의 자동 로드 패키지를 사용할 수 있습니다. 값이 `4646B819-1AE0-4E79-97F4-8A8176FDD664`인 경우

## <a name="troubleshooting"></a>문제 해결

### <a name="the-sourceexplorerpackage-package-did-not-load-correctly"></a>SourceExplorerPackage 패키지가 제대로 로드 되지 않았습니다.

작업 영역 확장성 많이 MEF 기반 이며 컴퍼지션 오류로 인해 패키지를 로드 하지 못하도록 폴더 열기를 호스트 합니다. 예를 들어 확장 형식을 사용 하 여 내보냅니다 `ExportFileContextProviderAttribute`, 형식에서만 구현 되지만 `IWorkspaceProviderFactory<IFileContextActionProvider>`, Visual Studio에서 폴더를 열려고 할 때 오류가 발생 합니다.

::: moniker range="vs-2017"

오류 세부 정보에서 확인할 수 있습니다 _%LOCALAPPDATA%\Microsoft\VisualStudio\15.0_id\ComponentModelCache\Microsoft.VisualStudio.Default.err_합니다. 확장에 의해 구현 된 형식에 대 한 오류를 해결 합니다.

::: moniker-end

::: moniker range=">=vs-2019"

오류 세부 정보에서 확인할 수 있습니다 _%LOCALAPPDATA%\Microsoft\VisualStudio\16.0_id\ComponentModelCache\Microsoft.VisualStudio.Default.err_합니다. 확장에 의해 구현 된 형식에 대 한 오류를 해결 합니다.

::: moniker-end

## <a name="next-steps"></a>다음 단계

* [파일 컨텍스트를](workspace-file-contexts.md) -파일 상황에 맞는 공급자 폴더 열기 작업 영역에 대 한 코드 인텔리전스를 제공 합니다.
* [인덱싱](workspace-indexing.md) -작업 영역 인덱싱 수집 및 작업 영역에 대 한 정보를 유지 합니다.
