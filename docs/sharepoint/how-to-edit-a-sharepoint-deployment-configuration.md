---
title: '방법: SharePoint 배포 구성 편집 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.DeploymentConfig
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ffa7923bbe7e8a7b44fec280a5528ab023feed37
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63444705"
---
# <a name="how-to-edit-a-sharepoint-deployment-configuration"></a>방법: SharePoint 배포 구성 편집
  배포 구성을 만들거나 기존 배포 구성을 수정할 수 있습니다. 예를 들어, 하나의 단계를 실행 또는 배포 프로세스의 단계 순서를 변경할 수 있습니다. 만들기 또는 기본 제공 및 프로그래밍 방식으로 추가 구성을 변경할 수 없으므로 배포 구성을 수정 수 있습니다.

## <a name="create-a-sharepoint-deployment-configuration"></a>SharePoint 배포 구성 만들기

#### <a name="to-create-a-sharepoint-deployment-configuration"></a>SharePoint 배포 구성을 만들려면

1. **솔루션 탐색기**, SharePoint 프로젝트를 선택한 다음, 메뉴 모음에서 **프로젝트**하십시오 _ProjectName_**속성**합니다.

2. 에 **SharePoint** 탭을 선택 합니다 **새로 만들기** 단추입니다.

     합니다 **새 배포 구성 추가** 대화 상자가 나타납니다.

3. 에 **이름을** 텍스트 상자에 배포 구성의 이름을 입력 합니다.

4. 에 **사용 가능한 배포 단계** 창 배포 구성에 추가 선택 하는 단계를 선택 합니다 (**>**) 단추를 선택한 후는 **확인** 단추입니다.

    > [!NOTE]
    > 배포 전 명령 또는 배포 후 명령이 구성한 경우 이러한 단계는 사용자 지정 된 배포 구성에 추가한 경우에 실행 됩니다.

## <a name="change-the-active-deployment-configuration"></a>활성 배포 구성 변경

#### <a name="to-change-the-active-deployment-configuration"></a>활성 배포 구성을 변경 하려면

1. **솔루션 탐색기**, SharePoint 프로젝트를 선택한 다음, 메뉴 모음에서 **프로젝트** > **\<*ProjectName*> 속성**합니다.

2. 선택 된 **SharePoint** 탭 합니다.

3. 에 **활성 배포 구성** 목록 상자에서 사용 하려는 배포 구성의 이름을 선택 합니다.

## <a name="see-also"></a>참고자료
- [패키지 및 SharePoint 솔루션 배포](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
