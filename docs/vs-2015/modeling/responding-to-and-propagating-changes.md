---
title: 변경 내용 전파에 응답 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, events
ms.assetid: fc2e9ac5-7a84-44ed-9945-94e45f89c227
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a9838e934421e619c85f348052fbe589288391c1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68158839"
---
# <a name="responding-to-and-propagating-changes"></a>변경 내용에 대한 대응 및 전파
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

요소를 생성, 삭제 하거나 업데이트할 때이 모델의 다른 부분 또는 파일, 데이터베이스 또는 다른 구성 요소와 같은 외부 리소스에 변경 내용을 전파 하는 코드를 작성할 수 있습니다.  
  
## <a name="in-this-section"></a>섹션 내용  
 예를 들어, 다음 순서 대로 이러한 기술을 살펴보겠습니다.  
  
|방법|시나리오|자세한 내용은 다음을 참조하세요.|  
|---------------|---------------|--------------------------|  
|계산 도메인 속성을 정의 합니다.|도메인 속성 값은 모델의 다른 속성에서 계산 됩니다. 예를 들어, 가격이 관련 요소의 가격 합계입니다.|[계산된 스토리지 속성 및 사용자 지정 스토리지 속성](../modeling/calculated-and-custom-storage-properties.md)|  
|사용자 지정 저장소 도메인 속성을 정의 합니다.|모델 또는 외부에서 다른 부분에 저장 하는 도메인 속성입니다. 예를 들어 모델의 트리에 식 문자열을 구문 분석할 수 있습니다.|[계산된 스토리지 속성 및 사용자 지정 스토리지 속성](../modeling/calculated-and-custom-storage-properties.md)|  
|OnValueChanging 등 OnDeleting 변경 처리기를 재정의 합니다.|다양 한 요소를의 동기화를 유지 하 고 동기화 외부 값에서 모델을 사용 하 여 키를 누릅니다.<br /><br /> 값이 정의 된 범위를 제한 합니다.<br /><br /> 속성 값 및 기타 변경 전후의 직전에 호출 됩니다. 예외를 throw 하 여 변경 내용을 종료할 수 있습니다.|[도메인 속성 값 변경 처리기](../modeling/domain-property-value-change-handlers.md)|  
|규칙|변경에 발생 한 트랜잭션의 끝 직전 실행 대기 중인 규칙을 정의할 수 있습니다. 실행 취소 또는 다시 실행에서 실행 되지 않습니다. 저장소의 한 부분을 상호 동기화 되도록 사용 합니다.|[규칙으로 모델 내부의 변경 내용 전파](../modeling/rules-propagate-changes-within-the-model.md)|  
|이벤트를 저장 합니다.|모델링 저장소 추가 또는 요소 또는 링크를 삭제 하거나 속성의 값을 변경 하는 등의 이벤트에 대 한 알림을 제공 합니다. 이벤트는 실행 취소 및 다시 실행에도 실행 됩니다. 저장소 이벤트를 사용 하 여 저장소에 있지 않은 값을 업데이트 합니다.|[이벤트 처리기로 모델 외부의 변경 내용 전파](../modeling/event-handlers-propagate-changes-outside-the-model.md)|  
|.NET 이벤트|도형에는 마우스 클릭 및 기타 제스처에 응답 하는 이벤트 처리기가 있습니다. 각 개체에 대 한 이러한 이벤트에 등록 해야 합니다. 등록은 InitializeInstanceResources, 재정의에서 일반적으로 수행 및 각 요소에 대해 수행 해야 합니다.<br /><br /> 일반적으로 이러한 이벤트는 트랜잭션 외부에서 발생 합니다.|[방법: 모양 또는 데코레이터 클릭 가로채기](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)|  
|범위 규칙|범위 규칙의 셰이프를 범위를 제한 하도록 특별히 사용 됩니다.|[BoundsRules로 모양 위치 및 크기 제한](../modeling/boundsrules-constrain-shape-location-and-size.md)|  
|선택 규칙|특히 선택 규칙 항목을 선택할 수를 제한 합니다.|[방법: 현재 선택 항목 액세스 및 제약](../modeling/how-to-access-and-constrain-the-current-selection.md)|  
|OnAssocatedPropertyChanged|모양 및 연결선 섀도, 화살표, 색 및 선 두께 및 스타일 등의 기능을 사용 하 여 모델 요소의 상태를 나타냅니다.|[모양 및 연결선을 업데이트하여 모델 반영](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)|  
  
## <a name="comparing-rules-and-store-events"></a>**규칙 및 저장소 이벤트를 비교합니다.**  
 변경 notifiers, 규칙 및 이벤트 모델의 변경이 발생할 때 실행 됩니다.  
  
 규칙에는 변경 내용이 발생 한 종료 트랜잭션을 일반적으로 적용 됩니다 및 이벤트는 트랜잭션의 변경 내용을 커밋한 후에 적용 됩니다.  
  
 외부 저장소에서 일관성을 유지 하려면 저장소 및 규칙 개체를 사용 하 여 모델을 동기화 하려면 store 이벤트를 사용 합니다.  
  
- **사용자 지정 규칙을 만드는** 추상 규칙에서 파생 클래스로 사용자 지정 규칙을 만듭니다. 또한 사용자 지정 규칙에 대 한 프레임 워크를 알려야 합니다. 자세한 내용은 [규칙이 전파 변경 내용을 내에서 모델](../modeling/rules-propagate-changes-within-the-model.md)합니다.  
  
- **이벤트 구독** 이벤트를 구독할 수 있습니다, 전에 이벤트 처리기 및 대리자를 만듭니다. 사용 하 여는 <xref:Microsoft.VisualStudio.Modeling.Store.EventManagerDirectory%2A>속성 이벤트를 구독할 수 있습니다. 자세한 내용은 [이벤트 처리기 전파 변경 외부 모델](../modeling/event-handlers-propagate-changes-outside-the-model.md)합니다.  
  
- **변경을 실행 취소 중** 트랜잭션의 실행을 취소 하면 이벤트가 발생 하지만 규칙이 적용 되지 않습니다. 규칙 값을 변경 하 고 해당 변경 내용을 취소할 경우에 취소 작업을 실행 하는 동안 값을 원래 값으로 재설정 됩니다. 이벤트가 발생할 때 원래 값으로 다시 값을 수동으로 변경 해야 합니다. Transactons 및 실행 취소 하는 방법에 대 한 자세한 내용은를 참조 하세요. [방법: 트랜잭션을 사용 모델을 업데이트 하 여](../modeling/how-to-use-transactions-to-update-the-model.md)입니다.  
  
- **규칙 및 이벤트를 이벤트 인수를 전달** 두 이벤트 규칙 전달 되는 `EventArgs` 모델 변경 방법에 대 한 정보가 포함 된 매개 변수입니다.  
  
## <a name="see-also"></a>관련 항목  
 [방법: 모양 또는 데코레이터 클릭 가로채기](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)   
 [도메인별 언어를 사용자 지정하는 코드 작성](../modeling/writing-code-to-customise-a-domain-specific-language.md)
