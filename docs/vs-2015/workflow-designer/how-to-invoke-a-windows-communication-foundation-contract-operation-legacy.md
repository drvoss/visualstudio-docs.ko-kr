---
title: '방법: Windows Communication Foundation 계약 작업 (레거시)를 호출 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: a9058345-708f-4fcf-8739-2a43e5285b7a
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1398d7fb62943c04ca026175a3f46b282bf6da69
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65696326"
---
# <a name="how-to-invoke-a-windows-communication-foundation-contract-operation-legacy"></a>방법: Windows Communication Foundation 계약 작업 호출(레거시)
이 항목에서는 [!INCLUDE[indigo1](../includes/indigo1-md.md)] 또는 [!INCLUDE[wfd1](../includes/wfd1-md.md)]를 대상으로 하는 레거시 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)]를 사용하여 [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] 계약 작업을 호출하는 방법에 대해 설명합니다.  
  
 위로 끌어 놓은 후에 **SendActivity** 활동 워크플로 디자인 화면에 도구 상자에서 기존 계약을 가져올 고는 호출할 작업을 결정 해야 **SendActivity** 작업입니다. 계약을 통해 해당 작업을 선택 합니다 [작업 선택 대화 상자 (레거시)](../workflow-designer/choose-operation-dialog-box-legacy.md)합니다.  
  
 또한 서비스에서 구성 파일을 사용하고 있는 경우에는 <xref:System.Workflow.Activities.ChannelToken>을 지정해야 합니다. <xref:System.Workflow.Activities.ChannelToken>은 보내기 활동에서 워크플로 서비스에 연결하는 데 사용할 엔드포인트 구성을 식별합니다.  
  
### <a name="to-invoke-a-wcf-contract-operation-from-a-sendactivity-activity"></a>SendActivity 활동에서 WCF 계약 작업을 호출하려면  
  
1. 두 번 클릭 합니다 **SendActivity** 디자이너의 활동에에서 다음 줄임표를 클릭 하거나는 **ServiceOperationInfo** 속성에는 **속성** 창.  
  
2. 경우는 **작업 선택** 열립니다 대화 상자를 클릭 **가져오기** 대화 상자의 오른쪽 위 모퉁이에서.  
  
     합니다 [찾아.NET 유형 선택 대화 상자 (레거시)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md) 열립니다.  
  
3. 원하는 계약이 들어 있는 어셈블리나 프로젝트를 검색합니다.  
  
4. 계약을 선택 하 고 클릭 **확인**합니다.  
  
5. 아래 **사용 가능한 작업**를 호출 하 고 클릭 하려는 작업 선택 **확인**합니다.  
  
### <a name="to-specify-a-channel-token"></a>채널 토큰을 지정하려면  
  
1. 디자이너에서 <xref:System.Workflow.Activities.SendActivity> 활동을 선택합니다.  
  
2. 에 **속성** 창에 대 한 이름을 지정 합니다 <xref:System.Workflow.Activities.ChannelToken>합니다. 이 이름은 채널 토큰을 고유하게 식별합니다.  
  
3. 채널 토큰 노드를 확장하고 사용할 클라이언트 엔드포인트의 이름을 <xref:System.Workflow.Activities.ChannelToken.EndpointName%2A> 필드에서 지정합니다. 구성 파일에서 동일한 이름을 사용하는 엔드포인트 구성이 채널을 구성하는 데 사용됩니다.  
  
4. 구성 파일에 엔드포인트 구성이 아직 없으면 만듭니다. 클라이언트를 구성 하는 방법에 대 한 자세한 내용은 참조 하세요. [WCF Client Overview](https://msdn.microsoft.com/library/f60d9bc5-8ade-4471-8ecf-5a07a936c82d)합니다.  
  
## <a name="see-also"></a>참고 항목  
 [작업 선택 대화 상자 (레거시)](../workflow-designer/choose-operation-dialog-box-legacy.md)   
 [방법: WCF 계약 작업 구현 (레거시)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)   
 [레거시 워크플로 활동](../workflow-designer/legacy-workflow-activities.md)