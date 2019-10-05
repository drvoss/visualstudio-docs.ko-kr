---
title: '오류: 사용자 수 있습니다 하지 실행할 저장 프로시저 sp_enable_sql_debug | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e051cd594ee26a57fdbb7dcdc5bdad81f06cf771
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62850088"
---
# <a name="error-user-could-not-execute-stored-procedure-spenablesqldebug"></a>오류: 사용자는 sp_enable_sql_debug 저장 프로시저를 실행할 수 없습니다.

저장 프로시저 sp_enable_sql_debug를 서버에서 실행할 수 없는 경우입니다. 이 오류의 원인은 다음과 같습니다.

- 연결에 문제가 있는 경우입니다. 서버에 안정적으로 연결되어 있어야 합니다.

- 서버에 대해 필요한 권한이 없는 경우입니다. SQL Server 2005에서 디버깅하려면 Visual Studio를 실행하는 데 사용되는 계정과 SQL Server에 연결하는 데 사용되는 계정이 모두 sysadmin 역할의 멤버여야 합니다. SQL Server에 연결하는 데 사용한 계정이 Windows 사용자 계정(Windows 인증을 사용하는 경우)이거나 사용자 ID와 암호로 지정된 계정(SQL 인증을 사용하는 경우)입니다.

자세한 내용은 [방법: 디버깅을 위해 SQL Server 사용 권한 설정](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)합니다.

## <a name="see-also"></a>참고 항목

- [방법: 디버깅을 위해 SQL Server 사용 권한 설정](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)
- [SQL 디버깅 설정](/previous-versions/visualstudio/visual-studio-2010/s4sszxst\(v\=vs.100\))