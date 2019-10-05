---
title: '방법: 프로젝트 출력 참조 추가 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project output references [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, project output references
- SharePoint development in Visual Studio, advanced packaging tools
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2ae3965647416d7a8e11cf0ea5e24cef1e54a09b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62967255"
---
# <a name="how-to-add-a-project-output-reference"></a>방법: 프로젝트 출력 참조 추가
  SharePoint에 비 SharePoint 프로젝트 어셈블리 (또는 Silverlight 프로젝트에서.xap 파일)를 배포 하려면 프로젝트 출력 참조로 추가 합니다.

 이 프로세스는 두 프로젝트 간에 솔루션 빌드 종속성을 만듭니다. SharePoint 프로젝트를 빌드 및 배포 하기 전에 프로젝트 출력 참조를 사용 하 여 연결 하는 프로젝트는 빌드됩니다.

### <a name="to-add-a-project-output-reference"></a>프로젝트 출력 참조를 추가 하려면

1. 하나 이상의 SharePoint 프로젝트 및 비 SharePoint 프로젝트를 포함 하는 솔루션을 로드 합니다.

2. **솔루션 탐색기**, SharePoint 프로젝트 노드의 항목을 선택 합니다.

3. 에 **속성** 창 선택 합니다 **프로젝트 출력 참조** 속성을를 선택한 다음 줄임표 (![ASP.NET 모바일 디자이너 줄임표](../sharepoint/media/mwellipsis.gif "ASP. NET 모바일 디자이너 줄임표")) 단추를 클릭 합니다.

4. 에 **프로젝트 출력 참조** 대화 상자를 선택 합니다 **추가** 단추입니다.

5. 속성 창에서 화살표 옆에 선택 합니다 **배포 유형을** 속성인 참조와 같은 비 SharePoint 항목에 대 한 적절 한 값을 선택 하 고 **ElementFile**.

6. 옆의 화살표를 선택 **프로젝트 이름**비 SharePoint 프로젝트 항목의 이름을 선택한 다음 선택 합니다 **확인** 단추입니다.

## <a name="see-also"></a>참고자료
- [프로젝트 항목에 패키징 및 배포 정보를 제공 합니다.](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
- [방법: 안전한 컨트롤로 표시 컨트롤](../sharepoint/how-to-mark-controls-as-safe-controls.md)
- [패키지 및 SharePoint 솔루션 배포](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
