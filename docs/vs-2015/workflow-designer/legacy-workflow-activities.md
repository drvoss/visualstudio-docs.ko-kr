---
title: 레거시 워크플로 활동 | Microsoft Docs
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: fa5a6da8d45435fc7c755905a19e95e90a98ad57
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63000156"
---
# <a name="legacy-workflow-activities"></a>레거시 워크플로 활동
[!INCLUDE[wf](../includes/wf-md.md)]에는 제어 흐름, 조건, 이벤트 처리, 상태 관리, 응용 프로그램 및 서비스와의 통신을 위한 기능을 제공하는 일련의 기본 활동이 포함되어 있습니다. 워크플로를 디자인할 때 [!INCLUDE[wfd1](../includes/wfd1-md.md)]에서 제공한 시스템 제공 활동을 사용하거나 사용자가 직접 사용자 지정 활동을 만들 수 있습니다.  
  
 다음 표에서는 기본적으로 제공되는 [!INCLUDE[wf2](../includes/wf2-md.md)]프레임워크 활동 집합을 보여 줍니다. 많은 전부는 아니지만, 이러한 작업에서 액세스할 수 있는 activity designer가 표시 됩니다는 **도구 상자** 의 [!INCLUDE[wfd2](../includes/wfd2-md.md)]합니다. 활동을 만들려면 해당 디자이너를 끌어 합니다 **도구 상자** 디자인 화면에 놓습니다.  
  
|활동|설명|  
|--------------|-----------------|  
|[CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65025)|사용 된 **HandleExternalEventActivity** 로컬 서비스와의 입출력 통신에 대 한 작업입니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][CallExternalMethodActivity 활동 사용](http://go.microsoft.com/fwlink?LinkID=65060)합니다.|  
|[CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050)|모든 복합 활동의 자식 활동이 실행을 완료하기 전에 취소된 복합 활동의 정리 논리를 포함시킬 때 사용합니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][CancellationHandlerActivity 활동을 사용 하 여](http://go.microsoft.com/fwlink?LinkID=65061)입니다.|  
|[CodeActivity](http://go.microsoft.com/fwlink?LinkID=65026)|워크플로에 Visual Basic 또는 C# 코드를 추가할 수 있도록 합니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][CodeActivity 활동을 사용 하 여](http://go.microsoft.com/fwlink?LinkID=65062)입니다.|  
|[CompensatableSequenceActivity](http://go.microsoft.com/fwlink?LinkID=65027)|보정 가능한 버전 [SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020)합니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][CompensatableSequenceActivity 활동을 사용 하 여](http://go.microsoft.com/fwlink?LinkID=65002)입니다.|  
|[CompensatableTransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65051)|보정 가능한 버전 **TransactionScopeActivity**합니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][CompensatableTransactionScopeActivity 활동을 사용 하 여](http://go.microsoft.com/fwlink?LinkID=65063)입니다.|  
|[CompensateActivity](http://go.microsoft.com/fwlink?LinkID=65052)|오류가 발생하면 워크플로에서 이미 수행한 작업을 실행 취소하거나 보정하기 위해 코드를 호출할 수 있도록 합니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][CompensateActivity 활동을 사용 하 여](http://go.microsoft.com/fwlink?LinkID=65064)입니다.|  
|[CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65053)|완료 된 TransactionScopeActivity 활동에 대 한 보정을 수행 하는 하나 이상의 활동에 대 한 래퍼 [!INCLUDE[crdefault](../includes/crdefault-md.md)] [CompensationHandlerActivity 활동을 사용 하 여](http://go.microsoft.com/fwlink?LinkID=65065)입니다.|  
|[ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)|에 적용 되는 조건에 따라 자식 활동을 실행 합니다 [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017) 활동 자체 각 자식에 별도로 적용 되는 조건을 기반으로 합니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][ConditionedActivityGroup 활동 사용](http://go.microsoft.com/fwlink?LinkID=65066)합니다.|  
|[DelayActivity](http://go.microsoft.com/fwlink?LinkID=65028)|시간 제한 간격을 기반으로 한 지연을 워크플로에 빌드할 수 있습니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][DelayActivity 활동 사용](http://go.microsoft.com/fwlink?LinkID=65067)합니다.|  
|[EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029)|지정된 이벤트가 발생할 때 실행되는 활동을 하나 이상 래핑합니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][EventDrivenActivity 활동을 사용 하 여](http://go.microsoft.com/fwlink?LinkID=65068)입니다.|  
|[EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018)|이벤트와 활동을 연결하는 프레임워크를 제공합니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][EventHandlersActivity 활동 사용](http://go.microsoft.com/fwlink?LinkID=65069)합니다.|  
|[EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030)|주 자식 활동와 동시에 실행 되는 [EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018)합니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][EventHandlingScopeActivity 활동 사용](http://go.microsoft.com/fwlink?LinkID=65070)합니다.|  
|[FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65054)|지정하는 형식의 예외를 처리하는 데 사용합니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][FaultHandlerActivity 활동을 사용 하 여](http://go.microsoft.com/fwlink?LinkID=65071)입니다.|  
|[FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055)|순서가 지정 된 형식의 자식 활동 목록이 있는 복합 활동을 나타냅니다 [FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65054)합니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][FaultHandlersActivity 활동을 사용 하 여](http://go.microsoft.com/fwlink?LinkID=65072)입니다.|  
|[HandleExternalEventActivity](http://go.microsoft.com/fwlink?LinkID=65031)|와 함께 사용 합니다 [CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65025) 로컬 서비스와의 입출력 통신에 대 한 작업입니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][HandleExternalEventActivity 활동 사용](http://go.microsoft.com/fwlink?LinkID=65073)합니다.|  
|[IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65033)|각 분기에서 조건을 테스트 하 고 조건이 인 첫 번째 분기에서 활동을 수행 **true**합니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][IfElseActivity 활동 사용](http://go.microsoft.com/fwlink?LinkID=65074)합니다.|  
|[IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)|분기를 나타냅니다는 [IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65033)합니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][IfElseBranchActivity 활동을 사용 하 여](http://go.microsoft.com/fwlink?LinkID=65075)입니다.|  
|[InvokeWebServiceActivity](http://go.microsoft.com/fwlink?LinkID=65035)|워크플로에서 웹 서비스를 호출할 수 있도록 합니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][InvokeWebServiceActivity 활동을 사용 하 여](http://go.microsoft.com/fwlink?LinkID=65076)입니다.|  
|[InvokeWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65036)|워크플로에서 다른 워크플로를 호출할 수 있도록 합니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][InvokeWorkflowActivity 활동을 사용 하 여](http://go.microsoft.com/fwlink?LinkID=65077)입니다.|  
|[ListenActivity](http://go.microsoft.com/fwlink?LinkID=65037)|만 포함 하는 복합 활동 [EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029) 자식 활동입니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][ListenActivity 활동 사용](http://go.microsoft.com/fwlink?LinkID=65078)합니다.|  
|[ParallelActivity](http://go.microsoft.com/fwlink?LinkID=65038)|둘 이상의 자식 예약 하는 방법을 제공 **SequenceActivity** 활동 분기가 동시에 처리 합니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][ParallelActivity 활동 사용](http://go.microsoft.com/fwlink?LinkID=65079)합니다.|  
|[PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)|규칙 컬렉션을 나타낼 때 사용합니다. 규칙은 조건과 그 결과 작업으로 구성됩니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][PolicyActivity 활동](http://go.microsoft.com/fwlink?LinkID=65004)합니다.|  
|[ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)|단일 자식 활동의 여러 인스턴스를 만듭니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][ReplicatorActivity 활동을 사용 하 여](http://go.microsoft.com/fwlink?LinkID=65080)입니다.|  
|[SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020)|순차 실행을 위해 여러 활동을 함께 연결하는 간단한 방법을 제공합니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][SequenceActivity 활동 사용](http://go.microsoft.com/fwlink?LinkID=65081)합니다.|  
|[SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65041)|새 상태로의 전환을 지정합니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][SetStateActivity 활동](http://go.microsoft.com/fwlink?LinkID=65082)합니다.|  
|[StateActivity](http://go.microsoft.com/fwlink?LinkID=65042)|상태 시스템 워크플로의 상태를 나타냅니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][StateActivity 활동 사용](http://go.microsoft.com/fwlink?LinkID=65083)합니다.|  
|[StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65043)|에 사용 되는 [StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) 종료 시 실행 되는 자식 활동의 컨테이너로 작업 합니다 **StateActivity** 활동입니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][StateFinalizationActivity 활동](http://go.microsoft.com/fwlink?LinkID=65008)합니다.|  
|[StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65044)|에 사용 되는 [StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) 입력할 때 실행 되는 자식 활동의 컨테이너로 작업 합니다 **StateActivity** 활동입니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][StateInitializationActivity 활동 사용](http://go.microsoft.com/fwlink?LinkID=65006)합니다.|  
|[SuspendActivity](http://go.microsoft.com/fwlink?LinkID=65056)|특별한 주의가 필요한 일부 오류 조건이 발생할 경우 개입할 수 있도록 워크플로 작업을 일시 중단합니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][SuspendActivity 활동을 사용 하 여](http://go.microsoft.com/fwlink?LinkID=65084)입니다.|  
|[SynchronizationScopeActivity](http://go.microsoft.com/fwlink?LinkID=65057)|동기화된 도메인에서 포함된 활동을 순차적으로 실행합니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][SynchronizationScopeActivity 활동을 사용 하 여](http://go.microsoft.com/fwlink?LinkID=65085)입니다.|  
|[TerminateActivity](http://go.microsoft.com/fwlink?LinkID=65058)|오류 조건이 발생할 경우 즉시 워크플로 작업을 중지할 수 있도록 합니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][TerminateActivity 활동을 사용 하 여](http://go.microsoft.com/fwlink?LinkID=65086)입니다.|  
|[ThrowActivity](http://go.microsoft.com/fwlink?LinkID=65059)|워크플로에 대해 프로세스 메타데이터의 일부로 throw된 비즈니스 예외를 캡처할 수 있도록 합니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][ThrowActivity 활동을 사용 하 여](http://go.microsoft.com/fwlink?LinkID=65087)입니다.|  
|[TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093)|트랜잭션 및 예외 처리를 위한 프레임워크를 제공합니다. 자세한 내용은 [TransactionScopeActivity 활동을 사용 하 여](http://go.microsoft.com/fwlink?LinkID=65088)입니다.|  
|[WebServiceFaultActivity](http://go.microsoft.com/fwlink?LinkID=65046)|웹 서비스 오류 발생을 모델링할 수 있습니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][WebServiceFaultActivity 활동을 사용 하 여](http://go.microsoft.com/fwlink?LinkID=65089)입니다.|  
|[WebServiceInputActivity](http://go.microsoft.com/fwlink?LinkID=65047)|웹 서비스에서 데이터를 받습니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][WebServiceInputActivity 활동을 사용 하 여](http://go.microsoft.com/fwlink?LinkID=65090)입니다.|  
|[WebServiceOutputActivity](http://go.microsoft.com/fwlink?LinkID=65048)|워크플로에 대한 웹 서비스 요청에 응답합니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][WebServiceOutputActivity 활동을 사용 하 여](http://go.microsoft.com/fwlink?LinkID=65092)입니다.|  
|[WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)|조건이 충족될 때까지 워크플로가 반복될 수 있도록 합니다. [!INCLUDE[crdefault](../includes/crdefault-md.md)][WhileActivity 활동을 사용 하 여](http://go.microsoft.com/fwlink?LinkID=65091)입니다.|  
  
 [!INCLUDE[crabout](../includes/crabout-md.md)] 사용자 지정 작업 만들기를 참조 하는 방법 [사용자 지정 활동 개발](http://go.microsoft.com/fwlink?LinkID=65023) 하 고 [레거시 활동 디자이너를 사용 하 여](../workflow-designer/using-the-legacy-activity-designer.md)입니다.  
  
## <a name="in-this-section"></a>섹션 내용  
 [활동 뷰(레거시)](../workflow-designer/activity-views-legacy.md)  
 다양한 활동의 디자인 뷰에 대해 설명합니다.  
  
 [방법: 도구 상자에 활동 추가(레거시)](../workflow-designer/how-to-add-activities-to-the-toolbox-legacy.md)  
 도구 상자에 활동을 추가하는 방법을 보여 줍니다.  
  
 [방법: 선언적 규칙 조건 만들기(레거시)](../workflow-designer/how-to-create-a-declarative-rule-condition-legacy.md)  
 선언적 규칙 조건을 만드는 단계를 소개합니다.  
  
 [방법: PolicyActivity 규칙 집합 만들기(레거시)](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md)  
 PolicyActivity 규칙 집합을 만드는 단계를 설명합니다.  
  
 [방법: WCF 계약 작업 구현(레거시)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)  
 [!INCLUDE[indigo2](../includes/indigo2-md.md)] 계약 작업을 구현하는 단계를 보여 줍니다.  
  
 [방법: WCF 계약 작업 호출(레거시)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)  
 [!INCLUDE[indigo2](../includes/indigo2-md.md)] 계약 작업을 호출하는 단계를 보여 줍니다.  
  
## <a name="see-also"></a>참고 항목  
 [Windows Workflow Foundation 활동](http://go.microsoft.com/fwlink?LinkID=65005)   
 [워크플로 개발](http://go.microsoft.com/fwlink?LinkID=65010)   
 [워크플로 활동 개발](http://go.microsoft.com/fwlink?LinkID=65023)