---
title: 16bpp 렌더링 대상 형식 변형 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 24b22ad9-5ad0-4161-809a-9b518eb924bf
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8a63261a4ef8a6304bec8c2bdde1d9ec9113405e
ms.sourcegitcommit: 8530d15aa72fe058ee3a3b4714c36b8638f8b494
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/19/2019
ms.locfileid: "74188585"
---
# <a name="16-bpp-render-target-format-variant"></a>16 bpp 렌더링 대상 형식 변형
모든 렌더링 대상 및 백 버퍼에 대한 픽셀 형식을 DXGI_FORMAT_B5G6R5_UNORM으로 설정합니다.

## <a name="interpretation"></a>해석
 렌더링 대상 또는 백 버퍼는 일반적으로 B8G8R8A8_UNORM와 같은 32 bpp (픽셀 당 32 비트) 형식을 사용 합니다. 32-bpp 형식에서 많은 양의 메모리 대역폭을 사용할 수 있습니다. B5G6R5_UNORM 형식은 32-bpp 형식 크기의 절반에 해당 하는 16 bpp 형식이 기 때문에이를 사용 하면 메모리 대역폭의 압력을 줄일 수 있지만 색 정확도가 낮아질 수 있습니다.

 이러한 변형으로 성능이 크게 향상되면 앱에서 메모리 대역폭을 너무 많이 사용함을 나타내는 것일 수 있습니다. 특히 프로 파일링 된 프레임에 지나치게 많은 그리기 또는 알파 혼합이 있는 경우 상당한 성능 향상을 얻을 수 있습니다.

16 bpp 렌더링 대상 형식은 응용 프로그램에 다음과 같은 조건이 있는 경우 사용량을 사용 하 여 메모리 대역을 줄일 수 있습니다.
- 고화질 색 복제는 필요 하지 않습니다.
- 알파 채널이 필요 하지 않습니다.
- 보통 부드러운 그라데이션을 포함 하지 않습니다 (색 충실도 축소 된 줄무늬 아티팩트에 취약).

메모리 대역폭을 줄이는 다른 전략은 다음과 같습니다.
- 과도 한 그리기 또는 알파 혼합의 양을 줄입니다.
- 프레임 버퍼의 크기를 줄입니다.
- 질감 리소스의 크기를 줄입니다.
- 텍스처 리소스의 압축을 줄입니다.

일반적으로 이러한 최적화에 수반되는 이미지 품질 문제도 고려해야 합니다.

스왑 체인의 일부인 응용 프로그램에는 16 bpp를 지원 하지 않는 백 버퍼 형식 (DXGI_FORMAT_B5G6R5_UNORM)이 있습니다. 이러한 스왑 체인은 `D3D11CreateDeviceAndSwapChain` 또는 `IDXGIFactory::CreateSwapChain`를 사용 하 여 생성 됩니다. 이 제한 사항을 해결 하려면 다음 단계를 수행 합니다.
1. `CreateTexture2D`를 사용 하 여 렌더링 대상 B5G6R5_UNORM 형식을 만들고 해당 대상에 렌더링 합니다.
2. 렌더링 대상을 원본 질감으로 사용 하 여 전체 화면 쿼드를 그리면 렌더링 대상을 스왑 체인 백 버퍼에 복사 합니다.
3. 교환 체인에 있는 호출입니다.

   이 전략이 렌더링 대상을 스왑 체인 백 버퍼에 복사 하는 데 사용 되는 것 보다 더 많은 대역폭을 절약 하는 경우 렌더링 성능이 향상 됩니다.

   바둑판식으로 렌더링 기법을 사용 하는 GPU 아키텍처는 16 bpp 프레임 버퍼 형식을 사용 하 여 상당한 성능상의 이점을 얻을 수 있습니다. 이러한 향상 된 기능은 프레임 버퍼의 더 큰 부분이 각 타일의 로컬 프레임 버퍼 캐시에 맞을 수 있기 때문입니다. 타일식 렌더링 아키텍처는 경우에 따라 모바일 송수화기 및 태블릿 컴퓨터의 GPU에 있으므로 이 방식의 아키텍처가 이러한 위치 밖으로 드러나는 일은 거의 없습니다.

## <a name="remarks"></a>주의
 렌더링 대상을 만드는 `ID3D11Device::CreateTexture2D`에 대한 호출 시 마다 렌더링 대상 형식은 DXGI_FORMAT_B5G6R5_UNORM으로 다시 설정됩니다. 특히 이 형식은 pDesc에서 전달된 D3D11_TEXTURE2D_DESC 개체가 렌더링 대상을 설명하는 경우 재정의됩니다. 즉, 다음과 같은 경우입니다.

- BindFlags 멤버에 D3D11_BIND_REDNER_TARGET 플래그 집합이 있는 경우

- BindFlags 멤버에 D3D11_BIND_DEPTH_STENCIL 플래그가 지워진 경우

- Usage 멤버가 D3D11_USAGE_DEFAULT로 설정된 경우

## <a name="restrictions-and-limitations"></a>제한 사항
 B5G6R5 형식에는 알파 채널이 없으므로 이 변형은 알파 콘텐츠를 유지하지 않습니다. 앱에서 렌더링하려면 렌더링 대상에 알파 채널이 있어야 하는 경우 간단히 B5G6R5 형식으로 전환할 수 있는 것이 아닙니다.

## <a name="example"></a>예제
 다음과 같은 코드를 사용 하 여 `CreateTexture2D`를 사용 하 여 만든 렌더링 대상에 대해 **16 Bpp 렌더링 대상 형식** 변형을 재현할 수 있습니다.

```cpp
D3D11_TEXTURE2D_DESC target_description;

target_description.BindFlags = D3D11_BIND_RENDER_TARGET;
target_description.Format = DXGI_FORMAT_B5G6R5_UNORM;
d3d_device->CreateTexture2D(&target_description, nullptr, &render_target);
```
