---
title: 사용자 지정 매개 변수 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- wizards, custom parameters
- custom parameters
ms.assetid: ba5c364b-66e6-47ea-9760-a0b70de8f0a0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a879c7a842bdabff396fa2df31d0aa7326b19c50
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66312208"
---
# <a name="custom-parameters"></a>사용자 지정 매개 변수
사용자 지정 매개 변수는 마법사를 시작한 후 마법사의 작업을 제어 합니다. 관련 *.vsz* 파일은 통합된 개발 환경 (IDE)에서 패키지 되 고 마법사를 시작할 때 문자열의 배열로 마법사에 전달 하는 사용자 정의 매개 변수 배열을 제공 합니다. 마법사는 다음 문자열의 배열을 구문 분석 하 고 마법사의 실제 작동을 제어 하는 정보를 사용 합니다. 이런 방식이으로 마법사에 기능의 내용에 따라 사용자 지정할 수는 *.vsz* 파일입니다.

 반면에 컨텍스트 매개 변수 마법사가 시작 하는 경우 프로젝트의 상태를 정의 합니다. 자세한 내용은 [컨텍스트 매개 변수](../../extensibility/internals/context-parameters.md)합니다.

 다음은의 예는 *.vsz* 사용자 지정 매개 변수 파일:

```
VSWIZARD 8.0
Wizard=VsWizard.VsWizard_Engine
Param="WIZARD_NAME = Sample Wizard"
Param="WIZARD_UI = FALSE"
Param="RELATIVE_PATH = VSWizards\Classwiz\ATL"
Param="PREPROCESS_FUNCTION = CanAddATLSupport"
Param="PROJECT_TYPE = CSPROJ"
```

 작성자를 *.vsz* 파일 매개 변수 값을 추가 합니다. 사용자가 선택 하는 경우 **새 프로젝트** 또는 **새 항목 추가** 에 **파일** 메뉴에서 프로젝트를 마우스 오른쪽 단추로 클릭 하거나 **솔루션 탐색기**, IDE 문자열의 배열에 이러한 값을 수집합니다. IDE에 프로젝트의 다음 호출 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> 메서드를 <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> 집합과 프로젝트 호출 플래그를 <xref:EnvDTE.IVsExtensibility.RunWizardFile%2A> 마법사를 실행 하 고 결과 반환 하는 일을 담당 하는 메서드.

 마법사는 문자열의 배열 구문 분석 및 문자열에 적절 하 게 작동 하는 일을 담당 합니다. 사용자 지정 매개 변수를 구현 하 여 이런 방식으로 다양 한 기능을 수행 하는 마법사를 하나 만들 수 있습니다. 즉, 하나의 마법사 세 가지 있을 수 있습니다 *.vsz* 파일입니다. 각 파일 가지의 다양 한 상황에서 마법사의 동작을 제어 하는 사용자 지정 매개 변수를 전달 합니다.

 자세한 내용은 [마법사 (.vsz) 파일](../../extensibility/internals/wizard-dot-vsz-file.md)합니다.

## <a name="see-also"></a>참고자료
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>
- [컨텍스트 매개 변수](../../extensibility/internals/context-parameters.md)
- [마법사](../../extensibility/internals/wizards.md)
- [마법사 (.vsz) 파일](../../extensibility/internals/wizard-dot-vsz-file.md)