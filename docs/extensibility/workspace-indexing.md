---
title: Visual Studio에서 인덱싱 작업 영역 | Microsoft Docs
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 9bf7df777d27003fa5763debc772a8804ec28ef5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62952712"
---
# <a name="workspace-indexing"></a>작업 영역 인덱싱

솔루션에서 프로젝트 시스템은 빌드에 대 한 기능을 제공 하는 일을 담당, 디버깅 **GoTo** 기호 검색 및 더 합니다. 프로젝트 시스템 프로젝트 내에서 파일의 기능과 관계를 파악할 수 있으므로이 작업을 수행할 수 있습니다. [폴더 열기](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) 작업 영역을 다양 한 IDE 기능을 제공 하려면 동일한 이해 해야 합니다. 수집 및이 데이터의 영구 저장소에 인덱싱 작업 영역을 호출 프로세스입니다. 비동기 Api 집합을 통해이 인덱싱된 데이터를 쿼리할 수 있습니다. Extender를 제공 하 여 인덱싱 프로세스에 참여할 수 있습니다 <xref:Microsoft.VisualStudio.Workspace.Indexing.IFileScanner>는 특정 형식의 파일을 처리 하는 방법을 알고 있어야 합니다.

## <a name="types-of-indexed-data"></a>인덱싱된 데이터의 형식

인덱싱되는 데이터의 세 가지 종류가 있습니다. 참고 파일 스캐너에서 예상 되는 형식 인덱스에서 deserialize 된 형식에서 서로 다릅니다.

|데이터|파일 스캐너 형식|인덱스 쿼리 결과 유형|관련된 형식|
|--|--|--|--|
|참조|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceInfo>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceResult>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceInfoType>|
|기호|<xref:Microsoft.VisualStudio.Workspace.Indexing.SymbolDefinition>|<xref:Microsoft.VisualStudio.Workspace.Indexing.SymbolDefinitionSearchResult>|<xref:Microsoft.VisualStudio.Workspace.Indexing.ISymbolService> 대신 사용할 `IIndexWorkspaceService` 쿼리에 대 한|
|데이터 값|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileDataValue>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileDataResult`1>||

## <a name="querying-for-indexed-data"></a>인덱싱된 데이터에 대 한 쿼리

두 가지가 비동기 지속 된 데이터를 액세스할 수 있습니다. 첫 번째 방법은 <xref:Microsoft.VisualStudio.Workspace.Indexing.IIndexWorkspaceData>합니다. 단일 파일의 기본 액세스할 `FileReferenceResult` 및 `FileDataResult` 에 결과 캐시 합니다. 두 번째는 <xref:Microsoft.VisualStudio.Workspace.Indexing.IIndexWorkspaceService> 캐싱을 사용 하지 않는 있지만 더 많은 쿼리 기능을 허용 합니다.

```csharp
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Indexing;

private static IIndexWorkspaceData GetCachedIndexedData(IWorkspace workspace)
{
    // Gets access to indexed data wrapped in a cache.
    return workspace?.GetIndexWorkspaceDataService()?.CreateIndexWorkspaceData();
}

private static IIndexWorkspaceService GetDirectIndexedData(IWorkspace workspace)
{
    // Gets direct access to indexed data.
    // Can also be casted to IIndexWorkspaceService2.
    return workspace?.GetIndexWorkspaceService();
}
```

## <a name="participating-in-indexing"></a>인덱싱에 참여

다음 순서에 따라 약 인덱싱 작업 영역:

1. 검색 및 지 속성 (처음 열면 검색)에 해당 작업 영역에서 파일 시스템 엔터티.
1. 파일당 최고 우선 순위를 사용 하 여 일치 하는 공급자를 검색 하 라는 메시지가 표시 `FileReferenceInfo`s입니다.
1. 파일당 최고 우선 순위를 사용 하 여 일치 하는 공급자를 검색 하 라는 메시지가 표시 `SymbolDefinition`s입니다.
1. 모든 공급자에 대 한 요청은 파일당 `FileDataValue`s입니다.

확장을 구현 하 여 스캐너를 내보낼 수 있습니다 `IWorkspaceProviderFactory<IFileScanner>` 내보내고은 형식과 <xref:Microsoft.VisualStudio.Workspace.Indexing.ExportFileScannerAttribute>합니다. 합니다 `SupportedTypes` 특성 인수에서 하나 이상의 값이 있어야 <xref:Microsoft.VisualStudio.Workspace.Indexing.FileScannerTypeConstants>합니다. 예제 검색 프로그램에 대 한 VS SDK를 참조 하세요 [샘플](https://github.com/Microsoft/VSSDK-Extensibility-Samples/blob/master/Open_Folder_Extensibility/C%23/SymbolScannerSample/TxtFileSymbolScanner.cs)합니다.

> [!WARNING]
> 지 원하는 파일 스캐너를 내보내지 않는 `FileScannerTypeConstants.FileScannerContentType` 형식입니다. Microsoft 내부 용도로,만 사용 됩니다.

고급 시나리오에서는 확장 파일 형식의 임의의 집합을 동적으로 지원할 수 있습니다. MEF 내보내기 하는 대신 `IWorkspaceProviderFactory<IFileScanner>`, 확장을 내보낼 수 있습니다 `IWorkspaceProviderFactory<IFileScannerProvider>`합니다. 이 팩터리 형식 되며 가져올 인스턴스화된 되며가 인덱싱 시작 되 면 해당 <xref:Microsoft.VisualStudio.Workspace.Indexing.IFileScannerProvider.GetSymbolScannersAsync%2A> 메서드를 호출 합니다. `IFileScanner` 인스턴스 값을 지 원하는 `FileScannerTpeConstants` 기호 뿐 아니라, 적용 됩니다.

## <a name="next-steps"></a>다음 단계

* [작업 영역 및 언어 서비스](workspace-language-services.md) -언어 서비스 작업 영역을 열고 폴더를 통합 하는 방법을 알아봅니다.
* [작업 영역 빌드](workspace-build.md) -폴더 열기에서 지 원하는 MSBuild 및 메이크파일와 같은 시스템을 구축 합니다.