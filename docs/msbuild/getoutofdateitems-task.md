---
title: GetOutOfDateItems 작업 | Microsoft Docs
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.getoutofdateitems
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), GetOutOfDateItems task
- GetOutOfDateItems task (MSBuild (C++))
author: mikeblome
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: d3dc343c595606faf5bd31d7f087f7ba8d95f69e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747312"
---
# <a name="getoutofdateitems-task"></a>GetOutOfDateItems 작업

이전 tlog를 읽고, 새 tlog를 쓰며, 최신 상태가 아닌 항목 집합을 반환하는 도우미 작업입니다.

## <a name="parameters"></a>매개 변수

다음 표에서는 **GetOutOfDateItems** 작업의 매개 변수에 대해 설명합니다.

|매개 변수|설명|
|---------------|-----------------|
|**CheckForInterdependencies**|선택적 **bool** 매개 변수입니다.|
|**CommandMetadataName**|선택적 **string** 매개 변수입니다.|
|**DependenciesMetadataName**|선택적 **string** 매개 변수입니다.|
|**HasInterdependencies**|선택적 **bool** 출력 매개 변수입니다.|
|**OutOfDateSources**|선택적 **ITaskItem** 출력 매개 변수입니다.|
|**OutputsMetadataName**|필수 **문자열** 매개 변수입니다.|
|**Sources**|선택적 **ITaskItem[]** 매개 변수입니다.|
|**TLogDirectory**|필수 **문자열** 매개 변수입니다.|
|**TLogNamePrefix**|필수 **문자열** 매개 변수입니다.|

## <a name="see-also"></a>참고 항목

[작업 참조](../msbuild/msbuild-task-reference.md)