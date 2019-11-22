---
title: Legacy Workflow Activities | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflows, activities
- activities
- workflow activities
ms.assetid: 4af7a06b-1e82-43c8-aec8-0dc5fb63d08a
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e6bdfb5e2a51a274bd5f0490954a2825a2e488c5
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302949"
---
# <a name="legacy-workflow-activities"></a>레거시 워크플로 활동
[!INCLUDE[wf](../includes/wf-md.md)]에는 제어 흐름, 조건, 이벤트 처리, 상태 관리, 응용 프로그램 및 서비스와의 통신을 위한 기능을 제공하는 일련의 기본 활동이 포함되어 있습니다. 워크플로를 디자인할 때 [!INCLUDE[wfd1](../includes/wfd1-md.md)]에서 제공한 시스템 제공 활동을 사용하거나 사용자가 직접 사용자 지정 활동을 만들 수 있습니다.

 다음 표에서는 기본적으로 제공되는 [!INCLUDE[wf2](../includes/wf2-md.md)]프레임워크 활동 집합을 보여 줍니다. Many, but not all, of these activities are represented by activity designers that can be accessed from the **Toolbox** of the [!INCLUDE[wfd2](../includes/wfd2-md.md)]. To create an activity, drag its designer from the **Toolbox** and drop it on the design surface.

|활동|설명|
|--------------|-----------------|
|[CallExternalMethodActivity](https://go.microsoft.com/fwlink?LinkID=65025)|Used with the **HandleExternalEventActivity** activity for input and output communications with a local service. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the CallExternalMethodActivity Activity](https://go.microsoft.com/fwlink?LinkID=65060).|
|[CancellationHandlerActivity](https://go.microsoft.com/fwlink?LinkID=65050)|모든 복합 활동의 자식 활동이 실행을 완료하기 전에 취소된 복합 활동의 정리 논리를 포함시킬 때 사용합니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the CancellationHandlerActivity Activity](https://go.microsoft.com/fwlink?LinkID=65061).|
|[CodeActivity](https://go.microsoft.com/fwlink?LinkID=65026)|워크플로에 Visual Basic 또는 C# 코드를 추가할 수 있도록 합니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the CodeActivity Activity](https://go.microsoft.com/fwlink?LinkID=65062).|
|[CompensatableSequenceActivity](https://go.microsoft.com/fwlink?LinkID=65027)|A compensatable version of [SequenceActivity](https://go.microsoft.com/fwlink?LinkID=65020). [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the CompensatableSequenceActivity Activity](https://go.microsoft.com/fwlink?LinkID=65002).|
|[CompensatableTransactionScopeActivity](https://go.microsoft.com/fwlink?LinkID=65051)|A compensatable version of **TransactionScopeActivity**. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the CompensatableTransactionScopeActivity Activity](https://go.microsoft.com/fwlink?LinkID=65063).|
|[CompensateActivity](https://go.microsoft.com/fwlink?LinkID=65052)|오류가 발생하면 워크플로에서 이미 수행한 작업을 실행 취소하거나 보정하기 위해 코드를 호출할 수 있도록 합니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the CompensateActivity Activity](https://go.microsoft.com/fwlink?LinkID=65064).|
|[CompensationHandlerActivity](https://go.microsoft.com/fwlink?LinkID=65053)|A wrapper for one or more activities that perform compensation for a completed TransactionScopeActivity activity [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the CompensationHandlerActivity Activity](https://go.microsoft.com/fwlink?LinkID=65065).|
|[ConditionedActivityGroup](https://go.microsoft.com/fwlink?LinkID=65017)|Executes child activities based on a condition that applies to the [ConditionedActivityGroup](https://go.microsoft.com/fwlink?LinkID=65017) activity itself and based on conditions that apply separately to each child. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the ConditionedActivityGroup Activity](https://go.microsoft.com/fwlink?LinkID=65066).|
|[DelayActivity](https://go.microsoft.com/fwlink?LinkID=65028)|시간 제한 간격을 기반으로 한 지연을 워크플로에 빌드할 수 있습니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the DelayActivity Activity](https://go.microsoft.com/fwlink?LinkID=65067).|
|[EventDrivenActivity](https://go.microsoft.com/fwlink?LinkID=65029)|지정된 이벤트가 발생할 때 실행되는 활동을 하나 이상 래핑합니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the EventDrivenActivity Activity](https://go.microsoft.com/fwlink?LinkID=65068).|
|[EventHandlersActivity](https://go.microsoft.com/fwlink?LinkID=65018)|이벤트와 활동을 연결하는 프레임워크를 제공합니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the EventHandlersActivity Activity](https://go.microsoft.com/fwlink?LinkID=65069).|
|[EventHandlingScopeActivity](https://go.microsoft.com/fwlink?LinkID=65030)|Executes its main child activity concurrently with an [EventHandlersActivity](https://go.microsoft.com/fwlink?LinkID=65018). [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the EventHandlingScopeActivity Activity](https://go.microsoft.com/fwlink?LinkID=65070).|
|[FaultHandlerActivity](https://go.microsoft.com/fwlink?LinkID=65054)|지정하는 형식의 예외를 처리하는 데 사용합니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the FaultHandlerActivity Activity](https://go.microsoft.com/fwlink?LinkID=65071).|
|[FaultHandlersActivity](https://go.microsoft.com/fwlink?LinkID=65055)|Represents a composite activity that has an ordered list of child activities of type [FaultHandlerActivity](https://go.microsoft.com/fwlink?LinkID=65054). [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the FaultHandlersActivity Activity](https://go.microsoft.com/fwlink?LinkID=65072).|
|[HandleExternalEventActivity](https://go.microsoft.com/fwlink?LinkID=65031)|Used in conjunction with the [CallExternalMethodActivity](https://go.microsoft.com/fwlink?LinkID=65025) activity for input and output communications with a local service. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the HandleExternalEventActivity Activity](https://go.microsoft.com/fwlink?LinkID=65073).|
|[IfElseActivity](https://go.microsoft.com/fwlink?LinkID=65033)|Tests a condition on each branch and performs activities on the first branch for which the condition equals **true**. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the IfElseActivity Activity](https://go.microsoft.com/fwlink?LinkID=65074).|
|[IfElseBranchActivity](https://go.microsoft.com/fwlink?LinkID=65034)|Represents a branch of an [IfElseActivity](https://go.microsoft.com/fwlink?LinkID=65033). [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the IfElseBranchActivity Activity](https://go.microsoft.com/fwlink?LinkID=65075).|
|[InvokeWebServiceActivity](https://go.microsoft.com/fwlink?LinkID=65035)|워크플로에서 웹 서비스를 호출할 수 있도록 합니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the InvokeWebServiceActivity Activity](https://go.microsoft.com/fwlink?LinkID=65076).|
|[InvokeWorkflowActivity](https://go.microsoft.com/fwlink?LinkID=65036)|워크플로에서 다른 워크플로를 호출할 수 있도록 합니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the InvokeWorkflowActivity Activity](https://go.microsoft.com/fwlink?LinkID=65077).|
|[ListenActivity](https://go.microsoft.com/fwlink?LinkID=65037)|A composite activity that contains only [EventDrivenActivity](https://go.microsoft.com/fwlink?LinkID=65029) child activities. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the ListenActivity Activity](https://go.microsoft.com/fwlink?LinkID=65078).|
|[ParallelActivity](https://go.microsoft.com/fwlink?LinkID=65038)|Provides a way to schedule two or more child **SequenceActivity** activity branches for processing at the same time. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the ParallelActivity Activity](https://go.microsoft.com/fwlink?LinkID=65079).|
|[PolicyActivity](https://go.microsoft.com/fwlink?LinkID=65019)|규칙 컬렉션을 나타낼 때 사용합니다. 규칙은 조건과 그 결과 작업으로 구성됩니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the PolicyActivity Activity](https://go.microsoft.com/fwlink?LinkID=65004).|
|[ReplicatorActivity](https://go.microsoft.com/fwlink?LinkID=65039)|단일 자식 활동의 여러 인스턴스를 만듭니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the ReplicatorActivity Activity](https://go.microsoft.com/fwlink?LinkID=65080).|
|[SequenceActivity](https://go.microsoft.com/fwlink?LinkID=65020)|순차 실행을 위해 여러 활동을 함께 연결하는 간단한 방법을 제공합니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the SequenceActivity Activity](https://go.microsoft.com/fwlink?LinkID=65081).|
|[SetStateActivity](https://go.microsoft.com/fwlink?LinkID=65041)|새 상태로의 전환을 지정합니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the SetStateActivity Activity](https://go.microsoft.com/fwlink?LinkID=65082).|
|[StateActivity](https://go.microsoft.com/fwlink?LinkID=65042)|상태 시스템 워크플로의 상태를 나타냅니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the StateActivity Activity](https://go.microsoft.com/fwlink?LinkID=65083).|
|[StateFinalizationActivity](https://go.microsoft.com/fwlink?LinkID=65043)|Used in a [StateActivity](https://go.microsoft.com/fwlink?LinkID=65042) activity as a container for child activities that are executed when leaving the **StateActivity** activity. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the StateFinalizationActivity Activity](https://go.microsoft.com/fwlink?LinkID=65008).|
|[StateInitializationActivity](https://go.microsoft.com/fwlink?LinkID=65044)|Used in a [StateActivity](https://go.microsoft.com/fwlink?LinkID=65042) activity as a container for child activities that are executed when entering the **StateActivity** activity. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the StateInitializationActivity Activity](https://go.microsoft.com/fwlink?LinkID=65006).|
|[SuspendActivity](https://go.microsoft.com/fwlink?LinkID=65056)|특별한 주의가 필요한 일부 오류 조건이 발생할 경우 개입할 수 있도록 워크플로 작업을 일시 중단합니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the SuspendActivity Activity](https://go.microsoft.com/fwlink?LinkID=65084).|
|[SynchronizationScopeActivity](https://go.microsoft.com/fwlink?LinkID=65057)|동기화된 도메인에서 포함된 활동을 순차적으로 실행합니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the SynchronizationScopeActivity Activity](https://go.microsoft.com/fwlink?LinkID=65085).|
|[TerminateActivity](https://go.microsoft.com/fwlink?LinkID=65058)|오류 조건이 발생할 경우 즉시 워크플로 작업을 중지할 수 있도록 합니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the TerminateActivity Activity](https://go.microsoft.com/fwlink?LinkID=65086).|
|[ThrowActivity](https://go.microsoft.com/fwlink?LinkID=65059)|워크플로에 대해 프로세스 메타데이터의 일부로 throw된 비즈니스 예외를 캡처할 수 있도록 합니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the ThrowActivity Activity](https://go.microsoft.com/fwlink?LinkID=65087).|
|[TransactionScopeActivity](https://go.microsoft.com/fwlink?LinkID=65093)|트랜잭션 및 예외 처리를 위한 프레임워크를 제공합니다. For more information, see [Using the TransactionScopeActivity Activity](https://go.microsoft.com/fwlink?LinkID=65088).|
|[WebServiceFaultActivity](https://go.microsoft.com/fwlink?LinkID=65046)|웹 서비스 오류 발생을 모델링할 수 있습니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the WebServiceFaultActivity Activity](https://go.microsoft.com/fwlink?LinkID=65089).|
|[WebServiceInputActivity](https://go.microsoft.com/fwlink?LinkID=65047)|웹 서비스에서 데이터를 받습니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the WebServiceInputActivity Activity](https://go.microsoft.com/fwlink?LinkID=65090).|
|[WebServiceOutputActivity](https://go.microsoft.com/fwlink?LinkID=65048)|워크플로에 대한 웹 서비스 요청에 응답합니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the WebServiceOutputActivity Activity](https://go.microsoft.com/fwlink?LinkID=65092).|
|[WhileActivity](https://go.microsoft.com/fwlink?LinkID=65049)|조건이 충족될 때까지 워크플로가 반복될 수 있도록 합니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Using the WhileActivity Activity](https://go.microsoft.com/fwlink?LinkID=65091).|

 [!INCLUDE[crabout](../includes/crabout-md.md)] how to create custom activities, see [Developing Custom Activities](https://go.microsoft.com/fwlink?LinkID=65023) and [Using the Legacy Activity Designer](../workflow-designer/using-the-legacy-activity-designer.md).

## <a name="in-this-section"></a>단원 내용
 [Activity Views (Legacy)](../workflow-designer/activity-views-legacy.md) Describes the different design views of activities.

 [How to: Add Activities to the Toolbox (Legacy)](../workflow-designer/how-to-add-activities-to-the-toolbox-legacy.md) Shows how to add activities to the toolbox.

 [How to: Create a Declarative Rule Condition (Legacy)](../workflow-designer/how-to-create-a-declarative-rule-condition-legacy.md) Shows the steps to create a declarative rule condition.

 [How to: Create a PolicyActivity Rule Set (Legacy)](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md) Shows the steps to create a PolicyActivity rule set.

 [How to: Implement a WCF Contract Operation (Legacy)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md) Shows the steps to implement a [!INCLUDE[indigo2](../includes/indigo2-md.md)] contract operation.

 [How to: Invoke a WCF Contract Operation (Legacy)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md) Shows the steps to invoke a [!INCLUDE[indigo2](../includes/indigo2-md.md)] contract operation.

## <a name="see-also"></a>관련 항목:
 [Windows Workflow Foundation Activities](https://go.microsoft.com/fwlink?LinkID=65005) [Developing Workflows](https://go.microsoft.com/fwlink?LinkID=65010) [Developing Workflow Activities](https://go.microsoft.com/fwlink?LinkID=65023)