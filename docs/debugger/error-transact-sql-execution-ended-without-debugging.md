---
title: '오류: 디버깅 없이 Transact-sql 실행이 종료 되었습니다. | Microsoft Docs'
ms.date: 11/08/2018
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.sqlde_sql_executed_but_not_debugged
dev_langs:
- CSharp
- VB
- FSharp
- C++
- SQL
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e86e24f775d8470b54ed7b9c54d27a5d3c1ee8da
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/13/2020
ms.locfileid: "75916297"
---
# <a name="error-transact-sql-execution-ended-without-debugging"></a>오류: 디버깅 없이 Transact-SQL 실행이 중지되었습니다.

이 오류는 Transact-sql 또는 SQLCLR 프로시저를 디버깅 하려고 하는데 디버거가 SQL Server에서 디버깅 메시지를 받지 못하는 경우에 발생 합니다.

이 문제는 네트워크 문제나 SQL Server 문제로 인해 발생할 수 있지만 가장 가능성이 높은 원인은 사용 권한 문제입니다.

다음 두 가지 계정과 관련이 있습니다.

- 애플리케이션 계정은 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]가 실행되는 사용자 계정입니다.

- 연결 계정은 SQL Server에 연결하는 데 사용되는 ID입니다. 이 계정은 연결에서 SQL 인증을 사용 하는 것 처럼 Visual Studio가 실행 되는 id와 동일할 필요는 없습니다.

  SQL 디버깅을 사용 하려면 응용 프로그램 계정이 연결 계정과 일치 하거나 sysadmin 이어야 합니다.

  Sa와 같은 SQL 계정 이름을 사용 하는 경우 응용 프로그램 계정이 sysadmin으로 SQL Server에 설정 되어야 합니다. 기본적으로 SQL server가 실행 되 고 있는 컴퓨터의 관리자는 SQL Server sysadmins입니다.

  이 오류를 해결하려면 다음 작업을 수행해야 합니다.

  - 권한 설정을 확인합니다. 자세한 내용은 [방법: 디버깅을 위한 SQL Server 권한 설정](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)을 참조 하세요.

  - SQL 디버깅이 올바르게 설정되어 있는지 확인합니다.

  - 네트워크 또는 데이터베이스 관리자에게 문의합니다.

## <a name="see-also"></a>참조

- [SQL 디버깅 설정](/previous-versions/visualstudio/visual-studio-2010/s4sszxst(v=vs.100))
- [방법: 디버깅을 위한 SQL Server 권한 설정](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)
- [디버거 설정 및 준비](../debugger/debugger-settings-and-preparation.md)
- [Remote Debugging](../debugger/remote-debugging.md)