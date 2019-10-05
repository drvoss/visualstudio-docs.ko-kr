---
title: UsingTask 요소(MSBuild) | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#UsingTask
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- UsingTask element [MSBuild]
- <UsingTask> element [MSBuild]
ms.assetid: 20247902-9446-4a1f-8253-5c7a17e4fe43
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 36e310688b8305b2d5986a1b29d34895f02bc4d7
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63411000"
---
# <a name="usingtask-element-msbuild"></a>UsingTask 요소(MSBuild)
[Task](../msbuild/task-element-msbuild.md) 요소에서 참조하는 작업을 작업의 구현이 포함된 어셈블리에 매핑합니다.

 \<Project> \<UsingTask>

## <a name="syntax"></a>구문

```xml
<UsingTask TaskName="TaskName"
    AssemblyName = "AssemblyName"
    TaskFactory = "ClassName"
    Condition="'String A'=='String B'" />
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|특성|설명|
|---------------|-----------------|
|`AssemblyName`|`AssemblyName` 특성 또는 `AssemblyFile` 특성이 필요합니다.<br /><br /> 로드할 어셈블리의 이름입니다. `AssemblyName` 특성에서는 강력한 이름의 어셈블리를 허용하지만 필수적 요소는 아닙니다. 이 특성을 사용하면 .NET Framework에서 <xref:System.Reflection.Assembly.Load%2A> 메서드를 사용하여 어셈블리를 로드하는 것과 같은 결과를 얻을 수 있습니다.<br /><br /> `AssemblyFile` 특성을 사용하는 경우에는 이 특성을 사용할 수 없습니다.|
|`AssemblyFile`|`AssemblyName` 또는 `AssemblyFile` 특성이 필요합니다.<br /><br /> 어셈블리의 파일 경로입니다. 이 특성에는 전체 경로 또는 상대 경로를 모두 사용할 수 있습니다. 상대 경로는 `UsingTask` 요소가 선언된 대상 파일이나 프로젝트의 디렉터리를 기준으로 합니다. 이 특성을 사용하면 .NET Framework에서 <xref:System.Reflection.Assembly.LoadFrom%2A> 메서드를 사용하여 어셈블리를 로드하는 것과 같은 결과를 얻을 수 있습니다.<br /><br /> `AssemblyName` 특성을 사용하는 경우에는 이 특성을 사용할 수 없습니다.|
|`TaskFactory`|선택적 특성입니다.<br /><br /> 지정된 `Task` 이름의 인스턴스 생성을 담당하는 어셈블리에 클래스를 지정합니다.  사용자는 또한 작업 팩터리가 수신해서 작업을 생성하는 데 사용하는 하위 요소로 `TaskBody`를 지정할 수 있습니다. `TaskBody`의 내용은 작업 팩터리에만 해당합니다.|
|`TaskName`|필수 특성입니다.<br /><br /> 어셈블리에서 참조할 작업의 이름입니다. 모호성이 발생할 가능성이 있으면 이 특성에 항상 전체 네임스페이스를 지정해야 합니다. 모호성이 있으면 MSBuild에서는 일치하는 임의의 항목을 선택하므로 예기치 않은 결과가 발생할 수 있습니다.|
|`Condition`|선택적 특성입니다.<br /><br /> 평가할 조건입니다. 자세한 내용은 [조건](../msbuild/msbuild-conditions.md)을 참조하세요.|

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[ParameterGroup](../msbuild/parametergroup-element.md)|지정된 `TaskFactory`에서 생성한 작업에 나타나는 매개 변수 집합입니다.|
|[Task](../msbuild/task-element-msbuild.md)|작업의 인스턴스를 생성하기 위해 `TaskFactory`로 전달되는 데이터입니다.|

### <a name="parent-elements"></a>부모 요소

| 요소 | 설명 |
| - | - |
| [프로젝트](../msbuild/project-element-msbuild.md) | [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 프로젝트 파일의 필수 루트 요소입니다. |

## <a name="remarks"></a>주의
 환경 변수, 명령줄 속성, 프로젝트 수준 속성 및 프로젝트 수준 항목은 직접 또는 가져온 프로젝트 파일을 통해 프로젝트 파일에 포함된 `UsingTask` 요소에서 참조할 수 있습니다. 자세한 내용은 [작업](../msbuild/msbuild-tasks.md)을 참조하세요.

> [!NOTE]
> MSBuild 엔진을 통해 전역으로 등록된 *.tasks* 파일 중 하나에서 `UsingTask` 요소를 가져오는 경우 프로젝트 수준 속성 또는 항목에는 의미가 없습니다. 프로젝트 수준 값은 MSBuild에 대해 전역이 아닙니다.

 MSBuild 4.0에서는 작업 사용을 *.overridetask* 파일에서 로드할 수 있습니다.

## <a name="example"></a>예제
 다음 예제에서는 `AssemblyName` 특성에서 `UsingTask` 요소를 사용하는 방법을 보여 줍니다.

```xml
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">
       <ParameterGroup>
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>
              ...
</ParameterGroup>
       <TaskBody>
      ... Task factory-specific data ...
       </TaskBody>
</UsingTask>
```

## <a name="example"></a>예제
 다음 예제에서는 `AssemblyFile` 특성에서 `UsingTask` 요소를 사용하는 방법을 보여 줍니다.

```xml
<UsingTask TaskName="Email"
              AssemblyFile="c:\myTasks\myTask.dll" />
```

## <a name="see-also"></a>참고 항목
- [작업](../msbuild/msbuild-tasks.md)
- [작업 참조](../msbuild/msbuild-task-reference.md)
- [프로젝트 파일 스키마 참조](../msbuild/msbuild-project-file-schema-reference.md)
