---
title: 엔터티 간의 연결 만들기 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.BDC.Association_Dialog
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
ms.openlocfilehash: c285b699487bd761447e5fbdf6ccd77987a8c0a8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62952895"
---
# <a name="create-an-association-between-entities"></a>엔터티 간의 연결 만들기
  연결을 만들어 비즈니스 데이터 연결 (BDC) 모델의 엔터티 간의 관계를 정의할 수 있습니다. Visual Studio는 각 연결에 대 한 정보를 사용 하 여 모델의 소비자에 게 제공 하는 메서드를 생성 합니다. 이러한 메서드는 SharePoint 웹 파트, 목록 또는 사용자 지정 애플리케이션에서 사용되어 UI(사용자 인터페이스)에 데이터 관계를 표시할 수 있습니다.

## <a name="create-an-association"></a>연결 만들기
 선택 하 여 연결을 만들 합니다 **연결** Visual Studio에서 컨트롤 **도구 상자**(원본 엔터티 라고 함)는 첫 번째 엔터티를 선택 하 고 다음 두 번째 엔터티를 선택 (호출을 대상 엔터티)입니다. 연결의 세부 정보를 정의할 수 있습니다 합니다 **연결 편집기**합니다. 자세한 내용은 [방법: 엔터티 간의 연결을 만들](../sharepoint/how-to-create-an-association-between-entities.md)합니다.

## <a name="association-methods"></a>연결 메서드
 SharePoint 비즈니스 데이터 웹 파트와 같은 응용 프로그램 엔터티 서비스 클래스의 메서드를 호출 하 여 연결을 사용 합니다. 선택 하 여 엔터티 서비스 클래스에 메서드를 추가할 수 있습니다 합니다 **연결 편집기**합니다.

 기본적으로 **연결 편집기** 원본과 대상 엔터티에 연결 탐색 메서드를 추가 합니다. 소스 엔터티에 연결 탐색 메서드를 통해 소비자를 대상 엔터티 목록을 검색할 수 있습니다. 대상 엔터티에 연결 탐색 메서드를 통해 소비자를 대상 엔터티에 관련 된 소스 엔터티를 검색할 수 있습니다.

 적절 한 정보를 반환 하는 이러한 메서드의 각 코드를 추가 해야 합니다. 또한 다른 유형의 고급 시나리오를 지 원하는 메서드를 추가할 수 있습니다. 이러한 각 방법에 대 한 자세한 내용은 참조 하세요. [지원 되는 작업](http://go.microsoft.com/fwlink/?LinkId=169286)합니다.

## <a name="types-of-associations"></a>두 종류의 연결
 BDC 디자이너에서 두 가지 유형의 연결을 만들 수 있습니다: 외래 키 기반 연결 및 외래 키가 없는 연결 합니다.

### <a name="foreign-key-based-association"></a>외래 키 기반 연결
 원본 엔터티를 대상 엔터티에 정의 된 형식 설명자 식별자와 관련 하 여 외래 키 기반 연결을 만들 수 있습니다. 이 관계는 모델의 소비자가 사용자를 위한 향상된 된 UI를 제공할 수 있습니다. 예를 들어 사용자는 드롭다운 목록에서 고객에 게 표시할 수 있는 판매 주문을 만들 수 있도록 하는 Outlook에서 양식 또는 고객의 프로필 페이지를 열 수 있도록 하는 SharePoint에서 판매 주문 목록입니다.

 외래 키 기반 연결을 만들려면 식별자와 동일한 이름과 형식을 공유 하는 설명자 형식입니다. 예를 들어 간의 외래 키 기반 연결을 만들 수 있습니다는 `Contact` 엔터티 및 `SalesOrder` 엔터티. 합니다 `SalesOrder` 엔터티 반환을 `ContactID` Finder 또는 특정 Finder 메서드 반환 매개 변수의 일부로 형식 설명자입니다. 두 형식 설명자에 표시 된 **연결 편집기**합니다. 사이 외래 키 기반 관계를 만들려면를 `Contact` 엔터티 및 `SalesOrder` 엔터티를 선택 합니다 `ContactID` 각이 필드 옆에 있는 식별자입니다.

 대상 엔터티 컬렉션을 반환 하는 소스 엔터티의 연결 탐색기 메서드에 코드를 추가 합니다. 다음 예제에서는 연락처에 대 한 판매 주문을 반환합니다.

 [!code-csharp[SP_BDC#7](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#7)]
 [!code-vb[SP_BDC#7](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#7)]

 원본 엔터티를 반환 하는 대상 엔터티의 연결 탐색기 메서드에 코드를 추가 합니다. 다음 예에서는 판매 주문에 관련 된 연락처를 반환 합니다.

 [!code-csharp[SP_BDC#8](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderservice.cs#8)]
 [!code-vb[SP_BDC#8](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderservice.vb#8)]

### <a name="foreign-keyless-association"></a>외래 키 연결
 형식 설명자 필드 식별자 매핑 없이 연결을 만들 수 있습니다. 원본 엔터티 대상 엔터티 간에 직접적인 관계가 없는 경우이 유형의 연결을 만듭니다. 예를 들어, 한 `SalesOrderDetail` 테이블에 외래 키에서 기본 키에 매핑되는 없는 `Contact` 테이블.

 에 정보를 표시 하려는 경우는 `SalesOrderDetail` 관련 된 테이블을 `Contact`, 간의 외래 키 연결을 만들 수 있습니다는 `Contact` 엔터티 및 `SalesOrderDetail` 엔터티.

 연결 탐색 메서드에 `Contact` 엔터티를 반환 합니다 `SalesOrderDetail` 엔터티 테이블을 조인 하 여 또는 저장된 프로시저를 호출 하 여 합니다.

 다음 예에서는 테이블을 조인 하 여 모든 판매 주문 세부 정보를 반환 합니다.

 [!code-csharp[SP_BDC#9](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#9)]
 [!code-vb[SP_BDC#9](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#9)]

 연결 탐색 메서드에 `SalesOrderDetail` 엔터티를 반환할 관련 `Contact`합니다. 다음은 이에 대한 예입니다.

 [!code-csharp[SP_BDC#10](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderdetailservice.cs#10)]
 [!code-vb[SP_BDC#10](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderdetailservice.vb#10)]

## <a name="see-also"></a>참고자료
- [비즈니스 데이터 연결 모델 디자인](../sharepoint/designing-a-business-data-connectivity-model.md)
- [방법: 엔터티 간의 연결 만들기](../sharepoint/how-to-create-an-association-between-entities.md)
