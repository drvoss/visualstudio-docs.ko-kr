---
title: '방법: 엔터티 간의 연결 만들기 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- AssociationGroupTool
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], create an assocation
- Business Data Connectivity service [SharePoint development in Visual Studio], associations between entities
- BDC [SharePoint development in Visual Studio], associations between entities
- Business Data Connectivity service [SharePoint development in Visual Studio], create an assocation
- Business Data Connectivity service [SharePoint development in Visual Studio], associate external content types
- Business Data Connectivity service [SharePoint development in Visual Studio], relate entities
- BDC [SharePoint development in Visual Studio], relate entities
- BDC [SharePoint development in Visual Studio], associate external content types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ce6d0bad9da4f11b5fae1daf93657c6908cf5e95
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62966798"
---
# <a name="how-to-create-an-association-between-entities"></a>방법: 엔터티 간의 연결 만들기
  연결을 만들어 비즈니스 데이터 연결 (BDC) 모델의 엔터티 간의 관계를 정의할 수 있습니다. Visual Studio는 각 연결에 대 한 정보를 사용 하 여 모델의 소비자에 게 제공 하는 메서드를 생성 합니다. 이러한 메서드는 SharePoint 웹 파트, 목록 또는 사용자 지정 애플리케이션에서 사용되어 UI(사용자 인터페이스)에 데이터 관계를 표시할 수 있습니다.

 BDC 디자이너에서 두 가지 유형의 연결을 만들 수 있습니다: 외래 키 기반 연결 및 외래 키가 없는 연결 합니다. 자세한 내용은 [엔터티 간의 연결을 만들](../sharepoint/creating-an-association-between-entities.md)합니다.

### <a name="to-create-an-association-between-entities"></a>엔터티 간의 연결을 만들려면

1. 에 **BusinessDataConnectivity** 탭의 **도구 상자**, 선택는 **연결** 항목.

2. BDC 디자이너에서 소스 엔터티를 선택한 다음 대상 엔터티를 선택합니다.

     합니다 **연결 편집기** 나타납니다.

3. 외래 키 기반 연결을 만들려는 경우 선택 합니다 **외래 키 연결** 확인란 합니다.

    1. 에 **원본 ID** 열의 합니다 **식별자 매핑** 테이블에 표시 되는 각 일치 하는 형식 설명자 옆에 있는 식별자를 선택 합니다는 **필드** 열.

         예를 들어 합니다 **원본 ID** 열을 선택 `ContactID` 옆에 `ReadList.salesOrderList.SalesOrderList.SalesOrder.ContactID` 형식 설명자 및 `ReadItem.salesOrder.SalesOrder.ContactID` 형식 설명자입니다.

4. 외래 키 연결을 만들려는 경우 선택을 취소 합니다 **외래 키 연결** 확인란 합니다.

5. **확인** 단추를 선택합니다.

6. BDC 디자이너에서 대상 엔터티에 원본 엔터티 사이의 연결을 나타내는 선이 나타납니다.

     Visual Studio는 대상 엔터티 서비스 클래스 및 서비스 원본 엔터티 클래스에는 연결 탐색기 메서드를 추가합니다. 연결 탐색 메서드에 대 한 자세한 내용은 참조 하세요. [지원 되는 작업](http://go.microsoft.com/fwlink/?LinkId=169286)합니다.

7. 소스 엔터티의 연결 탐색기 메서드를 대상 엔터티의 컬렉션을 반환 하는 코드를 추가 합니다.

8. 대상 엔터티의 연결 탐색기 메서드에서 관련된 원본 엔터티를 반환 하는 코드를 추가 합니다.

     연결 탐색 방법의 예제를 참조 하세요 [엔터티 간의 연결을 만들](../sharepoint/creating-an-association-between-entities.md)합니다.

## <a name="see-also"></a>참고자료
- [엔터티 간의 연결 만들기](../sharepoint/creating-an-association-between-entities.md)
- [비즈니스 데이터 연결 모델 디자인](../sharepoint/designing-a-business-data-connectivity-model.md)
- [방법: Finder 메서드 추가](../sharepoint/how-to-add-a-finder-method.md)
- [방법: 특정 Finder 메서드 추가](../sharepoint/how-to-add-a-specific-finder-method.md)
- [방법: Creator 메서드 추가](../sharepoint/how-to-add-a-creator-method.md)
- [방법: Deleter 메서드 추가](../sharepoint/how-to-add-a-deleter-method.md)
- [방법: Updater 메서드 추가](../sharepoint/how-to-add-an-updater-method.md)
- [BDC 모델 디자인 도구 개요](../sharepoint/bdc-model-design-tools-overview.md)
- [방법: 메서드에 매개 변수를 추가 합니다.](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [방법: 메서드 인스턴스 정의](../sharepoint/how-to-define-a-method-instance.md)
- [방법: 매개 변수의 형식 설명자 정의](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)
- [연습: 비즈니스 데이터를 사용 하 여 SharePoint에 외부 목록 만들기](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)
