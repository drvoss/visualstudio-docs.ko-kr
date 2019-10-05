---
title: 작업 선택 대화 상자 (레거시) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Workflow.Activities.Design.OperationPickerDialog.UI
ms.assetid: bc3ec902-7797-494e-af48-e70c97eb6779
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b42ecd7ad38144786ff12d5cad20c9e8a1437646
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63417569"
---
# <a name="choose-operation-dialog-box-legacy"></a>작업 선택 대화 상자(레거시)
에 대해 설명 하는 방법을 사용 하 여는 **작업 선택** 레거시 대화 상자 [!INCLUDE[wfd1](../includes/wfd1-md.md)]합니다. 레거시 [!INCLUDE[wfd2](../includes/wfd2-md.md)]는 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] 또는 [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]를 대상으로 해야 하는 경우에 사용합니다.  
  
 합니다 **작업 선택** 대화 상자와 연결할 작업을 선택 하는 데 사용 됩니다는 <xref:System.Workflow.Activities.ReceiveActivity> 활동 또는 <xref:System.Workflow.Activities.SendActivity> 활동입니다. 이 대화 상자를 사용 하 여 해당 작업을 하는 방법에 대 한 자세한 내용은 참조 하세요. [방법: WCF 계약 작업 구현 (레거시)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md) 고 [방법: WCF 계약 작업 호출 (레거시)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)합니다.  
  
 다음 표에 사용자 인터페이스 (UI) 요소에는 **작업 선택** 대화 상자.  
  
|UI 요소|설명|  
|----------------|-----------------|  
|**계약 추가**|자동으로 새 계약을 만듭니다. 이 계약에 새 작업을 정의할 수 있습니다. 이 UI 요소는 <xref:System.Workflow.Activities.ReceiveActivity>에만 사용됩니다.|  
|**작업 추가**|새 작업에서 만든 새 계약을 추가 합니다 **작업 선택** 대화 상자. **참고:**  통해 만든 계약에만 새 작업을 추가할 수 있습니다 합니다 **작업 선택** 대화 상자. <br /><br /> 이 UI 요소는 <xref:System.Workflow.Activities.ReceiveActivity>에만 사용됩니다.|  
|**가져오기...**|이전에 정의된 계약을 가져오며 해당 계약에서 작업을 선택할 수 있습니다.|  
|**작업 이름**|현재 선택한 작업의 이름입니다. 이 텍스트 상자를 통해 작업을 만든 경우에 편집할 수는 **작업 선택** 대화 상자.|  
|**매개 변수**|현재 선택한 작업에 대한 매개 변수 정의가 포함된 탭입니다. **참고:**  매개 변수 정의 통해 작업을 만든 경우에 변경할 수 있습니다 합니다 **작업 선택** 대화 상자.|  
|**속성**|클라이언트와 서비스 간에 보낸 메시지의 <xref:System.Net.Security.ProtectionLevel> 설정이 포함된 탭입니다. **참고:**  이 탭을 통해 작업을 만든 경우에 사용 합니다 **작업 선택** 대화 상자.|  
|**권한**|해당 작업을 호출할 수 있는 사용자의 <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionName%2A> 및 <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionRole%2A> 속성이 포함된 탭입니다. 예를 들어, 관리자 그룹에서 사용자가 해당 작업을 호출할 허용 된 경우 다음 쓰듯이 "Administrators"는 **역할** 입력란입니다.<br /><br /> 이 탭을 통해 만든 두 작업에 사용 된 **ChooseOperation** 대화 상자 및 작업을 통해 가져온 합니다 **가져오기** 단추입니다.|  
  
> [!NOTE]
> 합니다 **작업 선택** 계약이 나 작업만 다른 사용 되는 대화 상자 표시 <xref:System.Workflow.Activities.SendActivity> 워크플로에서 활동입니다. 마찬가지로, 합니다 **작업 선택** 대화 상자 <xref:System.Workflow.Activities.ReceiveActivity> 계약이 나 작업만 다른 사용 되는 활동을 보여 줍니다 **ReceiveActivity** 워크플로에서 활동입니다.  
  
## <a name="see-also"></a>참고 항목  
 [방법: WCF 계약 작업 구현 (레거시)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)   
 [방법: WCF 계약 작업 호출 (레거시)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)   
 [Windows Workflow Foundation용 레거시 디자이너 UI 도움말](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)