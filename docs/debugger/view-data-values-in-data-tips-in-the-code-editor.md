---
title: DataTips에서 변수 값을 확인 합니다. | Microsoft Docs
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
ms.openlocfilehash: 2a4674dec4b15f608eb25ffaf62c97efcc2363ab
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62929967"
---
# <a name="view-data-values-in-datatips-in-the-code-editor"></a>코드 편집기에서 DataTips의 데이터 값 보기

DataTips를 통해 디버깅하는 동안 프로그램의 변수에 대한 정보를 손쉽게 볼 수 있습니다. DataTips는 중단 모드에서 현재 실행 범위 내의 변수에 대해서만 작동합니다. 읽을 하려는 처음 코드를 디버그 하려는 경우 [초보자를 위한 디버깅](../debugger/debugging-absolute-beginners.md) 하 고 [기술 및 도구 디버깅](../debugger/write-better-code-with-visual-studio.md) 이 문서를 진행 하기 전에 합니다.

## <a name="work-with-datatips"></a>DataTips를 사용 하 여 작동 합니다.

DataTips는 중단 모드 에서만에서 현재 실행 범위에 있는 변수 에서만 나타납니다.

### <a name="display-a-datatip"></a>DataTip을 표시

1. 코드에서 중단점을 설정 하 고 키를 눌러 디버깅을 시작할 **F5** 누르거나 **디버그** > **디버깅 시작**합니다.

1. 중단점에서 일시 중지 하는 경우 현재 범위에 있는 변수 위에 마우스를 가져갑니다. 이름 및 변수의 현재 값을 보여 주는 DataTip이 나타납니다.

### <a name="make-a-datatip-transparent"></a>DataTip을 투명 하 게 만들기

DataTip을 DataTip에서 그 아래에 있는 코드를 투명 하 게 하려면 키를 누릅니다 **Ctrl**합니다. 누르고 DataTip 투명 하 게 유지 합니다 **Ctrl** 키입니다. 이 고정 또는 부동 DataTips에 대 한 작동 하지 않습니다.
### <a name="pin-a-datatip"></a>DataTip pin

파일을 열린 상태로 유지 됩니다 있도록 DataTip을 고정 하려면 압정 선택 **소스에 고정** 아이콘입니다.

![DataTip을 고정할](../debugger/media/dbg-tips-data-tips-pinned.png "DataTip을 고정")

코드 창에서 끌어 고정된 된 DataTip을 이동할 수 있습니다. 압정 아이콘을 DataTip을 고정 되어 줄 옆에 있는 여백에 나타납니다.

>[!NOTE]
>DataTips는 항상 실행이 일시 중단 된 컨텍스트, 하지는 현재 커서 위치나 DataTip에서 계산 됩니다. 현재 컨텍스트에서 변수와 이름이 같은 다른 함수에 변수를 마우스로 가리키면 현재 컨텍스트의 변수 값이 표시 됩니다.

### <a name="unpin-a-datatip-from-source"></a>원본의 DataTip을 고정 해제

고정된 된 DataTip을 float를 DataTip 위에 놓고 상황에 맞는 메뉴에서 압정 아이콘을 선택 합니다.

고정 해제 된 위치로 압정 아이콘으로 변경 하 고 이제 DataTip 부동 또는 열려 있는 창을 모두 위에 놓을 수 있습니다. 부동 DataTips는 디버깅 세션이 종료 될 때를 닫습니다.

### <a name="repin-a-datatip"></a>DataTip을 다시 고정

원본에 부동 DataTip을 다시 고정 하려면 코드 편집기에서 위로 마우스를 압정 아이콘을 선택 합니다. 압정 아이콘으로 고정 된 위치로 변경 및 DataTip이 코드 창에만 다시 고정 합니다.

DataTip 비 소스 코드 창에 대 한 부동 창인 경우 압정 아이콘으로 표시를 사용할 수 없는 및 DataTip repinned 수 없습니다. 압정 아이콘에 액세스 하려면 DataTip 코드 편집기 창으로 끌거나 코드 창 포커스를 제공 하 여 반환 합니다.

### <a name="close-a-datatip"></a>DataTip을 닫으려면

DataTip을 닫으려면 DataTip을 마우스로 및 닫기 선택 (**x**) 상황에 맞는 메뉴에서 아이콘입니다.

### <a name="close-all-datatips"></a>모든 DataTips를 닫으려면

모든 DataTips를 닫으려면에 **디버그** 메뉴에서 **모든 DataTips 지우기**합니다.

### <a name="close-all-datatips-for-a-specific-file"></a>특정 파일에 대 한 모든 DataTips를 닫으려면

모든 DataTips를 닫으려면는 특정 파일에 **디버그** 메뉴에서 **지우기 고정 된 모든 DataTips를 \<파일 이름 >** 합니다.

## <a name="expand-and-edit-information"></a>확장 하 고 정보 편집
DataTips를 사용하면 배열, 구조체 또는 개체를 확장하여 해당 멤버를 볼 수 있습니다. DataTips에서 변수 값을 편집할 수도 있습니다.

### <a name="expand-a-variable"></a>변수 확장

해당 요소를 보려면 DataTip에서 개체를 확장 하려면 요소가 트리 형태로 표시할 항목 이름 앞에 있는 확장 화살표 위로 가져갑니다. 고정 된 DataTip을 선택 합니다 **+** 변수 앞 이름을 지정 하 고 다음 트리를 확장 합니다.

![확장 DataTip](../debugger/media/dbg-tour-data-tips.png "DataTip 확장")

확장된 된 보기에서 아래로 이동 하려면 키보드에서 마우스 또는 화살표 키를 사용할 수 있습니다.

또한 마우스로 해당 압정 아이콘을 선택 하 여 확장 된 항목을 고정 된 DataTip 고정할 수 있습니다. 요소 트리를 축소 한 후 고정 된 DataTip에 나타납니다.

### <a name="edit-the-value-of-a-variable"></a>변수 값 편집

변수 또는 DataTip에서 요소 값을 편집 하려면 선택 값, 새 값을 형식 및 키를 눌러 **Enter**합니다. 선택은 읽기 전용 값에 대 한 비활성화 됩니다.

## <a name="visualize-complex-data-types"></a>복잡 한 데이터 형식을 시각화합니다

하나 이상의 변수 또는 DataTip에서 요소 옆에 있는 돋보기 아이콘을 의미 [시각화 도우미](../debugger/create-custom-visualizers-of-data.md)와 같은 합니다 [텍스트 시각화 도우미](../debugger/string-visualizer-dialog-box.md), 변수에 사용할 수 있습니다. 시각화 도우미 보다 의미 있는, 경우에 따라 그래픽 방식으로 정보를 표시 합니다.

데이터 형식에 대 한 기본 시각화 도우미를 사용 하 여 요소를 보려면 돋보기 아이콘을 선택 ![시각화 아이콘](../debugger/media/dbg-tips-visualizer-icon.png "시각화 아이콘")합니다. 데이터 형식에 대 한 시각화 도우미 목록에서 선택 하려면 돋보기 아이콘 옆의 화살표를 선택 합니다.

## <a name="add-a-variable-to-a-watch-window"></a>조사식 창에 변수를 추가 합니다.

변수 조사를 계속 하려는 경우에 추가할 수 있습니다는 **조사식** DataTip에서 창입니다. DataTip에서 변수를 마우스 오른쪽 단추로 클릭 **조사식 추가**합니다.

변수의 나타나는 합니다 **조사식** 창입니다. Visual Studio 버전을 지 원하는 둘 이상의 경우 **Watch** 창에 변수 표시 됩니다 **조사식 1**합니다.

## <a name="import-and-export-datatips"></a>DataTips 내보내기 및 가져오기

DataTips를 공유 하거나 텍스트 편집기를 사용 하 여 편집할 수 있는 XML 파일로 내보낼 수 있습니다. 또한 받거나 편집할 DataTip XML 파일을 가져올 수 있습니다.

**DataTips를 내보내려면:**

1. 선택 **디버깅할** > **DataTips 내보내기**합니다.

1. 에 **DataTips 내보내기** 대화 상자에서 파일의 이름을 입력 XML 파일을 저장할 위치로 이동한 다음 선택 **저장**합니다.

**DataTips를 가져오려면:**

1. 선택 **디버깅할** > **DataTips 가져오기**합니다.

1. 에 **DataTips 가져오기** 대화 상자를 연 다음 선택 하려는 DataTips XML 파일을 선택 합니다 **엽니다**합니다.

## <a name="see-also"></a>참고자료
- [디버깅이란?](../debugger/what-is-debugging.md)
- [디버깅 기술 및 도구](../debugger/write-better-code-with-visual-studio.md)
- [디버깅 소개](../debugger/debugger-feature-tour.md)
- [디버거에서 데이터 보기](../debugger/viewing-data-in-the-debugger.md)
- [조사식 및 간략한 조사식 창](../debugger/watch-and-quickwatch-windows.md)
- [Create Custom Visualizers of Data](../debugger/create-custom-visualizers-of-data.md)(데이터의 사용자 지정 시각화 도우미 만들기)
