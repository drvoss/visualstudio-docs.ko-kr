---
title: 마법사 인터페이스 (IDTWizard) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDTWizard interface
- wizards, interface
ms.assetid: 09618d9d-d115-45b6-bccc-de328994b39c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7bd4e9a650bee4f5f13f1aeab39a59a1c04a253c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66330906"
---
# <a name="wizard-interface-idtwizard"></a>마법사 인터페이스(IDTWizard)
통합된 개발 환경 (IDE)에서 사용 하 여 <xref:EnvDTE.IDTWizard> 마법사를 사용 하 여 통신 하는 인터페이스입니다. 마법사는 IDE에서 설치 하려면이 인터페이스를 구현 해야 합니다.

 <xref:EnvDTE.IDTWizard.Execute%2A> 메서드는 연결 된 유일한 메서드는 <xref:EnvDTE.IDTWizard> 인터페이스입니다. 이 메서드를 구현 하는 마법사 및 IDE 인터페이스에서 메서드를 호출 합니다. 다음 예제에서는 메서드의 서명을 보여 줍니다.

```
/* IDTWizard Method */
STDMETHOD(Execute)(THIS_
   /* [in] */ IDispatch *Application,
   /* [in] */ long hwndOwner,
   /* [in] */ SAFEARRAY * *ContextParams,
   /* [in] */ SAFEARRAY * *CustomParams,
   /* [out] [in] */ wizardResult *RetVal
   );
```

 시작 메커니즘은 둘 다에 대해 유사 합니다 **새 프로젝트** 하 고 **새 항목 추가** 마법사. 호출 중 하나를 시작 하려면를 <xref:EnvDTE.IDTWizard> Dteinternal.h에 정의 된 인터페이스입니다. 컨텍스트 및 인터페이스를 호출할 때 인터페이스에 전달 되는 사용자 지정 매개 변수 집합이 다릅니다.

 다음 정보를 설명 합니다 <xref:EnvDTE.IDTWizard> 마법사에서 작업을 구현 해야 하는 인터페이스를 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. 호출 하 여 IDE <xref:EnvDTE.IDTWizard.Execute%2A> 메서드에 전달 된 다음 마법사에서:

- DTE 개체

     DTE 개체 자동화 모델의 루트입니다.

- 코드 세그먼트와 같이 창 대화 상자에 대 한 핸들 `hwndOwner ([in] long)`합니다.

     이 마법사를 사용 하 여 `hwndOwner` 마법사 대화 상자에 대 한 부모로 합니다.

- 컨텍스트 매개 변수를 전달할 인터페이스 variant로 서 SAFEARRAY에 대 한 코드 세그먼트에 표시 된 것 처럼 `[in] SAFEARRAY (VARIANT)* ContextParams`합니다.

     컨텍스트 매개 변수는 시작 되 고 마법사의 종류와 관련 된 값의 배열 및 프로젝트의 현재 상태를 포함 합니다. IDE 마법사 컨텍스트 매개 변수를 전달합니다. 자세한 내용은 [컨텍스트 매개 변수](../../extensibility/internals/context-parameters.md)합니다.

- 사용자 지정 매개 변수를 전달할 인터페이스 변형으로 SAFEARRAY에 대 한 코드 세그먼트에 표시 된 것 처럼 `[in] SAFEARRAY (VARIANT)* CustomParams`합니다.

     사용자 지정 매개 변수는 사용자 정의 매개 변수 배열을 포함 합니다. .Vsz 파일 IDE를 사용자 지정 매개 변수를 전달합니다. 값으로 결정 됩니다는 `Param=` 문입니다. 자세한 내용은 [사용자 지정 매개 변수](../../extensibility/internals/custom-parameters.md)합니다.

- 인터페이스에 대 한 값을 반환 합니다.

    ```
    wizardResultSuccess = -1,
    wizardResultFailure = 0
    wizardResultCancel = 1
    wizardResultBackout = 2
    ```

## <a name="see-also"></a>참고 항목
- [컨텍스트 매개 변수](../../extensibility/internals/context-parameters.md)
- [사용자 지정 매개 변수](../../extensibility/internals/custom-parameters.md)
- [마법사](../../extensibility/internals/wizards.md)
- [마법사(.Vsz) 파일](../../extensibility/internals/wizard-dot-vsz-file.md)