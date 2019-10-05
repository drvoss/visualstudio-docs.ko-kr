---
title: '방법: 모델에 엔터티 추가 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- EntityTool
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], entity
- Business Data Connectivity service [SharePoint development in Visual Studio], adding an entity
- Business Data Connectivity service [SharePoint development in Visual Studio], entity
- BDC [SharePoint development in Visual Studio], adding an entity
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c7d74b731bd1857330c40a7929d84efe40a03201
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63431244"
---
# <a name="how-to-add-an-entity-to-a-model"></a>방법: 모델에 엔터티 추가
  엔터티를 만들려면 Visual Studio에서 엔터티 컨트롤을 추가 **도구 상자** 비즈니스 데이터 연결 (BDC) 디자이너에 있습니다.

### <a name="to-add-an-entity-to-the-model"></a>모델에 엔터티를 추가 하려면

1. BDC 프로젝트를 만들거나 기존 BDC 프로젝트를 엽니다. 자세한 내용은 [비즈니스 데이터 연결 모델 만들기](../sharepoint/creating-a-business-data-connectivity-model.md)합니다.

2. 에 **도구 상자**에서 **BusinessDataCatalog** 그룹에 추가 **엔터티** 컨트롤을 디자이너로 합니다.

     새 엔터티 디자이너에 표시 됩니다. Visual Studio 추가 `<Entity>` 프로젝트에서 BDC 모델 파일의 xml 요소입니다. 엔터티 요소의 특성에 대 한 자세한 내용은 참조 [엔터티](http://go.microsoft.com/fwlink/?LinkId=169296)합니다.

3. 디자이너에서 엔터티에 대 한 바로 가기 메뉴를 열고 **추가**를 선택한 후 **식별자**합니다.

     엔터티에 대해 새 식별자를 표시 됩니다.

    > [!NOTE]
    > 엔터티 및 식별자의 이름을 변경할 수 있습니다 합니다 **속성** 창입니다.

4. 클래스에서 엔터티의 필드를 정의 합니다. 프로젝트에 새 클래스를 추가 하거나 개체 관계형 디자이너 (O/R 디자이너)와 같은 다른 도구를 사용 하 여 만든 기존 클래스를 사용할 수 있습니다. 다음 예제에서는 Contact 라는 엔터티 클래스를 보여 줍니다.

     [!code-csharp[SP_BDC_Entity_Data_Class#1](../sharepoint/codesnippet/CSharp/sp_bdc_entity_data_class/bdcmodel1/contact.cs#1)]
     [!code-vb[SP_BDC_Entity_Data_Class#1](../sharepoint/codesnippet/VisualBasic/sp_bdc_entity_data_class/bdcmodel1/contact.vb#1)]

## <a name="see-also"></a>참고자료
- [방법: Creator 메서드 추가](../sharepoint/how-to-add-a-creator-method.md)
- [방법: Deleter 메서드 추가](../sharepoint/how-to-add-a-deleter-method.md)
- [방법: Updater 메서드 추가](../sharepoint/how-to-add-an-updater-method.md)
- [방법: Finder 메서드 추가](../sharepoint/how-to-add-a-finder-method.md)
- [방법: 특정 Finder 메서드 추가](../sharepoint/how-to-add-a-specific-finder-method.md)
