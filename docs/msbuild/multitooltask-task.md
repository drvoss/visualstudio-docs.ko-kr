---
title: MultiToolTask 작업 | Microsoft Docs
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.multitooltask
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), MultiToolTask task
- MultiToolTask task (MSBuild (C++))
author: mikeblome
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: 137fb53a46c3fa31a69602906ef53d2f65e25c4b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747242"
---
# <a name="multitooltask-task"></a>MultiToolTask 작업

설명이 없습니다.

## <a name="parameters"></a>매개 변수

다음 표에서는 **MultiToolTask** 작업의 매개 변수에 대해 설명합니다.

|매개 변수|설명|
|---------------|-----------------|
|**EnvironmentVariablesToSet**|선택적 **string[]** 매개 변수입니다.|
|**SemaphoreProcCount**|선택적 **string** 매개 변수입니다.|
|**SchedulerFunction**|선택적 **string** 매개 변수입니다.|
|**SchedulerVerbose**|선택적 **bool** 매개 변수입니다.|
|**Sources**|필수 **ITaskItem[]** 매개 변수입니다.|
|**TaskAssemblyName**|선택적 **string** 매개 변수입니다.|
|**TaskName**|필수 **문자열** 매개 변수입니다.|
|**TrackerLogDirectory**|필수 **문자열** 매개 변수입니다.|

## <a name="see-also"></a>참고 항목

[작업 참조](../msbuild/msbuild-task-reference.md)