---
title: 비즈니스 데이터 연결 모델 만들기 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], model
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
- SharePoint development in Visual Studio, Business Data Connectivity service
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9f3da13858507a3ff176aaa0a44051674fd5285f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63443551"
---
# <a name="create-a-business-data-connectivity-model"></a>비즈니스 데이터 연결 모델 만들기
  비즈니스 데이터 연결 (BDC) 모델을 만들 수도 있고 Visual Studio를 사용 하 여 기존 BDC 모델을 사용자 지정할 수 있습니다. 각 SharePoint 프로젝트 모델 하나만 포함할 수 있습니다. 자세한 내용은 [SharePoint 비즈니스 데이터 통합](../sharepoint/integrating-business-data-into-sharepoint.md)합니다.

## <a name="create-a-new-model"></a>새 모델 만들기
 새 모델을 만들려면를 **비즈니스 데이터 연결 모델** 프로젝트 또는 추가 **비즈니스 데이터 연결 모델** 항목을 **빈 SharePoint 프로젝트**합니다.

> [!NOTE]
> 있어야 [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] 컴퓨터에 설치 합니다.

 Visual Studio 프로젝트에 폴더를 추가 합니다. 이 폴더에 대해 지정한 이름을 가진 합니다 **비즈니스 데이터 연결 모델** 항목에 **새 항목 추가** 대화 상자. 새 만들면 **비즈니스 데이터 연결 모델** Visual Studio 프로젝트 폴더의 이름을 **BdcModel1**합니다.

 Visual Studio 새 폴더로 다음 파일을 추가합니다.

|파일|설명|
|----------|-----------------|
|모델 정의 파일|엔터티, 메서드, 줄의 lob (기간 업무) 시스템 개체 및 모델을 설명 하는 다른 메타 데이터를 정의 하는 XML을 포함 합니다.<br /><br /> BDC 디자이너를 사용 하 여이 파일의 메타 데이터를 수정할 **BDC 탐색기**를 **BDC 메서드 세부 정보** 창 및 **속성** 창입니다.|
|엔터티 서비스 코드 파일|검색, 업데이트 및 기본 엔터티 인스턴스를 삭제 하는 메서드를 포함 합니다.|

 엔터티의 속성을 정의 하려면 엔터티 코드 파일을 편집 합니다. 자세한 내용은 [방법: 모델에 엔터티 추가](../sharepoint/how-to-add-an-entity-to-a-model.md)합니다.

 검색, 업데이트 및 엔터티의 인스턴스를 삭제, 엔터티 서비스 코드 파일에 코드를 추가 합니다. 자세한 내용은 [비즈니스 데이터 연결 모델 디자인](../sharepoint/designing-a-business-data-connectivity-model.md)합니다.

 Visual Studio 프로젝트를 컴파일할 때 어셈블리를 만듭니다. 프로젝트 어셈블리에 코드를 추가 하는 프로젝트에 다른 항목을 추가 하지 않으면 확인 (예:는 **순차 워크플로** 항목 또는 **웹 파트** 항목). 솔루션 패키지는 어셈블리를 전역 어셈블리 캐시에 복사 하지 않고 솔루션을 배포 하는 경우에 해당 항목에 대 한 코드 실행 되지 않습니다.  SharePoint BDC 데이터베이스로 어셈블리를 배포 하는 솔루션 패키지입니다.

> [!NOTE]
> Visual Studio 프로젝트를 디버깅할 때 로컬 컴퓨터에 두 위치 모두에 어셈블리를 복사 합니다.

## <a name="add-an-existing-model"></a>기존 모델 추가
 SharePoint Designer와 같은 다른 도구를 사용 하 여 만든 모델을 가져올 수 있습니다. 다음과 같은 상황에서 프로젝트에 기존 모델을 가져올 수 있습니다.

- SharePoint 서버 팜에 이미 배포 된 모델을 사용자 지정 합니다.

- 패키지 및 여러 SharePoint 서버 팜에 기존 모델을 배포 합니다.

  두 경우 모두 가져와야 하는 모델에 정의 된 LOB 시스템을 받지 않습니다 및 계속 예상 대로 작동 합니다. Visual Studio를 사용 하 여 기존 모델을 SharePoint 프로젝트에 추가할 **기존 항목 추가** 대화 상자. 자세한 내용은 [방법: SharePoint 프로젝트에 기존 BDC 모델 파일 추가](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)합니다.

  옵션을 선택 하 여 가져온된 모델 형식.NET Framework 어셈블리의 LOB 시스템을 추가할 수 있습니다 합니다 **추가.NET 어셈블리 LobSystem**합니다. 이 옵션을 사용 하면 사용자 지정 코드를 작성 하 고 디자이너를 사용 하 여 가져온된 모델에 대 한 메타 데이터를 정의할 수 있습니다.

## <a name="related-topics"></a>관련 항목

|제목|설명|
|-----------|-----------------|
|[방법: BDC 모델 만들기](../sharepoint/how-to-create-a-bdc-model.md)|새 BDC 모델을 만드는 방법을 보여 줍니다.|
|[방법: SharePoint 프로젝트에 기존 BDC 모델 파일 추가](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)|기존 모델을 SharePoint 프로젝트로 가져오는 방법을 보여 줍니다.|
|[방법: 리소스 파일을 사용 하 여 지역화 된 이름, 속성 및 사용 권한을 지정 합니다.](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)|웹 파트 또는 웹 페이지에서 모델을 사용할 경우 모델 메타 데이터와 병합 되는 문자열을 제공 하는 방법에 설명 합니다.|
|[방법: BDC 기능에 사용자 지정 어셈블리 포함](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)|기능에서 사용자 지정 어셈블리를 포함 하는 방법을 보여 줍니다.|
