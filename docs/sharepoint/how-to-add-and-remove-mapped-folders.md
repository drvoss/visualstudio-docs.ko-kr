---
title: '방법: 매핑된 폴더 추가 및 제거 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.MappedFolder
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, mapped folders
- mapped folders [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d5d1acc40b23c979a5746c50be50a584d11112b5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62966915"
---
# <a name="how-to-add-and-remove-mapped-folders"></a>방법: 매핑된 폴더 추가 및 제거
  일부 이미지 및 레이아웃 파일 계층 구조에 중첩 되어 같은 폴더 SharePoint에서 일반적으로 사용 합니다. 보다 쉽게 액세스 하려면 SharePoint 프로젝트에 이러한 폴더를 매핑할 수 있습니다. 매핑된 폴더는 SharePoint 프로젝트에 SharePoint 서버의 설치 파일의 실제 위치에 해당 하는입니다.

 SharePoint 응용 프로그램을 배포할 때는 매핑된 폴더 및 해당 하위 폴더에서 복사 하는 솔루션 패키지 (.wsp) 서버에 모든 내용을 SharePoint를 실행 하는 SharePoint 폴더 트리에서 지정된 된 위치에. 이 위치에 의해 결정 되는 **배포 위치** 매핑된 폴더에 대해 설정 된 속성입니다. 매핑된 폴더의 하위 폴더에 상대적인 됩니다 **배포 위치** 매핑된 폴더입니다. 유의 합니다 **배포 위치** 속성에 매핑된 폴더의 이름이 아니라 항목은 배포 하는 위치를 결정 합니다.
프로젝트에 대 한 바로 가기 메뉴 또는 메뉴 모음에서 명령을 사용 하 여 프로젝트에 매핑된 폴더를 추가할 수 있습니다. 사용할 수는 **추가 SharePoint "이미지" 매핑된 폴더** 하 고 **추가 SharePoint "레이아웃" 폴더** 추가 명령이 매핑된 가장 자주 사용 되는 폴더. 매핑할 수 있습니다 다른 사용 가능한 SharePoint 폴더의 모든 프로젝트에 사용 하 여 합니다 **SharePoint 매핑된 폴더 추가** 바로 가기 메뉴 명령을 클릭 한 다음에 있는 폴더를 지정 하는 **SharePoint 매핑된 폴더 추가** 대화 상자.

## <a name="add-mapped-folders-to-a-project"></a>프로젝트에 매핑된 폴더 추가
 다음 절차에 시각적 웹 파트 프로젝트에 매핑된 두 개의 폴더를 추가 하는 방법을 설명 합니다. 시작 하려면 비주얼 웹 파트 프로젝트를 만들어야 합니다.

#### <a name="to-add-mapped-folders-to-a-project"></a>프로젝트에 매핑된 폴더를 추가 하려면

1. 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 선택합니다.

2. 에 **새 프로젝트** 대화 상자에서 하나를 **Visual Basic** 또는 **Visual C#**  노드를 확장 합니다 **Office/SharePoint** 노드를 선택한 후는 **SharePoint 솔루션** 노드.

3. 프로젝트 템플릿 목록에서 선택 합니다 **SharePoint 2013 비주얼 웹 파트** 템플릿.

4. 에 **이름** 상자에 입력 합니다 **TestProject1**를 선택한 후는 **확인** 단추입니다.

5. 에 **SharePoint 사용자 지정 마법사**, 선택는 **마침** 기본 설정을 유지 하는 단추입니다.

6. **솔루션 탐색기**, 프로젝트 노드를 선택한 다음, 메뉴 모음에서 **프로젝트** > **추가 SharePoint "이미지" 매핑된 폴더**합니다.

     명명 된 폴더 **이미지** 프로젝트에 표시 되 고 TestProject1 라는 하위 폴더를 포함 합니다. 이 매핑된 폴더에는 시각적 웹 파트 프로젝트에 대 한 이미지가 포함 됩니다.

7. **솔루션 탐색기**, 프로젝트 노드를 선택한 다음, 메뉴 모음에서 **프로젝트** > **SharePoint 매핑된 폴더 추가** 합니다 표시하려면 **SharePoint 매핑된 폴더 추가** 대화 상자.

8. 매핑을 사용할 수 있는 폴더의 트리 뷰에서 선택 합니다 **리소스** 폴더를 선택한 후는 **확인** 단추입니다.

     명명 된 폴더 **리소스** 프로젝트에 나타납니다. 이 폴더는 문자열 리소스 파일과 같은 항목을 저장할 수 있습니다. 하위 폴더는 매핑된 폴더의 내용을 구성 하는 데 유용할 수 있지만 사용 하 여 매핑된 폴더를 추가 하면 자동으로 만들어지는 합니다 **SharePoint 매핑된 폴더 추가** 명령입니다. 하위 폴더를 추가 하려면 선택 합니다 **리소스** 폴더를 선택한 다음 메뉴 모음에서 **프로젝트** > **새 폴더**합니다.

## <a name="change-the-deployment-location-of-a-mapped-folder"></a>매핑된 폴더의 배포 위치를 변경 합니다.
 기본적으로 매핑된 폴더는 SharePoint 루트 설치 경로 기준으로 특정 위치에 추가 하는 토큰 \<SharePointRoot > 나타냅니다. 그러나 변경 하 여이 위치를 변경할 수는 **배포 위치** 매핑된 폴더의 속성입니다. 각 매핑된 폴더에는 자체 **배포 위치** 속성입니다.

#### <a name="to-change-the-deployment-location-of-a-mapped-folder"></a>매핑된 폴더의 배포 위치를 변경 하려면

1. 앞에서 만든 프로젝트에 매핑된 폴더를 선택 합니다.

2. 에 **속성** 창에서 줄임표를 선택 (![ASP.NET 모바일 디자이너 줄임표](../sharepoint/media/mwellipsis.gif "ASP.NET 모바일 디자이너 줄임표")) 단추를 **배포 위치** 속성입니다.

3. 에 **SharePoint 매핑된 폴더 추가** 대화 상자에서 원하는 가리키도록 매핑된 폴더는 폴더를 찾습니다.

4. 노드를 선택한 다음 선택 합니다 **확인** 단추입니다.

## <a name="rename-or-remove-mapped-folders"></a>이름을 바꾸거나 매핑된 폴더를 제거 합니다.

#### <a name="to-rename-or-remove-a-mapped-folder"></a>매핑된 폴더를 제거 하거나 이름을 변경 하려면

1. 앞에서 만든 프로젝트에 매핑된 폴더를 선택 합니다.

2. 매핑된 폴더의 이름을 바꾸려면 해당 바로 가기 메뉴를 열고, 선택 **이름 바꾸기**, 새 이름을 입력 하 고 Enter 키를 선택 합니다.

     안으로, 이름 바꾸기을 열고 원하는 매핑된 폴더를 선택할 수 있습니다는 **속성** 창에서 값을 설정한 후를 **폴더 이름** 속성을 새 이름입니다.

3. 매핑된 폴더를 프로젝트에서 제거 하려면 해당 바로 가기 메뉴를 열고, 선택 **삭제**를 선택한 후는 **확인** 제거를 확인 하는 대화 상자의 단추.

## <a name="see-also"></a>참고자료
- [SharePoint 솔루션 개발](../sharepoint/developing-sharepoint-solutions.md)
