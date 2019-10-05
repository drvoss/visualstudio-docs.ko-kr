---
title: TaskBody 요소(MSBuild) | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- TaskBody element [MSBuild]
- <TaskBody> element [MSBuild]
ms.assetid: 49d8741b-f1ea-4470-94fd-a1ac27341a6a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8f788df1dd3cad2baddd6d2966b04195af01fe7d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62938963"
---
# <a name="taskbody-element-msbuild"></a>TaskBody 요소(MSBuild)
`UsingTask` `TaskFactory`에 전달되는 데이터가 들어 있습니다. 자세한 내용은 [UsingTask 요소(MSBuild)](../msbuild/usingtask-element-msbuild.md)를 참조하세요.

 \<Project> \<UsingTask> \<TaskBody>

## <a name="syntax"></a>구문

```xml
<TaskBody Evaluate="true/false" />
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|특성|설명|
|---------------|-----------------|
|`Evaluate`|선택적 부울 특성입니다.<br /><br /> `true`인 경우, MSBuild는 내부 요소를 평가하고, 작업을 인스턴스화할 때 정보를 `TaskFactory`에 전달하기 전에 항목 및 속성을 확장합니다.|

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|데이터|`TaskBody` 태그 간에 텍스트는 그대로 `TaskFactory`로 전송됩니다.|

### <a name="parent-elements"></a>부모 요소

| 요소 | 설명 |
| - | - |
| [UsingTask](../msbuild/usingtask-element-msbuild.md) | [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]에서 작업을 등록하는 방법을 제공합니다. 프로젝트에는 `UsingTask` 요소가 없을 수도 있고 하나 이상 있을 수 있습니다. |

## <a name="example"></a>예제
 다음 예제에서는 `Evaluate` 특성에서 `TaskBody` 요소를 사용하는 방법을 보여 줍니다.

```xml
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">
       <ParameterGroup>
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>
              ...
</ParameterGroup>
       <TaskBody Evaluate="true">
      ... Task factory-specific data ...
       </TaskBody>
</UsingTask>
```

## <a name="see-also"></a>참고 항목
- [작업](../msbuild/msbuild-tasks.md)
- [작업 참조](../msbuild/msbuild-task-reference.md)
- [프로젝트 파일 스키마 참조](../msbuild/msbuild-project-file-schema-reference.md)
