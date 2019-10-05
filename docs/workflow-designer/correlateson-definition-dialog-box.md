---
title: 워크플로 디자이너-CorrelatesOn 정의 대화 상자
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CorrelatesOnDefinition.UI
ms.assetid: 8b2b627a-f236-4479-aa09-525df65e3413
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d7b7336a3f3b0c2725f4e52116d0add8bf13b90e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62949824"
---
# <a name="correlateson-definition-dialog-box"></a>CorrelatesOn 정의 대화 상자

**CorrelatesOn** 워크플로 디자이너에서 편집 대화 상자를 사용 합니다 <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> 의 속성을 <xref:System.ServiceModel.Activities.Receive> 활동. 자세한 내용은 [활동 디자이너 수신](../workflow-designer/receive-activity-designer.md)합니다.

<xref:System.ServiceModel.Activities.Receive> 활동 간의 상관 관계는 워크플로에서 서비스 작업 간의 다양한 상호 연결 방식을 지정합니다.

다음 표에 사용자 인터페이스 (UI) 요소에는 **CorrelatesOn** 대화 상자.

|UI 요소|설명|
|-|-----------------|
|**CorrelatesWith**|메시지를 적절한 워크플로 인스턴스로 라우팅하는 데 사용되는 <xref:System.ServiceModel.Activities.CorrelationHandle>입니다.|
|**XPath 쿼리**|받은 메시지에서 상관 관계 데이터를 추출하는 데 사용되는 쿼리가 포함된 키/값 쌍입니다. 이 값에 해당 하는 <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> 속성입니다. XPath 쿼리는 <xref:System.ServiceModel.MessageQuerySet> 개체에 포함되어 있습니다.|

## <a name="to-launch-the-correlateson-dialog-box"></a>CorrelatesOn 대화 상자를 시작하려면

합니다 **수신** 활동 디자이너에서 끌 수 있습니다 **도구 상자** 일반적으로 활동을 배치 하는 위치, 워크플로 디자이너 화면에 끌어 놓 및 합니다. Activity designer 만들어집니다를 <xref:System.ServiceModel.Activities.Receive> 기본값을 사용 하 여 작업 <xref:System.Activities.Activity.DisplayName%2A> 수신 합니다. 열려는 **CorrelatesOn 정의** 대화 상자를 선택 합니다 **수신** 활동 디자이너에 다음 속성 표의 컬렉션 텍스트 옆 줄임표 단추를 선택는  **CorrelatesOn** 속성입니다.

## <a name="see-also"></a>참고자료

- <xref:System.ServiceModel.Activities.Receive>
- [상관 관계 이니셜라이저 추가 대화 상자](../workflow-designer/add-correlationinitializers-dialog-box.md)
- [상관 관계 초기화 대화 상자](../workflow-designer/initialize-correlation-dialog-box.md)