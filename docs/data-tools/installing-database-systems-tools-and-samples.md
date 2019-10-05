---
title: 데이터베이스 호환성
ms.date: 09/06/2017
ms.topic: conceptual
helpviewer_keywords:
- database systems
- database compatibility
- databases for Visual Studio
ms.assetid: 821de34b-eaa9-40af-b9aa-b8305de16899
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 9115e675c43e04496712784371ac2301ef7c2f8a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62566692"
---
# <a name="compatible-database-systems-for-visual-studio"></a>Visual Studio용 호환 데이터베이스 시스템

Visual Studio에서 데이터에 연결 된 응용 프로그램을 개발 하려면 일반적으로 로컬 개발 컴퓨터에 데이터베이스 시스템을 설치 하 고 배포 응용 프로그램 및 데이터베이스를 프로덕션 환경으로 준비 되 면 합니다. Visual Studio의 일부로 컴퓨터에 SQL Server Express LocalDB를 설치 합니다 **데이터 저장소 및 처리** 워크 로드. 이 LocalDB 인스턴스는 쉽고 빠르게 데이터에 연결 된 응용 프로그램을 개발에 유용 합니다.

.NET 응용 프로그램에서 액세스할 수 있도록 하 고 Visual Studio 데이터 도구 창에 표시 될 데이터베이스 시스템의 경우 ADO.NET 데이터 공급자가 있어야 합니다. 구체적으로 공급자는.NET 응용 프로그램에서 엔터티 데이터 모델을 사용 하려는 경우 Entity Framework을 지원 해야 합니다. 대부분의 공급자는 NuGet 패키지 관리자를 통해 또는 Visual Studio Marketplace를 통해 제공 됩니다.

Azure 저장소 Api를 사용 하는 경우 설치 하 여 Azure storage 에뮬레이터 로컬 컴퓨터에서 개발 하는 동안 프로덕션에 배포할 준비가 될 때까지 요금이 부과 되지 않도록 하기 위해. 자세한 내용은 [개발 및 테스트에 대 한 Azure Storage 에뮬레이터를 사용 하 여](/azure/storage/common/storage-use-emulator)입니다.

다음은 Visual Studio 프로젝트에서 사용할 수 있는 더 인기가 많은 데이터베이스 시스템의 일부를 포함 합니다. 이 목록은 전체 목록이 아닙니다. Visual Studio 도구를 사용 하 여 긴밀 한 통합을 사용 하도록 설정 하는 ADO.NET 데이터 공급자를 제공 하는 타사 공급 업체의 목록을 참조 하세요 [ADO.NET 데이터 공급자](/dotnet/framework/data/adonet/data-providers)합니다.

## <a name="microsoft-sql-server"></a>Microsoft SQL Server

SQL Server는 Microsoft 주력 데이터베이스 제품입니다. SQL Server 2016은 탁월한 성능, 고급 보안 및 통합, 풍부한 보고 및 분석을 제공합니다. 다른 용도로 설계 된 다양 한 버전에 제공 합니다: 단일 컴퓨터에서 사용 하 여 확장성이 뛰어난 고성능 비즈니스 분석과에서. SQL Server Express는 재배포 및 포함에 맞게 조정할 수는 SQL Server의 모든 기능을 갖춘 버전입니다.  LocalDB는 구성이 필요 하지 않습니다 하 고 응용 프로그램의 프로세스에서 실행 되는 SQL Server Express는 간소화 된 버전입니다. 제품 중 하나 또는 모두를 다운로드할 수 있습니다 합니다 [SQL Server Express 다운로드 페이지](https://www.microsoft.com/sql-server/sql-server-editions-express)합니다. 이 섹션의 SQL 예제 많은 SQL Server LocalDB를 사용합니다. SQL Server Management Studio (SSMS)는 Visual Studio SQL Server 개체 탐색기에서 제공 하는 것 보다 더 많은 기능을 가진 독립 실행형 데이터베이스 관리 응용 프로그램입니다. SSMS는 이전 링크에서 얻을 수 있습니다.

## <a name="oracle"></a>Oracle

Oracle 데이터베이스의 유료 또는 무료 버전을 다운로드할 수 있습니다 합니다 [Oracle 기술 네트워크](http://www.oracle.com/technetwork/database/enterprise-edition/downloads/index-092322.html) 페이지입니다. Entity Framework 및 Tableadapter에 대 한 디자인 타임 지원을 해야 합니다 [Visual Studio 용 Oracle 개발자 도구](http://www.oracle.com/technetwork/developer-tools/visual-studio/overview/index.html)합니다. Oracle Instant Client 등 공식 Oracle 제품 다른 NuGet 패키지 관리자를 통해 제공 됩니다. 지침에 따라 Oracle 샘플 스키마를 다운로드할 수 있습니다 합니다 [Oracle 온라인 설명서](http://docs.oracle.com/cd/E11882_01/server.112/e10831/toc.htm)합니다.

## <a name="mysql"></a>MySQL

MySQL은 기업 및 웹 사이트에서 널리 사용 되는 인기 있는 오픈 소스 데이터베이스 시스템입니다. MySQL에 대 한 다운로드, Visual Studio 및 관련된 제품에 대 한 MySQL에 됨 [Windows에서 MySQL](http://www.mysql.com/why-mysql/windows/)합니다. 제 3 자는 다양 한 Visual Studio 확장 및 MySQL에 대 한 독립 실행형 관리 응용 프로그램을 제공합니다. NuGet 패키지 관리자에서 제품을 찾아볼 수 있습니다 (**도구가** > **NuGet 패키지 관리자** > **솔루션용 NuGet 패키지 관리**) .

## <a name="postgresql"></a>PostgreSQL

PostgreSQL은 무료, 오픈 소스 개체 관계형 데이터베이스 시스템입니다. Windows에 설치 하려면에서 다운로드할 수 있습니다 합니다 [PostgreSQL 다운로드 페이지](http://www.postgresql.org/download/windows/)합니다. 소스 코드에서 PostgreSQL을 빌드할 수 있습니다. PostgreSQL core 시스템에는 C 언어 인터페이스를 포함합니다. 많은 타사.NET 응용 프로그램에서 PostgreSQL을 사용 하는 NuGet 패키지를 제공 합니다. NuGet 패키지 관리자에서 제품을 찾아볼 수 있습니다 (**도구가** > **NuGet 패키지 관리자** > **솔루션용 NuGet 패키지 관리**) . 가장 인기 있는 패키지에서 제공 하는 것 [npgsql.org](http://www.npgsql.org)합니다.

## <a name="sqlite"></a>SQLite

SQLite는 응용 프로그램의 고유한 프로세스에서 실행 되는 포함 된 SQL 데이터베이스 엔진입니다. 다운로드할 수 있습니다 합니다 [SQLite 다운로드 페이지](http://www.sqlite.org/download.html)합니다. SQLite에 대 한 많은 타사 NuGet 패키지도 사용할 수 있습니다. NuGet 패키지 관리자에서 제품을 찾아볼 수 있습니다 (**도구가** > **NuGet 패키지 관리자** > **솔루션용 NuGet 패키지 관리**) .

## <a name="firebird"></a>Firebird

Firebird는 오픈 소스 SQL 데이터베이스 시스템입니다. 다운로드할 수 있습니다 합니다 [Firebird 다운로드 페이지](http://firebirdsql.org/en/downloads/)합니다. ADO.NET 데이터 공급자는 NuGet 패키지 관리자를 통해 사용할 수 있습니다.

## <a name="see-also"></a>참고자료

- [Visual Studio에서 데이터 액세스](../data-tools/accessing-data-in-visual-studio.md)
- [SQL Server 및 관련 구성 요소의 버전을 확인하는 방법](http://support.microsoft.com/kb/321185)