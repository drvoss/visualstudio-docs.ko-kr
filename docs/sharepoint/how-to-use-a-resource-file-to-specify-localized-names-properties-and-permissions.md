---
title: '방법: 리소스 파일을 사용 하 여 지역화 된 이름, 속성 및 사용 권한을 지정 합니다. | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], localize strings
- BDC [SharePoint development in Visual Studio], localize strings
- BDC [SharePoint development in Visual Studio], resource file
- Business Data Connectivity service [SharePoint development in Visual Studio], resource strings
- BDC [SharePoint development in Visual Studio], properties
- Business Data Connectivity service [SharePoint development in Visual Studio], properties
- Business Data Connectivity service [SharePoint development in Visual Studio], resource file
- BDC [SharePoint development in Visual Studio], resource strings
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2be88a29d3e9e3da9d1963aa1226ffca0a0a2bbd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62813051"
---
# <a name="how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions"></a>방법: 리소스 파일을 사용 하 여 지역화 된 이름, 속성 및 사용 권한을 지정 합니다.
  리소스 파일을 사용하여 지역화된 이름을 제공하고, 속성을 정의하고, BDC(비즈니스 데이터 연결) 모델에 정의된 개체에 대한 사용 권한을 적용할 수 있습니다. 이 정보를 지정 하려면 추가 **비즈니스 데이터 연결 리소스** 포함 된 프로젝트에 항목을 **비즈니스 데이터 연결 모델** 항목입니다. 그런 다음 리소스 파일의 XML을 편집하여 이름, 속성 및 사용 권한을 지정합니다.

### <a name="to-add-a-bdc-resource-file-to-a-sharepoint-project"></a>SharePoint 프로젝트에 BDC 리소스 파일을 추가 하려면

1. **솔루션 탐색기**, SharePoint 프로젝트의 폴더를 확장 한 다음 BDC 모델이 포함 된 폴더를 선택 합니다.

2. 메뉴 모음에서 **프로젝트** > **새 항목 추가**를 선택합니다.

3. 확장 된 **SharePoint** 노드를 선택한 후 합니다 **2010** 노드.

4. 에 **새 항목 추가** 대화 상자에서 **비즈니스 데이터 연결 리소스 항목**합니다.

5. 에 **이름** 상자, 리소스 파일의 이름을 지정 하 고 선택한 합니다 **추가** 단추입니다.

     확장명이 .bdcr인 리소스 파일이 프로젝트에 추가되고 편집할 수 있도록 열립니다.

6. XML을 추가하여 BDC 모델을 적용할 지역화된 이름, 속성 및 사용 권한을 정의합니다.

     이러한 요소를 정의 하는 방법에 대 한 자세한 내용은 [모델 및 리소스 파일](http://go.microsoft.com/fwlink/?LinkID=169283)합니다.

## <a name="see-also"></a>참고자료
- [방법: SharePoint 프로젝트에 기존 BDC 모델 파일 추가](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
- [비즈니스 데이터 연결 모델 만들기](../sharepoint/creating-a-business-data-connectivity-model.md)
- [방법: BDC 모델 만들기](../sharepoint/how-to-create-a-bdc-model.md)
- [방법: BDC 기능에 사용자 지정 어셈블리 포함](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)
- [SharePoint에 비즈니스 데이터 통합](../sharepoint/integrating-business-data-into-sharepoint.md)
