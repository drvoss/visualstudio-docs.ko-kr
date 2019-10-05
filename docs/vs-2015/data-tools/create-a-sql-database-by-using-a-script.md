---
title: 스크립트를 사용 하 여 SQL database 만들기 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
ms.assetid: 36f913c0-f5a7-4831-83a0-baba721ac95c
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7c0dc7b406f7e04aaa9848e2f5dcb96f17430f6d
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436953"
---
# <a name="create-a-sql-database-by-using-a-script"></a>스크립트를 사용 하 여 SQL database 만들기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 연습에서는 샘플 코드를 포함 하는 작은 데이터베이스를 만들려면 Visual Studio 사용 [ADO.NET을 사용 하 여 간단한 데이터 응용 프로그램을 만들](../data-tools/create-a-simple-data-application-by-using-adonet.md)합니다.  
  
 **항목 내용**  
  
- [데이터베이스 스키마가 포함 된 스크립트 만들기](../data-tools/create-a-sql-database-by-using-a-script.md#CreateScript)  
  
- [데이터베이스 프로젝트를 만들고 스키마 가져오기](../data-tools/create-a-sql-database-by-using-a-script.md#CreateProject)  
  
- [데이터베이스 배포](../data-tools/create-a-sql-database-by-using-a-script.md#DeployDatabase)  
  
## <a name="prerequisites"></a>전제 조건  
 이 연습을 완료 하려면 SQL Server Express LocalDB 또는 다른 SQL database에 설치 해야 합니다.  
  
## <a name="CreateScript"></a> 데이터베이스 스키마가 포함 된 스크립트 만들기  
  
#### <a name="to-create-a-script-from-which-you-can-import-a-schema"></a>스키마를 가져올 수 있는 스크립트를 만들려면  
  
1. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], 메뉴 모음에서 선택 **파일** > **New** > **파일**합니다.  
  
     합니다 **새 파일** 대화 상자가 나타납니다.  
  
2. 에 **범주** 목록에서 **일반**합니다.  
  
3. 에 **템플릿** 목록에서 **Sql 파일**를 선택한 후는 **열기** 단추.  
  
     TRANSACT-SQL 편집기가 열립니다.  
  
4. 다음 TRANSACT-SQL 코드를 복사 하 고 TRANSACT-SQL 편집기에 붙여 넣습니다.  
  
    ```  
    PRINT N'Creating Sales...';  
    GO  
    CREATE SCHEMA [Sales]  
        AUTHORIZATION [dbo];  
    GO  
    PRINT N'Creating Sales.Customer...';  
    GO  
    CREATE TABLE [Sales].[Customer] (  
        [CustomerID]   INT           IDENTITY (1, 1) NOT NULL,  
        [CustomerName] NVARCHAR (40) NOT NULL,  
        [YTDOrders]    INT           NOT NULL,  
        [YTDSales]     INT           NOT NULL  
    );  
    GO  
    PRINT N'Creating Sales.Orders...';  
    GO  
    CREATE TABLE [Sales].[Orders] (  
        [CustomerID] INT      NOT NULL,  
        [OrderID]    INT      IDENTITY (1, 1) NOT NULL,  
        [OrderDate]  DATETIME NOT NULL,  
        [FilledDate] DATETIME NULL,  
        [Status]     CHAR (1) NOT NULL,  
        [Amount]     INT      NOT NULL  
    );  
    GO  
    PRINT N'Creating Sales.Def_Customer_YTDOrders...';  
    GO  
    ALTER TABLE [Sales].[Customer]  
        ADD CONSTRAINT [Def_Customer_YTDOrders] DEFAULT 0 FOR [YTDOrders];  
    GO  
    PRINT N'Creating Sales.Def_Customer_YTDSales...';  
    GO  
    ALTER TABLE [Sales].[Customer]  
        ADD CONSTRAINT [Def_Customer_YTDSales] DEFAULT 0 FOR [YTDSales];  
    GO  
    PRINT N'Creating Sales.Def_Orders_OrderDate...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [Def_Orders_OrderDate] DEFAULT GetDate() FOR [OrderDate];  
    GO  
    PRINT N'Creating Sales.Def_Orders_Status...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [Def_Orders_Status] DEFAULT 'O' FOR [Status];  
    GO  
    PRINT N'Creating Sales.PK_Customer_CustID...';  
    GO  
    ALTER TABLE [Sales].[Customer]  
        ADD CONSTRAINT [PK_Customer_CustID] PRIMARY KEY CLUSTERED ([CustomerID] ASC) WITH (ALLOW_PAGE_LOCKS = ON, ALLOW_ROW_LOCKS = ON, PAD_INDEX = OFF, IGNORE_DUP_KEY = OFF, STATISTICS_NORECOMPUTE = OFF);  
    GO  
    PRINT N'Creating Sales.PK_Orders_OrderID...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [PK_Orders_OrderID] PRIMARY KEY CLUSTERED ([OrderID] ASC) WITH (ALLOW_PAGE_LOCKS = ON, ALLOW_ROW_LOCKS = ON, PAD_INDEX = OFF, IGNORE_DUP_KEY = OFF, STATISTICS_NORECOMPUTE = OFF);  
    GO  
    PRINT N'Creating Sales.FK_Orders_Customer_CustID...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [FK_Orders_Customer_CustID] FOREIGN KEY ([CustomerID]) REFERENCES [Sales].[Customer] ([CustomerID]) ON DELETE NO ACTION ON UPDATE NO ACTION;  
    GO  
    PRINT N'Creating Sales.CK_Orders_FilledDate...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [CK_Orders_FilledDate] CHECK ((FilledDate >= OrderDate) AND (FilledDate < '01/01/2020'));  
    GO  
    PRINT N'Creating Sales.CK_Orders_OrderDate...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [CK_Orders_OrderDate] CHECK ((OrderDate > '01/01/2005') and (OrderDate < '01/01/2020'));  
    GO  
    PRINT N'Creating Sales.uspCancelOrder...';  
    GO  
    CREATE PROCEDURE [Sales].[uspCancelOrder]  
    @OrderID INT  
    AS  
    BEGIN  
    DECLARE @Delta INT, @CustomerID INT  
    BEGIN TRANSACTION  
        SELECT @Delta = [Amount], @CustomerID = [CustomerID]  
         FROM [Sales].[Orders] WHERE [OrderID] = @OrderID;  
  
    UPDATE [Sales].[Orders]  
       SET [Status] = 'X'  
    WHERE [OrderID] = @OrderID;  
  
    UPDATE [Sales].[Customer]  
       SET  
       YTDOrders = YTDOrders - @Delta  
        WHERE [CustomerID] = @CustomerID  
    COMMIT TRANSACTION  
    END  
    GO  
    PRINT N'Creating Sales.uspFillOrder...';  
    GO  
    CREATE PROCEDURE [Sales].[uspFillOrder]  
    @OrderID INT, @FilledDate DATETIME  
    AS  
    BEGIN  
    DECLARE @Delta INT, @CustomerID INT  
    BEGIN TRANSACTION  
        SELECT @Delta = [Amount], @CustomerID = [CustomerID]  
         FROM [Sales].[Orders] WHERE [OrderID] = @OrderID;  
  
    UPDATE [Sales].[Orders]  
       SET [Status] = 'F',  
           [FilledDate] = @FilledDate  
    WHERE [OrderID] = @OrderID;  
  
    UPDATE [Sales].[Customer]  
       SET  
       YTDSales = YTDSales + @Delta  
        WHERE [CustomerID] = @CustomerID  
    COMMIT TRANSACTION  
    END  
    GO  
    PRINT N'Creating Sales.uspNewCustomer...';  
    GO  
    CREATE PROCEDURE [Sales].[uspNewCustomer]  
    @CustomerName NVARCHAR (40),  
    @CustomerID INT OUTPUT  
    AS  
    BEGIN  
    INSERT INTO [Sales].[Customer] (CustomerName) VALUES (@CustomerName);  
    SET @CustomerID = SCOPE_IDENTITY();  
    RETURN @@ERROR  
    END  
    GO  
    PRINT N'Creating Sales.uspPlaceNewOrder...';  
    GO  
    CREATE PROCEDURE [Sales].[uspPlaceNewOrder]  
    @CustomerID INT, @Amount INT, @OrderDate DATETIME, @Status CHAR (1)='O'  
    AS  
    BEGIN  
    DECLARE @RC INT  
    BEGIN TRANSACTION  
    INSERT INTO [Sales].[Orders] (CustomerID, OrderDate, FilledDate, Status, Amount)   
         VALUES (@CustomerID, @OrderDate, NULL, @Status, @Amount)  
    SELECT @RC = SCOPE_IDENTITY();  
    UPDATE [Sales].[Customer]  
       SET  
       YTDOrders = YTDOrders + @Amount  
        WHERE [CustomerID] = @CustomerID  
    COMMIT TRANSACTION  
    RETURN @RC  
    END  
    GO  
    CREATE PROCEDURE [Sales].[uspShowOrderDetails]  
    @CustomerID INT=0  
    AS  
    BEGIN  
    SELECT [C].[CustomerName], CONVERT(date, [O].[OrderDate]), CONVERT(date, [O].[FilledDate]), [O].[Status], [O].[Amount]  
      FROM [Sales].[Customer] AS C  
      INNER JOIN [Sales].[Orders] AS O  
         ON [O].[CustomerID] = [C].[CustomerID]  
      WHERE [C].[CustomerID] = @CustomerID  
    END  
    GO  
    ```  
  
5. 메뉴 모음에서 선택 **파일** > **이름으로 SqlQuery_1.sql 저장**합니다.  
  
     합니다 **다른 이름으로 파일 저장** 대화 상자가 나타납니다.  
  
6. 에 **파일 이름** 상자에 입력 합니다 `SampleImportScript.sql`, 하에서는 파일을 저장 하 고 선택한 위치를 확인 합니다 **저장** 단추입니다.  
  
7. 메뉴 모음에서 선택 **파일** > **솔루션 닫기**합니다.  
  
     다음으로, 데이터베이스 프로젝트를 만들고 사용자가 만든 스크립트에서 스키마를 가져와야 합니다.  
  
## <a name="CreateProject"></a> 데이터베이스 프로젝트를 만들고 스키마 가져오기  
  
#### <a name="to-create-a-database-project"></a>데이터베이스 프로젝트를 만들려면  
  
1. 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 선택합니다.  
  
     **새 프로젝트** 대화 상자가 나타납니다.  
  
2. 아래 **설치 됨**, 확장를 **템플릿** 노드를 확장를 **다른 언어** 노드를 선택 합니다 **SQL Server** 범주를 차례로 선택 된 **SQL Server 데이터베이스 프로젝트** 템플릿.  
  
    > [!NOTE]
    > 합니다 **다른 언어** 노드는 Visual Studio의 모든 설치의 경우에 표시 되지 않습니다.  
  
3. 에 **이름을** 상자에 입력 `Small Database`합니다.  
  
4. 선택 된 **솔루션용 디렉터리 만들기** 확인란이 아직 선택 하지 않은 경우 선택 합니다.  
  
5. 선택을 취소 합니다 **소스 제어에 추가** 확인란 선택을 취소 한 다음 선택 되어 있지 않으면 합니다 **확인** 단추입니다.  
  
     데이터베이스 프로젝트가 만들어지고 나타나는 **솔루션 탐색기**합니다.  
  
     그런 다음 스크립트에서 데이터베이스 스키마를 가져옵니다.  
  
#### <a name="to-import-a-database-schema-from-a-script"></a>스크립트에서 데이터베이스 스키마를 가져오려면  
  
1. 메뉴 모음에서 선택 **프로젝트** > **가져오기** > **스크립트**합니다.  
  
2. 에 **시작** 페이지에서 텍스트를 검토 하 고 다음을 선택 합니다 **다음** 단추입니다.  
  
3. 선택 합니다 **단일 파일** 옵션 단추를 선택한 다음 선택 합니다 **찾아보기** 단추.  
  
     합니다 **SQL 스크립트 가져오기** 대화 상자가 나타납니다.  
  
4. SampleImportScript.sql 파일을 저장 한 폴더를 열고 파일을 선택한 다음 선택 합니다 **열려** 단추입니다.  
  
5. 선택 된 **완료** 를 닫으려면 단추를 합니다 **SQL 스크립트 가져오기** 대화 상자.  
  
     스크립트를 가져오고 스크립트를 정의 하는 개체가 데이터베이스 프로젝트에 추가 됩니다.  
  
6. 요약 내용을 검토 한 다음 클릭 합니다 **완료** 를 닫으려면 단추를 합니다 **SQL 스크립트 파일 가져오기** 대화 상자.  
  
7. **솔루션 탐색기**, Sales, Scripts 및 Security 확장 프로젝트의 폴더 및.sql 파일에 포함 되어 있는지 확인 합니다.  
  
8. **SQL Server 개체 탐색기**, 데이터베이스가 표시 되는지 확인 합니다 **프로젝트** 노드.  
  
     이 시점에서 데이터베이스 테이블 및 저장된 프로시저와 같은 시스템 개체만 포함합니다. 데이터베이스를 배포 하면 사용자 테이블 및 스크립트를 정의 하는 저장된 프로시저에 포함 됩니다.  
  
## <a name="DeployDatabase"></a> 데이터베이스 배포  
 누를 때 합니다 **F5** 키 배포 (또는 게시) 기본적으로 LocalDB 데이터베이스에 데이터베이스입니다. 프로젝트 속성 페이지를 열어 데이터베이스를 다른 위치에 배포할 수 있습니다 선택 하는 **디버그** 탭을 클릭 한 다음 연결 문자열을 변경 합니다.
