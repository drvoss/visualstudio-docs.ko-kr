---
title: .mdf 파일 업그레이드
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Express
- SQL Server LocalDB
- LocalDB
- SQLEXPRESS
- upgrading SQLExpress to SQLExpress
- upgrading to LocalDB
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 1b2b6029002e62f5b13f5fc40bc24f817364c148
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67821670"
---
# <a name="upgrade-mdf-files"></a>.mdf 파일 업그레이드

이 항목에서는 데이터베이스 파일을 업그레이드 하는 방법을 설명 합니다 ( *.mdf*) 최신 버전의 Visual Studio를 설치 합니다. 다음 작업에 대 한 지침을 포함 합니다.

- 최신 버전의 SQL Server Express LocalDB를 사용 하는 데이터베이스 파일을 업그레이드

- 최신 버전의 SQL Server Express를 사용 하는 데이터베이스 파일을 업그레이드

- Visual Studio에서 데이터베이스 파일을 사용 하 여 작동 하지만 이전 버전의 SQL Server Express 또는 LocalDB를 사용 하 여 호환성이 유지 됩니다.

- 기본 데이터베이스 엔진이 SQL Server Express 확인

Visual Studio를 사용 하 여 데이터베이스 파일을 포함 하는 프로젝트를 열려면 ( *.mdf*) 이전 버전의 SQL Server Express 또는 LocalDB를 사용 하 여 생성 된 합니다. 그러나 SQL Server Express 또는 Visual Studio와 동일한 컴퓨터에 설치 하는 LocalDB의 버전을 계속 하려면 Visual Studio에서 프로젝트를 개발 해야 또는 데이터베이스 파일을 업그레이드 해야 합니다. 데이터베이스 파일을 업그레이드 하는 경우에 이전 버전의 SQL Server Express 또는 LocalDB를 사용 하 여 액세스할 수 없습니다.

수 또한 하 라는 메시지가 파일의 버전의 SQL Server Express 또는 현재 설치 된 LocalDB 인스턴스와 호환 되지 않습니다 경우는 이전 버전의 SQL Server Express 또는 LocalDB를 통해 만든 데이터베이스 파일을 업그레이드 합니다. 문제를 해결 하려면 Visual Studio 하 라는 메시지가 나타납니다 파일을 업그레이드 합니다.

> [!IMPORTANT]
> 업그레이드 하기 전에 데이터베이스 파일을 백업 하는 것이 좋습니다.

> [!WARNING]
> 업그레이드 하는 경우는 *.mdf* LocalDB 2014 (V12) 32 비트 LocalDB 2016 (V13) 이상에서 만든 파일 됩니다 32 비트 버전의 LocalDB에서 파일을 다시 열 수 있습니다.

데이터베이스를 업그레이드 하기 전에 다음 조건을 고려 하세요.

- 이전 버전 및 최신 버전의 Visual Studio에서 프로젝트에서 작동 하도록 하려는 경우 업그레이드 하지 마세요.

- SQL Server Express 대신 LocalDB를 사용 하는 환경에서 응용 프로그램을 사용할 경우 업그레이드 하지 마세요.

- 이러한 LocalDB 수락 하지 않았기 때문에 응용 프로그램에서 원격 연결을 사용 하는 경우를 업그레이드 하지 마세요.

- 응용 프로그램에서 인터넷 정보 서비스 (IIS)를 사용 하는 경우 업그레이드 하지 마세요.

- 샌드박스 환경에서 데이터베이스 응용 프로그램을 테스트 하려고 하지만 데이터베이스를 관리 하지 않으려는 경우 업그레이드를 고려 합니다.

### <a name="to-upgrade-a-database-file-to-use-the-localdb-version"></a>LocalDB 버전을 사용 하려면 데이터베이스 파일을 업그레이드 하려면

1. **서버 탐색기**를 선택 합니다 **데이터베이스에 연결** 단추입니다.

2. 에 **연결 추가** 대화 상자에서 다음 정보를 지정 합니다.

    - **데이터 원본**: `Microsoft SQL Server (SqlClient)`

    - **서버 이름**:

        - 기본 버전을 사용 하려면: `(localdb)\MSSQLLocalDB`합니다.  이 지정 ProjectV12 또는 ProjectV13, 설치 된 Visual Studio의 버전 및 첫 번째 LocalDB 인스턴스가 만들어질 때에 따라 합니다. 합니다 **MSSQLLocalDB** 노드에서 **SQL Server 개체 탐색기** 를 가리키는지 버전을 보여 줍니다.

        - 특정 버전을 사용 하려면: `(localdb)\ProjectsV12` 또는 `(localdb)\ProjectsV13`, 여기서 V12 LocalDB 2014 이며 V13 LocalDB 2016 합니다.

    - **데이터베이스 파일 첨부**: 주 데이터베이스의 실제 경로로 *.mdf* 파일입니다.

    - **논리적 이름**: 파일을 사용 하려는 이름입니다.

3. **확인** 단추를 선택합니다.

4. 메시지가 나타나면 선택 합니다 **예** 단추 파일을 업그레이드 합니다.

    데이터베이스를 업그레이드 하 고 LocalDB 데이터베이스 엔진에 연결 된 이전 버전의 LocalDB 사용 하 여 호환 되는 더 이상.

연결에 대 한 바로 가기 메뉴를 열고 다음을 선택 하 여 LocalDB를 사용 하려면 SQL Server Express 연결을 수정할 수도 있습니다 **연결 수정**합니다. 에 **연결 수정** 대화 상자에서 서버 이름을 변경 `(LocalDB)\MSSQLLocalDB`합니다. 에 **고급 속성** 대화 상자에서 확인 **사용자 인스턴스** 로 설정 되어 **False**합니다.

### <a name="to-upgrade-a-database-file-to-use-the-sql-server-express-version"></a>SQL Server Express 버전을 사용 하려면 데이터베이스 파일을 업그레이드 하려면

1. 데이터베이스에 연결에 대 한 바로 가기 메뉴에서 선택 **연결 수정**합니다.

2. 에 **연결 수정** 대화 상자를 선택 합니다 **고급** 단추입니다.

3. 에 **고급 속성** 대화 상자를 선택 합니다 **확인** 서버 이름을 변경 하지 않고 단추.

    데이터베이스 파일은 SQL Server Express의 현재 버전과 일치 하도록 업그레이드 됩니다.

### <a name="to-work-with-the-database-in-visual-studio-but-retain-compatibility-with-sql-server-express"></a>Visual Studio에서 데이터베이스를 사용 하 여 작동 하지만 SQL Server Express와 호환성을 유지 하려면

- Visual Studio에서 업그레이드 하지 않고도 프로젝트를 엽니다.

  - 프로젝트를 실행 하려면 선택 합니다 **F5** 키입니다.

  - 데이터베이스를 편집 하려면 엽니다는 *.mdf* 파일 **솔루션 탐색기**에서 노드를 확장 하 고 **서버 탐색기** 데이터베이스와 함께 작동 하도록 합니다.

### <a name="to-make-sql-server-express-the-default-database-engine"></a>수 있도록 SQL Server Express 기본 데이터베이스 엔진

1. 메뉴 모음에서 선택 **도구가** > **옵션**합니다.

2. 에 **옵션** 대화 상자에서 합니다 **Database Tools** 옵션을 선택한 후 **데이터 연결**합니다.

3. 에 **SQL Server 인스턴스 이름** 텍스트 상자에서 SQL Server Express 또는 사용 하려는 LocalDB 인스턴스의 이름을 지정 합니다. 인스턴스 이름이 없는 경우 지정 `.\SQLEXPRESS or (LocalDB)\MSSQLLocalDB`합니다.

4. **확인** 단추를 선택합니다.

    SQL Server Express 응용 프로그램에 대 한 기본 데이터베이스 엔진 됩니다.

## <a name="see-also"></a>참고자료

- [Visual Studio에서 데이터 액세스](accessing-data-in-visual-studio.md)
