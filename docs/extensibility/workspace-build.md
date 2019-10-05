---
title: Visual Studio에서 빌드 작업 영역 | Microsoft Docs
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 82660ee772280563b91830aaf1a18da0bc742b28
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62553330"
---
# <a name="workspace-build"></a>작업 영역 빌드

대 한 지원도 [폴더 열기](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) 시나리오를 제공 하는 extender 필요 [인덱싱된](workspace-indexing.md) 및 [파일 컨텍스트](workspace-file-contexts.md) 에 대 한 데이터를 [작업 영역](workspaces.md),으로 뿐만 아니라 빌드 작업 실행입니다.

다음은 해야 확장 프로그램에 대 한 개요입니다.

## <a name="build-file-context"></a>파일 컨텍스트를 작성 합니다.

- 공급자 팩터리
  - `ExportFileContextProviderAttribute` 특성과 `supportedContextTypeGuids` 와 모든 적용 가능한 `string` 상수 `BuildContextTypes`
  - 구현 `IWorkspaceProviderFactory<IFileContextProvider>`
  - 파일 컨텍스트 공급자
    - 반환 된 `FileContext` 각각에 대 한 빌드 작업 및 지원 구성
      - `contextType` 보낸 사람 <xref:Microsoft.VisualStudio.Workspace.Build.BuildContextTypes>
      - `context` 구현 <xref:Microsoft.VisualStudio.Workspace.Build.IBuildConfigurationContext> 사용 하 여 합니다 `Configuration` 빌드 구성 속성 (예를 들어 `"Debug|x86"`를 `"ret"`, 또는 `null` 해당 하지 않는 경우). 또는의 인스턴스를 사용 하 여 <xref:Microsoft.VisualStudio.Workspace.Build.BuildConfigurationContext>입니다. 구성 값 **해야** 인덱싱되는 파일 데이터 값의 구성과 일치 합니다.

## <a name="indexed-build-file-data-value"></a>인덱싱된 빌드 파일 데이터 값

- 공급자 팩터리
  - `ExportFileScannerAttribute` 특성과 `IReadOnlyCollection<FileDataValue>` 지원 되는 형식으로
  - 구현 `IWorkspaceProviderFactory<IFileScanner>`
- 파일 검색 `ScanContentAsync<T>`
  - 데이터를 반환 하면 `FileScannerTypeConstants.FileDataValuesType` 형식 인수는
  - 사용 하 여 생성 된 각 구성에 대 한 파일 데이터 값을 반환 합니다.
    - `type` 마찬가지로 `BuildConfigurationContext.ContextTypeGuid`
    - `context` 빌드 구성으로 (예를 들어 `"Debug|x86"`하십시오 `"ret"`, 또는 `null` 해당 하지 않는 경우). 이 값 **해야** 파일 컨텍스트에서 구성과 일치 합니다.

## <a name="build-file-context-action"></a>빌드 파일 컨텍스트 작업

- 공급자 팩터리
  - `ExportFileContextActionProvider` 특성과 `supportedContextTypeGuids` 와 모든 적용 가능한 `string` 상수 `BuildContextTypes`
  - 구현 `IWorkspaceProviderFactory<IFileContextActionProvider>`
- 작업 공급자 `IFileContextActionProvider.GetActionsAsync`
  - 반환을 `IFileContextAction` 일치 하는 지정 된 `FileContext.ContextType` 값
- 파일 컨텍스트 작업
  - 구현 `IFileContextAction` 및 <xref:Microsoft.VisualStudio.Workspace.Extensions.VS.IVsCommandItem>
  - `CommandGroup` 속성 반환 `16537f6e-cb14-44da-b087-d1387ce3bf57`
  - `CommandId` 됩니다 `0x1000` 빌드의 `0x1010` 다시 작성에 대 한 또는 `0x1020` 에 대 한 정리

>[!NOTE]
>이후는 `FileDataValue` 인덱싱해야 합니다 어느 정도의 작업 영역 및 전체 빌드 기능에 대 한 파일이 검색 됩니다 지점 중 하나는 시간 됩니다. 지연을 먼저 열어 폴더의 이전에 캐시 된 인덱스가 없기 때문에 표시 됩니다.

## <a name="reporting-messages-from-a-build"></a>빌드에서 메시지를 보고합니다.

빌드 수 화면 정보, 경고 및 오류 메시지 사용자에 게 두 가지 방법 중 하나입니다. 간단한 방법을 사용 하는 것은 <xref:Microsoft.VisualStudio.Workspace.Build.IBuildMessageService> 제공을 <xref:Microsoft.VisualStudio.Workspace.Build.BuildMessage>, 같이:

```csharp
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Build;

private static void OutputBuildMessage(IWorkspace workspace)
{
    IBuildMessageService buildMessageService = workspace.GetBuildMessageService();

    if (buildMessageService != null)
    {
      // Example error build message. See the documentation for BuildMessage for more information.
      var message = new BuildMessage()
      {
          Type = BuildMessage.TaskType.Error,
          Code = "MY1001",
          TaskText = "This is a sample error",
          ProjectFile = "buildfile.bld",
          File = "sourcefile.src"
          LogMessage = $"This is sample text that will only go to the Build output window pane.\n"

          // And any other properties to set
      };

      buildMessageService.ReportBuildMessages(new BuildMessage[] { message });
    }
}
```

`BuildMessage.Type` 및 `BuildMessage.LogMessage` 정보 사용자에 게 표시 되는의 동작을 제어 합니다. 모든 `BuildMessage.TaskType` 이외의 값 `None` 생성을 **오류 목록** 제공된 된 세부 정보를 사용 하 여 항목입니다. `LogMessage` 항상 출력 됩니다는 **빌드** 창의 합니다 **출력** 도구 창입니다.

또는 확장 직접 상호 작용할 수는 **오류 목록** 하거나 **빌드** 창입니다. Visual Studio 2017 버전 15.7 이전 버전에는 버그가 있습니다 위치 합니다 `pszProjectUniqueName` 인수의 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane2.OutputTaskItemStringEx2*> 무시 됩니다.

>[!WARNING]
>호출자에 게 `IFileContextAction.ExecuteAsync` 에 대 한 임의의 기본 구현을 제공할 수는 `IProgress<IFileContextActionProgressUpdate>` 인수입니다. 실행 하지 않도록 `IProgress<IFileContextActionProgressUpdate>.Report(IFileContextActionProgressUpdate)` 직접. 현재이 인수를 사용 하기 위한 일반적인 지침은 없습니다 있지만 이러한 지침 변경 될 수 있습니다.

## <a name="build-related-apis"></a>빌드 관련 Api

- <xref:Microsoft.VisualStudio.Workspace.Build.IBuildConfigurationContext> 빌드 구성 세부 정보를 제공합니다.
- <xref:Microsoft.VisualStudio.Workspace.Build.IBuildMessageService> 표시 <xref:Microsoft.VisualStudio.Workspace.Build.BuildMessage>의사용자에 게 합니다.

## <a name="tasksvsjson-and-launchvsjson"></a>tasks.vs.json 및 launch.vs.json

Launch.vs.json 또는 tasks.vs.json 파일 작성에 대 한 내용은 참조 하세요 [빌드를 사용자 지정 및 디버그 작업](../ide/customize-build-and-debug-tasks-in-visual-studio.md)합니다.

## <a name="next-steps"></a>다음 단계

* [언어 서버 프로토콜](language-server-protocol.md) -Visual Studio 언어 서버를 통합 하는 방법을 알아봅니다.