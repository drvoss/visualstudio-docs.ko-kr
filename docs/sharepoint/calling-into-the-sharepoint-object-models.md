---
title: SharePoint 개체 모델 호출 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, client object model
- SharePoint development in Visual Studio, server object model
- SharePoint commands [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, extensibility features
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 24634143a40f7b163c0b658bddb5596041868033
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62988403"
---
# <a name="call-into-the-sharepoint-object-models"></a>SharePoint 개체 모델 호출
  Visual Studio에서 SharePoint 도구의 확장을 만들 때 특정 작업을 수행 하려면 SharePoint Api를 호출 해야 합니다. 예를 들어 SharePoint 프로젝트용 사용자 지정 배포 단계를 만드는 경우에 솔루션을 배포 하는 작업의 일부를 수행 하려면 SharePoint Api를 호출 해야 합니다.

 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] 및 [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] SharePoint 도구 확장에서 사용할 수 있는 두 가지 개체 모델을 제공 합니다: 서버 개체 모델과 클라이언트 개체 모델입니다. 각 개체 모델에 SharePoint 도구 확장의 컨텍스트에서 장단점에 있습니다.

 SharePoint 개체 모델의 개요를 보려면 [SharePoint의 프로그래밍 모델 개요 도구 확장](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)합니다.

## <a name="use-the-client-object-model-in-extension-projects"></a>확장 프로젝트에서 클라이언트 개체 모델을 사용 합니다.
 SharePoint 도구의 확장을 개발 하는 경우 다른 관리 되는 Api 집합이 같은 프로젝트에서 클라이언트 개체 모델을 사용할 수 있습니다. 어셈블리에 대 한 참조를 클라이언트 개체 모델에서 프로젝트에 추가할 수 있습니다 하 고 코드에서 직접 클라이언트 개체 모델에서 Api를 호출할 수 있습니다.

 그러나 클라이언트 개체 모델에 SharePoint 도구 확장의 컨텍스트에서 두 가지 단점이 있습니다.

- 클라이언트 개체 모델에는 서버 개체 모델의 하위 집합만을 제공합니다. 클라이언트 개체 모델에서 노출 되지 않는 SharePoint 기능을 사용 해야 할 경우 서버 개체 모델을 사용 해야 합니다.

- 대부분의 경우에서 클라이언트 개체 모델을 사용 하 여 SharePoint 도구 확장에서 작동 해야 하지만 클라이언트 개체 모델에 대 한 호출이 예상 대로 작동 하지 않는 경우가 발생할 수 있습니다. 클라이언트 개체 모델은 원격 서버 또는 팜에 SharePoint 사이트를 호출할 클라이언트 응용 프로그램에서 사용할 하도록 설계 되었습니다. Visual Studio에서 SharePoint 도구 개발 컴퓨터의 로컬 SharePoint 설치 에서만 작동합니다. 따라서 클라이언트 개체 모델을 사용 하 여 SharePoint 도구 확장에서 문의할 SharePoint 사이트에 클라이언트 개체 모델을 사용할 설계 된 방식에 있지는 로컬 컴퓨터입니다.

  Visual Studio에서 SharePoint 도구 확장에서 클라이언트 개체 모델을 사용 하는 방법을 보여주는 연습을 참조 하세요. [연습: 서버 탐색기 확장의 SharePoint 클라이언트 개체 모델을 호출할](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)합니다.

## <a name="use-the-server-object-model-in-extension-projects"></a>확장 프로젝트에서 서버 개체 모델을 사용 합니다.
 서버 개체 모델에는 클라이언트 개체 모델의 상위 집합입니다. 서버 개체 모델을 사용 하는 경우에 모든 기능을 사용할 수 있는 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] 및 [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] 프로그래밍 방식으로 노출 합니다.

 SharePoint 도구 확장 Api를 사용 하 여 서버 개체 모델에서 수 있지만 Api를 직접 호출할 수 없습니다. 서버 개체 모델은.NET Framework 3.5를 대상으로 하는 64 비트 프로세스 에서만에서 호출 수 있습니다. 그러나 SharePoint 도구 확장 필요를 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 32 비트 Visual Studio 프로세스에서 실행 합니다. 이렇게 하면 SharePoint 서버 개체 모델에서 어셈블리를 직접 참조에서 SharePoint 도구 확장 됩니다.

 사용자 지정 SharePoint 도구 확장에서 서버 개체 모델을 사용 하려는 경우 만들어야 *SharePoint 명령을* API를 호출 합니다. 서버 개체 모델을 직접 호출할 수 있는 보조 어셈블리는 SharePoint 명령을 정의 합니다. 확장 프로젝트에서 직접 호출할 있습니다 하지 하는 SharePoint 명령을 ExecuteCommand 메서드를 사용 하 여는 <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> 개체입니다.

 만들기 및 SharePoint 명령을 사용 하는 방법에 대 한 자세한 내용은 참조 하세요. [방법: SharePoint 명령 만들기](../sharepoint/how-to-create-a-sharepoint-command.md) 고 [방법: SharePoint 명령 실행](../sharepoint/how-to-execute-a-sharepoint-command.md)합니다. SharePoint 명령을 배포 하는 방법에 대 한 정보를 참조 하세요 [Visual Studio에서 SharePoint 도구의 확장을 배포할](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)합니다.

 SharePoint 명령 만들기 및 사용 하는 방법을 보여주는 연습을 참조 하세요. [연습: SharePoint 프로젝트용 사용자 지정 배포 단계를 만듭니다](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md) 고 [연습: 웹 파트를 표시 하려면 서버 탐색기 확장](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)합니다.

### <a name="understand-how-sharepoint-commands-are-executed"></a>SharePoint 명령이 실행 되는 방식을 이해 합니다.
 SharePoint 명령을 정의 하는 어셈블리 명명 된 64 비트 호스트 프로세스에서 로드 되 *vssphost4.exe*합니다. 명령을 실행 하 여 SharePoint 명령은 SharePoint 도구 확장에서를 호출한 후 *vssphost4.exe* 32 비트 Visual Studio 프로세스 대신 (*devenv.exe*). 레지스트리에서 값을 설정 하 여 SharePoint 명령 실행 방법의 몇 가지 측면을 제어할 수 있습니다. 자세한 내용은 [Visual Studio에서 SharePoint 도구의 확장을 디버그](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)합니다.

## <a name="see-also"></a>참고자료
- [방법: SharePoint 명령 만들기](../sharepoint/how-to-create-a-sharepoint-command.md)
- [방법: SharePoint 명령 실행](../sharepoint/how-to-execute-a-sharepoint-command.md)
- [SharePoint의 프로그래밍 모델 개요 도구 확장](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
