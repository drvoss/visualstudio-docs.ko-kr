---
title: SharePoint 용 사이트 열, 콘텐츠 형식 및 목록 만들기 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.ListDesigner.ContentTypeSetting
- VS.SharePointTools.ContentTypeDesigner.CommonPropertiesPage
- VS.SharePointTools.ListDesigner.CreatingLists
- VS.SharePointTools.ListDesigner.ListPage
- VS.SharePointTools.ListDesigner.ViewPage
- VS.SharePointTools.ListDesigner.CommonPropertiesPage
- VS.SharePointTools.ContentTypeDesigner.ColumnsPage
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8cecb3e78cea90b927dc6b67b5b4a2cb50bfa87c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62581098"
---
# <a name="create-site-columns-content-types-and-lists-for-sharepoint"></a>SharePoint 용 사이트 열, 콘텐츠 형식 및 목록 만들기
  Visual Studio는 많은 기본 SharePoint 항목을 포함 하 여 프로젝트 항목 템플릿을 *나열* 하 고 *콘텐츠 형식*, 사이트 열을 통합할 수 있는 (또는  *필드*). 콘텐츠 형식 및 목록에 대한 새로운 디자이너를 사용하면 이러한 항목을 이전보다 쉽게 만들 수 있습니다.

## <a name="site-columns"></a>사이트 열
 사이트 열은 SharePoint 프로젝트에 추가할 수 있는 가장 기본적인 요소 중 하나입니다. 사이트 열은 연락처 목록의 연락처에 대한 전화 번호, 설명 또는 도시 이름과 같은 데이터의 형식을 나타냅니다.

 새로운 사이트 열 프로젝트 항목 템플릿을 사용하면 이전 Visual Studio 버전의 경우보다 쉽게 사이트 열을 만들 수 있습니다. 새 사이트 열을 만든 후 사이트 열에서 XML을 수정할 수 있습니다 *Elements.xml* 사이트 열에 표시 하려는 그룹의 표시 이름, 데이터 형식 등의 원하는 정보를 포함 하는 파일 SharePoint입니다. 사이트 열에 대 한 자세한 내용은 참조 하세요. [열에 대 한 소개](http://go.microsoft.com/fwlink/?LinkId=224996)합니다.

## <a name="content-types-and-lists"></a>콘텐츠 형식 및 목록
 콘텐츠 형식과 목록은 SharePoint에서 가장 자주 사용되는 요소입니다.

 콘텐츠 형식은 SharePoint 목록 또는 문서 라이브러리에 있는 항목의 범주에 대한 메타데이터, 워크플로 및 동작을 정의합니다. 예를 들어 연락처 목록 또는 작업 목록의 정보에 대한 콘텐츠 형식을 만들 수 있습니다. 연락처 콘텐츠 형식에는 이름, 전자 메일, 전화 번호, 주소 등의 열이 포함될 수 있습니다. 사이트 수준에서 정의하는 콘텐츠 형식은 사이트의 모든 목록 또는 문서 라이브러리와 독립적입니다. SharePoint 사이트에 여러 목록 또는 문서 라이브러리가 있는 동일한 콘텐츠 형식을 사용할 수 있습니다. 또한 같은 목록 또는 문서 라이브러리에서 여러 콘텐츠 형식을 사용할 수도 있습니다.

 목록은 SharePoint에서 다른 사용자와 공유할 수 있는 정보의 컬렉션입니다. 목록은 데이터를 포함하는 열의 행으로 구성되어 있습니다. 목록의 몇 가지 예로 작업 목록, 연락처 목록 및 알림 목록을 들 수 있습니다.

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]의 새로운 콘텐츠 형식 및 목록 디자이너를 사용하면 이전 Visual Studio 버전의 경우보다 사이트 콘텐츠 형식 및 목록을 훨씬 쉽고 자연스럽게 만들 수 있습니다. UI를 통해 익숙한 방식으로 콘텐츠 형식 및 목록을 시각적으로 생성할 수 있으며, 목록의 데이터를 정렬 및 그룹화하고 그룹 제목을 사용할 수 있습니다. 콘텐츠 형식에 대 한 자세한 내용은 참조 하세요. [콘텐츠 형식](http://go.microsoft.com/fwlink/?LinkId=224997)합니다. 목록에 대 한 자세한 내용은 참조 하세요. [목록 양식을](http://go.microsoft.com/fwlink/?LinkId=224998) 하 고 [목록 뷰](http://go.microsoft.com/fwlink/?LinkId=224999)합니다.

## <a name="related-topics"></a>관련 항목

|제목|설명|
|-----------|-----------------|
|[연습: SharePoint 용 사이트 열, 콘텐츠 형식 및 목록 만들기](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)|사용자 지정 콘텐츠 형식에서 사용되는 사이트 열을 만드는 방법을 보여 줍니다. 이 경우 콘텐츠 형식이 사용자 지정 목록에서 사용됩니다.|

## <a name="see-also"></a>참고자료
- [SharePoint 2010에서 개발 시작](http://go.microsoft.com/fwlink/?LinkId=225000)
