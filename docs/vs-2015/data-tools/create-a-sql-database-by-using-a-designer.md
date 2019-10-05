---
title: 디자이너를 사용 하 여 SQL database 만들기 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- SQL Server Express
- local data
- LocalDB
- SQLEXPRESS
- data [Visual Studio], Local data
- SQL Express
- data [Visual Studio], walkthroughs
- databases, creating
- database files, creating
ms.assetid: 99c2b06f-47aa-414e-8057-a3453712fd23
caps.latest.revision: 54
author: gewarren
ms.author: gewarren
manager: jillfra
robots: noindex,nofollow
ms.openlocfilehash: f816095992379748b6d1888b5df54dc5433a8306
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436963"
---
# <a name="create-a-sql-database-by-using-a-designer"></a>디자이너를 사용 하 여 SQL database 만들기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

테이블 추가 및 만들기 및 SQL Server Express LocalDB의 로컬 데이터베이스 파일을 업데이트 하려면 Visual Studio를 사용 하 여 열 정의와 같은 기본 작업을 탐색할 수 있습니다. 이 연습을 마친 후 로컬 데이터베이스를 사용하여 고급 기능을 알아보고 다른 연습을 미리 준비할 수 있습니다.  
  
 SQL Server Management Studio (별도 다운로드) 또는에서 TRANSACT-SQL 문을 사용 하 여 데이터베이스를 만들 수도 있습니다는 **SQL Server 개체 탐색기** Visual Studio의 도구 창입니다.  
  
 이 연습에서는 다음 작업을 수행하는 방법을 알아봅니다.  
  
- [프로젝트를 만들고 로컬 데이터베이스 파일](../data-tools/create-a-sql-database-by-using-a-designer.md#BKMK_CreateNewSQLDB)  
  
- [테이블, 열, 기본 키 및 외래 키 만들기](../data-tools/create-a-sql-database-by-using-a-designer.md#BKMK_CreateNewTbls)  
  
- [데이터로 테이블 채우기](../data-tools/create-a-sql-database-by-using-a-designer.md#BKMK_Populating)  
  
## <a name="prerequisites"></a>전제 조건  
 이 연습을 완료 하려면 SQL Server Data Tools를 설치 했는지를 확인 합니다. 에 **뷰** 표시 메뉴 **SQL Server 개체 탐색기**합니다. 이 없으면 이동할 **프로그램 추가 / 제거**, 클릭 **Visual Studio 2015**를 선택 **변경**, 상자 옆에 선택 및 **SQL Server Data Tools**.  
  
## <a name="BKMK_CreateNewSQLDB"></a> 프로젝트를 만들고 로컬 데이터베이스 파일  
  
#### <a name="to-create-a-project-and-a-database-file"></a>프로젝트 및 데이터베이스 파일을 만들려면  
  
1. 라는 Windows Forms 프로젝트를 만듭니다 `SampleDatabaseWalkthrough`합니다.  
  
2. 메뉴 모음에서 선택 **프로젝트** > **새 항목 추가**합니다.  
  
3. 선택한 항목 템플릿 목록에서 아래로 스크롤하여 **서비스 기반 데이터베이스**합니다.  
  
    ![항목 템플릿 대화 상자](../data-tools/media/raddata-vsitemtemplates.png "raddata VSItemTemplates")  
  
4. 데이터베이스 이름을 **SampleDatabase**를 선택한 후 합니다 **추가** 단추입니다.  
  
5. 경우는 **데이터 원본** 창이 열려 있지 않으면, Shift + Alt + D 키를 선택 하 여 또는 메뉴 모음을 선택 하면에서 열어서 **뷰** > **기타 Windows**  >  **데이터 원본**합니다.  
  
6. 에 **데이터 원본** 창에서 합니다 **새 데이터 소스 추가** 링크 합니다.  
  
7. **데이터 소스 구성 마법사**를 선택 합니다 **다음** 단추는 기본 설정을 적용 하 고 선택한를 네 번을 **마침** 단추.  
  
   데이터베이스의 속성 창을 열어 연결 문자열 및 기본 .mdf 파일 위치를 볼 수 있습니다. 데이터베이스 파일이 프로젝트 폴더에 표시 됩니다.  
  
- Visual Studio에서 선택 **뷰** > **SQL Server 개체 탐색기** 창이 열려 있지 않은 경우. 확장 하 여 속성 창을 엽니다는 **데이터 연결** 노드, SampleDatabase.mdf에 대 한 바로 가기 메뉴를 열고 및 선택한 다음 **속성**합니다.  
  
- 선택할 수 있습니다 **뷰** > **서버 탐색기**창이 아직 열려 있지 않은 경우. 확장 하 여 속성 창을 엽니다는 **데이터 연결** 노드. SampleDatabase.mdf에 대 한 바로 가기 메뉴를 열고 선택한 **속성**합니다.  
  
## <a name="BKMK_CreateNewTbls"></a> 테이블, 열, 기본 키 및 외래 키 만들기  
 이 단원에서는 몇 가지 테이블과 각 테이블의 기본 키 그리고 몇 행의 샘플 데이터를 만들어야 합니다. 다음 연습에서는 애플리케이션에서 이 정보를 표시하는 방법을 배웁니다. 또한 외래 키를 만들어 한 테이블의 레코드가 다른 테이블의 레코드에 해당하는 방식을 지정할 수 있습니다.  
  
#### <a name="to-create-the-customers-table"></a>Customers 테이블을 만들려면  
  
1. **서버 탐색기** 또는 **SQL Server 개체 탐색기**를 확장 합니다 **데이터 연결** 노드를 펼친 다음는 **SampleDatabase.mdf**노드.  
  
2. 바로 가기 메뉴를 열고 **테이블**를 선택한 후 **새 테이블 추가**합니다.  
  
     **테이블 디자이너**가 열리고 사용자가 만드는 테이블의 단일 열을 나타내는 한 개의 기본 행이 포함된 표가 표시됩니다. 표에 행을 추가하여 테이블에 열을 추가합니다.  
  
3. 표에서 다음 각 항목에 대한 행을 추가합니다.  
  
    |열 이름|데이터 형식|null 허용|  
    |-----------------|---------------|-----------------|  
    |`CustomerID`|`nchar(5)`|False(선택 취소)|  
    |`CompanyName`|`nvarchar(50)`|False(선택 취소)|  
    |`ContactName`|`nvarchar (50)`|True(선택)|  
    |`Phone`|`nvarchar (24)`|True(선택)|  
  
4. 바로 가기 메뉴를 열고 합니다 `CustomerID` 행을 선택한 후 **기본 키 설정**합니다.  
  
5. 기본 행에 대 한 바로 가기 메뉴를 열고 선택한 **삭제**합니다.  
  
6. 다음 샘플과 일치하도록 스크립트 창에서 첫 번째 줄을 업데이트하여 Customers 테이블 이름을 지정합니다.  
  
    ```  
    CREATE TABLE [dbo].[Customers]  
    ```  
  
     다음과 같이 표시되어야 합니다.  
  
     ![테이블 디자이너](../data-tools/media/raddata-table-designer.png "raddata 테이블 디자이너")  
  
7. 왼쪽 위 모서리에는 **테이블 디자이너**를 선택 합니다 **업데이트** 단추입니다.  
  
8. 에 **데이터베이스 업데이트 미리 보기** 대화 상자를 선택 합니다 **데이터베이스 업데이트** 단추입니다.  
  
     변경 내용이 로컬 데이터베이스 파일에 저장됩니다.  
  
#### <a name="to-create-the-orders-table"></a>Orders 테이블을 만들려면  
  
1. 다른 테이블을 추가한 다음, 다음 표의 각 항목에 대한 행을 추가합니다.  
  
    |열 이름|데이터 형식|null 허용|  
    |-----------------|---------------|-----------------|  
    |`OrderID`|`int`|False(선택 취소)|  
    |`CustomerID`|`nchar(5)`|False(선택 취소)|  
    |`OrderDate`|`datetime`|True(선택)|  
    |`OrderQuantity`|`int`|True(선택)|  
  
2. 설정할 **OrderID** 기본 키와 기본 행을 한 다음 삭제 합니다.  
  
3. 다음 샘플과 일치하도록 스크립트 창에서 첫 번째 줄을 업데이트하여 Orders 테이블 이름을 지정합니다.  
  
    ```  
    CREATE TABLE [dbo].[Orders]  
    ```  
  
4. 왼쪽 위 모서리에는 **테이블 디자이너**를 선택 합니다 **업데이트** 단추입니다.  
  
5. 에 **데이터베이스 업데이트 미리 보기** 대화 상자를 선택 합니다 **데이터베이스 업데이트** 단추입니다.  
  
     변경 내용이 로컬 데이터베이스 파일에 저장됩니다.  
  
#### <a name="to-create-a-foreign-key"></a>외래 키를 만들려면  
  
1. 그리드의 오른쪽에 컨텍스트 창에서 바로 가기 메뉴를 열고 **외래 키**를 선택한 후 **새 외래 키 추가**다음 그림과 같이 합니다.  
  
     ![테이블 디자이너에서 외래 키를 추가](../data-tools/media/foreignkey.png "ForeignKey")  
  
2. 표시 되는 텍스트 상자에서 바꿉니다 **ToTable** 사용 하 여 `Customers`입니다.  
  
3. T-SQL 창에서 마지막 줄 다음 샘플과 일치 하도록 업데이트 합니다.  
  
    ```  
    CONSTRAINT [FK_Orders_Customers] FOREIGN KEY ([CustomerID]) REFERENCES [Customers]([CustomerID])  
    ```  
  
4. 왼쪽 위 모서리에는 **테이블 디자이너**를 선택 합니다 **업데이트** 단추입니다.  
  
5. 에 **데이터베이스 업데이트 미리 보기** 대화 상자를 선택 합니다 **데이터베이스 업데이트** 단추입니다.  
  
     변경 내용이 로컬 데이터베이스 파일에 저장됩니다.  
  
## <a name="BKMK_Populating"></a> 데이터로 테이블 채우기  
  
#### <a name="to-populate-the-tables-with-data"></a>테이블을 데이터로 채우려면  
  
1. **서버 탐색기** 하거나 **SQL Server 개체 탐색기**, 샘플 데이터베이스에 대 한 노드를 확장 합니다.  
  
2. 에 대 한 바로 가기 메뉴를 열고를 **테이블** 노드를 선택 **새로 고침**를 차례로 확장 하 고는 **테이블** 노드.  
  
3. Customers 테이블에 대 한 바로 가기 메뉴를 열고 선택한 **테이블 데이터 표시**합니다.  
  
4. 세 명 이상의 고객에 대해 원하는 모든 데이터를 추가합니다.  
  
     고객 ID를 5자로 지정할 수 있지만 나중에 이 절차에서 사용할 수 있도록 기억하기 쉬운 1자 정도를 선택하면 됩니다.  
  
5. Orders 테이블에 대 한 바로 가기 메뉴를 열고 선택한 **테이블 데이터 표시**합니다.  
  
6. 세 개 이상의 주문에 대한 데이터를 추가합니다.  
  
    > [!IMPORTANT]
    > 모든 주문 ID와 주문 수량이 정수이고 각 고객 ID가 Customers 테이블의 CustomerID 열에 지정한 값과 일치하는지 확인합니다.  
  
7. 메뉴 모음에서 선택 **파일** > **모두 저장**합니다.  
  
8. 메뉴 모음에서 선택 **파일** > **솔루션 닫기**합니다.  
  
    > [!NOTE]
    > 가장 좋은 방법은 만든 데이터베이스 파일을 복사한 후 복사본을 다른 위치에 붙여 넣거나 복사본에 다른 이름을 지정하여 데이터베이스 파일을 백업하는 것입니다.  
  
## <a name="next-steps"></a>다음 단계  
 몇 가지 샘플 데이터를 사용 하 여 로컬 데이터베이스 파일을 설정 했으므로 데이터베이스 작업을 보여 주는 연습을 완료할 수 있습니다.
