---
title: SetEnv 작업 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- vc.task.setenv
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (Visual C++), tasks
- SetEnv task (MSBuild (Visual C++))
ms.assetid: fd9e4225-68cb-4608-8b27-468b0218c936
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 49d25d49554c587bcaaba8ef09bac967d4b5599a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68157371"
---
# <a name="setenv-task"></a>SetEnv 작업
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

지정된 환경 변수의 값을 설정하거나 삭제합니다.  
  
## <a name="parameters"></a>매개 변수  
 다음 표에서는 **SetEnv** 작업의 매개 변수에 대해 설명합니다.  
  
|매개 변수|설명|  
|---------------|-----------------|  
|**이름**|필수 **String** 매개 변수입니다.<br /><br /> 환경 변수의 이름입니다.|  
|**OutputEnvironmentVariable**|선택적 **String** 출력 매개 변수입니다.<br /><br /> **이름** 매개 변수에서 지정한 환경 변수에 할당된 값이 포함됩니다.|  
|**접두사**|`Boolean` 필수 매개 변수입니다.<br /><br /> `true`인 경우 **이름** 매개 변수에서 지정한 환경 변수 값 앞에 **값** 매개 변수의 값을 연결한 다음 환경 변수에 대한 결과를 할당합니다. `false`인 경우 환경 변수에 대한 **값** 매개 변수의 값만 할당합니다.|  
|**Target**|선택적 **문자열** 매개 변수입니다.<br /><br /> 환경 변수가 저장되는 위치를 지정합니다. "`User`" 또는 "`Machine`"을 지정합니다.<br /><br /> 자세한 내용은 [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) 웹 사이트에서 "EnvironmentVariableTarget 열거형"을 참조하세요.|  
|**값**|선택적 **문자열** 매개 변수입니다.<br /><br /> **이름** 매개 변수에서 지정한 환경 변수에 할당된 값입니다. **값**이 비어 있고 해당 변수가 존재하면 변수가 삭제됩니다. 변수가 존재하지 않으면 작업을 수행할 수 없더라도 오류가 발생하지 않습니다.<br /><br /> 자세한 내용은 [MSDN](http://go.microsoft.com/fwlink/?LinkId=737) 웹 사이트에서 "Environment::SetEnvironmentVariable 메서드"를 참조하세요.|  
  
## <a name="remarks"></a>설명  
  
## <a name="see-also"></a>참고 항목  
 [작업 참조](../msbuild/msbuild-task-reference.md)
