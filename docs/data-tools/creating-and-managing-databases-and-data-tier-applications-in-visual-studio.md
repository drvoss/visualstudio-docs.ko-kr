---
title: 데이터베이스 프로젝트 및 DAC 프로젝트
ms.date: 11/21/2018
ms.topic: conceptual
helpviewer_keywords:
- databases, managing change
ms.assetid: 40b51f5a-d52c-44ac-8f84-037a0917af33
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 2a86d9511e470c9a810ff58e80e4cae1f9a0cb11
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62567242"
---
# <a name="database-projects-and-data-tier-applications"></a>데이터베이스 프로젝트 및 데이터 계층 응용 프로그램

데이터베이스 프로젝트를 사용 하 여 새 데이터베이스를 만들 새 데이터 계층 응용 프로그램 (Dac)을 기존 데이터베이스 및 데이터 계층 응용 프로그램을 업데이트 합니다. 데이터베이스 프로젝트와 DAC 프로젝트 관리 또는 네이티브 코드에 이러한 기술을 적용 하는 동일한 방식에서 버전 제어 및 프로젝트 관리 기술을 데이터베이스 개발 작업에 적용할 수 있습니다. DAC 프로젝트, 데이터베이스 프로젝트 또는 서버 프로젝트를 만들고 버전 제어에서 여 데이터베이스 및 데이터베이스 서버에 변경 내용을 관리 개발 팀을 할 수 있습니다. 팀의 멤버 수 다음 파일을 체크 아웃 확인, 빌드 및 팀과 공유 하기 전에 격리 된 개발 환경 또는 샌드박스, 변경 내용을 테스트 합니다. 을 코드 품질을 보장 하기 위해 팀 완료 하 고 변경 내용을 프로덕션에 배포 하기 전에 데이터베이스의 특정 릴리스에 대 한 모든 변경 내용을 스테이징 환경에서 테스트할 수 있습니다.

데이터 계층 응용 프로그램에서 지원 되는 데이터베이스 기능 목록을 참조 하세요 [SQL Server 개체에 대 한 DAC 지원](/sql/relational-databases/data-tier-applications/dac-support-for-sql-server-objects-and-versions)합니다. 데이터베이스의 데이터 계층 응용 프로그램에서 지원 되지 않는 기능을 사용 하면 데이터베이스에 변경 내용을 관리 하 데이터베이스 프로젝트를 대신 사용 해야 합니다.

## <a name="common-high-level-tasks"></a>일반적인 상위 수준 작업

| 상위 수준 작업 | 지원 내용 |
| - | - |
| **데이터 계층 응용 프로그램 개발을 시작 합니다.** SQL Server 2008을 사용 하 여 데이터 계층 응용 프로그램 (DAC)을 개념이 도입 되었습니다. DAC는 SQL Server 데이터베이스 및 클라이언트-서버 또는 3 계층 응용 프로그램에서 사용 되는 인스턴스 개체 지원에 대 한 정의 포함 합니다. DAC는 테이블 및 뷰, 로그인 등 인스턴스 엔터티가 같은 데이터베이스 개체를 포함합니다. DAC 프로젝트를 만들고 DAC 패키지 파일을 빌드, SQL Server 데이터베이스 엔진의 인스턴스에 배포에 대 한 데이터베이스 관리자는 DAC 패키지 파일 보내기를 Visual Studio를 사용할 수 있습니다. | - [데이터 계층 애플리케이션](/sql/relational-databases/data-tier-applications/data-tier-applications)<br />- [SQL Server Management Studio](/sql/ssms/sql-server-management-studio-ssms) |
| **반복 데이터베이스 개발을 수행 합니다.** 개발자는 프로젝트의 부분을 확인 하 고 격리 된 개발 환경에서 업데이트할 수 있습니다. 이러한 유형의 환경을 사용 하 여 팀의 다른 멤버에 영향을 주지 않고 변경 내용을 테스트할 수 있습니다. 변경 내용을 완료 되 면 다시 버전 제어, 다른 팀 멤버 수에 변경 내용을 가져오는 및 빌드 및 테스트 서버에 배포 하는 위치에 파일을 확인 합니다. | - [프로젝트 기반 오프 라인 데이터베이스 개발 (SQL Server Data Tools)](/sql/ssdt/project-oriented-offline-database-development)<br />- [TRANSACT-SQL 디버거 (SQL Server Management Studio)](/sql/ssms/scripting/transact-sql-debugger) |
| **프로토타입 만들기, 테스트 결과 및 수정 하 고 데이터베이스 스크립트 및 개체를 확인 합니다.** 이러한 일반적인 작업 중 하나를 수행 하 여 TRANSACT-SQL 편집기를 사용할 수 있습니다. | - [쿼리 및 텍스트 편집기 (SQL Server Management Studio)](/sql/ssms/scripting/query-and-text-editors-sql-server-management-studio) |

## <a name="see-also"></a>참고자료

- [.NET용 Visual Studio 데이터 도구](../data-tools/visual-studio-data-tools-for-dotnet.md)