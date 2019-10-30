---
title: CPPClean 작업 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vc.task.cppclean
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), CPPClean task
- CPPClean task (MSBuild (C++))
ms.assetid: b62a482e-8fb5-4999-b50b-6605a078e291
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6d6e893dcf289c5060f519523b18b53b701f8055
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748117"
---
# <a name="cppclean-task"></a>CPPClean 작업
C++ 프로젝트가 빌드될 때 MSBuild가 만드는 임시 파일을 삭제합니다. 빌드 파일을 삭제하는 프로세스는 *정리*라고 합니다.

## <a name="parameters"></a>매개 변수
 다음 표에서는 **CPPClean** 작업의 매개 변수에 대해 설명합니다.

|매개 변수|설명|
|---------------|-----------------|
|**DeletedFiles**|선택적 `ITaskItem[]` 출력 매개 변수입니다.<br /><br /> 작업에서 사용하고 내보낼 수 있는 MSBuild 출력 파일 항목의 배열을 정의합니다.|
|**DoDelete**|선택적 **Boolean** 매개 변수입니다.<br /><br /> `true`인 경우 임시 빌드 파일을 정리합니다.|
|**FilePatternsToDeleteOnClean**|필수 `String` 매개 변수입니다.<br /><br /> 정리할 파일의 확장명을 세미콜론으로 구분된 목록으로 지정합니다.|
|**FilesExcludedFromClean**|선택적 `String` 매개 변수입니다.<br /><br /> 정리하지 않을 파일을 세미콜론으로 구분된 목록으로 지정합니다.|
|**FoldersToClean**|필수 `String` 매개 변수입니다.<br /><br /> 정리할 디렉터리를 세미콜론으로 구분된 목록으로 지정합니다. 사용자가 전체 또는 상대 경로를 지정할 수 있고 경로에 와일드카드 기호(*)가 포함될 수 있습니다.|

## <a name="see-also"></a>참고 항목
- [작업 참조](../msbuild/msbuild-task-reference.md)