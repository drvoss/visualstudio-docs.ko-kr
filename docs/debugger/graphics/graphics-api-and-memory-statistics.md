---
title: 그래픽 API 및 메모리 통계 | Microsoft Docs
ms.date: 03/02/2017
ms.topic: conceptual
f1_keywords:
- vs.graphics.apistatistics
- vs.graphics.memorystatistics
ms.assetid: 27d2f303-e3ed-4219-9009-345a0d849506
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7810889d4af411477573c71aa694d797a90763f3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62896021"
---
# <a name="graphics-api-and-memory-statistics"></a>그래픽 API 및 메모리 통계
<!-- VERSIONLESS -->
Visual Studio 2017 이상 그래픽 API 통계 및 메모리 통계 도구를 지원 합니다.  이러한 두 도구를 통해 Direct3D API 사용 뿐만 아니라 다양 한 리소스의 GPU 메모리 사용량에서 다양 한 비트 정보를 볼 수 있습니다.

## <a name="graphics-api-statistics"></a>그래픽 API 통계
Visual Studio 그래픽 진단의 그래픽 API 통계를 사용 하면 모든 적용 된 Direct3D 호출 및 각 호출의 수를 볼 수 있습니다.  창을 보려면를 선택 합니다 **보기 > API 통계** 메뉴 항목입니다.

![API 통계](media/gfx_diag_api_statistics.png)

이 도구는 DirectX 호출 수를 인지 하지 못할 수도 있다는, 검색 또는 너무 자주 수행 중인 호출에서 유용 하 게 수 있습니다.

모두 복사 데이터 창에서을 마우스 오른쪽 단추로 추가 분석을 위해 Excel 같은에 붙여 넣을 수 있는 CSV로 수 있습니다.

## <a name="memory-statistics"></a>메모리 통계
이 도구는 프레임에서 만든 리소스에 대 한 그래픽 드라이버를 할당 하는 메모리의 양을 표시 됩니다.  이 창을 보려면 선택 합니다 **보기 > 메모리 통계** 메뉴 항목입니다.

![메모리 통계](media/gfx_diag_memory_statistics.png)

합니다 **GPU 할당** 열에 표시 된 이벤트에 의해 사용 된 메모리의 크기를 표시 합니다 **이벤트** 열입니다.  조사식 아이콘을 선택할 수도 있습니다 ![조사식 아이콘](media/gfx_watch.png) 보려는 합니다 [리소스 기록](graphics-event-list.md#resource-history) 선택한 이벤트에 대 한 합니다.

API 통계 도구와 마찬가지로 추가 분석을 위해 Excel 같은에 붙여 넣을 수 있는 CSV로 모두 복사 데이터 창에 있는 단추로 수 있습니다.

## <a name="see-also"></a>참고 항목
- [그래픽 진단(DirectX 그래픽 디버그)](visual-studio-graphics-diagnostics.md)
- [리소스 기록](graphics-event-list.md#resource-history)
<!-- /VERSIONLESS -->