---
title: 성능 탐색기 창 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performanceexplorer
- vs.performance.explorer
helpviewer_keywords:
- performance tools, Performance Explorer
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f27d1436aaeb0ec75876edf9119dff93f7539483
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/19/2018
ms.locfileid: "31582113"
---
# <a name="performance-explorer-window"></a>성능 탐색기 창

Visual Studio IDE의 **성능 탐색기** 창에서는 Visual Studio 프로파일링 도구를 사용하여 성능 세션을 구성 및 시작할 수 있습니다.

## <a name="performance-explorer-toolbar"></a>성능 탐색기 도구 모음

**성능 탐색기** 도구 모음에서는 다음 옵션을 사용할 수 있습니다.

- **성능 마법사 시작** - 성능 탐색기 창에 새 성능 세션을 추가할 수 있는 성능 마법사를 표시합니다.

- **새 성능 세션** - 성능 탐색기 창에 빈 성능 세션을 추가합니다.

- **시작** - **시작** 명령 단추 목록을 사용하면 프로파일을 즉시 사용하도록 설정한 대상 응용 프로그램을 시작(**프로파일링 시작**)하거나 프로파일링을 일시 중단한 대상 응용 프로그램을 시작(**일시 중지된 프로파일링 시작**)할 수 있습니다.

- **방법** - 세션의 프로파일링 방법(샘플링 또는 계측)을 지정합니다.

- **중지** - 대상 응용 프로그램과 프로파일러를 즉시 종료합니다.

- **연결/분리** - 프로파일러를 연결할 실행 중인 프로세스를 선택할 수 있는 **프로세스에 프로파일러 연결** 대화 상자를 표시합니다.

## <a name="performance-explorer-window"></a>성능 탐색기 창

**성능 탐색기** 창에는 성능 세션 하나 이상의 이진 파일 및 보고서 데이터 파일이 표시되는 트리 컨트롤이 포함되어 있습니다.

- **세션 이름** - 트리 컨트롤의 루트에는 세션의 이름이 포함되어 있습니다. 세션 이름을 마우스 오른쪽 단추로 클릭하여 세션 속성을 설정하거나 대상 응용 프로그램 및 프로파일러를 시작합니다.

- **대상** - 세션에서 프로파일링할 이진 파일의 이름이 표시됩니다. **대상**을 마우스 오른쪽 단추로 클릭하여 이진 파일, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 프로젝트 또는 웹 사이트를 추가하거나 제거합니다. 대상 이름을 마우스 오른쪽 단추로 클릭하면 개별 이진 파일에 대한 속성을 설정할 수 있습니다.

- **보고서** - 세션에 대해 생성되는 프로파일러 데이터 파일의 이름이 표시됩니다. **보고서**를 마우스 오른쪽 단추로 클릭하여 기존 보고서를 추가하거나 두 프로파일러 데이터 파일을 비교합니다. 보고서 이름을 마우스 오른쪽 단추로 클릭하여 프로파일러 데이터 파일을 열거나 제거하거나 내보냅니다.

## <a name="see-also"></a>참고 항목

[개요](../profiling/overviews-performance-tools.md)  
[성능 세션 구성](../profiling/configuring-performance-sessions.md)  
[데이터 수집 제어](../profiling/controlling-data-collection.md)