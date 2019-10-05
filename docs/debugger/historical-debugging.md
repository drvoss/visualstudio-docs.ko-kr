---
title: 기록 디버깅 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7cc5ddf2-2f7c-4f83-b7ca-58e92e9bfdd2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e44e62997cac1060047de03253880bbf577935da
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62895171"
---
# <a name="historical-debugging-c-visual-basic-c"></a>기록 디버깅 (C#, Visual Basic의 경우 C++)

기록 디버깅은 IntelliTrace에서 수집된 정보에 의존하는 디버깅 모드입니다. 이 디버깅을 사용하면 애플리케이션 실행 도중 앞이나 뒤로 이동하며 상태를 검사할 수 있습니다.

 Visual Studio Enterprise Edition(Professional 또는 Community Edition 아님)에서 IntelliTrace를 사용할 수 있습니다.

## <a name="why-use-historical-debugging"></a>기록 디버깅을 사용하는 이유는?

 버그를 찾는 중단점을 설정하는 것은 적중하느냐 누락하느냐의 문제입니다. 코드에서 버그가 있을 것으로 의심되는 위치 가까이에 중단점을 설정하면 디버거에서 애플리케이션을 실행할 때 중단점이 적중될 것으로 기대할 수 있고, 이에 따라 실행이 중단된 위치가 버그 소스를 노출할 수 있습니다. 그러지 않은 경우 코드 내의 다른 위치에 중단점을 설정하고 디버거를 다시 실행해야 합니다. 즉, 문제를 발견할 때까지 테스트 단계를 반복적으로 실행해야 합니다.

 ![중단점을 설정](../debugger/media/breakpointprocesa.png "BreakpointProcesa")

 IntelliTrace와 기록 디버깅을 사용하여 중단점을 설정하고 디버깅을 다시 시작하고 테스트 단계를 반복할 필요 없이 애플리케이션 내부를 이동하면서 상태(호출 스택 및 로컬 변수)를 검사할 수 있습니다. 이렇게 하면 특히 버그가 테스트 시나리오의 깊은 수준에 있어서 실행하는 데 오래 걸리는 경우 많은 시간을 절약할 수 있습니다.

## <a name="how-do-i-start-using-historical-debugging"></a>기록 디버깅을 사용하여 시작하는 방법은?

IntelliTrace는 기본적으로 설정되어 있습니다. 이벤트 및 함수 호출 관심 하 고 전체 응용 프로그램 상태의 스냅숏 보기 것인지 결정 하면 됩니다. 찾으려는 항목을 정의하는 방법에 대한 자세한 내용은 [IntelliTrace 기능](../debugger/intellitrace-features.md)을 참조하세요. 지원 되는 기능 언어 및 앱에 따라 형식입니다.

- 기록 디버깅을 사용 하는 스냅숏을 보려면 참조 [IntelliTrace를 사용 하 여 이전 앱 상태를 검사 합니다.](../debugger/view-historical-application-state.md)
- 변수를 검사 하 고 코드를 탐색 하는 방법에 알아보려면 참조 [기록 디버깅을 사용 하 여 앱 검사](../debugger/historical-debugging-inspect-app.md)
- IntelliTrace 이벤트를 사용 하 여 디버깅 하는 방법에 대 한 자세한 내용은를 참조 하세요. [연습: IntelliTrace를 사용 하 여](../debugger/walkthrough-using-intellitrace.md)입니다.