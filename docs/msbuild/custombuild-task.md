---
title: CustomBuild 작업 | Microsoft Docs
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.custombuild
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), CustomBuild task
- CustomBuild task (MSBuild (C++))
author: ghogen
ms.author: ghogen
ms.workload:
- multiple
ms.openlocfilehash: d95b6e7d4197487adc13050572ac31310701c759
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595347"
---
# <a name="custombuild-task"></a>CustomBuild 작업

Microsoft C++ 컴파일러 도구 cmd.exe를 래핑합니다. 이 클래스는 [TrackedVCToolTask](../msbuild/trackedvctooltask-base-class.md)에서 파생되나 파일 종속성 검색을 위해 파일 추적을 사용하지는 않습니다. 증분 빌드가 제대로 작동하려면 모든 종속성은AdditionalDependencies로 명시적으로 지정되어야 합니다.

## <a name="parameters"></a>매개 변수

다음 표에서는 **CustomBuild** 작업의 매개 변수에 대해 설명합니다.

|매개 변수|설명|
|---------------|-----------------|
|**BuildSuffix**|선택적 **string** 매개 변수입니다.|
|**Sources**|필수 **ITaskItem[]** 매개 변수입니다.|
|**TrackerLogDirectory**|선택적 **string** 매개 변수입니다.|

## <a name="see-also"></a>참조

[작업 참조](../msbuild/msbuild-task-reference.md)
