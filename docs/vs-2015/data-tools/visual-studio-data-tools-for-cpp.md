---
title: Visual Studio 데이터 도구에 대 한 C++ | Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 3a3849d9-1bc7-47d1-805e-1755223ccba2
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: jillfra
robots: noindex,nofollow
ms.openlocfilehash: 85978a79fc1e0110e5b13d6dc0e3198d20ac674a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68146558"
---
# <a name="visual-studio-data-tools-for-c"></a>C++용 Visual Studio 데이터 도구
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

네이티브 C++ 데이터 원본에 액세스 하는 경우에 종종 가장 빠른 성능을 제공할 수 있습니다. 그러나 데이터에 대 한 도구, C++ Visual Studio에서 응용 프로그램을.NET 응용 프로그램에 대 한 다양 하지 않습니다. 예를 들어, 데이터 원본으로 끌어서 데이터 원본 windows를 사용할 수 없습니다는 C++ 디자인 화면입니다. 개체-관계형 레이어를 필요한를 사용 하는 경우에 직접 작성 하거나 타사 제품을 사용 합니다.  Microsoft Foundation Class 라이브러리를 사용 하는 응용 프로그램 메모리에 데이터를 저장 하 고 사용자에 게 표시 하려면 일부 데이터베이스 클래스와 함께 문서 및 뷰를 사용할 수 있지만 데이터 바인딩 기능에 대 한 마찬가지입니다. 자세한 내용은 [시각적 개체에 대 한 데이터 액세스 C++ ](https://msdn.microsoft.com/library/7wtdsdkh.aspx) 합니다.  
  
 네이티브 SQL database에 연결 C++ 응용 프로그램은 ODBC 및 OLE DB 드라이버 및 Windows와 함께 제공 되 고 ADO 공급자 사용할 수 있습니다.     이러한 인터페이스를 지 원하는 모든 데이터베이스에 연결할 수 있습니다. ODBC 드라이버에는 표준입니다. OLE DB는 이전 버전과 호환성을 위해 제공 됩니다. 이러한 데이터 기술에 대 한 자세한 내용은 참조 하세요. [Windows Data Access Components](https://msdn.microsoft.com/library/windows/desktop/aa968814\(v=vs.85\).aspx)  
  
 SQL Server 2005에 포함 된 사용자 지정 기능을 활용 하 여 나중에 사용 하 여 [SQL Server Native Client](https://msdn.microsoft.com/sqlserver/aa937733)합니다. 네이티브 클라이언트는 SQL Server ODBC 드라이버와 단일 네이티브 동적 연결 라이브러리 (DLL)의 SQL Server OLE DB 공급자도 포함 됩니다. Microsoft SQL Server에 네이티브 코드 Api (ODBC, OLE DB 및 ADO)를 사용 하 여 응용 프로그램 지원 합니다.  SQL Server Data Tools를 사용 하 여 SQL Server Native Client를 설치합니다. 프로그래밍 가이드는 여기서: [SQL Server Native Client 프로그래밍](https://msdn.microsoft.com/library/ms130892.aspx)합니다.  
  
## <a name="to-connect-to-localdb-through-odbc-and-sql-native-client-from-a-c-application"></a>ODBC 및 SQL Native Client를 통해 localDB에 연결 하는 C++ 응용 프로그램  
  
1. SQL Server 데이터 도구를 설치합니다.  
  
2. 샘플 SQL database에 연결 하는 경우, Northwind 데이터베이스를 다운로드 하 고 새 위치에 압축을 풉니다.  
  
3. SQL Server Management Studio를 사용 하 여 압축 푼된 Northwind.mdf 파일 localDB에 연결 합니다. SQL Server Management Studio가 시작 되 면 (localdb) \MSSQLLocalDB에 연결 합니다.  
  
    ![SSMS 연결 대화 상자](../data-tools/media/raddata-ssms-connect-dialog.png "raddata SSMS 연결 대화 상자")  
  
    그런 다음 왼쪽된 창에서 localdb 노드를 마우스 오른쪽 단추로 클릭 하 고 선택 **연결**합니다.  
  
    ![데이터베이스 연결 하는 SSMS](../data-tools/media/raddata-ssms-attach-database.png "raddata SSMS 연결할 데이터베이스")  
  
4. ODBC Windows SDK 샘플을 다운로드 하 고 새 위치에 압축을 풉니다. 이 샘플에서는 데이터베이스 및 쿼리를 실행할 명령에 연결 하는 데 사용 되는 기본 ODBC 명령을 보여 줍니다. 이러한 함수에 대 한 자세히 알아볼 수 있습니다 합니다 [Microsoft ODBC Open Database Connectivity ()](https://msdn.microsoft.com/library/windows/desktop/ms710252\(v=vs.85\).aspx)합니다. 솔루션을 처음 로드 하면 (에 C++ 폴더), Visual Studio 현재 버전의 Visual Studio 솔루션을 업그레이드 하려면 제공 됩니다. **예**를 클릭합니다.  
  
5. Native client를 사용 하는, 해당 헤더 파일 및 lib 파일 필요 합니다. 이러한 파일 함수와 sql.h에 정의 된 ODBC 함수 이외의 SQL server에 관련 된 정의 포함 합니다. **프로젝트** > **속성** > **VC + + 디렉터리**, 디렉터리를 포함 하는 다음을 추가 합니다.  
  
   **\<시스템 드라이브 >: \Program Files\Microsoft SQL Server\110\SDK\Include** 및이 라이브러리 디렉터리:  
  
   **c:\Program Files\Microsoft SQL Server\110\SDK\Lib**  
  
6. Odbcsql.cpp에 다음이 줄을 추가 합니다. #define 관련이 없는 OLE DB 정의에서 컴파일할 수 없습니다.  
  
   ```  
   #define _SQLNCLI_ODBC_  
   #include <sqlncli.h>  
   ```  
  
    Note는 샘플 사용 하지 않으므로 실제로 네이티브 클라이언트 기능을 이전 단계를 컴파일하고 실행 하려면 필요 하지 않습니다. 하지만 프로젝트는 이제이 기능을 사용 하 여에 대 한 구성 합니다. 자세한 내용은 [SQL Server Native Client 프로그래밍](https://msdn.microsoft.com/library/ms130892\(v=sql.130\).aspx)을 참조하세요.  
  
7. ODBC 하위 시스템에 사용할 드라이버를 지정 합니다. 샘플은 명령줄 인수로 드라이버 연결 문자열 특성에 전달합니다. **프로젝트** > **속성** > **디버깅**를이 명령 인수를 추가 합니다.  
  
   ```  
   DRIVER="SQL Server Native Client 11.0"  
   ```  
  
8. F5 키를 눌러 애플리케이션을 빌드하고 실행합니다. 데이터베이스를 입력 하 라는 메시지가 표시 되는 드라이버에서 대화 상자가 표시 됩니다. 입력 `(localdb)\MSSQLLocalDB`를 확인 하 고 **트러스트 된 연결 사용**합니다. **확인**을 누릅니다. 성공적으로 연결을 나타내는 메시지를 사용 하 여 콘솔에 표시 됩니다. 또한 나타납니다 명령 프롬프트에서 SQL 문을 입력할 수 있습니다. 다음 화면에는 예제 쿼리 및 결과 보여 줍니다.  
  
    ![ODBC 샘플 쿼리 출력](../data-tools/media/raddata-odbc-sample-query-output.png "raddata ODBC 샘플 쿼리 출력")  
  
## <a name="see-also"></a>참고 항목  
 [Visual Studio에서 데이터 액세스](../data-tools/accessing-data-in-visual-studio.md)
