---
title: 데이터 액세스
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
f1_keywords:
- "80025080"
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio]
- data access [Visual Studio]
- data [C#]
- ADO.NET, data access
ms.assetid: 9812a6d5-23d2-4427-8b98-70a2abfec3bc
caps.latest.revision: 103
author: gewarren
ms.author: gewarren
manager: jillfra
robots: noindex,nofollow
ms.openlocfilehash: 7f13a97adbec1da1bd0f279e14cf510532b9c62f
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65688631"
---
# <a name="accessing-data-in-visual-studio"></a>Visual Studio에서 데이터 액세스
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio에서 거의 모든 데이터베이스 제품 또는 서비스의 형식으로 어디서 나 데이터에 연결 하는 응용 프로그램을 만들 수 있습니다-공용, 개인 또는 하이브리드 클라우드 또는 로컬 영역 네트워크에 로컬 컴퓨터에서.

 JavaScript, Python, PHP, Ruby에서 응용 프로그램 또는 C++를 가져오기 라이브러리 및 코드를 작성 하 여 다른 작업을 수행 하기와 같은 데이터에 연결 합니다. .NET 응용 프로그램에 대 한 Visual Studio 데이터 원본 탐색, 개체 모델을 저장 하 고 메모리에서 데이터를 조작 하 고, 사용자 인터페이스에 데이터 바인딩 만들기에 사용할 수 있는 도구를 제공 합니다.     Microsoft Azure는 Azure Storage에 연결 하기 위한.NET, Java, Node.js, PHP, Python, Ruby 및 모바일 앱 및 Visual Studio의 도구에 대 한 Sdk를 제공 합니다.

 다음 목록에는 Visual Studio에서 사용할 수 있는 여러 데이터베이스 및 저장소 시스템의 일부에 지나지 보여 줍니다. 합니다 [Microsoft Azure](https://azure.microsoft.com/) 제품은 모든 프로 비전 및 관리의 기본 데이터 저장소를 포함 하는 데이터 서비스입니다.  [Azure Tools for Visual Studio](https://www.visualstudio.com/features/azure-tools-vs.aspx) Visual Studio에서 직접 Azure 데이터 저장소를 사용 하 여 작업할 수 있도록 하는 선택적 구성 요소입니다. 대부분의 다른 SQL 및 NoSQL 데이터베이스 제품 여기에 나와 있는 로컬 컴퓨터에서 로컬 네트워크에서 또는 Microsoft Azure 가상 머신에서 호스트할 수 있습니다. 이 시나리오에서는 자체 데이터베이스를 관리 담당 합니다.

 **Microsoft Azure**

||||
|-|-|-|
|SQL Database|DocumentDB|Storage (blob, 테이블, 큐, 파일)|
|SQL Data Warehouse|SQL Server Stretch Database|StorSimple|

 기타...

 **SQL**

||||
|-|-|-|
|SQL Server 2005 – 2016 Express LocalDB 등|Firebird|MariaDB|
|MySQL|Oracle|PostgreSQL|
|SQLite|||

 기타...

 **NoSQL**

||||
|-|-|-|
|Apache Cassandra|CouchDB|MongoDB|
|NDatabase|OrientDB|RavenDB|
|VelocityDB|||

 기타...

 여러 데이터베이스 공급 업체와 타사 NuGet 패키지에서 Visual Studio 통합을 지원합니다. Nuget.org 또는 Visual Studio에서 NuGet 패키지 관리자를 통해 제공 되는 서비스를 탐색할 수 있습니다 (**도구가** > **NuGet 패키지 관리자** > **NuGet 관리 솔루션에 대 한 패키지**). 다른 데이터베이스 제품 확장으로 Visual Studio와 통합 합니다.   로 이동 하 여 이러한 제품은 Visual Studio Gallery에서 찾아볼 수 있습니다 **도구가** > **확장 및 업데이트** 을 선택한 다음 **Online** 왼쪽 대화 상자의 창입니다.  자세한 내용은 [데이터베이스 시스템, 도구 및 샘플 설치](../data-tools/installing-database-systems-tools-and-samples.md)합니다.

> [!NOTE]
> 2016 년 4 월 12 일에 SQL Server 2005 지원 연장이 종료 되었습니다.   이 날짜 이후에 SQL Server 2005를 사용 하려면 Visual Studio 2015 이상에서 데이터 도구를 계속 하지 않을 수도가 있습니다. 자세한 내용은 참조는 [SQL Server 2005 지원 종료 알림](https://www.microsoft.com/sql-server/sql-server-2005)합니다.

### <a name="net-languages"></a>.NET 언어
 .NET Core를 포함 하 여 모든.NET 데이터 액세스, ADO.NET, 모든 종류의 관계형 및 비관계형 데이터 원본에 액세스 하기 위한 인터페이스를 정의 하는 클래스 집합을 기반으로 합니다. Visual Studio에 여러 도구 및 데이터베이스에 연결할 수 있도록 ADO.NET을 사용 하는 디자이너에 데이터를 조작 하 고 사용자에 게 데이터를 표시 합니다. 이 섹션의에서 설명서에서는 이러한 도구를 사용 하는 방법을 설명 합니다. ADO.NET 명령 개체에 대해 직접 프로그래밍할 수 있습니다. ADO.NET Api를 직접 호출 하는 방법에 대 한 자세한 내용은 참조 하세요. [ADO.NET](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx) MSDN 라이브러리에서.

 특히 ASP.NET과 관련 된 데이터 액세스 설명서를 참조 하세요 [데이터로 작업](http://www.asp.net/web-forms/overview/presenting-and-managing-data) ASP.NET 사이트의. ASP.NET MVC로 Entity Framework를 사용 하 여에 대 한 자습서를 참조 하세요 [Getting Started with Entity Framework 6 Code First MVC 5를 사용 하 여](http://www.asp.net/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application)입니다.

 UWP (유니버설 Windows 플랫폼) 앱에서 C# 또는 Visual Basic Microsoft Azure SDK for.NET을 사용 하 여 Azure Storage 및 다른 Azure 서비스에 액세스할 수 있습니다. Windows.Web.HttpClient 클래스 RESTful 서비스와 통신할 수 있도록 합니다. 자세한 내용은 [Windows.Web.Http를 사용 하 여 HTTP 서버에 연결 하는 방법을](https://msdn.microsoft.com/library/windows/apps/dn469430.aspx)합니다.

 로컬 컴퓨터의 데이터 저장소에 대 한 앱과 동일한 프로세스에서 실행 되는 SQLite를 사용 하는 것이 좋습니다. 개체-관계형 매핑 (ORM) 계층을 필요한 경우에 Entity Framework를 사용할 수 있습니다. 자세한 내용은 [데이터 액세스](https://msdn.microsoft.com/windows/uwp/data-access/index) Windows 개발자 센터에서.

 Azure 서비스에 연결 하는 경우 다운로드 해야 최신 [Azure SDK 도구](https://azure.microsoft.com/downloads/)합니다.

#### <a name="data-providers"></a>데이터 공급자
 ADO.NET에서 수 있으려면 데이터베이스에 대 한 사용자 지정 권한이 있어야 합니다 *ADO.NET 데이터 공급자* 하거나 다른 ODBC 또는 OLE DB 인터페이스를 노출 해야 합니다. Microsoft에서 제공 된 [ADO.NET 데이터 공급자 목록은](https://msdn.microsoft.com/data/dd363565) ODBC 및 OLE DB 공급자 뿐만 아니라 SQL Server 제품에 대 한 합니다.

#### <a name="data-modeling"></a>데이터 모델링
 .NET에서는 모델링 및 데이터 원본에서 검색 한 후 메모리에서 데이터를 조작 하기 위한 세 가지 선택 해야 합니다.

 엔터티 프레임 워크 기본 Microsoft ORM 기술입니다. 최고급.NET 개체로 관계형 데이터에 대 한 프로그램에 사용할 수 있습니다. 새 응용 프로그램 모델을 필요한 경우 기본적으로 첫 번째 선택 이어야 합니다. 기본 ADO.NET 공급자에서 사용자 지정 지원을 해야합니다.

 LINQ to SQL 이전 세대 개체 관계형 매퍼입니다. 덜 복잡 한 시나리오에 적합 하 않지만 더 이상 활성 개발 중입니다.

 데이터 집합의 세 가지 모델링 기술 중 가장 오래 된 합니다. 주로 나타나는 하지 엄청난 양의 데이터를 처리 하거나 하는 복잡 한 쿼리 또는 변환을 수행 "데이터 폼" 응용 프로그램의 신속한 개발을 위한 설계 되었습니다. 데이터 집합 개체를 논리적으로 SQL 데이터베이스 개체를.NET 개체 보다 훨씬 더 유사한 DataTable 및 DataRow 개체 이루어져 있습니다. SQL 데이터 원본을 기반으로 상대적으로 간단한 응용 프로그램에 대해 데이터 집합에 적합 한 선택 될 수 있습니다.

 이러한 기술 중 하나를 사용 하는 요구 사항이 있습니다. 일부 시나리오에서는 성능은 중요 하며, 경우에 특히 사용할 수 있습니다 단순히 DataReader 개체를 데이터베이스에서 읽고 목록과 같은 컬렉션 개체에 필요한 값을 복사할\<T >입니다.

### <a name="native-c"></a>네이티브 C++
 C++SQL Server에 연결 하는 응용 프로그램 사용 해야 합니다 [SQL Server Native Client](https://msdn.microsoft.com/sqlserver/aa937733.aspx)합니다. 사용 하 여 다른 데이터베이스를 액세스할 수 있습니다 [ODBC](https://msdn.microsoft.com/library/ms710252\(v=vs.85\).aspx) 또는 OLE DB 드라이버 직접. ODBC 현재 표준 데이터베이스 인터페이스 이지만 대부분의 데이터베이스 시스템 ODBC 인터페이스를 통해 액세스할 수 없는 사용자 지정 기능을 제공 합니다.  OLE DB는 레거시 COM 데이터 액세스 기술 계속 지원 하지만 새로운 응용 프로그램에 적합 하지 않습니다.  자세한 내용은 [데이터 액세스](https://msdn.microsoft.com/library/a9455752-39c4-4457-b14e-197772d3df0b)합니다.

 C++REST 서비스를 사용 하는 프로그램에서 사용할 수는 [ C++ REST SDK](https://github.com/Microsoft/cpprestsdk)합니다.

 C++Microsoft Azure Storage를 사용 하는 프로그램에서 사용할 수는 [Microsoft Azure Storage 클라이언트](http://www.nuget.org/packages/wastorage)합니다.

#### <a name="data-modeling"></a>데이터 모델링
 Visual Studio에 대 한 ORM 계층을 제공 하지 않습니다 C++입니다.  [ODB](http://www.codesynthesis.com/products/odb/) 되는 인기 있는 오픈 소스 ORM에 대 한 C++합니다.

 레거시 시각적 개체에 대 한 자세한 내용은 C++ 데이터 액세스 기술 참조 [데이터 액세스](https://msdn.microsoft.com/library/a9455752-39c4-4457-b14e-197772d3df0b)

### <a name="javascript"></a>JavaScript
 [Visual Studio의 JavaScript](https://msdn.microsoft.com/library/hh334522.aspx) 플랫폼 간 앱을 UWP 앱, 클라우드 서비스, 웹 사이트 및 웹 앱을 빌드하기 위한 최고 수준의 언어입니다. 데이터베이스 제품 확인 하 고 원하는 JavaScript 라이브러리를 설치 하려면 Bower, Grunt, Gulp, npm 및 Visual Studio 내에서 NuGet을 사용할 수 있습니다. Sdk를 다운로드 하 여 Azure storage 및 서비스에 연결 합니다 [Azure 웹 사이트](https://azure.microsoft.com/)합니다.  표시 되는 서버 쪽 JavaScript (Node.js) ADO.NET 데이터 소스에 연결 하는 라이브러리입니다.

### <a name="python"></a>Python
 설치할 [Python Tools for Visual Studio](http://microsoft.github.io/PTVS/) CPython 또는 IronPython (.NET) 응용 프로그램을 만들려면 원하는 Python 프레임 워크와 함께 합니다.  Python Tools for Visual Studio 웹 사이트에 데이터를 포함 하 여 연결에 대 한 몇 가지 자습서 [Django 및 azure SQL Database](https://github.com/Microsoft/PTVS/wiki/Django-and-SQL-Database-on-Azure)를 [Django 및 Azure에서 MySQL](https://github.com/Microsoft/PTVS/wiki/Django-and-MySQL-on-Azure) 고 [Bottle 및 MongoDB에 Azure](https://github.com/Microsoft/PTVS/wiki/Bottle-and-MongoDB-on-Azure)합니다.

## <a name="in-this-section"></a>단원 내용
 [데이터베이스 시스템, 도구 및 샘플 설치](../data-tools/installing-database-systems-tools-and-samples.md) 얻거나 데이터베이스 제품 및 Visual Studio 확장을 지 원하는 드라이버 하는 방법 및 실험 및 학습 목적에 대 한 샘플 데이터베이스를 찾을 수 있는 위치에 설명 합니다.

 [.NET 용 visual Studio 데이터 도구](https://msdn.microsoft.com/6b145922-2f00-47db-befc-bf351b4809a1) Visual Studio 도구 창을 사용 하 여 데이터 원본에 연결 하 고 데이터 집합 또는 Entity Framework 모델을 만들 사용자 인터페이스 컨트롤에 데이터 바인딩 방법에 설명 합니다.

## <a name="related-topics"></a>관련 항목
 [데이터, 장치 및 Analytics](https://msdn.microsoft.com/data-and-devices) Cortana Analytics Suite 및 사물 인터넷에 대 한 지원을 비롯 한 Microsoft 지능형 클라우드를 소개 합니다.

 [Microsoft Azure Storage](/azure/storage/) Azure blob, 테이블, 큐 및 파일을 사용 하 여 응용 프로그램을 만드는 방법과 Azure Storage에 설명 합니다.

 [Azure SQL Database](https://azure.microsoft.com/documentation/services/sql-database/) 관계형 데이터베이스 서비스로, Azure SQL Database에 연결 하는 방법에 설명 합니다.

 [SQL Server Data Tools](https://msdn.microsoft.com/library/hh272686\(v=vs.103\).aspx) 디자인, 탐색, 테스트 및 데이터에 연결 된 응용 프로그램 및 데이터베이스의 배포를 간소화 하는 도구에 설명 합니다.

 [ADO.NET](https://msdn.microsoft.com/library/5b96ed06-9759-4966-a797-a1d5f6ee50ca) ADO.NET 아키텍처 및 응용 프로그램 데이터를 관리 하 고 XML 데이터 소스와 상호 작용을 ADO.NET 클래스를 사용 하는 방법에 설명 합니다.

 [ADO.NET Entity Framework](https://msdn.microsoft.com/data/ef) 대신 개념적 모델을 관계형 데이터베이스에 대해 직접 프로그래밍할 수 있는 데이터 응용 프로그램을 만드는 방법을 설명 합니다.

 [WCF Data Services 4.5](https://msdn.microsoft.com/library/73d2bec3-7c92-4110-b905-11bb0462357a) 사용 하는 방법에 설명 합니다 [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] 구현 하는 웹 또는 인트라넷용 데이터 서비스를 배포 하는 [Open Data Protocol (OData)](http://go.microsoft.com/fwlink/?LinkID=182204)합니다.

 [Office 솔루션의 데이터](https://msdn.microsoft.com/library/8478c095-864b-4ed3-8a70-1fc19b411c6a) Office 솔루션에서 데이터가 작동 하는 방법을 설명 하는 항목에 대 한 링크를 포함 합니다. 스키마 지향 프로그래밍, 데이터 캐싱 및 서버 쪽 데이터 액세스에 대 한 정보가 포함 됩니다.

 [LINQ (Language-Integrated Query)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) 에 기본 제공 쿼리 기능을 설명 합니다 C# 및 Visual Basic 및 관계형 데이터베이스, XML 문서, 데이터 집합 및 메모리 내 컬렉션을 쿼리 하기 위한 일반적인 모델입니다.

 [Visual Studio의 XML 도구](../xml-tools/xml-tools-in-visual-studio.md) XML 데이터를 XSLT 디버깅,.NET Framework XML 기능을 사용 하 여 작업 및 XML 쿼리 아키텍처에 설명 합니다.

 [XML 문서 및 데이터](https://msdn.microsoft.com/library/e695047f-3c0f-4045-8708-5baea91cc380) 포괄적이 고 통합 된.NET Framework에서 데이터 및 XML 문서를 사용 하는 클래스 집합에 대해 간략하게 설명 합니다.
