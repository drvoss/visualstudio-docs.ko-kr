---
title: Visual Studio에서 부하 테스트 결과 비교
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, reporting
- load tests, results
ms.assetid: 31874114-459a-45d5-9f8b-2ea503627db8
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 8829644e34c169f8992959013f70d453a70d41b8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49834289"
---
# <a name="report-load-tests-results-for-test-comparisons-or-trend-analysis"></a>테스트 비교 또는 추세 분석을 위한 부하 테스트 결과 보고

둘 이상의 테스트 결과를 기반으로 Microsoft Excel 부하 테스트 보고서를 생성할 수 있습니다. 다음과 같은 두 가지 유형의 부하 테스트 보고서를 사용할 수 있습니다.

- 비교 실행&mdash;이 보고서는 테이블 차트와 가로 막대형 차트를 사용하여 side by side 비교 데이터를 표시하는 실제로 두 개의 보고서입니다.

- 추세&mdash;둘 이상의 보고서에 대한 추세 분석을 생성할 수 있습니다. 결과는 꺾은선형 차트를 사용하여 표시됩니다.

이러한 보고서는 성능 데이터를 관련자와 공유하고 시스템의 전반적인 성능 및 상태가 점점 좋아지는지 아니면 나빠지는지에 대한 정보를 전달하는 데 사용할 수 있습니다.

보고서 정의는 부하 테스트 데이터베이스에 저장됩니다. 보고서가 저장되면 해당 보고서의 정의가 데이터베이스에 저장되고 나중에 다시 사용할 수 있습니다.

또한 관련자가 데이터베이스에 연결하지 않아도 보고서를 볼 수 있도록 스프레드시트 파일을 관련자와 공유할 수도 있습니다.

> [!NOTE]
> 부하 테스트에 주석을 추가하면 Excel 보고서에 해당 주석이 표시됩니다. 자세한 내용은 [방법: 완료된 부하 테스트를 분석하는 동안 주석 추가](../test/how-to-add-comments-on-a-completed-load-test.md)를 참조하세요.

## <a name="tasks"></a>작업

|작업|관련 항목|
|-|-|
|**성능 및 스트레스 보고서 만들기:** Microsoft Excel을 사용하여 부하 및 웹 성능 테스트에 대한 보고서를 만들 수 있습니다.|- [방법: Microsoft Excel을 사용하여 부하 테스트 성능 보고서 만들기](../test/how-to-create-load-test-performance-reports-using-microsoft-excel.md)|
|**Microsoft Word를 사용하여 수동으로 성능 및 스트레스 보고서 만들기:** 요약, 테이블 및 그래프 데이터를 Microsoft Word 문서에 복사하여 붙여넣는 방법으로 부하 및 웹 성능 테스트에 대한 보고서를 수동으로 만들 수 있습니다.|- [방법: Microsoft Word를 사용하여 수동으로 부하 테스트 성능 보고서 만들기](../test/how-to-manually-create-a-load-test-performance-report-using-microsoft-word.md)|

## <a name="see-also"></a>참고 항목

- [부하 테스트 결과 분석](../test/analyze-load-test-results-using-the-load-test-analyzer.md)