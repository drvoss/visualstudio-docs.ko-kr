---
title: 새 데이터 원본 추가
ms.date: 11/21/2018
ms.topic: conceptual
f1_keywords:
- vs.datasource.datasourcefieldspicker
helpviewer_keywords:
- data [Visual Studio], data sources
- data sources
ms.assetid: ed28c625-bb89-4037-bfde-cfa435d182a2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 05a07fc3cb72f923d28ff907c9aec69620cbd40d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62824896"
---
# <a name="add-new-data-sources"></a>새 데이터 원본 추가

Visual Studio의.NET data tools의 컨텍스트에서 용어 *데이터 원본* 데이터 저장소에 연결 하는 데이터는.NET 응용 프로그램에 사용할 수 있도록.NET 개체를 가리킵니다. Visual Studio 디자이너에서 데이터베이스 개체를 끌어서 폼에 데이터를 바인딩하는 상용구 코드를 생성 하는 데이터 원본의 출력을 사용할 수는 **데이터 원본** 창입니다. 이 유형의 데이터 원본 수 있습니다.

- 일부 종류의 데이터베이스와 연결 된 Entity Framework 모델의 클래스입니다.

- 일부 종류의 데이터베이스와 연결 된 데이터 집합입니다.

- Windows Communication Foundation (WCF) 데이터 서비스 또는 REST 서비스와 같은 네트워크 서비스를 나타내는 클래스입니다.

- SharePoint 서비스를 나타내는 클래스입니다.

- 클래스 또는 솔루션에서 수집 합니다.

> [!NOTE]
> 데이터 바인딩 기능을 사용 하지 않는 경우 데이터 집합, Entity Framework, LINQ to SQL, WCF, 또는 SharePoint에서 "data source" 개념이 적용 되지 않습니다. SQLCommand 개체를 사용 하 여 데이터베이스에 직접 연결 하 고 데이터베이스와 직접 통신 하기만 됩니다.

만들고 사용 하 여 데이터 소스를 편집 합니다 **데이터 소스 구성 마법사** Windows Forms 또는 Windows Presentation Foundation 응용 프로그램입니다. Entity Framework를 먼저 엔터티 클래스를 만들고 다음을 선택 하 여 마법사를 시작 **프로젝트** > **새 데이터 소스 추가** (이 문서의 뒷부분에서 자세히 설명).

![데이터 소스 구성 마법사](../data-tools/media/data-source-configuration-wizard.png)

## <a name="data-sources-window"></a>데이터 소스 창

데이터 원본을 만든 후에 저장 되는 **데이터 원본** 도구 창입니다.

> [!TIP]
> 열려는 합니다 **데이터 원본** 창 프로젝트가 열려 있는지 확인 하 고 다음 키를 누릅니다 **Shift**+**Alt**+**D**선택할지 **뷰** > **기타 Windows** > **데이터 원본**합니다.

데이터 원본으로 끌 수 있습니다 합니다 **데이터 원본** 양식 디자인 화면 또는 컨트롤을 창입니다. 이렇게 하면 데이터 저장소에서 데이터를 표시 하는 상용구 코드를 생성 합니다.

다음 그림에서는 Windows form으로 삭제 된 데이터 집합을 보여 줍니다. 선택 하는 경우 **F5** 응용 프로그램을 기본 데이터베이스의에서 데이터를 폼의 컨트롤에 나타납니다.

![데이터 원본 끌기 작업](../data-tools/media/raddata-data-source-drag-operation.png)

## <a name="data-source-for-a-database-or-a-database-file"></a>데이터베이스 또는 데이터베이스 파일에 대 한 데이터 원본

데이터 집합 또는 데이터베이스 또는 데이터베이스 파일에 대 한 데이터 원본으로 사용 하는 Entity Framework 모델을 만들 수 있습니다.

### <a name="dataset"></a>데이터 세트

데이터 원본으로 데이터 집합을 만들려면 다음을 실행 합니다 **데이터 소스 구성 마법사** 를 선택 하 여 **프로젝트** > **새 데이터 소스 추가**합니다. 선택 된 **데이터베이스** 데이터 소스를 입력 하 고 지시에 따라 새 또는 기존 데이터베이스 연결 또는 데이터베이스 파일을 지정 합니다.

### <a name="entity-classes"></a>엔터티 클래스

데이터 원본으로 Entity Framework 모델을 만들려면

1. 실행 된 **엔터티 데이터 모델 마법사** 엔터티 클래스를 만들 수 있습니다. 선택 **프로젝트** > **새 항목 추가** > **ADO.NET 엔터티 데이터 모델**합니다.

   ![새 Entity Framework 모델 프로젝트 항목](../data-tools/media/raddata-new-entity-framework-model-project-item.png)

1. 모델을 생성 하려는 방법을 선택 합니다.

   ![엔터티 데이터 모델 마법사](../data-tools/media/raddata-entity-data-model-wizard.png)

1. 데이터 원본으로 모델을 추가 합니다. 생성된 된 클래스에 표시 된 **데이터 소스 구성 마법사** 선택 하는 경우를 **개체** 범주입니다.

   ![엔터티 클래스를 사용 하 여 데이터 소스 구성 마법사](../data-tools/media/raddata-data-source-configuration-wizard-with-entity-classes.png)

## <a name="data-source-for-a-service"></a>서비스에 대 한 데이터 원본

서비스에서 데이터 원본을 만들려면 실행 합니다 **데이터 소스 구성 마법사** 선택한를 **서비스** 데이터 소스 형식입니다. 이 바로 가기에는 **서비스 참조 추가** 대화 상자에서 프로젝트를 마우스 오른쪽 단추로 클릭 하 여 액세스할 수 있습니다 **솔루션 탐색기** 를 선택 하 고 **서비스참조추가**.

서비스에서 데이터 소스를 만들 때 Visual Studio 프로젝트에 대 한 서비스 참조를 추가 합니다. Visual Studio는 또한 서비스에서 반환 하는 개체에 해당 하는 프록시 개체를 만듭니다. 예를 들어 데이터 집합을 반환 하는 서비스는 데이터 집합으로 프로젝트에 표시 됩니다. 반환 형식으로 프로젝트는 특정 형식의 표현 반환 되는 서비스입니다.

다음 유형의 서비스에서 데이터 소스를 만들 수 있습니다.

- [WCF Data Services](/dotnet/framework/data/wcf/wcf-data-services-overview)

- [WCF 서비스](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)

- 웹 서비스

    > [!NOTE]
    > 에 표시 되는 항목의 **데이터 원본** 창 서비스를 반환 하는 데이터에 따라 달라 집니다. **데이터 원본 구성 마법사**에서 바인딩 가능한 개체를 만들기에 충분한 정보를 제공하지 않는 서비스도 있습니다. 예를 들어 서비스가 형식화 되지 않은 데이터 집합을 반환 하는 경우에 아무런 항목도 표시 합니다 **데이터 원본** 창 마법사를 완료 합니다. 형식화 되지 않은 데이터 집합 스키마를 제공 하지 않으며 마법사가 데이터 원본을 만들려면 충분 한 정보를 갖고 있지 않으므로 때문입니다.

## <a name="data-source-for-an-object"></a>개체에 대 한 데이터 원본

실행 하 여 하나 이상의 공용 속성을 노출 하는 개체 로부터 데이터 소스를 만들 수 있습니다 합니다 **데이터 소스 구성 마법사** 을 선택한 다음는 **개체** 데이터 소스 형식입니다. 개체의 모든 public 속성에 표시 되는 **데이터 원본** 창입니다. Entity Framework를 사용 하는 모델을 생성 하는 경우 엔터티 클래스는 응용 프로그램에 대 한 데이터 소스를 찾을 위치입니다.

에 **데이터 개체 선택** 페이지에서 바인딩할 하려는 개체를 찾으려면 트리 뷰에서 노드를 확장 합니다. 트리 뷰에서 프로젝트 및 어셈블리와 프로젝트에서 참조 하는 다른 프로젝트에 대 한 노드를 포함 합니다.

어셈블리 또는 트리 보기에 나타나지 않으면 프로젝트의 개체에 바인딩하려면 클릭 **참조 추가** 사용 하 여는 **참조 추가 대화 상자** 어셈블리 또는 프로젝트에 대 한 참조를 추가 합니다. 참조를 추가한 후 어셈블리 또는 프로젝트를 트리 뷰에 추가 됩니다.

> [!NOTE]
> 개체는 트리 뷰에 표시 하려면 먼저 개체를 포함 하는 프로젝트를 작성 해야 합니다.

> [!NOTE]
> 구현 하는 개체 끌어서 놓기 데이터 바인딩을 지원 하기 위해 합니다 <xref:System.ComponentModel.ITypedList> 또는 <xref:System.ComponentModel.IListSource> 인터페이스에는 기본 생성자가 있어야 합니다. 아니면 Visual Studio 데이터 원본 개체를 인스턴스화할 수 없습니다 하 고 디자인 화면으로 항목을 끌면 오류가 표시 됩니다.

## <a name="data-source-for-a-sharepoint-list"></a>SharePoint 목록을 데이터 원본

실행 하 여 SharePoint 목록의 데이터 소스를 만들 수는 **데이터 소스 구성 마법사** 선택 하 고는 **SharePoint** 데이터 소스 형식입니다. SharePoint은 서비스에서 데이터 원본을 만드는 것과 같습니다는 SharePoint 데이터 원본 만들기 WCF Data Services를 통해 데이터를 노출 합니다. 선택 하는 **SharePoint** 항목에 **데이터 소스 구성 마법사** 열립니다는 **서비스 참조 추가** 대화 상자에서 SharePoint 데이터 서비스에 연결 SharePoint 서버를 가리키면 됩니다. SharePoint SDK 필요합니다.

## <a name="see-also"></a>참고자료

- [.NET용 Visual Studio 데이터 도구](../data-tools/visual-studio-data-tools-for-dotnet.md)