---
title: '방법: 모듈을 사용 하 여 파일 포함 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, modules
- modules [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5813a6f89062bf53f7f8c0b57b4ed3a8ef9c4edf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62813646"
---
# <a name="how-to-include-files-by-using-a-module"></a>방법: 모듈을 사용 하 여 파일 포함
  *모듈* (사용 하 여 혼동 하면 안 [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] 모듈)은 SharePoint에 ASPX 마스터 페이지와 같은 파일, 텍스트 파일 또는 이미지를 배포할 수 있도록 하는 컨테이너입니다.

 외부 문서 라이브러리 또는 일반 파일 (예: default.aspx) 문서 라이브러리에 파일을 배포 하려면 선택할 수 있습니다. 문서 라이브러리에 파일을 추가 하려면 지정 `Type="GhostableInLibrary"` 특성으로는 **파일** 요소입니다. 이 설정은 SharePoint 라이브러리에 추가 될 때 파일을 사용 하 여 이동할 목록 항목을 만들려면 지시 합니다. 문서 라이브러리 외부 파일을 배포 하려면를 지정 하거나 `Type="Ghostable"` 생략 합니다 **형식** 특성입니다.

## <a name="add-a-module-to-a-sharepoint-solution"></a>SharePoint 솔루션에 모듈 추가

#### <a name="to-add-a-module"></a>모듈을 추가 하려면

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]에서 SharePoint 프로젝트를 열거나 만듭니다.

     자세한 내용은 [SharePoint 프로젝트 및 프로젝트 항목 템플릿](../sharepoint/sharepoint-project-and-project-item-templates.md)합니다.

2. **솔루션 탐색기**, 프로젝트 노드를 선택한 다음, 메뉴 모음에서 **프로젝트** > **새 항목 추가**합니다.

     **새 항목 추가** 대화 상자가 열립니다.

3. SharePoint 템플릿 목록에서 선택 합니다 **모듈** 템플릿을 선택한 후 합니다 **추가** 단추입니다.

     이 단계에서는 프로젝트에서 Module1이라는 노드를 만듭니다.

4. Module1을 아래에서 삭제 합니다 *Sample.txt* 파일입니다.

     Sample.txt 예를 들어 목적으로 모든 새 모듈에 포함 되어 있으며 필요 하지 않습니다. (참고는 파일을 삭제 하면 해당 항목에서에서 제거 모듈의 *Elements.xml* 파일입니다.)

5. 파일을 SharePoint의 특정 폴더 구조에 배포를 원한다 면에서 Module1 아래 해당 폴더를 만듭니다 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Module1 노드를 선택 하 여 선택한 다음 메뉴 모음에서 **프로젝트**, **새로 만들기 폴더**합니다.

6. 파일을 추가 하 고 그런 다음 메뉴 모음에서 선택 하려는 폴더를 선택 **프로젝트**하십시오 **기존 항목 추가**합니다.

7. SharePoint에 배포 하 고 선택 하려는 하나 이상의 파일을 선택 합니다 **추가** 단추입니다.

     파일을 프로젝트에 추가 하면 항목에 대 한 모듈의 Elements.xml 파일에 자동으로 추가 됩니다. SharePoint 서버에 의해 지정 되는 프로젝트의 루트 디렉터리를 기준으로 파일 복사는 프로젝트를 배포할 때 합니다 **파일** 요소의 **Url** 와 같은 특성 `Url="Module1/New Folder/SomeFile.doc`합니다. 파일에 대 한 배포 위치를 변경 하려는 경우 하거나 이동할 다른 폴더로 **솔루션 탐색기** 변경 하거나 해당 **Url** 설정 합니다.

8. 문서 라이브러리에 표시 하려는 모든 파일을 추가 합니다 `Type="GhostableInLibrary"` 특성에서 해당 항목을 *Elements.xml*합니다. 예를 들면 다음과 같습니다.

    ```xml
    <File Path="Module1\Some Folder\SomePage.aspx" Url="Module1/Some Folder/SomePage.aspx" Type="GhostableInLibrary" />
    ```

9. 프로젝트를 배포 합니다.

     파일을 SharePoint의 지정된 된 위치에 복사합니다.

## <a name="see-also"></a>참고자료
- [패키지 및 SharePoint 솔루션 배포](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
- [SharePoint 솔루션 개발](../sharepoint/developing-sharepoint-solutions.md)
