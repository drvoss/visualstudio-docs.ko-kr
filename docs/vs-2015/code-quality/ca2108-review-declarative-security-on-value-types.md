---
title: 'CA2108: 값 형식에서 선언적 보안을 검토 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ReviewDeclarativeSecurityOnValueTypes
- CA2108
helpviewer_keywords:
- ReviewDeclarativeSecurityOnValueTypes
- CA2108
ms.assetid: d62bffdd-3826-4d52-a708-1c646c5d48c2
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f6a17bf57f00923cfd31bd477f211ba66169672a
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65687362"
---
# <a name="ca2108-review-declarative-security-on-value-types"></a>CA2108: 값 형식에서 선언적 보안을 검토하십시오.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReviewDeclarativeSecurityOnValueTypes|
|CheckId|CA2108|
|범주|Microsoft.Security|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 Public 또는 protected 값 형식이로 보호 되는 [데이터 및 모델링](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) 또는 [링크 요구가](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)합니다.

## <a name="rule-description"></a>규칙 설명
 값 형식 할당 되 고 다른 생성자를 실행 하기 전에 해당 기본 생성자에서 초기화 됩니다. 값 형식이 요청 또는 LinkDemand를 통해 보안이 유지 되 고 호출자에 게 이외의 모든 생성자 보안 검사를 충족 하는 권한이 없는 경우 기본값을 실패 하 고 보안 예외가 throw 됩니다. 값 형식 할당이 해제 되지 않습니다. 기본 생성자에서 설정 된 상태에서 중단 됩니다. 값 형식의 인스턴스를 전달 하는 호출자가 만들거나 인스턴스에 액세스 권한이 있는지를 가정 하지 마십시오.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 형식에서 보안 검사를 제거 하 고 그 자리에 메서드 수준의 보안을 사용 하 여 확인 하지 않는 한이 규칙 위반을 고정할 수 없습니다. 이러한 방식으로 위반을 수정 해도 값 형식의 인스턴스를 얻는 부적절 한 권한 있는 호출자 참고 합니다. 해당 기본 상태인 값 형식의 인스턴스는 중요 한 정보를 노출 하지 않습니다 하 고 유해한 방식으로 사용할 수 없습니다 확인 해야 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 모든 호출자에 게 보안에 위협을 없이 해당 기본 상태인 값 형식의 인스턴스를 얻을 수 있는 경우이 규칙에서 경고를 무시할 수 있습니다.

## <a name="example"></a>예제
 다음 예제에서는이 규칙을 위반 하는 값 형식을 포함 하는 라이브러리를 보여 줍니다. `StructureManager` 형식 값 형식의 인스턴스를 전달 하는 호출자가 만들거나 인스턴스에 액세스 권한이 있는지를 가정 합니다.

 [!code-csharp[FxCop.Security.DemandOnValueType#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.DemandOnValueType/cs/FxCop.Security.DemandOnValueType.cs#1)]

## <a name="example"></a>예제
 다음 응용 프로그램 라이브러리의 약점을 보여 줍니다.

 [!code-csharp[FxCop.Security.TestDemandOnValueType#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestDemandOnValueType/cs/FxCop.Security.TestDemandOnValueType.cs#1)]

 이 예제의 결과는 다음과 같습니다.

 **구조 사용자 지정 생성자: 요청이 실패 했습니다.** 
**새 값 SecuredTypeStructure 100 100**
**SecuredTypeStructure 200 200 새 값**
## <a name="see-also"></a>참고 항목
 [링크 요청만](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [데이터 및 모델링](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)
