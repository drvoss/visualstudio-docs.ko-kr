---
title: SharePoint 응용 프로그램 성능 프로 파일링 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Profiling.SilverlightWebPartOnly
- VS.SharePointTools.Profiling.DotNetTrustLevel
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, profiling
- performance testing [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, performance testing
- profiling [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8b59a3de88403300a46b7992a2dad72e3d6b59e0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62563327"
---
# <a name="profile-the-performance-of-sharepoint-applications"></a>SharePoint 응용 프로그램의 성능을 프로 파일링

SharePoint 응용 프로그램 느리거나 비효율적으로 수행 하는 경우 Visual Studio에서 문제가 있는 코드 및 기타 요소를 식별 하는 프로 파일링 기능을 사용할 수 있습니다. 부하 테스트 기능을 사용 하 여 많은 사용자가 액세스할 때 응용 프로그램이 동시에 같은 스트레스 상태에서 SharePoint 응용 프로그램을 수행 하는 방법을 확인할 수 있습니다. 웹 성능 테스트를 실행 하 여 웹 응용 프로그램의 성능을 측정할 수 있습니다. 코딩 된 UI 테스트를 사용 하 여 전체 SharePoint 응용 프로그램 사용자 인터페이스를 포함 하 여 올바르게 작동 하는지 여부를 확인할 수 있습니다. 이러한 테스트를 함께 사용 하면 도움이 되는지 응용 프로그램을 배포 하기 전에 성능 문제를 식별 합니다.

## <a name="profile-tools-overview"></a>프로필 도구 개요

프로 파일링 관찰 하 고 실행 될 때 응용 프로그램의 성능 동작 기록의 프로세스를 말합니다. 응용 프로그램 프로 파일링에서 병목, 비효율적인 코드 및로 인해 응용 프로그램이 느리게 실행 되거나 너무 많은 메모리를 사용 하 여 메모리 할당 문제 같은 문제를 발견할 수 있습니다. 예를 들어, 프로 파일링 코드에서 자주 호출 되 고 응용 프로그램의 전반적인 성능이 저하 될 수 있는 코드 세그먼트인 핫스폿을 식별을 사용할 수는 있습니다. 핫스폿을 확인 한 후 종종 최적화 하거나 제거할 수 있습니다.

확인 하 고 이러한 종류의 성능 문제를 찾이 통합된 개발 환경 (IDE)에서 여러 프로 파일링 도구를 사용할 수 있습니다. 이러한 도구는 다른 종류의 Visual Studio 프로젝트와 마찬가지로 SharePoint 프로젝트에서 동일한 방식으로 작동 합니다. 프로 파일링 도구 성능 마법사를 지정 하는 테스트를 사용 하는 성능 세션의 생성을 안내 합니다. 성능 세션에는 하나 이상의 프로 파일링 실행의 결과 함께 응용 프로그램에서 성능 정보 수집에 사용 되는 구성 데이터 집합이 있습니다. 성능 세션은 프로젝트 폴더에 저장 되며에서 볼 수 있습니다 **성능 탐색기**합니다. 자세한 내용은 [성능 컬렉션 메서드 이해](../profiling/understanding-performance-collection-methods.md)를 참조하세요.

만들고 응용 프로그램에서 프로필 분석을 실행 한 후 보고서의 성능에 대 한 세부 정보를 제공 합니다. 이 보고서는 시간, 계층 함수 호출 스택 또는 호출 트리를 통해 CPU 사용량 그래프와 같은 항목을 포함할 수 있습니다. 보고서의 정확한 내용은 샘플링 또는 계측 등 실행 하는 테스트의 유형에 따라 달라질 수 있습니다. 자세한 내용은 [프로 파일링 도구 보고서 개요](http://go.microsoft.com/fwlink/?LinkId=224689)합니다.

## <a name="performance-session-process"></a>성능 세션 프로세스

응용 프로그램을 프로 파일링 하려면 성능 세션을 만들려면 프로 파일링 도구 성능 마법사를 사용 하 여 시작 합니다. 메뉴 모음에서 선택 **분석**하십시오 **성능 마법사 시작**합니다. 마법사 완료 되 면 원하는 프로필 메서드 등 응용 프로그램을 프로 파일링 하려면 성능 세션에 대 한 필요한 정보를 입력 합니다. 자세한 내용은 [방법: 웹 사이트 또는 웹 응용 프로그램 성능 마법사를 사용 하 여 프로 파일링](http://go.microsoft.com/fwlink/?LinkId=224692)합니다. 대 안으로, 설정 하 고 성능 세션을 실행 하려면 명령줄 옵션을 사용할 수 있습니다. 자세한 내용은 [프로 파일링 도구에서 명령줄 사용](http://go.microsoft.com/fwlink/?LinkId=224703)합니다. 성능 세션의 모든 측면을 수동으로 구성 하려는 경우 참조 [방법: 프로 파일링 도구를 사용 하 여 성능 세션 수동으로 만들기](http://go.microsoft.com/fwlink/?LinkId=224691)합니다. 단위 테스트에서 성능 세션에서 만들 수도 합니다 **테스트 결과** 창에서 단위 테스트에 대 한 바로 가기 메뉴를 열고 선택 **성능 세션 만들기**합니다.

성능 세션을 설정한 후 세션 구성이 저장 되, 프로 파일링 데이터를 제공 하도록 서버 구성 및 응용 프로그램을 실행 합니다. 응용 프로그램을 사용 하면 성능 데이터 로그 파일에 기록 됩니다. 성능 세션에 나와 **성능 탐색기** 아래 합니다 **대상** 폴더입니다. 성능 세션에는 다음이 완료 되 면 해당 보고서에 나타납니다 합니다 **보고서** 폴더에서 **성능 탐색기**합니다. 보고서를 표시 하려면에서 엽니다 **성능 탐색기**합니다. 을 확인 하거나 성능 세션의 속성을 구성 하려면에서 바로 가기 메뉴를 열고 **성능 탐색기**를 선택한 후 **속성**합니다. 성능 세션의 특정 속성에 대 한 자세한 내용은 참조 하세요. [프로 파일링 도구 성능 세션 구성](http://go.microsoft.com/fwlink/?LinkId=224694)합니다. 성능 세션의 결과 해석 하는 방법에 대 한 자세한 내용은 [프로 파일링 도구 데이터 분석](http://go.microsoft.com/fwlink/?LinkId=224704)합니다.

## <a name="stress-test"></a>스트레스 테스트

Visual Studio에서 부하 테스트 및 웹 성능 테스트를 만들어 응용 프로그램의 스트레스 성능을 분석할 수 있습니다. Visual Studio에서 부하 테스트를 만들면 불리에 대해 응용 프로그램을 테스트 하는 시나리오의 조합을 지정 합니다. 이러한 요소는 부하 패턴, 테스트 조합 모델, 테스트 조합, 네트워크 조합 및 웹 브라우저 조합에 포함 됩니다. 부하 테스트 시나리오에는 단위 테스트 및 웹 성능 테스트를 모두 포함할 수 있습니다.

그림 1: 부하 테스트 결과 예제

![실행 중인 부하 테스트 그래프 뷰](../sharepoint/media/load-webgraphs.png "실행 중인 부하 테스트 그래프 뷰")

웹 성능 테스트는 최종 사용자는 SharePoint 응용 프로그램 상호 작용할 수 있는 방법을 시뮬레이션 합니다. 브라우저 세션에서 HTTP 요청을 기록 하 여 또는 사용 하 여 웹 성능 테스트를 만들 수 있습니다 합니다 **웹 성능 테스트 레코더**합니다. 웹 요청에 표시 된 **웹 성능 테스트 편집기** 브라우저 세션이 완료 된 후입니다. 결과 디버깅할 수 있습니다 합니다 **웹 성능 테스트 결과 뷰어**합니다. 사용 하 여 웹 성능 테스트를 수동으로 빌드할 수는 **웹 성능 테스트 편집기**합니다.

## <a name="test-user-interfaces"></a>사용자 인터페이스 테스트

코딩 된 UI 테스트는 자동으로 사용자 인터페이스 (UI)를 통해 SharePoint 응용 프로그램을 구동 합니다. 이러한 테스트는 단추와 제대로 작동 하는지 확인 하려면 메뉴 등 UI 컨트롤을 설명 합니다. 이러한 종류의 테스트 유효성 검사 또는 다른 논리가 이루어집니다 ui에서와 같은 웹 페이지의 경우 특히 유용 합니다. 수동 테스트를 자동화 하려면 코딩 된 UI 테스트를 사용할 수도 있습니다. 코딩 된 UI 테스트 SharePoint 응용 프로그램에 대 한 동일한 방식으로 다른 유형의 응용 프로그램에 대 한 테스트를 만들려면. 자세한 내용은 [코딩 된 UI 테스트를 사용 하 여 SharePoint 2010 응용 테스트](../test/testing-sharepoint-2010-applications-with-coded-ui-tests.md)합니다.

## <a name="related-topics"></a>관련 항목

|제목|설명|
|-----------|-----------------|
|[연습: SharePoint 응용 프로그램을 프로 파일링](../sharepoint/walkthrough-profiling-a-sharepoint-application.md)|SharePoint 응용 프로그램에서 샘플링 프로필 분석을 수행 하는 방법에 설명 합니다.|
|[릴리스 전에 앱 성능 테스트](/azure/devops/test/load-test/run-performance-tests-app-before-release?view=vsts)|SharePoint 응용 프로그램 스트레스 테스트 하는 데 도움이 되는 부하 테스트를 만드는 방법을 설명 합니다.|
|[코드 단위 테스트](../test/unit-test-your-code.md)|단위 테스트를 사용 하 여 코드에서 논리 오류를 찾는 방법을 설명 합니다.|
|[코딩된 UI 테스트를 사용하여 SharePoint 2010 애플리케이션 테스트](../test/testing-sharepoint-2010-applications-with-coded-ui-tests.md)|SharePoint 응용 프로그램의 사용자 인터페이스를 테스트 하는 방법에 설명 합니다.|

## <a name="see-also"></a>참고자료

- [SharePoint 솔루션 빌드 및 디버그](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [코드 품질 향상](../test/improve-code-quality.md)