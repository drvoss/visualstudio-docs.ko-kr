---
title: '방법: 워크플로 디자이너에서 검색 사용'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f42d3115-2ed2-4941-8f1e-92dac41c30fa
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 0a80bfecaa288eabc0161d0262535a7912411f78
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62949576"
---
# <a name="how-to-use-search-in-the-workflow-designer"></a>방법: 워크플로 디자이너에서 검색 사용

큰 규모의 더 복잡 한 워크플로 만들기를 용이 하 게 키워드로 항목을 찾으려면 워크플로 디자이너 내에서 검색할 수 있습니다. 디자이너는 바꾸기를 지원하지 않습니다.

## <a name="quick-find"></a>빠른 찾기

빠른 찾기는 디자이너에서 다음을 찾습니다.

- <xref:System.Activities.Activity> 개체, <xref:System.Activities.Statements.FlowNode> 개체, <xref:System.Activities.Statements.State> 개체, 전환 및 기타 사용자 지정 흐름 제어 항목의 속성

- 변수

- 인수

- 식

### <a name="use-quick-find"></a>빠른 찾기 사용

1. 워크플로 디자이너를 연을 누릅니다 **Ctrl + F**를 선택 하거나 **편집** > **찾기 및 바꾸기** > **빠른 찾기**.

2. 에 검색어를 입력 합니다 **찾을 내용** 텍스트 상자 클릭 **다음 찾기**합니다.

3. 검색어는 현재 워크플로에 있습니다. 다음 이미지에는 디자이너에 있는 중인 활동 표시 이름을 보여 줍니다.

   ![워크플로 디자이너의 검색 결과](../workflow-designer/media/designersearch.png)

## <a name="find-in-files"></a>파일에서 찾기

파일에서 찾기는 XAML 파일을 포함 하 여 워크플로 파일에서 문자열을 찾습니다.

### <a name="use-find-in-files"></a>파일에서 찾기 사용

1. Visual Studio에서 눌러 **Ctrl**+**Shift**+**F**를 선택 하거나 **편집**  >   **찾기 및 바꾸기** > **파일에서 찾기**합니다.

2. 에 검색 조건을 입력 합니다 **찾을 내용** 텍스트 상자 클릭 **모두 찾기**합니다.

3. 찾기 결과가 표시 되는 **찾기 결과** 보기. 워크플로 디자이너의 일치 항목이 포함 된 활동을 탐색 결과 항목을 두 번 클릭 합니다.