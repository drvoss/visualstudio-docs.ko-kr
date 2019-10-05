---
title: Visual Studio에서 SharePoint 도구 확장 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio, extending tools
- extensibility [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, extending tools
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7d70d9b5bac260dc0731d06ebb11780114f0edf5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62967424"
---
# <a name="extend-the-sharepoint-tools-in-visual-studio"></a>Visual Studio에서 SharePoint 도구 확장
  Visual Studio에서 SharePoint 도구에는 많은 응용 프로그램 개발 시나리오의 요구 사항을 충족 합니다. 그러나 사용자 또는 다른 개발자가 필요로 하는 기능 제공 하지 않는 경우를 발견할 수 있습니다. 이러한 경우에는 필요한 기능을 만들 수 있는 SharePoint 도구를 확장할 수 있습니다.

## <a name="how-to-extend-the-sharepoint-tools"></a>SharePoint 도구 확장 하는 방법
 SharePoint 프로젝트 시스템을 확장할 수 있습니다 및 **SharePoint 연결** 에서 노드를 **서버 탐색기** 창입니다.

### <a name="extend-the-sharepoint-project-system"></a>SharePoint 프로젝트 시스템 확장
 Visual Studio 프로젝트 템플릿 및 SharePoint 솔루션을 만드는 데 사용할 수 있는 항목 템플릿 집합이 포함 됩니다. 예를 들어, 이벤트 수신기, 목록 정의 워크플로 및 웹 파트에 대 한 템플릿이 있습니다. 그러나 필드 또는 사용자 지정 작업과 같은 SharePoint 구성 요소를 만들기 위한 SharePoint 프로젝트 항목의 고유한 형식을 정의할 수 있습니다. Visual Studio에서 이미 설치 되어 있는 SharePoint 프로젝트 항목 형식에 대 한 확장을 만들 수도 있습니다 및 SharePoint 프로젝트 확장을 만들 수 있습니다.

 자세한 내용은 [SharePoint 프로젝트 시스템 확장](../sharepoint/extending-the-sharepoint-project-system.md)합니다.

### <a name="extend-the-sharepoint-connections-node-in-server-explorer"></a>서버 탐색기에서 SharePoint 연결 노드 확장
 Visual Studio에서 사용할 수 있습니다는 **SharePoint 연결** 에서 노드를 **서버 탐색기** 계층적 트리 뷰에서 여러 구성 요소 중 하나 이상의 로컬 SharePoint 사이트에는 창입니다. 확장할 수도 있습니다는 **SharePoint 연결** 다음과 같은 방법으로 노드:

- 고유한 노드를 추가 합니다. 기본적으로 표시 되지 않는 SharePoint 사이트의 구성 요소를 표시 하려는 경우에 유용 합니다.

- 기존 노드를 확장 합니다. 예를 들어, 기존 노드는 새 자식 노드를 추가할 수 있습니다 또는 노드에 바로 가기 메뉴 항목을 추가 하 고 개발자가 메뉴 항목을 클릭할 때 작업을 수행할 수 있습니다.

  자세한 내용은 [서버 탐색기에서 SharePoint 연결 노드 확장](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)합니다.

## <a name="development-computer-requirements"></a>개발 컴퓨터 요구 사항
 SharePoint 도구의 확장을 만들려면 개발 컴퓨터에는 Visual Studio에서 SharePoint 솔루션 만들기에 대 한 동일한 요구 사항을 충족 해야 합니다.

 설치 하는 것이 좋습니다는 [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]합니다. SDK는 프로젝트 템플릿 및 Visual Studio를 확장 하는 데 사용할 수 있는 도구를 포함 합니다. 특히, SDK는 프로젝트 템플릿으로 쉽게 Visual Studio 확장 (VSIX) 패키지를 만드는 데 사용할 수를 포함 합니다. VSIX 패키지는 Visual Studio에서 Visual Studio 확장을 배포 하는 기본 방법입니다. 모든 SharePoint 도구 확장은 VSIX 패키지를 사용 하 여 배포 되어야 합니다. 모든이 문서의 연습에서는 있다고 가정 합니다 [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)] 설치 합니다.

 Visual Studio SDK를 설치 하려면 [Visual Studio SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)합니다. Visual Studio 확장에 대 한 자세한 내용은 참조 하세요. [Visual Studio 확장 개발 시작](../extensibility/starting-to-develop-visual-studio-extensions.md)합니다.

## <a name="see-also"></a>참고자료

- [SharePoint의 프로그래밍 모델 개요 도구 확장](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
- [SharePoint 프로젝트 시스템 확장](../sharepoint/extending-the-sharepoint-project-system.md)
- [서버 탐색기에서 SharePoint 연결 노드 확장](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [SharePoint 도구 확장의 프로그래밍 개념 및 기능](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)
- [참조 &#40;SharePoint 도구 확장성&#41;](../sharepoint/reference-sharepoint-tools-extensibility.md)
- [Visual Studio에서 SharePoint 도구에 대 한 확장명 디버깅](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)
- [Visual Studio에서 SharePoint 도구에 대 한 확장 배포](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)