---
title: ZipDirectory 작업 | Microsoft Docs
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ZipDirectory
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ZipDirectory task [MSBuild]
- MSBuild, ZipDirectory task
ms.assetid: 916bb2e3-3017-4828-ae27-c0b5c99bbb48
caps.latest.revision: 16
author: Mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2188ef3026e36d5c97cf35cd29362411c473973e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62777478"
---
# <a name="zipdirectory-task"></a>ZipDirectory 작업
디렉터리의 콘텐츠에서 *.zip* 보관을 만듭니다.

>[!NOTE]
>`ZipDirectory` 작업은 MSBuild 15.8 이상에서만 사용할 수 있습니다.

## <a name="parameters"></a>매개 변수
 다음 표에서는 `ZipDirectory` 작업의 매개 변수에 대해 설명합니다.

|매개 변수|설명|
|---------------|-----------------|
|`DestinationFile`|필수 <xref:Microsoft.Build.Framework.ITaskItem> 매개 변수<br /><br /> 생성할 *.zip* 파일의 전체 경로입니다.|
|`Overwrite`|선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`인 경우 건너뜁니다. 대상 파일이 있으면 덮어씁니다. 기본값은 `false`입니다.|
|`SourceDirectory`|필수 <xref:Microsoft.Build.Framework.ITaskItem> 매개 변수입니다.<br /><br /> *.zip* 보관을 만들 디렉터리를 지정합니다.|

## <a name="remarks"></a>주의
 이 작업은 위에 나와 있는 매개 변수 외에 <xref:Microsoft.Build.Utilities.Task> 클래스에서 직접 상속하는 <xref:Microsoft.Build.Tasks.TaskExtension> 클래스의 매개 변수도 상속합니다. 이러한 추가 매개 변수 및 해당 설명이 포함된 목록은 [TaskExtension 기본 클래스](../msbuild/taskextension-base-class.md)를 참조하세요.

## <a name="example"></a>예제
 다음 예제에서는 프로젝트를 빌드한 후 출력 디렉터리에서 *.zip* 보관을 만듭니다.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <Target Name="ZipOutputPath" AfterTargets="Build">
        <ZipDirectory
            SourceDirectory="$(OutputPath)"
            DestinationFile="$(MSBuildProjectDirectory)\output.zip" />
    </Target>

</Project>
```

## <a name="see-also"></a>참고 항목
- [작업](../msbuild/msbuild-tasks.md)
- [작업 참조](../msbuild/msbuild-task-reference.md)
