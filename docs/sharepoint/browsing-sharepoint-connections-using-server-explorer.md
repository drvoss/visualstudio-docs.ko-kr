---
title: 서버 탐색기를 사용 하 여 SharePoint 연결 찾아보기 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.SharePointExplorer.SharePointConnection
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, browsing SharePoint sites
- SharePoint development in Visual Studio, SharePoint Connections
- SharePoint Connections [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8dfde37125b78e2ff8077712321b3a19816582cf
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63387800"
---
# <a name="browse-sharepoint-connections-by-using-server-explorer"></a>서버 탐색기를 사용 하 여 SharePoint 연결 찾아보기
  로컬 SharePoint 연결에서 검색할 수 있습니다 **서버 탐색기**합니다. 이 방법을 사용하면 시스템에서 SharePoint 사이트의 구성 요소를 탐색할 수 있습니다. 목록 정 및 콘텐츠 형식과 같은 SharePoint 사이트 구성 요소 라는 노드에 나타납니다 **SharePoint 연결** 의 트리 뷰에서 **서버 탐색기**합니다. 표시할 **서버 탐색기**, 메뉴 모음에서 **뷰** > **서버 탐색기**합니다. SharePoint 사이트 구성 요소를 표시하는 것 외에도 바로 가기 메뉴의 명령을 사용하여 항목을 제거하거나, 속성을 보거나, 트리 뷰를 새로 고칠 수 있습니다.

> [!IMPORTANT]
> SharePoint 사이트를 탐색하려면 SharePoint 사이트 컬렉션의 관리자여야 하고 로컬 컴퓨터의 관리자로서 Visual Studio를 실행해야 합니다. 사이트에 표시 되는 고, 그렇지 **서버 탐색기**, 하지만 해당 노드를 확장할 수 없습니다. 사이트 컬렉션의 관리자가 같은지를 확인 하려면 웹 브라우저를 열고에서 사이트를 엽니다는 **사이트 작업** 메뉴 선택 **사이트 사용 권한**를 선택한 후는 **권한: 팀 사이트** 페이지를 선택 합니다 **Site Collection Administrators** 명령을 합니다 **관리** 리본의 그룹. 사이트 컬렉션 관리자는 사용자 이름 텍스트 상자에 표시 됩니다. 경우는 **Site Collection Administrators** 명령이 리본 메뉴의 관리 그룹에 표시 되지 않으면, 사이트 모음에 대해 관리자가 아니라면 및 사이트 관리자에서 적절 한 권한을 받아야 합니다.

## <a name="server-explorer-nodes"></a>서버 탐색기 노드
 SharePoint 사이트의 모든 구성 요소에서 노드로 표시 되는 **서버 탐색기** 트리 보기 아래에서 **SharePoint 연결**합니다. 기본 SharePoint 사이트에 표시 하는 토론 유형을 나타냅니다는 토론 라는 콘텐츠 형식을 포함 하는 예를 들어 합니다 **토론** SharePoint 사이트의 페이지입니다. 토론 콘텐츠 형식에는 여러 필드가 포함 됩니다. 이러한 필드를 보려면 **서버 탐색기**를 확장 합니다 **ContentTypes** 노드를 차례로 **토론** 노드. 아래에 있는 제목, 본문 및 토론 주제 등의 여러 필드 노드가 됩니다.

## <a name="node-shortcut-menu-commands"></a>노드 바로 가기 메뉴 명령
 각 노드에 노드를 마우스 오른쪽 단추로 클릭 하거나 노드를 선택한 다음 선택 하 여 액세스할 수 있는 바로 가기 메뉴를 **Shift**+**F10** 키입니다. 노드 명령에는 다음과 같습니다.

|명령 이름|설명|
|------------------|-----------------|
|새로 고침|트리 뷰 노드를 표시 된 마지막 시간 이후 발생 했을 수 있는 모든 변경 내용을 반영 하도록 업데이트 합니다.|
|삭제|트리 보기에서 선택한 노드를 제거합니다. **참고:**  SharePoint 연결 아래에이 명령을 사용할 수는 **SharePoint 연결** 노드.|
|속성|선택한 노드에 대 한 사용 가능한 속성을 표시 합니다 **속성** 창입니다. 속성은 모두 읽기 전용 및 일부 노드는 연관 된 속성입니다.|
|연결 추가|이동 하려는 SharePoint 사이트를 지정할 수 있습니다. 사용할 수는 **SharePoint 연결** 노드 및 하위 사이트 노드.|
|브라우저에서 보기|웹 브라우저에서 선택된 된 항목을 표시합니다. 이 명령은 아래에 몇 가지 목록에서 사용 될 합니다 **나열** 에 포함 된 노드 **목록 및 라이브러리**합니다.|

## <a name="related-topics"></a>관련 항목

|제목|설명|
|-----------|-----------------|
|[방법: SharePoint 연결 추가 또는 제거](../sharepoint/how-to-add-or-remove-sharepoint-connections.md)|새 SharePoint 사이트에 추가 하는 데 필요한 단계를 설명 합니다 **SharePoint 연결** 노드에서 **서버 탐색기**합니다.|

## <a name="see-also"></a>참고자료
- [SharePoint 솔루션 개발](../sharepoint/developing-sharepoint-solutions.md)
