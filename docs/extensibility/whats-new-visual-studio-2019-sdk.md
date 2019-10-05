---
title: Visual Studio 2019 SDK의 새로운 기능 | Microsoft Docs
ms.date: 03/29/2019
ms.topic: conceptual
ms.assetid: 4a07607b-0c87-4866-acd8-6d68358d6a47
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d4be152cfb39ddea9ddaeea56464a3447be4f2c6
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66320600"
---
# <a name="whats-new-in-the-visual-studio-2019-sdk"></a>Visual Studio 2019 SDK의 새로운 기능

Visual Studio SDK는 Visual Studio 2019에 대 한 다음 새로운 및 업데이트 된 기능.

## <a name="synchronously-autoloaded-extensions-warning"></a>동기적으로 자동 확장의 경고

이제 사용자가 설치 된 확장 중 하나라도 시작 시 자동 동기적으로 하는 경우 경고를 표시 됩니다. 에 있는 경고에 대 한 자세히 알아볼 수 있습니다 [동기적으로 자동 확장](synchronously-autoloaded-extensions.md)합니다.

## <a name="single-unified-visual-studio-sdk"></a>통합 된 단일 Visual Studio SDK

단일 NuGet 패키지를 통해 이제 Visual Studio SDK의 모든 자산을 가져올 수 있습니다 [Microsoft.VisualStudio.SDK](https://www.nuget.org/packages/microsoft.visualstudio.sdk)합니다.

## <a name="editor-registration-enhancements"></a>편집기 등록 향상 된 기능

생성 된 후 Visual Studio에 지원 되는 사용자 지정 편집기 등록 편집기 (예를 들어.xaml 및.rc) 특정 확장에 대 한 해당 선호도 선언할 수 있습니다 하거나 있는 모든 확장에 대 한 적합 (. *). 편집기 등록에 대 한 지원을 확대 Visual Studio 2019 16.1 버전부터 했습니다.

### <a name="filenames"></a>파일 이름

편집기 새 적용 하 여 특정 파일 이름 지원 등록할 수 있습니다에 또는 특정 파일 확장명에 대 한 지원 등록 대신 `ProvideEditorFilename` 편집자 패키지 특성입니다.

예를 들어, 모든.json 파일을 지 원하는 편집기 적용이 `ProvideEditorExtension` 해당 패키지에 특성:

```cs
[ProvideEditorExtension(typeof(MyEditor), ".json", MyEditor.Priority)]
```

부터 시작 하 여 16.1, MyEditor만 몇 개의 잘 알려진.json 파일을 지 원하는 경우 대신를 적용할 수 있으므로 이러한 `ProvideEditorFilename` 해당 패키지에 특성:

```cs
[ProvideEditorFilename(typeof(MyEditor), "particular.json", MyEditor.Priority)]
[ProvideEditorFilename(typeof(MyEditor), "special.json",    MyEditor.Priority)]
```

### <a name="uicontexts"></a>UIContexts

편집기를 사용 하는 경우를 나타내는 하나 이상의 UIContexts를 등록할 수 있습니다. UIContexts의 하나 이상의 인스턴스를 적용 하 여 등록 된 `ProvideEditorUIContextAttribute` 편집기를 등록 하는 패키지에 있습니다.

편집기에 있는 경우 등록 된 UIContexts:

- 하나 이상의 등록 된 해당 UIContexts 활성 상태인 경우 지정된 된 확장명을 사용 하 여 파일을 열 때 편집기 편집기 검색에 포함 됩니다.
- 등록 된 UIContexts 하나도 활성 상태인 경우 편집기 편집기 검색에 포함 되지 않습니다.

편집기 모든 UIContexts를 등록 하지 않으면 해당 확장에 대 한 편집기 검색에 항상 포함 됩니다.

예를 들어 편집기 에서만 사용 가능 시기를 C# 프로젝트를 열지이 선호도 적용 하 여 선언할 수는 `ProvideEditorUIContext` 특성:

```cs
[ProvideEditorUIContext(typeof(MyEditor), KnownUIContexts.CSharpProjectContext)]
```
