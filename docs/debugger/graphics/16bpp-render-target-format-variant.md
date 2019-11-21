---
title: 16bpp Render Target Format Variant | Microsoft Docs
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
# <a name="16-bpp-render-target-format-variant"></a>16 bpp Render Target Format Variant
모든 렌더링 대상 및 백 버퍼에 대한 픽셀 형식을 DXGI_FORMAT_B5G6R5_UNORM으로 설정합니다.

## <a name="interpretation"></a>해석
 A render target or back buffer typically uses a 32 bpp (32 bits per pixel) format such as B8G8R8A8_UNORM. 32-bpp formats can consume a large amount of memory bandwidth. Because the B5G6R5_UNORM format is a 16-bpp format that's half the size of 32-bpp formats, using it can relieve pressure on memory bandwidth, but at the cost of reduced color fidelity.

 이러한 변형으로 성능이 크게 향상되면 앱에서 메모리 대역폭을 너무 많이 사용함을 나타내는 것일 수 있습니다. You can gain significant performance improvement, especially when the profiled frame had a significant amount of overdraw or alpha-blending.

A 16-bpp render target format can reduce memory band with usage when your application has the following conditions:
- Doesn't require high-fidelity color reproduction.
- Doesn't require an alpha channel.
- Doesn't often have smooth gradients (which are susceptible to banding artifacts under reduced color fidelity).

Other strategies to reduce memory bandwidth include:
- Reduce the amount of overdraw or alpha-blending.
- Reduce the dimensions of the frame buffer.
- Reduce dimensions of texture resources.
- Reduce compressions of texture resources.

일반적으로 이러한 최적화에 수반되는 이미지 품질 문제도 고려해야 합니다.

Applications that are a part of a swap chain have a back buffer format (DXGI_FORMAT_B5G6R5_UNORM) that doesn't support 16 bpp. These swap chains are created by using `D3D11CreateDeviceAndSwapChain` or `IDXGIFactory::CreateSwapChain`. To work around this limitation, do the following steps:
1. Create a B5G6R5_UNORM format render target by using `CreateTexture2D` and render to that target.
2. Copy the render target onto the swap-chain backbuffer by drawing a full-screen quad with the render target as your source texture.
3. Call Present on your swap chain.

   If this strategy saves more bandwidth than is consumed by copying the render target to the swap-chain backbuffer, then rendering performance is improved.

   GPU architectures that use tiled rendering techniques can see significant performance benefits by using a 16 bpp frame buffer format. This improvement is because a larger portion of the frame buffer can fit in each tile's local frame buffer cache. 타일식 렌더링 아키텍처는 경우에 따라 모바일 송수화기 및 태블릿 컴퓨터의 GPU에 있으므로 이 방식의 아키텍처가 이러한 위치 밖으로 드러나는 일은 거의 없습니다.

## <a name="remarks"></a>주의
 렌더링 대상을 만드는 `ID3D11Device::CreateTexture2D`에 대한 호출 시 마다 렌더링 대상 형식은 DXGI_FORMAT_B5G6R5_UNORM으로 다시 설정됩니다. 특히 이 형식은 pDesc에서 전달된 D3D11_TEXTURE2D_DESC 개체가 렌더링 대상을 설명하는 경우 재정의됩니다. 즉, 다음과 같은 경우입니다.

- BindFlags 멤버에 D3D11_BIND_REDNER_TARGET 플래그 집합이 있는 경우

- BindFlags 멤버에 D3D11_BIND_DEPTH_STENCIL 플래그가 지워진 경우

- Usage 멤버가 D3D11_USAGE_DEFAULT로 설정된 경우

## <a name="restrictions-and-limitations"></a>제한 사항
 B5G6R5 형식에는 알파 채널이 없으므로 이 변형은 알파 콘텐츠를 유지하지 않습니다. 앱에서 렌더링하려면 렌더링 대상에 알파 채널이 있어야 하는 경우 간단히 B5G6R5 형식으로 전환할 수 있는 것이 아닙니다.

## <a name="example"></a>예제
 The **16 bpp Render Target Format** variant can be reproduced for render targets created by using `CreateTexture2D` by using code like this:

```cpp
D3D11_TEXTURE2D_DESC target_description;

target_description.BindFlags = D3D11_BIND_RENDER_TARGET;
target_description.Format = DXGI_FORMAT_B5G6R5_UNORM;
d3d_device->CreateTexture2D(&target_description, nullptr, &render_target);
```
