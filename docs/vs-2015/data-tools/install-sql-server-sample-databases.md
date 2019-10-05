---
title: SQL Server 예제 데이터베이스 설치 | Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 38840167-c3f8-4cb3-8d15-8af04a0a20a1
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 056e5d1fad258d063e30cfd97e85529ff3a0c9bd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68160170"
---
# <a name="install-sql-server-sample-databases"></a>SQL Server 샘플 데이터베이스 설치
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

예제 데이터베이스는 SQL 및 LINQ 쿼리, 데이터 바인딩, Entity Framework 모델링 및 등을 사용 하 여 실험에 대 한 유용 합니다.  각 데이터베이스 제품 예제 데이터베이스 자체에 있습니다. Northwind 및 AdventureWorks는 두 가지 인기 있는 SQL Server 샘플 데이터베이스입니다.  
  
 **AdventureWorks** 현재 샘플 데이터베이스인 SQL Server 제품에 제공 합니다. .mdf 파일로 다운로드할 수 있습니다 합니다 [Codeplex의 AdventureWorks 페이지](http://msftdbprodsamples.codeplex.com/)합니다. 일반 및 간단한 (LT) 버전 가지가 데이터베이스의 사용 가능한 여기 있습니다. 대부분의 시나리오에서 LT 버전은 덜 복잡 한 이기 때문에 기본 설정입니다.  
  
 **Northwind** 몇 년 동안 사용 된 SQL Server 데이터베이스를 비교적 간단 합니다. .bak 파일로 다운로드할 수 있습니다 합니다 [CodePlex의 Northwind 데이터베이스 페이지](https://northwinddatabase.codeplex.com/)합니다. 사용 권한 문제를 방지 하려면 사용자 폴더 아래에 없는 새 폴더로 파일을 압축을 풉니다.  
  
#### <a name="to-restore-a-database-from-a-bak-file-in-visual-studio"></a>Visual Studio에서.bak 파일에서 데이터베이스를 복원 하려면  
  
1. Microsoft SQL Server 데이터베이스를 백업 하는 경우 결과.bak 파일. 데이터베이스 파일을 다시 사용할 수 있는 파일의.bak이 하도록 해야 *복원*합니다. 주 메뉴에서 선택 **뷰** > **SQL Server 개체 탐색기**합니다. 표시 되지 않으면 설치 해야 합니다. 로 이동 **Control Panel** > **프로그램 및 기능**Microsoft Visual Studio 2015를 찾아 클릭 합니다 **변경** 단추입니다. 설치 관리자 창에서 설치 된 구성 요소 목록이 표시 되 면 선택 합니다 **SQL Server 개체 탐색기** 확인란을 선택 하 고 다음 설치를 계속 합니다.  
  
2. SQL Server 개체 탐색기에서 모든 SQL Server 데이터베이스 엔진 (예를 들어, localdb)를 마우스 오른쪽 단추로 누르고**새 쿼리**합니다.  
  
     ![SQL Server 개체 탐색기 새 쿼리](../data-tools/media/raddata-sql-server-object-explorer-new-query.png "raddata SQL Server 개체 탐색기 새 쿼리")  
  
3. 먼저.bak 파일 내에서 데이터베이스 및 로그 파일의 논리적 이름입니다. 를 가져오려면 SQL 쿼리 편집기에이 쿼리를 입력 하 고 선택한 다음 녹색 **실행** 창의 맨 위에 있는 단추입니다. .Bak 파일을 가리키도록 필요에 따라 파일 경로 수정 합니다.  
  
    ```  
    RESTORE FILELISTONLY  
    FROM DISK = 'C:\nw\northwind.bak'  
    GO  
    ```  
  
     결과 창에 표시 되는 논리적 이름을 적어 둡니다.  Northwind 데이터베이스에 대 한 두 개의 논리적 이름은 Northwind 및 Northwind_log입니다.  
  
4. 이제 데이터베이스를 만들려면이 쿼리를 실행 합니다. 고유한 원본 및 대상 경로, 논리적 데이터베이스 이름 및 적절 하 게 Northwind에 대 한 실제 파일 이름을 대체 합니다. .Mdf 및.ldf 확장명을 유지 합니다.  
  
    ```  
    RESTORE DATABASE Northwind  
    FROM DISK = 'c:\nw\northwind.bak'  
    WITH MOVE 'Northwind' TO 'c:\nw\northwind.mdf',  
    MOVE 'Northwind_log' TO 'c:\nw\northwind.ldf'  
    ```  
  
5. SQL Server 개체 탐색기에서 마우스 오른쪽 단추로 클릭 합니다 **데이터베이스** 노드를 하는 Northwind 데이터베이스 노드를 표시 됩니다. 그렇지 않은 경우 마우스 오른쪽 단추로 클릭 데이터베이스 및 선택 **새 데이터베이스 추가**합니다. 이름 및 바로 전에 만든.mdf 파일의 위치를 입력 합니다.  
  
6. 데이터베이스 Visual Studio에서 데이터 원본으로 사용할 준비가 되었습니다.  
  
#### <a name="to-restore-a-database-from-a-bak-file-in-sql-server-management-studio"></a>SQL Server Management Studio의.bak 파일에서 데이터베이스를 복원 하려면  
  
1. SQL Server Management Studio 다운로드 사이트에서 다운로드 합니다.  
  
2. Ssms에서 **개체 탐색기** 창에서 마우스 오른쪽 단추로 클릭는 **데이터베이스** 노드를 선택**Restore Database**,.bak 파일의 위치를 지정 합니다.  
  
     ![데이터베이스를 복원 하는 SSMS](../data-tools/media/raddata-ssms-restore-database.png "raddata 데이터베이스를 복원 하는 SSMS")
