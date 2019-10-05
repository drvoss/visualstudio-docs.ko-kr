---
title: Entity Framework 도구
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1b06b573-84aa-4458-b3f5-e238df47bf45
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: eace6e7f3d970de5aa0ab0e74530d3182af0e177
ms.sourcegitcommit: 16d8ffc624adb716753412a22d586eae68a29ba2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67412292"
---
# <a name="entity-framework-tools-in-visual-studio"></a>Visual Studio에서 entity Framework 도구

Entity Framework는.NET 개발자가 도메인별 개체를 사용 하 여 관계형 데이터로 작업할 수 있도록 하는 개체-관계형 매핑 기술 합니다. 개발자들이 보통 작성해야 하는 데이터 액세스 코드가 대부분 필요하지 않게 됩니다. Entity Framework는 모델링 기술을 새로운.NET 응용 프로그램에 대 한 권장 되는 개체-관계형 매핑을 (ORM).

Entity Framework 도구는 EF (Entity Framework) 응용 프로그램을 빌드할 수 있도록 설계 되었습니다. Entity Framework에 대 한 전체 설명서는 다음 있습니다. [개요-EF 6](/ef/ef6/)합니다.

  > [!NOTE]
  > 이 페이지에 설명 된 Entity Framework 도구는 생성 하는 데 사용 됩니다 *.edmx* 파일을 EF Core에서 지원 되지 않습니다. 기존 데이터베이스에서 EF Core 모델을 생성, 참조 [리버스 엔지니어링-EF Core](/ef/core/managing-schemas/scaffolding)합니다. EF 6 및 EF Core 간의 차이점에 대 한 자세한 내용은 참조 하세요. [비교 EF 6 및 EF Core](/ef/efcore-and-ef6/)합니다.

Entity Framework Tools를 사용 하 여 만들 수 있습니다는 *개념적 모델* 기존 데이터베이스 다음 그래픽으로 시각화 하 고 개념적 모델을 편집 합니다. 또는 먼저 개념적 모델을 그래픽으로 만든 후 모델을 지원하는 데이터베이스를 생성할 수 있습니다. 이 두 경우 모두 기본 데이터베이스가 변경될 때 모델을 자동으로 업데이트하고 애플리케이션에 대한 개체 계층 코드를 자동으로 생성할 수 있습니다. 데이터베이스 생성 및 개체 계층 코드 생성 작업은 사용자 지정할 수 있습니다.

Entity Framework tools의 일부로 설치 되는 **데이터 저장소 및 처리** Visual Studio 설치 관리자에서 워크 로드. 아래에서 개별 구성 요소로 설치할 수도 있습니다는 **Sdk, 라이브러리 및 프레임 워크** 범주입니다.

다음은 Visual Studio에서 Entity Framework 도구를 구성 하는 특정 도구입니다.

- 사용할 수는 [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)]  **[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] 디자이너** (**Entity Designer**)를 시각적으로 만들고 엔터티, 연결, 매핑 및 상속 관계를 수정 합니다. 합니다 **Entity Designer** 경우에 생성 [!INCLUDE[TLA#tla_cshrp](../data-tools/includes/tlasharptla_cshrp_md.md)] 또는 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 개체 계층 코드입니다.

- 사용할 수는  **[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] 마법사** 기존 데이터베이스에서 개념적 모델을 생성 하 여 응용 프로그램에 데이터베이스 연결 정보를 추가 합니다.

- 사용할 수는 **데이터베이스 만들기 마법사** 를 먼저 개념적 모델을 만든 다음 모델을 지 원하는 데이터베이스를 만듭니다.

- 사용할 수는 **모델 업데이트 마법사** 기본 데이터베이스가 변경 된 경우에 개념적 모델, 저장소 모델 및 매핑을 업데이트 합니다.

  > [!NOTE]
  > Visual Studio 2010부터 Entity Framework 도구 지원 하지 않는 [!INCLUDE[ss2k](../data-tools/includes/ss2k_md.md)]합니다.

도구 생성 또는 수정 된 *.edmx* 파일입니다. 이렇게 *.edmx* 파일 개념적 모델, 저장소 모델 간의 매핑을 설명 하는 정보를 포함 합니다. 자세한 내용은 [EDMX](https://docs.microsoft.com/ef/ef6/)합니다.

[Entity Framework 파워 도구가](https://marketplace.visualstudio.com/items?itemName=EntityFrameworkTeam.EntityFrameworkPowerToolsBeta4) 엔터티 데이터 모델을 사용 하는 응용 프로그램을 빌드하는 데 도움이 됩니다. Power tools 수 개념적 모델을 생성, 기존 모델의 유효성을 검사, 개념적 모델을 기반으로 하는 개체 클래스가 포함 된 소스 코드 파일을 생성 및 모델을 생성 하는 뷰가 포함 된 소스 코드 파일을 생성 합니다. 자세한 내용은 [Pre-Generated 매핑 뷰](https://docs.microsoft.com/ef/ef6/fundamentals/performance/pre-generated-views)합니다.

## <a name="related-topics"></a>관련 항목

| 제목 | 설명 |
| - | - |
| [ADO.NET Entity Framework](/dotnet/framework/data/adonet/ef/index) | 사용 하는 방법에 설명 [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] 도구는 [!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)] 응용 프로그램을 만드는 제공 합니다. |
| [엔터티 데이터 모델](/dotnet/framework/data/adonet/entity-data-model) | 에 빌드된 응용 프로그램에서 사용 되는 데이터로 작업 하는 것에 대 한 정보 및 링크를 제공 [!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)]합니다. |
| [Entity Framework (EF) 설명서)](https://docs.microsoft.com/ef/ef6/get-started) | 비디오, 자습서 및 Entity Framework를 최대한을 내릴 수 있도록 고급 설명서의 인덱스를 제공 합니다. |
| [ASP.NET 5 응용 프로그램을 새 데이터베이스](https://docs.efproject.net/en/latest/platforms/aspnetcore/new-db.html) | Entity Framework 7을 사용 하 여 새 ASP.NET 5 응용 프로그램을 만드는 방법을 설명 합니다. |

## <a name="see-also"></a>참고자료

- [.NET용 Visual Studio 데이터 도구](../data-tools/visual-studio-data-tools-for-dotnet.md)