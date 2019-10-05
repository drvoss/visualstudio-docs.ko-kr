---
title: ASP.NET 웹 앱에 대 한 코드 분석 구성
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.asp
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 51638db2cf258cc1a91c659c137c6a17811fa8c8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62820699"
---
# <a name="how-to-configure-code-analysis-for-an-aspnet-web-application"></a>방법: ASP.NET 웹 애플리케이션에 대한 코드 분석 구성

Visual Studio에서 코드 분석의 목록에서 선택할 수 있습니다 *규칙 집합* 적용할 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 웹 응용 프로그램입니다. 기본 규칙 집합은 Microsoft 최소 권장 규칙. 웹 사이트에 적용 되도록 설정 하는 다른 규칙을 선택할 수 있습니다.

1. 웹 사이트를 선택 **솔루션 탐색기**합니다.

2. 에 **분석** 메뉴에서 클릭 **웹 사이트에 대 한 코드 분석 구성**합니다.

3. 솔루션을 선택 하는 경우 솔루션에 둘 이상의 프로젝트에서 빌드 구성과 대상 운영 체제를 선택 합니다 **Configuration** 하 고 **플랫폼** 나열 합니다.

4. 솔루션의 각 프로젝트에 대해 클릭 합니다 **규칙 집합** 열 및 실행 되도록 설정 된 규칙의 이름을 클릭 합니다.

5. 기본적으로 솔루션의 모든 프로젝트에 대해 코드 분석을 실행 합니다. 를 사용 하지 않도록 설정 하거나 특정 프로젝트에 대 한 코드 분석을 사용 하도록 설정 하려면 다음이 단계를 수행 합니다.

    1. 프로젝트 이름을 마우스 오른쪽 단추로 클릭 하 고 속성을 클릭 합니다.

    2. 선택 하거나 선택 취소 합니다 **코드 분석 사용** 확인란 합니다. 선택 하 여 코드 분석을 수동으로 실행할 수도 있습니다 **웹 사이트에서 코드 분석 실행** 에서 합니다 **분석** 메뉴.

6. 에 **이 규칙 집합 실행** 드롭 다운 목록에서 다음이 단계를 수행 합니다.

    - 사용 하려는 규칙 집합을 선택 합니다.

    - 선택  **\<찾아보기 >** 목록에 없는 기존 사용자 지정 규칙 집합을 지정 하려면.

    - 정의 된 [사용자 지정 규칙 집합](../code-quality/how-to-create-a-custom-rule-set.md)합니다.