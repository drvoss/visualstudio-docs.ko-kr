---
title: 선택한 연결에서 지원되지 않는 데이터베이스 공급자를 사용합니다.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 5fab6be50a9b4c273a7bb911d8afde5cf65d7676
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65460576"
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>선택한 연결에서 지원되지 않는 데이터베이스 공급자를 사용합니다.

이 메시지는.NET Framework Data Provider for SQL Server에서 사용 하지 않는 항목을 끌어 오면 나타납니다 **서버 탐색기** 또는 **데이터베이스 탐색기** 에 [시각적 개체에 LINQ to SQL 도구 Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)합니다.

합니다 **O/R 디자이너** .NET Framework Provider for SQL Server를 사용 하는 데이터 연결만 지원 합니다. Microsoft SQL Server 또는 Microsoft SQL Server 데이터베이스 파일에 대한 연결만 유효합니다.

이 오류를 해결 하려면 SQL Server에 대 한.NET Framework Data Provider를 사용 하는 데이터 연결의 항목만 추가 합니다 **O/R 디자이너**합니다.

## <a name="see-also"></a>참고자료

- <xref:System.Data.SqlClient>
- [Visual Studio의 LINQ to SQL 도구](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
