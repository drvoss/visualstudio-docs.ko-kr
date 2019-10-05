---
title: 단계별 디버깅 옵션 (레거시) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- branch stepping
- stepping, options in workflow debugging
- debugging, stepping options
- debugging workflows, stepping options
- instance stepping
ms.assetid: 3e9e3041-68c7-4f16-9bd6-da5e5144744b
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b1f0761ba750146ce7f8cc52e6992dae689f7779
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62976954"
---
# <a name="debug-stepping-options-legacy"></a>단계별 디버깅 옵션(레거시)
이 항목에서는 [!INCLUDE[wf](../includes/wf-md.md)]에서 동시 활동이 있는 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 애플리케이션을 디버깅하는 방법에 대해 설명합니다. 레거시 [!INCLUDE[wfd2](../includes/wfd2-md.md)]는 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] 또는 [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]를 대상으로 해야 하는 경우에 사용합니다.  
  
 동시에 실행 예는 레거시 활동을 디버깅할 때 **ParallelActivity** 하거나 **ConditionedActivityGroup**, 코드를 단계별로 실행 하려면 다음 두 옵션 중 하나를 사용할 수 있습니다 .  
  
- **분기 단계별 실행.** 이 단계별 실행이 모드를 사용 하면 단계별로 같은 복합 활동의 특정 분기를 디버그 하는 **ParallelActivity** 또는 **ConditionalActivityGroup** 활동입니다. 이 옵션을 사용하여 디버깅하는 경우 워크플로의 다른 활동이 동시에 실행되어 제어가 변경되는 것을 확인할 수 없습니다. 워크플로의 다른 활동이 동시에 실행될 수 있지만 디버거는 현재 선택된 분기의 활동만 단계별로 실행합니다. 맨 왼쪽 분기에 기본적으로 예를 들어를 **ParallelActivity** 활동과의 첫 번째 자식 활동을 **ConditionedActivityGroup** 활동 단계별 실행에 사용 됩니다. 다른 분기나 자식 활동을 디버깅하려면 해당 분기나 자식 활동에 명시적 중단점을 설정해야 합니다. 중단점이 트리거되면 단계별 실행이 해당 분기에서 계속됩니다.  
  
- **인스턴스 단계별 실행.** 이 단계별 실행 모드를 사용하여 워크플로에서 동시에 실행되는 활동을 단계별로 실행하고 디버깅할 수 있습니다. 이 옵션을 사용하면 워크플로 내에서 동시에 실행되는 활동이 실행될 때 제어가 변경되는 것을 확인할 수 있습니다.  
  
  기본적으로 분기 단계별 실행 옵션이 선택되며, 사용자는 레거시 워크플로를 디버깅하는 동안 두 옵션 사이를 전환할 수 있습니다.  
  
  레거시 상태 시스템 워크플로를 디버깅할 때는 인스턴스 단계별 실행 옵션을 선택해야 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [레거시 워크플로 디버깅](../workflow-designer/debugging-legacy-workflows.md)   
 [방법: 단계별 디버깅 옵션 변경(레거시)](../workflow-designer/how-to-change-the-debug-stepping-option-legacy.md)