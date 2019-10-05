---
title: 새 연결 추가 | Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 8a93c287-2834-4a83-a590-bdc3fe8d293f
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ff1ec43d6faec329db6138598d84e47db009113e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68192567"
---
# <a name="add-new-connections"></a>새 연결 추가
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

데이터베이스 또는 서비스에 대 한 연결을 테스트 하 고 데이터베이스의 내용과 스키마를 사용 하 여 탐색할 수 있습니다 **서버 탐색기**하십시오 **클라우드 탐색기**, 또는 **SQL Server 개체 탐색기**. 이러한 windows 기능을 어느 정도 까지는 겹칩니다. 기본 차이점은:  
  
 서버 탐색기  
 Visual Studio에서 기본적으로 설치 합니다. 연결을 테스트 하 고 SQL Server 데이터베이스, ADO.NET 공급자를 설치 하 고, 다른 데이터베이스 및 일부 Azure 서비스 보기를 사용할 수 있습니다. 또한 시스템 성능 카운터, 이벤트 로그, 메시지 큐 등과 같은 하위 수준 개체를 보여 줍니다. 데이터 원본에 없는 ADO.NET 공급자 여기에 표시 되지 않습니다 되지만 계속 사용할 수 있습니다이 Visual Studio에서 프로그래밍 방식으로 연결 하 여 합니다.  
  
 클라우드 탐색기  
 선택 하 여 수동으로 Visual Studio 확장으로이 창의 설치 **도구가** > **확장 및 업데이트** > **Online**  >  **Visual Studio 갤러리**합니다. 탐색 하 고 Azure 서비스에 연결에 대 한 특수 한 기능을 제공 합니다.  
  
 SQL Server 개체 탐색기  
 SQL Server Data Tools를 사용 하 여 설치 하 고 아래에 표시 된 **보기** 메뉴. 있습니다 표시 되지 않으면로 이동 **프로그램 및 기능** 제어판에서 Visual Studio를 찾은 후 선택 **변경** SQL Server Data Tools에 대 한 확인란을 선택한 후 설치 관리자를 다시 실행 합니다. 사용 하 여 **SQL Server 개체 탐색기** 보기 (ADO.NET 공급자가 이러한) 하는 경우 SQL 데이터베이스에 새 데이터베이스를 만들, 스키마 수정, 저장된 프로시저 만들기, 연결 문자열을 검색할 데이터를 보기 합니다. 없는 ADO.NET 공급자가 설치 되어 있는 SQL database 여기에 표시 되지 않습니다 하지만 프로그래밍 방식으로를 여전히 연결할 수 있습니다.  
  
## <a name="add-a-connection-in-server-explorer"></a>서버 탐색기에서 연결 추가  
 데이터베이스에 대 한 연결을 만들려면 클릭 합니다 **연결 추가** 에서 아이콘 **서버 탐색기**를 마우스 오른쪽 단추로 클릭 하거나 **서버 탐색기** 에서 **데이터 연결이** 노드를 선택 **연결 추가**합니다. 여기에서 다른 서버, SharePoint 서비스 또는 Azure 서비스에 데이터베이스에 연결할 수 있습니다.  
  
 ![서버 탐색기 새 연결 아이콘이](../data-tools/media/raddata-server-explorer-new-connection-icon.png "raddata 서버 탐색기에 대 한 새 연결 아이콘")  
  
 그러면 합니다 **연결 추가** 대화 상자. 여기에서에서는 입력 한 SQL Server LocalDB 인스턴스의 이름입니다.  
  
 ![새 연결 추가](../data-tools/media/raddata-add-new-connection-dialog.png "raddata 새 연결 대화 상자 추가")  
  
## <a name="change-the-provider"></a>공급자 변경  
 데이터 원본이 것을 원하지 않을 경우 클릭 합니다 **변경** 새 데이터 원본 및/또는 새로운 ADO.NET 데이터 공급자를 선택 하는 단추입니다. 새 공급자를 구성한 방법에 따라 자격 증명을 요청할 수 있습니다.  
  
 ![AD0.NET 데이터 공급자를 변경](../data-tools/media/raddata-change-ad0-net-data-provider.png "raddata AD0.NET 데이터 공급자 변경")  
  
## <a name="test-the-connection"></a>연결 테스트  
 데이터 소스를 선택한 후 클릭 **연결 테스트**합니다. 성공 하지 못하면 해야 문제를 해결 하는 공급 업체의 설명서에 따라 합니다.  
  
 ![연결 테스트](../data-tools/media/raddata-test-connection.png "raddata 연결 테스트")  
  
 만들 준비가 테스트가 성공 하는 경우는 *데이터 원본*, 있으며 실제로 의미 하는 Visual Studio 용어입니다는 *데이터 모델* 기본 데이터베이스 또는 서비스를 기반으로 하는 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [.NET용 Visual Studio 데이터 도구](../data-tools/visual-studio-data-tools-for-dotnet.md)
