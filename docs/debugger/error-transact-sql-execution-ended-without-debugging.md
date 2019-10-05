---
title: '오류: TRANSACT-SQL 실행이 디버깅 없이 끝났습니다 | Microsoft Docs'
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
ms.openlocfilehash: 71d1f14bef8eb69fa6c6fc4d9c3f669826079c99
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62850166"
---
# <a name="error-transact-sql-execution-ended-without-debugging"></a>오류: 디버깅 없이 Transact-SQL 실행이 중지됨

이 오류는 TRANSACT-SQL 또는 SQLCLR 프로시저를 디버깅 하려는 SQL Server에서 디버거가 디버깅 메시지를 수신 하지 못하는 경우 발생 합니다.

이 문제는 SQL Server의 문제 또는 네트워크 문제로 인해 발생할 수 있습니다 하지만 가장 가능성이 높은 원인은 사용 권한 문제입니다.

다음 두 가지 계정과 관련이 있습니다.

- 애플리케이션 계정은 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]가 실행되는 사용자 계정입니다.

- 연결 계정은 SQL Server에 연결하는 데 사용되는 ID입니다. 이 계정은 연결 SQL 인증을 사용 하는 것 처럼 Visual Studio가 실행 되는 id와 동일 하 게 반드시 합니다.

  응용 프로그램 계정이 연결 계정과 일치 하거나 sysadmin 이어야 해야 SQL 디버깅에 필요 합니다.

  Sa 같은 SQL 계정 이름인을 사용 하는 경우 응용 프로그램 계정 해야 설정할 SQL Server에서 sysadmin으로 합니다. 기본적으로 SQL server에서 실행 되는 컴퓨터의 관리자는 SQL Server sysadmin입니다.

  이 오류를 해결하려면 다음 작업을 수행해야 합니다.

  - 권한 설정을 확인합니다. 자세한 내용은 [방법: 디버깅을 위해 SQL Server 사용 권한 설정](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)합니다.

  - SQL 디버깅이 올바르게 설정되어 있는지 확인합니다.

  - 네트워크 또는 데이터베이스 관리자에게 문의합니다.

## <a name="see-also"></a>참고 항목

- [SQL 디버깅 설정](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/s4sszxst(v=vs.100))
- [방법: 디버깅을 위해 SQL Server 사용 권한 설정](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)
- [디버거 설정 및 준비](../debugger/debugger-settings-and-preparation.md)
- [Remote Debugging](../debugger/remote-debugging.md)