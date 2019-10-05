---
title: .NET 용 데이터 도구
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c3175080-1dfb-4ab8-a460-92dadbb844b4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
- dotnet
ms.openlocfilehash: a4a62f629244d44680b3d5ac3233bd45b975302e
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66745304"
---
# <a name="visual-studio-data-tools-for-net"></a>.NET용 Visual Studio 데이터 도구

Visual Studio 및.NET 함께 제공 광범위 한 API 및 도구 지원 데이터베이스에 연결, 메모리에서 데이터 모델링 및 사용자 인터페이스에 데이터를 표시 합니다. 데이터 액세스 기능을 제공 하는.NET 클래스 라고 [ADO.NET](/dotnet/framework/data/adonet/index)합니다. Visual Studio에서 도구는 데이터와 함께 ADO.NET, 관계형 데이터베이스 및 XML 지원 하기 위해 기본적으로 설계 되었습니다. 많은 NoSQL 데이터베이스 공급 업체 또는 제 삼자에 게이 오늘날에는 ADO.NET 공급자에 제공합니다.

[.NET core](/dotnet/core/) ADO.NET 데이터 집합 및 해당 관련된 형식을 제외 하 고 지원 합니다. .NET Core를 대상으로 하는 개체-관계형 매핑 (ORM) 계층을 필요로 하는 경우 사용 하 여 [Entity Framework Core](/ef/core/)합니다.

다음 다이어그램은 기본 아키텍처의 단순화 된 보기를 보여줍니다.

![ADO.NET 아키텍처](../data-tools/media/raddata-ado-net-architecture-diagram.png)

## <a name="typical-workflow"></a>일반적인 워크플로

일반적인 과정은 다음과 같습니다.

1. 로컬 컴퓨터에 개발 또는 테스트 데이터베이스를 설치 합니다. 참조 [데이터베이스 시스템, 도구 및 샘플 설치](../data-tools/installing-database-systems-tools-and-samples.md)합니다. Azure 데이터 서비스를 사용 하는 경우이 단계가 필요 하지 않습니다.

2. Visual Studio에서 데이터베이스 (또는 서비스 또는 로컬 파일)에 대 한 연결을 테스트 합니다. 참조 [새 연결 추가](../data-tools/add-new-connections.md)합니다.

3. (선택 사항) 도구를 사용 하 여 생성 하 고 새 모델을 구성 합니다. Entity Framework를 기반으로 하는 모델은 새 응용 프로그램에 대 한 기본 권장 사항을입니다. 모델 중 하나를 사용 하는 응용 프로그램 상호 작용 하는 데이터 원본입니다. 모델은 데이터베이스 또는 서비스 및 응용 프로그램 사이 논리적으로 배치 합니다. 참조 [새 데이터 원본을 추가](../data-tools/add-new-data-sources.md)합니다.

4. 데이터 소스를 끌어 합니다 **데이터 원본** 지정 하는 방식으로 사용자에 게 데이터를 표시 하는 데이터 바인딩 코드를 생성 하는 Windows Forms, ASP.NET 또는 Windows Presentation Foundation 디자인 화면으로 창. 참조 [Visual Studio에서 데이터에 컨트롤 바인딩](../data-tools/bind-controls-to-data-in-visual-studio.md)합니다.

5. 비즈니스 규칙, 검색 및 데이터 유효성 검사 또는 기본 데이터베이스를 노출 하는 사용자 지정 기능을 활용 하는 항목에 대 한 사용자 지정 코드를 추가 합니다.

3 단계를 건너뛸 수 있으며 모델을 사용 하는 것이 아니라 데이터베이스에 직접 명령 실행 하는.NET 응용 프로그램을 프로그래밍할 수 있습니다. 이 경우에 관련 설명서를 찾을 수 있습니다. [ADO.NET](/dotnet/framework/data/adonet/index). 여전히 사용할 수 있는 참고 합니다 **데이터 소스 구성 마법사** 및 메모리와 해당 개체에 데이터 바인딩 UI 컨트롤에 고유한 개체를 채울 때 데이터 바인딩 코드를 생성 하는 디자이너입니다.

## <a name="see-also"></a>참고자료

- [Visual Studio에서 데이터 액세스](../data-tools/accessing-data-in-visual-studio.md)