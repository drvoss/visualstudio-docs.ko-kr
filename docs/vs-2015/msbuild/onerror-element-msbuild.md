---
title: OnError 요소(MSBuild) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#OnError
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- OnError Element [MSBuild]
- <OnError Element [MSBuild]
ms.assetid: 765767d3-ecb7-4cd9-ba1e-d9468964dddc
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 10f89d21441418ae0b5c267c0fea7e8451115afe
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49228711"
---
# <a name="onerror-element-msbuild"></a>OnError 요소(MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
`ContinueOnError` 특성이 실패한 태스크의 `false`인 경우 하나 이상의 대상이 실행되도록 합니다.  
  
 \<Project>  
 \<Target>  
 \<OnError>  
  
## <a name="syntax"></a>구문  
  
```  
<OnError ExecuteTargets="TargetName"  
    Condition="'String A'=='String B'" />  
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  
  
|특성|설명|  
|---------------|-----------------|  
|`Condition`|선택적 특성입니다.<br /><br /> 평가할 조건입니다. 자세한 내용은 [조건](../msbuild/msbuild-conditions.md)을 참조하세요.|  
|`ExecuteTargets`|필수 특성입니다.<br /><br /> 태스크가 실패한 경우 실행할 대상입니다. 여러 대상을 세미콜론으로 구분합니다. 여러 대상이 지정된 순서로 실행됩니다.|  
  
### <a name="child-elements"></a>자식 요소  
 없음  
  
### <a name="parent-elements"></a>부모 요소  
  
|요소|설명|  
|-------------|-----------------|  
|[Target](../msbuild/target-element-msbuild.md)|[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 작업의 컨테이너 요소입니다.|  
  
## <a name="remarks"></a>설명  
 `Target` 요소의 태스크 중 하나가 `ErrorAndStop`(또는 `false`)로 설정된 `ContinueOnError` 특성으로 실패한 경우 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]은 `OnError` 요소를 실행합니다. 태스크에 실패한 경우 `ExecuteTargets` 특성에 지정된 대상이 실행됩니다. 대상에 하나 이상의 `OnError` 요소가 있는 경우 태스크가 실패하면 `OnError` 요소는 순차적으로 실행됩니다.  
  
 `ContinueOnError` 특성에 대한 자세한 내용은 [Task 요소(MSBuild)](../msbuild/task-element-msbuild.md)를 참조하세요. 대상에 대한 자세한 내용은 [대상](../msbuild/msbuild-targets.md)을 참조하세요.  
  
## <a name="example"></a>예제  
 다음 코드는 `TaskOne` 및 `TaskTwo` 태스크를 실행합니다. `TaskOne`에 실패하는 경우 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]는 `OnError` 요소를 평가하고 `OtherTarget` 대상을 실행합니다.  
  
```  
<Target Name="ThisTarget">  
    <TaskOne ContinueOnError="ErrorAndStop">  
    </TaskOne>  
    <TaskTwo>  
    </TaskTwo>  
    <OnError ExecuteTargets="OtherTarget" />  
</Target>  
```  
  
## <a name="see-also"></a>참고 항목  
 [프로젝트 파일 스키마 참조](../msbuild/msbuild-project-file-schema-reference.md)   
 [대상](../msbuild/msbuild-targets.md)



