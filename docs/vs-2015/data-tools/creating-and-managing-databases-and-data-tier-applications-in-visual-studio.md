---
title: 데이터베이스 및 데이터 계층 응용 프로그램 만들기 및 관리
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
helpviewer_keywords:
- managing change, databases
- database features of Visual Studio, managing change
- databases, managing change
- managing change, database servers
ms.assetid: 40b51f5a-d52c-44ac-8f84-037a0917af33
caps.latest.revision: 40
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d6cb4a3beb12d2b33b8b13441df66116fe449d09
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63431154"
---
# <a name="creating-and-managing-databases-and-data-tier-applications-in-visual-studio"></a>데이터베이스 및 Visual Studio에서 데이터 계층 응용 프로그램 만들기 및 관리
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

중요]
> 이전 버전에 포함 된 데이터베이스 프로젝트 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 에서 지금 나와 [!INCLUDE[sql_Denali_long](../includes/sql-denali-long-md.md)] 도구입니다. 자세한 내용은 [SQL Server Developer Tools](http://go.microsoft.com/fwlink/?LinkId=228126)합니다.

 데이터베이스 프로젝트를 사용 하 여 새 데이터베이스를 만들 새 데이터 계층 응용 프로그램 (Dac)을 기존 데이터베이스 및 데이터 계층 응용 프로그램을 업데이트 합니다. 데이터베이스 프로젝트와 DAC 프로젝트 관리 또는 네이티브 코드에 이러한 기술을 적용 하는 동일한 방식에서 버전 제어 및 프로젝트 관리 기술을 데이터베이스 개발 작업에 적용할 수 있습니다. 개발 팀을 만들어 데이터베이스 및 데이터베이스 서버에 변경 내용 관리를 수 있습니다는 *DAC 프로젝트로*, *데이터베이스 프로젝트*, 또는 *서버 프로젝트* 및 버전 제어 합니다. 팀의 멤버 수 다음 파일을 체크 아웃 확인, 빌드 및에서 변경 내용을 테스트 하는 *격리 된 개발 환경*, 또는 샌드박스, 팀과 공유 하기 전에 합니다. 을 코드 품질을 보장 하기 위해 팀 완료 하 고 변경 내용을 프로덕션에 배포 하기 전에 데이터베이스의 특정 릴리스에 대 한 모든 변경 내용을 스테이징 환경에서 테스트할 수 있습니다.

 데이터 계층 응용 프로그램에서 지원 되는 데이터베이스 기능 목록을 참조 하세요 [데이터 계층 응용 프로그램에서 지 원하는 기능](http://go.microsoft.com/fwlink/?LinkId=164239) Microsoft 웹 사이트입니다. 데이터베이스의 데이터 계층 응용 프로그램에서 지원 되지 않는 기능을 사용 하면 데이터베이스에 변경 내용을 관리 하 데이터베이스 프로젝트를 대신 사용 해야 합니다.

## <a name="common-high-level-tasks"></a>일반적인 상위 수준 작업

|상위 수준 작업|지원 내용|
|----------------------|------------------------|
|**데이터 계층 응용 프로그램 개발을 시작 합니다.** DAC를 사용 하 여 도입 된 새로운 개념이 [!INCLUDE[sskatmai_r2](../includes/sskatmai-r2-md.md)] 에 대 한 정의 포함 하는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 데이터베이스 및 지원 인스턴스는 클라이언트-서버 또는 3 계층 응용 프로그램에서 사용 되는 개체입니다. DAC는 테이블 및 뷰, 로그인 등 인스턴스 엔터티가 같은 데이터베이스 개체를 포함합니다. 사용할 수 있습니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] DAC 프로젝트를 만들려면 DAC 패키지 파일을 빌드 및 배포의 인스턴스에 대 한 데이터베이스 관리자는 DAC 패키지 파일 보내기는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 데이터베이스 엔진입니다.|-   [데이터 계층 응용 프로그램 만들기 및 관리](http://go.microsoft.com/fwlink/?LinkId=160741) (Microsoft 웹 사이트)<br />-   [SQL Server Management Studio](http://go.microsoft.com/fwlink/?LinkId=227328)|
|**반복 데이터베이스 개발을 수행 합니다.** 개발자 또는 테스터 라면 프로젝트의 부분을 확인 하 고 격리 된 개발 환경에서이 업데이트 합니다. 이러한 유형의 환경을 사용 하 여 팀의 다른 멤버에 영향을 주지 않고 변경 내용을 테스트할 수 있습니다. 변경 내용을 완료 되 면 다시 버전 제어, 다른 팀 멤버 수에 변경 내용을 가져오는 및 빌드 및 테스트 서버에 배포 하는 위치에 파일을 확인 합니다.|-   [쿼리 및 텍스트 편집기 (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=227327) (Microsoft 웹 사이트)<br />-   [TRANSACT-SQL 디버거](http://go.microsoft.com/fwlink/?LinkId=227324) (Microsoft 웹 사이트)|
|**프로토타입 만들기, 테스트 결과 및 수정 하 고 데이터베이스 스크립트 및 개체를 확인 합니다.** 사용할 수는 [!INCLUDE[tsql](../includes/tsql-md.md)] 이러한 일반적인 작업 중 하나를 수행 하는 편집기입니다.|-   [쿼리 및 텍스트 편집기 (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=227327) (Microsoft 웹 사이트)|

## <a name="see-also"></a>참고 항목
 [.NET용 Visual Studio 데이터 도구](../data-tools/visual-studio-data-tools-for-dotnet.md)
