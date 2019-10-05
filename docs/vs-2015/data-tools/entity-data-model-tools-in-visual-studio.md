---
title: 엔터티 데이터 모델 도구
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
ms.assetid: 1b06b573-84aa-4458-b3f5-e238df47bf45
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: da608c7f937a09d56b25b87625580e5047d560cc
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65705042"
---
# <a name="entity-data-model-tools-in-visual-studio"></a>Visual Studio에서 엔터티 데이터 모델 도구
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Entity Framework는.NET 개발자가 도메인별 개체를 사용 하 여 관계형 데이터로 작업할 수 있도록 하는 개체-관계형 매핑 기술 합니다. 개발자들이 보통 작성해야 하는 데이터 액세스 코드가 대부분 필요하지 않게 됩니다. Entity Framework는 모델링 기술을 새로운.NET 응용 프로그램에 대 한 권장 되는 개체-관계형 매핑을 (ORM).

 최신 릴리스 버전은 2016 년 3 월부터 [Entity Framework 6](https://msdn.microsoft.com/data/ef) 합니다. [Entity Framework 7](https://docs.efproject.net/en/latest/) 시험판 인 합니다.

 [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] 도구를 작성할 수 있도록 설계 된 [!INCLUDE[adonet_ef](../includes/adonet-ef-md.md)] 응용 프로그램입니다. 에 대 한 전체 설명서 [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] 도구: [Entity Framework](https://msdn.microsoft.com/data/jj590134).

 사용 하 여 [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] 만들면 도구를 *개념적 모델* 기존 데이터베이스 다음 그래픽으로 시각화 하 고 개념적 모델을 편집 합니다. 또는 먼저 개념적 모델을 그래픽으로 만든 후 모델을 지원하는 데이터베이스를 생성할 수 있습니다. 이 두 경우 모두 기본 데이터베이스가 변경될 때 모델을 자동으로 업데이트하고 애플리케이션에 대한 개체 계층 코드를 자동으로 생성할 수 있습니다. 데이터베이스 생성 및 개체 계층 코드 생성 작업은 사용자 지정할 수 있습니다.

 다음은 Visual Studio 2015에서 엔터티 데이터 모델 도구를 구성 하는 특정 도구입니다.

- 사용할 수는 [!INCLUDE[vstecado](../includes/vstecado-md.md)]  **[!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] 디자이너** (**Entity Designer**)를 시각적으로 만들고 엔터티, 연결, 매핑 및 상속 관계를 수정 합니다. 합니다 **Entity Designer** 경우에 생성 [!INCLUDE[TLA#tla_cshrp](../includes/tlasharptla-cshrp-md.md)] 또는 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 개체 계층 코드입니다.

- 사용할 수는  **[!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] 마법사** 기존 데이터베이스에서 개념적 모델을 생성 하 여 응용 프로그램에 데이터베이스 연결 정보를 추가 합니다.

- 사용할 수는 **데이터베이스 만들기 마법사** 를 먼저 개념적 모델을 만든 다음 모델을 지 원하는 데이터베이스를 만듭니다.

- 사용할 수는 **모델 업데이트 마법사** 기본 데이터베이스가 변경 된 경우에 개념적 모델, 저장소 모델 및 매핑을 업데이트 합니다.

  > [!NOTE]
  > Visual Studio 2010부터 [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] 도구가 지원 하지 않습니다 [!INCLUDE[ss2k](../includes/ss2k-md.md)]합니다.

  도구 생성 하거나.edmx 파일을 수정 합니다. 이 파일에는 개념적 모델, 저장소 모델 간의 매핑을 설명 하는 정보가 들어 있습니다. 자세한 내용은 [EDMX](https://msdn.microsoft.com/data/jj650889.aspx)합니다.

  Entity Framework 파워 도구에서는 엔터티 데이터 모델을 사용 하는 응용 프로그램을 빌드할 수 있습니다. 도구 수 개념적 모델을 생성, 기존 모델의 유효성을 검사, 개념적 모델을 기반으로 하는 개체 클래스가 포함 된 소스 코드 파일을 생성 및 모델을 생성 하는 뷰가 포함 된 소스 코드 파일을 생성 합니다. 자세한 내용은 [Pre-Generated 매핑 뷰](https://msdn.microsoft.com/data/dn469601.aspx)합니다.

## <a name="related-topics"></a>관련 항목

|제목|설명|
|-----------|-----------------|
|[ADO.NET Entity Framework](https://msdn.microsoft.com/library/a437041f-6899-4ae7-96ce-aabf528d7205)|사용 하는 방법에 설명 [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] 도구는 [!INCLUDE[adonet_ef](../includes/adonet-ef-md.md)] 응용 프로그램을 만드는 제공 합니다.|
|[엔터티 데이터 모델](https://msdn.microsoft.com/library/2dda3d5b-4582-4ba0-a91d-fcd7a1498137)|에 빌드된 응용 프로그램에서 사용 되는 데이터로 작업 하는 것에 대 한 정보 및 링크를 제공 [!INCLUDE[adonet_ef](../includes/adonet-ef-md.md)]합니다.|
|[전체.NET (콘솔, WinForms, WPF 등)에서 시작](/ef/ef6/get-started)|Entity Framework 7을 사용 하 여.NET 데스크톱 응용 프로그램을 만드는 방법에 대 한 자습서를 제공 합니다.|
|[ASP.NET 5 응용 프로그램을 새 데이터베이스](https://docs.efproject.net/en/latest/platforms/aspnetcore/new-db.html)|Entity Framework 7을 사용 하 여 새 ASP.NET 5 응용 프로그램을 만드는 방법을 설명 합니다.|

## <a name="see-also"></a>참고 항목
 [.NET용 Visual Studio 데이터 도구](../data-tools/visual-studio-data-tools-for-dotnet.md)
