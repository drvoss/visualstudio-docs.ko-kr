---
title: DataTips에서 변수 값 보기 | Microsoft Docs
ms.custom: seodec18
ms.date: 11/21/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], DataTips
- DataTips tool
ms.assetid: ffa7bd18-439b-4685-a9b3-c7884b5de41f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f121c7aadb605e6eb87089556ddaf1b1f4999dbb
ms.sourcegitcommit: 0b90e1197173749c4efee15c2a75a3b206c85538
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/07/2019
ms.locfileid: "74903888"
---
# <a name="view-data-values-in-datatips-in-the-code-editor"></a>코드 편집기에서 DataTips의 데이터 값 보기

DataTips를 통해 디버깅하는 동안 프로그램의 변수에 대한 정보를 손쉽게 볼 수 있습니다. DataTips는 중단 모드에서 현재 실행 범위 내의 변수에 대해서만 작동합니다. 처음으로 코드를 디버그하려는 경우 이 문서를 진행하기 전에 [초보자를 위한 디버깅](../debugger/debugging-absolute-beginners.md)과 [기술 및 도구 디버깅](../debugger/write-better-code-with-visual-studio.md)을 먼저 읽고 오는것이 좋습니다.

## <a name="work-with-datatips"></a>DataTips 작업

DataTips는 중단 모드 에서만 나타나고 현재 실행 범위에 있는 변수에 대해서만 나타납니다.

### <a name="display-a-datatip"></a>DataTip 표시

1. 코드에 중단점을 설정 하 고 **F5** 키를 누르거나 **디버그** > **디버깅 시작**을 선택 하 여 디버깅을 시작 합니다.

1. 중단점에서 일시 중지 되 면 현재 범위에 있는 임의의 변수 위로 마우스를 가져갑니다. 변수의 이름 및 현재 값을 보여 주는 DataTip이 나타납니다.

### <a name="make-a-datatip-transparent"></a>Datatips를 투명 하 게 만들기

Datatip에서 아래 코드를 볼 수 있도록 DataTip을 투명 하 게 하려면 **ctrl**키를 누릅니다. **Ctrl** 키를 누르고 있으면 DataTip이 투명 하 게 유지 됩니다. 이는 고정 또는 부동 DataTips에는 적용 되지 않습니다.
### <a name="pin-a-datatip"></a>DataTip 고정

열려 있는 상태로 유지 되도록 DataTip을 고정 하려면 **원본에 고정** 압정 아이콘을 선택 합니다.

![DataTip 고정](../debugger/media/dbg-tips-data-tips-pinned.png "DataTip 고정")

고정 된 DataTip을 코드 창 주위로 끌어 이동할 수 있습니다. Datatips가 고정 된 줄 옆의 여백에 압정 아이콘이 표시 됩니다.

>[!NOTE]
>DataTips는 항상 현재 커서 또는 DataTip 위치가 아니라 실행이 일시 중단 된 컨텍스트에서 평가 됩니다. 현재 컨텍스트의 변수와 동일한 이름을 가진 다른 함수에서 변수를 가리키면 현재 컨텍스트의 변수 값이 표시 되는 것입니다.

### <a name="unpin-a-datatip-from-source"></a>원본에서 DataTip 고정 해제

고정 된 DataTip을 부동 하려면 Datatips 위로 마우스를 이동 하 고 상황에 맞는 메뉴에서 압정 아이콘을 선택 합니다.

압정 아이콘은 고정 해제 된 위치로 바뀌고, Datatips는 이제 모든 열린 창 위로 끌고 끌어 올 수 있습니다. 디버깅 세션이 종료 될 때 부동 DataTips가 닫힙니다.

### <a name="repin-a-datatip"></a>Datatips 다시 고정

부동 DataTip을 소스에 다시 고정 하려면 코드 편집기에서 해당 DataTip을 마우스로 가리키고 압정 아이콘을 선택 합니다. 압정 아이콘은 고정 된 위치로 바뀌고 Datatips는 코드 창에만 다시 고정 됩니다.

비 소스 코드 창에서 DataTip이 부동 상태인 경우 압정 아이콘을 사용할 수 없으며 DataTip을 다시 고정할 수 없습니다. 압정 아이콘에 액세스 하려면 코드 창 포커스를 끌거나 코드 편집기 창에 DataTip을 반환 합니다.

### <a name="close-a-datatip"></a>DataTip 닫기

Datatips를 닫으려면 Datatips 위에 마우스를 놓고 상황에 맞는 메뉴에서 닫기 (**x**) 아이콘을 선택 합니다.

### <a name="close-all-datatips"></a>모든 DataTips 닫기

모든 DataTips를 닫으려면 **디버그** 메뉴에서 **모든 datatips 지우기**를 선택 합니다.

### <a name="close-all-datatips-for-a-specific-file"></a>특정 파일에 대 한 모든 DataTips를 닫습니다.

특정 파일에 대 한 모든 DataTips를 닫으려면 **디버그** 메뉴에서 **\<파일 이름 >에 고정 된 모든 datatips 지우기**를 선택 합니다.

## <a name="expand-and-edit-information"></a>정보 확장 및 편집
DataTips를 사용하면 배열, 구조체 또는 개체를 확장하여 해당 멤버를 볼 수 있습니다. DataTips에서 변수 값을 편집할 수도 있습니다.

### <a name="expand-a-variable"></a>변수 확장

DataTip에서 개체를 확장 하 여 해당 요소를 보려면 항목 이름 앞에 있는 확장 화살표를 가리켜 요소를 트리 형식으로 표시 합니다. 고정 된 DataTip의 경우 변수 이름 앞에 **+** 를 선택 하 고 트리를 확장 합니다.

![DataTip 확장](../debugger/media/dbg-tour-data-tips.png "DataTip 확장")

키보드에서 마우스 또는 화살표 키를 사용 하 여 확장 된 뷰에서 위아래로 이동할 수 있습니다.

또한 확장 된 항목을 마우스로 가리키고 압정 아이콘을 선택 하 여 고정 된 DataTip에 고정할 수 있습니다. 그러면 트리가 축소 된 후 요소가 고정 된 DataTip에 나타납니다.

### <a name="edit-the-value-of-a-variable"></a>변수 값 편집

DataTip에서 변수나 요소의 값을 편집 하려면 값을 선택 하 고 새 값을 입력 한 다음 **enter**키를 누릅니다. 읽기 전용 값에는 선택이 비활성화 되어 있습니다.

::: moniker range=">= vs-2019"

## <a name="pin-properties-in-datatips-supported-in-visual-studio-2019-version-164-preview-3-or-higher"></a>DataTips의 속성 고정 (Visual Studio 2019 버전 16.4 Preview 3 이상에서 지원 됨)

> [!NOTE]
> 이 기능은 .NET Core 3.0 이상에서 지원 됩니다.

**Pinnable 속성** 도구를 사용 하 여 DataTips의 속성을 기준으로 개체를 신속 하 게 검사할 수 있습니다.  이 도구를 사용 하려면 속성 위로 마우스를 이동 하 고 표시 되는 고정 아이콘을 선택 하거나 마우스 오른쪽 단추를 클릭 하 고 결과 상황에 맞는 메뉴에서 **즐겨찾기로 멤버 고정** 옵션을 선택 합니다.  그러면 해당 속성은 개체의 속성 목록 맨 위에 표시 되 고 속성 이름과 값은 DataTip의 오른쪽 열에 표시 됩니다.  속성을 고정 해제 하려면 고정 아이콘을 다시 선택 하거나 상황에 맞는 메뉴에서 **멤버를 즐겨찾기로 고정 해제** 옵션을 선택 합니다.

![DataTip에서 속성 고정](../debugger/media/basic-pin-datatip.gif "DataTip에서 속성 고정")

Datatips에서 개체의 속성 목록을 볼 때 속성 이름을 전환 하 고 고정 되지 않은 속성을 필터링 할 수도 있습니다.  속성을 포함 하는 행을 마우스 오른쪽 단추로 클릭 하 고 상황에 맞는 메뉴의 값에서 고정 된 **멤버만 표시** 또는 **고정 멤버 이름 숨기기** 옵션을 선택 하 여 두 옵션 중 하나에 액세스할 수 있습니다.

::: moniker-end

## <a name="visualize-complex-data-types"></a>복합 데이터 형식 시각화

DataTip의 변수 또는 요소 옆에 있는 돋보기 아이콘은 [텍스트 시각화 도우미](../debugger/string-visualizer-dialog-box.md)와 같은 하나 이상의 [시각화 도우미가](../debugger/create-custom-visualizers-of-data.md)변수에 사용할 수 있음을 의미 합니다. 시각화 도우미는 보다 의미 있는 그래픽 방식으로 정보를 표시 합니다.

데이터 형식에 대 한 기본 시각화 도우미를 사용 하 여 요소를 보려면 돋보기 아이콘 ![시각화 도우미 아이콘](../debugger/media/dbg-tips-visualizer-icon.png "시각화 도우미 아이콘")을 선택 합니다. 돋보기 아이콘 옆의 화살표를 선택 하 여 데이터 형식에 대 한 시각화 도우미 목록에서 선택 합니다.

## <a name="add-a-variable-to-a-watch-window"></a>변수에 변수를 추가 조사식 창

변수를 계속 조사 하려면 DataTip에서 **조사식** 창에 변수를 추가할 수 있습니다. DataTip에서 변수를 마우스 오른쪽 단추로 클릭 하 고 **조사식 추가**를 선택 합니다.

변수가 **조사식** 창에 표시 됩니다. Visual Studio 버전에서 두 개 이상의 **조사식** 창을 지 원하는 경우 변수가 **조사식 1**에 표시 됩니다.

## <a name="import-and-export-datatips"></a>DataTips 가져오기 및 내보내기

텍스트 편집기를 사용 하 여 공유 하거나 편집할 수 있는 XML 파일로 DataTips를 내보낼 수 있습니다. 사용자가 받거나 편집한 DataTip XML 파일을 가져올 수도 있습니다.

**DataTips를 내보내려면:**

1.  > **디버깅** 을 선택 하 여 **DataTips를 내보냅니다**.

1. **DataTips 내보내기** 대화 상자에서 XML 파일을 저장할 위치로 이동 하 고 파일 이름을 입력 한 후 **저장**을 선택 합니다.

**DataTips를 가져오려면:**

1.  > **디버깅** 을 선택 하 여 **DataTips를 가져옵니다**.

1. **Datatips 가져오기** 대화 상자에서 열려는 datatips XML 파일을 선택한 다음 **열기**를 선택 합니다.

## <a name="see-also"></a>참조
- [디버깅이란?](../debugger/what-is-debugging.md)
- [디버깅 기술 및 도구](../debugger/write-better-code-with-visual-studio.md)
- [먼저 디버깅 살펴보기](../debugger/debugger-feature-tour.md)
- [디버거에서 데이터 보기](../debugger/viewing-data-in-the-debugger.md)
- [조사식 및 간략한 조사식 창](../debugger/watch-and-quickwatch-windows.md)
- [Create Custom Visualizers of Data](../debugger/create-custom-visualizers-of-data.md)(데이터의 사용자 지정 시각화 도우미 만들기)
