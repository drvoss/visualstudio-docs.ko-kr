---
title: 데이터 액세스 및 도구
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- "80025080"
helpviewer_keywords:
- data [Visual Studio]
- data access [Visual Studio]
- data [C#]
- ADO.NET, data access
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 5403803a4da0821978a8c6bbfc31e45c31104640
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66715264"
---
# <a name="access-data-in-visual-studio"></a>Visual Studio에서 데이터 액세스

Visual Studio에서 거의 모든 데이터베이스 제품 또는 서비스의 형식으로 어디서 나 데이터에 연결 하는 응용 프로그램을 만들 수 있습니다-공용, 개인 또는 하이브리드 클라우드 또는 로컬 영역 네트워크에 로컬 컴퓨터에서.

JavaScript, Python, PHP, Ruby에서 응용 프로그램 또는 C++를 가져오기 라이브러리 및 코드를 작성 하 여 다른 작업을 수행 하기와 같은 데이터에 연결 합니다. .NET 응용 프로그램에 대 한 Visual Studio 데이터 원본 탐색, 개체 모델을 저장 하 고 메모리에서 데이터를 조작 하 고, 사용자 인터페이스에 데이터 바인딩 만들기에 사용할 수 있는 도구를 제공 합니다. Microsoft Azure는 Azure Storage에 연결 하기 위한.NET, Java, Node.js, PHP, Python, Ruby 및 모바일 앱 및 Visual Studio의 도구에 대 한 Sdk를 제공 합니다.

다음 목록에는 Visual Studio에서 사용할 수 있는 여러 데이터베이스 및 저장소 시스템의 일부에 지나지 보여 줍니다. 합니다 [Microsoft Azure](https://azure.microsoft.com/) 제품은 모든 프로 비전 및 관리의 기본 데이터 저장소를 포함 하는 데이터 서비스입니다. 합니다 **Azure 개발** 의 워크 로드가 [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) Visual Studio에서 직접 Azure 데이터 저장소를 사용 하 여 사용할 수 있습니다.

![Azure 개발 워크로드](media/azure-development-workload.png)

대부분의 다른 SQL 및 NoSQL 데이터베이스 제품 여기에 나와 있는 로컬 컴퓨터에서 로컬 네트워크에서 또는 Microsoft Azure 가상 머신에서 호스트할 수 있습니다. Microsoft Azure 가상 머신에서 데이터베이스를 호스팅할 경우 데이터베이스 자체를 관리 하는 일을 담당 합니다.

**Microsoft Azure**

- SQL Database
- Azure Cosmos DB
- Storage (blob, 테이블, 큐, 파일)
- SQL Data Warehouse
- SQL Server Stretch Database
- StorSimple
- 기타...

**SQL**

- SQL Server 2005-2016(&a (Express 및 LocalDB 포함)
- Firebird
- MariaDB
- MySQL
- Oracle
- PostgreSQL
- SQLite
- 기타...

**NoSQL**

- Apache Cassandra
- CouchDB
- MongoDB
- NDatabase
- OrientDB|
- RavenDB
- VelocityDB
- 기타...

::: moniker range="vs-2017"

여러 데이터베이스 공급 업체와 타사 NuGet 패키지에서 Visual Studio 통합을 지원합니다. Nuget.org 또는 Visual Studio에서 NuGet 패키지 관리자를 통해 제공 되는 서비스를 탐색할 수 있습니다 (**도구가** > **NuGet 패키지 관리자** > **NuGet 관리 솔루션에 대 한 패키지**). 다른 데이터베이스 제품 확장으로 Visual Studio와 통합 합니다. 이러한 제품을 찾아볼 수 있습니다 합니다 [Visual Studio Marketplace](https://marketplace.visualstudio.com/) 으로 이동 **도구** > **확장 및 업데이트** 을 선택한 다음  **온라인** 대화 상자의 왼쪽된 창에서. 자세한 내용은 [Visual Studio에 대 한 호환 되는 데이터베이스 시스템](../data-tools/installing-database-systems-tools-and-samples.md)입니다.

::: moniker-end

::: moniker range=">=vs-2019"

여러 데이터베이스 공급 업체와 타사 NuGet 패키지에서 Visual Studio 통합을 지원합니다. Nuget.org 또는 Visual Studio에서 NuGet 패키지 관리자를 통해 제공 되는 서비스를 탐색할 수 있습니다 (**도구가** > **NuGet 패키지 관리자** > **NuGet 관리 솔루션에 대 한 패키지**). 다른 데이터베이스 제품 확장으로 Visual Studio와 통합 합니다. 이러한 제품을 찾아볼 수 있습니다 합니다 [Visual Studio Marketplace](https://marketplace.visualstudio.com/) 으로 이동 **확장** > **확장 관리** 을 선택한 다음  **온라인** 대화 상자의 왼쪽된 창에서. 자세한 내용은 [Visual Studio에 대 한 호환 되는 데이터베이스 시스템](../data-tools/installing-database-systems-tools-and-samples.md)입니다.

::: moniker-end

> [!NOTE]
> 2016 년 4 월 12 일에 SQL Server 2005 지원 연장이 종료 되었습니다. SQL Server 2005를 사용 하려면 Visual Studio 2015 이상에서 데이터 도구를 계속 하지 않을 수도가 있습니다. 자세한 내용은 참조는 [SQL Server 2005 지원 종료 알림](https://www.microsoft.com/sql-server/sql-server-2005)합니다.

## <a name="net-languages"></a>.NET 언어

.NET Core를 포함 하 여 모든.NET 데이터 액세스, ADO.NET, 모든 종류의 관계형 및 비관계형 데이터 원본에 액세스 하기 위한 인터페이스를 정의 하는 클래스 집합을 기반으로 합니다. Visual Studio에 여러 도구 및 데이터베이스에 연결할 수 있도록 ADO.NET을 사용 하는 디자이너에 데이터를 조작 하 고 사용자에 게 데이터를 표시 합니다. 이 섹션의에서 설명서에서는 이러한 도구를 사용 하는 방법을 설명 합니다. ADO.NET 명령 개체에 대해 직접 프로그래밍할 수 있습니다. ADO.NET Api를 직접 호출 하는 방법에 대 한 자세한 내용은 참조 하세요. [ADO.NET](/dotnet/framework/data/adonet/index)합니다.

ASP.NET과 관련 된 데이터 액세스 설명서를 참조 하세요 [데이터로 작업](https://www.asp.net/web-forms/overview/presenting-and-managing-data) ASP.NET 사이트의. ASP.NET MVC로 Entity Framework를 사용 하 여에 대 한 자습서를 참조 하세요 [Getting Started with Entity Framework 6 Code First MVC 5를 사용 하 여](/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application)입니다.

UWP (유니버설 Windows 플랫폼) 앱에서 C# 또는 Visual Basic Microsoft Azure SDK for.NET을 사용 하 여 Azure Storage 및 다른 Azure 서비스에 액세스할 수 있습니다. Windows.Web.HttpClient 클래스 RESTful 서비스와 통신할 수 있도록 합니다. 자세한 내용은 [Windows.Web.Http를 사용 하 여 HTTP 서버에 연결 하는 방법을](https://msdn.microsoft.com/library/windows/apps/dn469430.aspx)합니다.

로컬 컴퓨터의 데이터 저장소에 대 한 앱과 동일한 프로세스에서 실행 되는 SQLite를 사용 하는 것이 좋습니다. 개체-관계형 매핑 (ORM) 계층을 필요한 경우에 Entity Framework를 사용할 수 있습니다. 자세한 내용은 [데이터 액세스](/windows/uwp/data-access/index) Windows 개발자 센터에서.

Azure 서비스에 연결 하는 경우 다운로드 해야 최신 [Azure SDK 도구](https://azure.microsoft.com/downloads/)합니다.

### <a name="data-providers"></a>데이터 공급자

ADO.NET에서 수 있으려면 데이터베이스에 대 한 사용자 지정 권한이 있어야 합니다 *ADO.NET 데이터 공급자* 하거나 다른 ODBC 또는 OLE DB 인터페이스를 노출 해야 합니다. Microsoft에서 제공 된 [ADO.NET 데이터 공급자 목록은](https://docs.microsoft.com/dotnet/framework/data/adonet/ado-net-overview) ODBC 및 OLE DB 공급자 뿐만 아니라 SQL Server 제품에 대 한 합니다.

### <a name="data-modeling"></a>데이터 모델링

.NET에서는 모델링 및 데이터 원본에서 검색 한 후 메모리에서 데이터를 조작 하기 위한 세 가지 선택 해야 합니다.

[Entity Framework](../data-tools/entity-data-model-tools-in-visual-studio.md) 기본 Microsoft ORM 기술 합니다. 최고급.NET 개체로 관계형 데이터에 대 한 프로그램에 사용할 수 있습니다. 새 응용 프로그램 모델을 필요한 경우 기본적으로 첫 번째 선택 이어야 합니다. 기본 ADO.NET 공급자에서 사용자 지정 지원을 해야합니다.

[LINQ to SQL](../data-tools/linq-to-sql-tools-in-visual-studio2.md) 는 이전 세대 개체 관계형 매퍼입니다. 덜 복잡 한 시나리오에 적합 하 않지만 더 이상 활성 개발 중입니다.

[데이터 집합](../data-tools/dataset-tools-in-visual-studio.md) 세 가지 모델링 기술 중 가장 오래 된 합니다. 주로 나타나는 하지 엄청난 양의 데이터를 처리 하거나 하는 복잡 한 쿼리 또는 변환을 수행 "데이터 폼" 응용 프로그램의 신속한 개발을 위한 설계 되었습니다. 데이터 집합 개체를 논리적으로 SQL 데이터베이스 개체를.NET 개체 보다 훨씬 더 유사한 DataTable 및 DataRow 개체 이루어져 있습니다. SQL 데이터 원본을 기반으로 상대적으로 간단한 응용 프로그램에 대해 데이터 집합에 적합 한 선택 될 수 있습니다.

이러한 기술 중 하나를 사용 하는 요구 사항이 있습니다. 일부 시나리오에서는 성능은 중요 하며, 경우에 특히 사용할 수 있습니다 단순히 DataReader 개체를 데이터베이스에서 읽고 목록과 같은 컬렉션 개체에 필요한 값을 복사할\<T >입니다.

## <a name="native-c"></a>네이티브 C++

C++SQL Server에 연결 하는 응용 프로그램 사용 해야 합니다 [SQL Server 용 Microsoft® ODBC Driver 13.1](https://www.microsoft.com/download/details.aspx?id=53339) 대부분의 경우에서. 서버에 연결 하는 경우 OLE DB가 필요 하 고을 사용 합니다 [SQL Server Native Client](/sql/relational-databases/native-client/sql-server-native-client)합니다. 사용 하 여 다른 데이터베이스를 액세스할 수 있습니다 [ODBC](https://docs.microsoft.com/sql/odbc/microsoft-open-database-connectivity-odbc?view=sql-server-2017) 또는 OLE DB 드라이버 직접. ODBC 현재 표준 데이터베이스 인터페이스 이지만 대부분의 데이터베이스 시스템 ODBC 인터페이스를 통해 액세스할 수 없는 사용자 지정 기능을 제공 합니다. OLE DB는 레거시 COM 데이터 액세스 기술 계속 지원 하지만 새로운 응용 프로그램에 적합 하지 않습니다. 자세한 내용은 [시각적 개체에 대 한 데이터 액세스 C++ ](/cpp/data/data-access-in-cpp)합니다.

C++REST 서비스를 사용 하는 프로그램에서 사용할 수는 [ C++ REST SDK](https://github.com/Microsoft/cpprestsdk)합니다.

C++Microsoft Azure Storage를 사용 하는 프로그램에서 사용할 수는 [Microsoft Azure Storage 클라이언트](https://www.nuget.org/packages/Microsoft.Azure.Storage.CPP)합니다.

데이터 모델링&mdash;Visual Studio에 대 한 ORM 계층을 제공 하지 않습니다 C++합니다. [ODB](https://www.codesynthesis.com/products/odb/) 되는 인기 있는 오픈 소스 ORM에 대 한 C++합니다.

데이터베이스에 연결 하는 방법에 대 한 자세한 내용을 보려면 C++ 앱을 참조 하세요 [Visual Studio 데이터 도구에 대 한 C++ ](../data-tools/visual-studio-data-tools-for-cpp.md)합니다. 레거시 시각적 개체에 대 한 자세한 내용은 C++ 데이터 액세스 기술 참조 [데이터 액세스](/cpp/data/data-access-in-cpp)합니다.

## <a name="javascript"></a>JavaScript

[Visual Studio의 JavaScript](/scripting/javascript/javascript-language-reference) 플랫폼 간 앱을 UWP 앱, 클라우드 서비스, 웹 사이트 및 웹 앱을 빌드하기 위한 최고 수준의 언어입니다. 데이터베이스 제품 확인 하 고 원하는 JavaScript 라이브러리를 설치 하려면 Bower, Grunt, Gulp, npm 및 Visual Studio 내에서 NuGet을 사용할 수 있습니다. Sdk를 다운로드 하 여 Azure storage 및 서비스에 연결 합니다 [Azure 웹 사이트](https://azure.microsoft.com/)합니다. 표시 되는 서버 쪽 JavaScript (Node.js) ADO.NET 데이터 소스에 연결 하는 라이브러리입니다.

## <a name="python"></a>Python

설치할 [Visual Studio의 Python 지원](../python/overview-of-python-tools-for-visual-studio.md) Python 응용 프로그램을 만들려고 합니다. Azure 설명서에서 다음을 포함 하 여 데이터에 연결 하는 여러 자습서에 있습니다.

- [Django 및 azure SQL Database](/azure/app-service/app-service-web-get-started-python)
- [Django 및 Azure에서 MySQL](/azure/app-service-web/web-sites-python-ptvs-django-mysql)
- 작업할 [blob](/azure/storage/blobs/storage-quickstart-blobs-python)를 [파일](/azure/storage/files/storage-python-how-to-use-file-storage)를 [큐](/azure/storage/queues/storage-python-how-to-use-queue-storage), 및 [테이블 (Cosmo DB)](/azure/cosmos-db/table-storage-how-to-use-python)합니다.

## <a name="related-topics"></a>관련 항목

[Microsoft AI 플랫폼](https://azure.microsoft.com/overview/ai-platform/?v=17.42w)&mdash;Cortana Analytics Suite 및 사물 인터넷에 대 한 지원을 비롯 한 Microsoft 지능형 클라우드를 소개 합니다.

[Microsoft Azure Storage](/azure/storage/)&mdash;Azure blob, 테이블, 큐 및 파일을 사용 하 여 응용 프로그램을 만드는 방법과 Azure Storage에 설명 합니다.

[Azure SQL Database](/azure/sql-database/)&mdash;관계형 데이터베이스 서비스로, Azure SQL Database에 연결 하는 방법에 설명 합니다.

[SQL Server Data Tools](/sql/ssdt/download-sql-server-data-tools-ssdt)&mdash;디자인, 탐색, 테스트 및 데이터에 연결 된 응용 프로그램 및 데이터베이스의 배포를 간소화 하는 도구에 설명 합니다.

[ADO.NET](/dotnet/framework/data/adonet/index)&mdash;ADO.NET 아키텍처 및 응용 프로그램 데이터를 관리 하 고 XML 데이터 소스와 상호 작용을 ADO.NET 클래스를 사용 하는 방법에 설명 합니다.

[ADO.NET Entity Framework](https://docs.microsoft.com/ef/ef6/)&mdash;대신 개념적 모델을 관계형 데이터베이스에 대해 직접 프로그래밍할 수 있는 데이터 응용 프로그램을 만드는 방법을 설명 합니다.

[WCF Data Services 4.5](/dotnet/framework/data/wcf/index)&mdash;사용 하는 방법에 설명 합니다 [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] 구현 하는 웹 또는 인트라넷용 데이터 서비스를 배포 하는 [Open Data Protocol (OData)](https://www.odata.org/)합니다.

[Office 솔루션의 데이터](../vsto/data-in-office-solutions.md)&mdash;Office 솔루션에서 데이터가 작동 하는 방법을 설명 하는 항목에 대 한 링크를 포함 합니다. 스키마 지향 프로그래밍, 데이터 캐싱 및 서버 쪽 데이터 액세스에 대 한 정보가 포함 됩니다.

[LINQ (Language-Integrated Query)](/dotnet/csharp/linq/)&mdash;C# 및 Visual Basic 및 관계형 데이터베이스, XML 문서, 데이터 집합 및 메모리 내 컬렉션을 쿼리 하기 위한 일반적인 모델에 기본 제공 쿼리 기능을 설명 합니다.

[Visual Studio의 XML 도구](../xml-tools/xml-tools-in-visual-studio.md)&mdash;XML 데이터를 디버깅 XSLT.NET XML 기능을 사용 하 여 작업 및 XML 쿼리 아키텍처에 설명 합니다.

[XML 문서 및 데이터](/dotnet/standard/data/xml/index)&mdash;포괄적이 고 통합 된 XML 문서 및.NET의 데이터를 사용 하는 클래스 집합에 대해 간략하게 설명 합니다.
