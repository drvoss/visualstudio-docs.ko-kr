---
title: '방법: 디버그 단계별 옵션 (레거시) 변경 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- branch stepping
- debugging, stepping options
- debugging workflows, stepping options
- stepping, changing options
- instance stepping
ms.assetid: aedc06af-d58a-44d6-aee4-f397f1f923a0
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 505f876b9c7943c8b039b74459552b77ce539477
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62954455"
---
# <a name="how-to-change-the-debug-stepping-option-legacy"></a>방법: 단계별 디버깅 옵션 변경(레거시)
이 항목에서는 [!INCLUDE[wf](../includes/wf-md.md)]에서 동시 동작이 있는 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 애플리케이션의 단계별 디버깅 옵션을 변경하는 방법에 대해 설명합니다. 레거시 [!INCLUDE[wfd2](../includes/wfd2-md.md)]는 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] 또는 [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]를 대상으로 해야 하는 경우에 사용합니다.  
  
 동시에 실행 예는 레거시 활동을 디버깅할 때 **ParallelActivity** 하거나 **ConditionedActivityGroup**, 코드를 단계별로 실행 하려면 두 옵션 중 하나를 사용할 수 있습니다.  
  
 레거시 워크플로 프로젝트에서 단계별 디버깅 옵션을 변경하려면 다음 단계를 따르세요.  
  
## <a name="procedures"></a>절차  
  
#### <a name="to-change-the-debug-stepping-option"></a>디버그 단계별 옵션을 변경하려면  
  
1. Visual Studio를 시작합니다.  
  
2. 기존 레거시 워크플로 프로젝트를 열거나 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] 또는 [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]를 대상으로 하며 동시 활동을 사용하는 새 프로젝트를 만듭니다.  
  
3. 에 **워크플로** 메뉴에서에서 [!INCLUDE[wfd2](../includes/wfd2-md.md)], 가리킨 **디버그**를 가리킨 다음 **단계별 옵션**.  
  
4. 선택 **인스턴스** 하거나 **분기**합니다.  
  
## <a name="see-also"></a>참고 항목  
 [레거시 워크플로 디버깅](../workflow-designer/debugging-legacy-workflows.md)   
 [단계별 디버깅 옵션(레거시)](../workflow-designer/debug-stepping-options-legacy.md)