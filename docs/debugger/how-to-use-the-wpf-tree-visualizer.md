---
title: '방법: WPF 트리 시각화 도우미를 사용 하 여 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- WPF, debugging
- debugging, WPF
ms.assetid: 2a1bf1cd-90f9-4d06-9fb4-1bfc925afef3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4e005c1b41d2c563c5b47f358e87912cba64bf7f
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67821382"
---
# <a name="how-to-use-the-wpf-tree-visualizer"></a>방법: WPF 트리 시각화 도우미 사용
WPF 트리 시각화 도우미를 사용하여 WPF 개체의 표시 트리를 탐색하고 트리에 포함된 개체의 WPF 종속성 속성을 볼 수 있습니다. 시각적 트리에 대 한 자세한 내용은 참조 하세요. [WPF의 트리](/dotnet/framework/wpf/advanced/trees-in-wpf)합니다. 종속성 속성에 대 한 자세한 내용은 참조 하세요. [종속성 속성 개요](/dotnet/framework/wpf/advanced/dependency-properties-overview)합니다.

 WPF 트리 시각화 도우미를 열면 두 개의 창이 표시 됩니다: 합니다 **시각적 트리** 왼쪽 하며 **의 속성** _이름_ **:**  _형식_ 오른쪽 창입니다. 모든 개체를 선택 합니다 **시각적 트리** 창 및 **속성을** _이름_ **:** _형식_ 창은 해당 개체에 대 한 속성을 표시 하도록 자동으로 업데이트 합니다.

### <a name="to-open-the-wpf-tree-visualizer"></a>WPF 트리 시각화 도우미를 열려면

1. DataTip, **조사식** 창, **자동** 창 또는 **로컬** 창에서 WPF 개체 이름 옆에 나타나는 돋보기 모양 아이콘 옆의 화살표를 클릭합니다.

     시각화 도우미의 목록이 나타납니다.

2. **WPF 트리 시각화 도우미**를 클릭합니다.

### <a name="to-search-the-visual-tree"></a>표시 트리를 검색하려면

- **표시 트리** 창의 **검색** 상자에 검색할 문자열을 입력합니다.

  WPF 트리 시각화 도우미가 입력한 문자열과 일치하는 표시 트리의 첫 번째 개체를 즉시 찾습니다. 문자를 추가로 입력하여 좀 더 정확하게 일치하는 항목을 찾을 수 있습니다.

  - 표시 트리 내에서 다음 일치 항목으로 이동하려면 **다음**을 클릭합니다.

  - 이전 일치 항목으로 이동하려면 **이전**을 클릭합니다.

  - 검색 조건을 지우려면 **지우기**를 클릭합니다.

### <a name="to-search-the-properties-list"></a>속성 목록을 검색하려면

- 에 **의 속성** _이름_ **:** _형식_ 창에서 검색 하려는 문자열을 입력 합니다 **필터링**상자입니다.

  WPF 트리 시각화 도우미가 입력한 문자열과 일치하는 속성을 즉시 찾습니다. 이제 목록에는 입력한 문자열과 일치하는 속성만 표시됩니다. 문자를 추가로 입력하여 좀 더 정확하게 일치하는 항목을 찾을 수 있습니다.

  - 검색 조건을 지우려면 **지우기**를 클릭합니다.

### <a name="to-close-the-visualizer"></a>시각화 도우미를 닫으려면

- 대화 상자의 오른쪽 위 모퉁이에서 **닫기** 아이콘을 클릭합니다.

## <a name="see-also"></a>참고 항목
- [Create Custom Visualizers of Data](../debugger/create-custom-visualizers-of-data.md)(데이터의 사용자 지정 시각화 도우미 만들기)
- [WPF의 트리](/dotnet/framework/wpf/advanced/trees-in-wpf)
- [종속성 속성 개요](/dotnet/framework/wpf/advanced/dependency-properties-overview)
