---
title: System.Activities 탭, 도구 상자 항목 선택 대화 상자 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- VS.CHOOSEITEMS.SYSTEM.ACTIVITIES_COMPONENTS
- VS.CHOOSEITEMS.SYSTEM.ACTIVITIES COMPONENTS
ms.assetid: cef390cd-eeda-42e6-9d2e-18c8325a4f06
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 29eb905a4852bf521ebee72a498b44edbdcef8df
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63445397"
---
# <a name="systemactivities-tab-choose-toolbox-items-dialog-box"></a>System.Activities 탭, 도구 상자 항목 선택 대화 상자
이 탭에는 **도구 상자 항목 선택** 대화 상자에 목록이 표시 됩니다 [!INCLUDE[wf](../includes/wf-md.md)] 활동, 템플릿 및 항목을 사용할 수 있습니다. 이 목록을 표시 하려면 선택 **도구 상자 항목 선택** 에서 **도구** 메뉴 또는 마우스 오른쪽 단추로 클릭 합니다 **도구 상자** 선택 하 고 **항목 선택**표시할 합니다 **도구 상자 항목 선택** 대화 상자에서 선택한 후 해당 **System.Activities** 탭 합니다. 목록에 기본적으로 System.Activities, System.ServiceModel.Activities 및 System.Activities.Core.Presentation 어셈블리의 워크플로 활동이 포함 그러나만 시스템에서 제공한 표시 하는 활동 및 활동에 표시 되는 다른 어셈블리를 통해 추가 된 **도구 상자** 기본적으로 선택 됩니다. 최근에 추가 된 활동을 자동으로 선택 됩니다 및에 표시 된 **도구 상자** 클릭 하면 **확인** 대화 상자에서. 또한 이러한 항목에는 표시 된 **도구 상자** 활동/항목/템플릿이 있는 네임 스페이스에 해당 하는 새 범주입니다.  
  
> [!WARNING]
> 워크플로 활동이 없는 어셈블리를 추가하려고 하면 해당 어셈블리에 활동이 없음을 알리는 오류 대화 상자가 표시됩니다.  
  
 이 대화 상자는 프로젝트를 알 수 있으므로 합니다 **System.Activities** 탭 계속 독립 실행형 XAML 또는 워크플로가 아닌 프로젝트 형식에 표시 합니다.  
  
 각 탭에서 필터링이 수행됩니다. 이 통해 워크플로 활동을 추가할 수 없는 것을 의미 합니다 **.NET 구성 요소** 탭 합니다. 통해 추가 해야 합니다 **System.Activities** 자체 탭 합니다.  
  
 나오는 않으려는 모든 항목을 선택 취소할 수 있습니다는 **도구 상자** 이 대화 상자에서 탭 또는 수행할 수도 있습니다 사용 하 여는 **삭제** 의 상황에 맞는 메뉴 옵션을 **도구 상자** 어셈블리를 참조 해제에서 항목을 제거 하지 않는 합니다 **도구 상자**합니다.  
  
 활동을 디자이너로 끌어 놓아 인스턴스화하면 해당 항목이 포함된 어셈블리가 참조 어셈블리 목록에 자동으로 추가됩니다. 어셈블리 C를 참조하는 활동인 경우 참조 어셈블리 목록에 C를 추가하지 않습니다. 어셈블리 C는 GAC 또는 활동 B와 동일한 디렉터리에 있어야 독립 실행형의 경우 어셈블리는 GAC 또는 VS의 프로브 경로에 있어야 합니다. 그래야만 Workflow Designer 화면에 활동을 끌어 놓을 수 있습니다.  
  
 **도구 상자** 설정을 기본적으로 사용자 옵션으로 저장 하므로 열면 다음 시간 합니다 **도구 상자**, 사용자 지정된 워크플로 활동 목록이 표시 됩니다. 부작용이 중 하나는 특정 도메인 항목을 추가한 경우는 **도구 상자** 를 통해를 **도구 상자 항목 선택** 대화 상자가 계속 표시에서 작업 하는 경우 해당 항목을 참조는 워크플로 콘솔 응용 프로그램입니다. 표시 하지 않을 경우 다음 상황에 맞는 메뉴를 사용 하 여 삭제 하거나 통해의 선택을 취소 합니다 **도구 상자 항목 선택** 앞에서 설명한 대로 대화 상자.  
  
 이 대화 상자의 열에는 다음과 같은 정보가 포함되어 있습니다.  
  
 이름  
 로컬 컴퓨터에 현재 등록된 워크플로 활동의 이름을 나열합니다.  
  
 네임스페이스  
 활동의 구조를 정의하는 .NET Framework 클래스 라이브러리 네임스페이스의 계층 구조를 표시합니다.  
  
 어셈블리 이름  
 활동이 포함된 .NET Framework 어셈블리의 이름과 버전을 표시합니다.  
  
 디렉터리  
 워크플로 활동이 포함된 .NET Framework 어셈블리의 위치를 표시합니다. 모든 어셈블리의 기본 위치는 전역 어셈블리 캐시(GAC)입니다.  
  
 나열된 구성 요소를 정렬하려면 열 머리글을 선택합니다.