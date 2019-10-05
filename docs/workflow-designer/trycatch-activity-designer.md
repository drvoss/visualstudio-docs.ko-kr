---
title: 워크플로 디자이너-TryCatch 활동 디자이너
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TryCatch.UI
- System.Activities.Statements.Catch`1.UI
ms.assetid: 02a326c2-4009-442f-b7cb-e42121fd2992
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 079c25b2bbaa37432009f0eeade9673f8d0afd28
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62433957"
---
# <a name="trycatch-activity-designer"></a>TryCatch 활동 디자이너

합니다 **TryCatch** 활동 디자이너는 만들기 및 구성 하는 데 사용 되는 <xref:System.Activities.Statements.TryCatch> 활동입니다.

## <a name="the-trycatch-activity"></a>TryCatch 활동
 <xref:System.Activities.Statements.TryCatch> 활동에 포함 한 <xref:System.Activities.Statements.TryCatch.Try%2A> 활동의 컬렉션인 **Catch\<TException >** 및 <xref:System.Activities.Statements.TryCatch.Finally%2A> 활동. <xref:System.Activities.Statements.Catch%601> 형식의 **TException** 포함 된 <xref:System.Activities.Statements.Catch%601.ExceptionType%2A> 및 <xref:System.Activities.Statements.Catch%601.Action%2A>합니다. 둘 다 일반적인 예외 기반의 오류 처리 메커니즘을 구현하는 데 사용됩니다. <xref:System.Activities.Statements.TryCatch> 활동은 <xref:System.Activities.Statements.TryCatch.Try%2A> 활동을 실행하려고 합니다. 경우는 <xref:System.Activities.Statements.TryCatch.Try%2A> 작업 예외를 throw 합니다 <xref:System.Activities.Statements.TryCatch> 활동은 해당 **Catch < TException\>**  예외와 일치 하는 컬렉션입니다. 일치 하는 경우 해당 <xref:System.Activities.Statements.Catch%601.Action%2A> 해당 **Catch\<TException >** 실행 되 면 오류 처리는 예외에 대 한 논리를 제공 합니다. <xref:System.Activities.Statements.TryCatch.Try%2A> 섹션의 활동이 성공적으로 완료되었거나 <xref:System.Activities.Statements.TryCatch.Catches%2A>의 활동이 성공적으로 완료된 경우 <xref:System.Activities.Statements.TryCatch> 활동은 해당 <xref:System.Activities.Statements.TryCatch.Finally%2A> 활동을 실행합니다. 자세한 내용은 [Windows 워크플로 예외](/dotnet/framework/windows-workflow-foundation/exceptions)합니다.

### <a name="using-the-trycatch-activity-designer"></a>TryCatch 활동 디자이너 사용

액세스는 **TryCatch** 활동 디자이너를 **오류 처리** 범주의 합니다 **도구 상자**.

**TryCatch** 활동 디자이너에서 끌 수 있습니다 합니다 **도구 상자** 작업은 일반적으로, 등 배치 위치는 워크플로 디자이너 화면에 끌어 놓 및를 <xref:System.Activities.Statements.Sequence>합니다. 이렇게 하면 기본 <xref:System.Activities.Statements.TryCatch>인 TryCatch라는 이름의 <xref:System.Activities.Activity.DisplayName%2A> 활동이 만들어집니다. <xref:System.Activities.Activity.DisplayName%2A> 헤더의 값을 편집할 수 있습니다 합니다 **TryCatch** 활동 디자이너 또는 합니다 **DisplayName** 속성 그리드의 상자. 화면에서 다른 속성을 편집 해야 합니다 **TryCatch** 활동 디자이너입니다.

오른쪽 위 모서리에 있는 확장명 단추를 클릭 **TryCatch** 디자이너를 **시도**합니다 **Catch**, 및 **마지막** 상자에 확장 된 보기입니다. Catch를 추가 하려면 클릭 합니다 **새 catch 추가** 단추를 **TryCatch** 디자이너입니다. 단추가 형식 콤보 상자로 바뀝니다. 예외 형식을 선택하고 &lt;ENTER&gt; 키를 눌러 Catch를 추가합니다. 추가한 후에 **Catch**하면 catch 영역이 확장 되 고 활동 catch에 대 한 실행 논리를 정의 하는 catch를 삭제할 수 있습니다. 확장된 Catch 영역 오른쪽에는 텍스트 상자가 있습니다. 이 텍스트 상자를 사용하여 예외 변수의 이름을 지정할 수 있습니다. 동일한 활동에 대 한 예외 변수의 사용할 수 있습니다 **Catch**합니다.

합니다 **TryCatch** 디자이너 편집을 지원 하지 않습니다 **Catch**합니다. 삭제 해야 하는 예외 형식을 변경 하려는 경우는 **Catch** 하 고 새 계정을 추가 합니다. A **Catch** 선택 하 고 삭제 하거나 선택 하 여 삭제할 수 있습니다 **삭제** 마우스 오른쪽 단추로 클릭 하 여 액세스 되는 상황에 맞는 메뉴에 있습니다.

### <a name="the-trycatch-properties"></a>TryCatch 속성

다음 표는 <xref:System.Activities.Statements.TryCatch>속성 디자이너에서 사용 되는 방법을 설명 합니다.

|속성 이름|필수|사용|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.TryCatch> 활동의 선택적 이름을 지정합니다. 기본 TryCatch입니다.|
|<xref:System.Activities.Statements.TryCatch.Try%2A>|False|<xref:System.Activities.Statements.TryCatch>를 실행할 때 먼저 실행된 활동입니다.|
|<xref:System.Activities.Statements.TryCatch.Catches%2A>|False|컬렉션인 **Catch** 때 확인 해야 할 요소는 <xref:System.Activities.Statements.TryCatch.Try%2A> 활동이 예외를 throw 합니다.<br /><br /> <xref:System.Activities.Statements.TryCatch.Catches%2A>에 하나 이상의 활동을 추가하거나 <xref:System.Activities.Statements.TryCatch.Finally%2A> 블록에 활동을 추가해야 합니다.|
|<xref:System.Activities.Statements.TryCatch.Finally%2A>|False|<xref:System.Activities.Statements.TryCatch.Try%2A> 및 <xref:System.Activities.Statements.TryCatch.Catches%2A> 컬렉션의 필요한 모든 활동이 실행 완료될 때 실행할 활동입니다.<br /><br /> <xref:System.Activities.Statements.TryCatch.Catches%2A>에 하나 이상의 활동을 추가하거나 <xref:System.Activities.Statements.TryCatch.Finally%2A> 블록에 활동을 추가해야 합니다.|

## <a name="see-also"></a>참고자료

- [컬렉션](../workflow-designer/collection-activity-designers.md)
- [Rethrow](../workflow-designer/rethrow-activity-designer.md)
- [Throw](../workflow-designer/throw-activity-designer.md)