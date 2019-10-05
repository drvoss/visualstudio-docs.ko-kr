---
title: 1x1 뷰포트 크기 변형 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3dbc3247-00f5-4644-8ff9-72e9febcf09a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a5b2c96b11c2075ce88b43cdebc34b905141c973
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62848733"
---
# <a name="1x1-viewport-size-variant"></a>1x1 뷰포트 크기 변형
모든 렌더링 대상의 뷰포트 크기를 1x1 픽셀로 줄입니다.

## <a name="interpretation"></a>해석
 뷰포트가 더 작으면 음영 처리 해야 하는 픽셀 수를 줄입니다. 뷰포트가 더 작으면 해야 하는 꼭 짓 점 수가 줄이지는 않지만 프로세스입니다. 뷰포트 크기를 1x1픽셀로 설정하면 앱에서 픽셀 음영이 효과적으로 제거됩니다.

 이 변형이 성능을 크게 향상, 앱에서 너무 많은 채우기 속도 사용 하 나타낼 수 있습니다. 또한 확인을 위해 대상 플랫폼에 대해 너무 길어질 수 있습니다 또는 앱에는 상당한 시간이 픽셀을 음영 처리 나중에 덮어쓰기 소비할 수, 라고도 *overdraw*합니다. 더 작은 프레임 버퍼 수를 줄이거나 overdraw 양을 앱의 성능이 향상 됩니다.

## <a name="remarks"></a>설명
 `ID3D11DeviceContext::OMSetRenderTargets` 또는 `ID3D11DeviceContext::RSSetViewports`를 호출한 후에는 항상 뷰포트 크기가 1x1로 다시 설정됩니다.

## <a name="example"></a>예제
 이 변형은 다음 코드를 사용 하 여 재현할 수 있습니다.

```cpp
D3D11_VIEWPORT viewport;
viewport.TopLeftX = 0;
viewport.TopLeftY = 0;
viewport.Width = 1;
viewport.Height = 1;
d3d_context->RSSetViewports(1, &viewport);
```
