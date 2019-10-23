---
title: '연습: 프로그래밍 방식으로 그래픽 정보 캡처 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e2036588fe04825b0fe1a1aa2db7ae8f7e0b5ad4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72734764"
---
# <a name="walkthrough-capturing-graphics-information-programmatically"></a>연습: 프로그래밍 방식으로 그래픽 정보 캡처
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 그래픽 진단을 사용하여 Direct3D 앱에서 그래픽 정보를 프로그래밍 방식으로 캡처할 수 있습니다.

프로그래밍 방식 캡처는 다음과 같은 시나리오에서 유용합니다.

- 그래픽 앱이 swapchain present를 사용하지 않는 경우(예: 텍스처로 렌더링하는 경우) 프로그래밍 방식으로 캡처를 시작합니다.

- 앱이 렌더링되지 않는 경우(예: DirectCompute를 사용하여 계산을 수행하는 경우) 프로그래밍 방식으로 캡처를 시작합니다.

- @No__t_0when를 호출 하는 것은 수동 테스트에서 예측 하 고 캡처하는 것이 어렵고 런타임에 응용 프로그램의 상태에 대 한 정보를 사용 하 여 프로그래밍 방식으로 예측할 수 있습니다.

## <a name="CaptureDX11_2"></a> Windows 10의 프로그래밍 방식 캡처
이 연습 부분에서는 Windows 10에서 DirectX 11.2 API를 사용하는 앱의 프로그래밍 방식 캡처를 보여 줍니다. 이 API는 강력한 캡처 방법을 사용합니다.

이 섹션에서는 다음 작업을 수행하는 방법을 보여줍니다.

- 프로그래밍 캡처를 사용하도록 앱 준비

- IDXGraphicsAnalysis 인터페이스 가져오기

- 그래픽 정보 캡처

> [!NOTE]
> 프로그래밍 캡처의 이전 구현은 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]에 대 한 Visual Studio용 원격 도구에 의존 하 여 캡처 기능을 제공 합니다.

### <a name="preparing-your-app-to-use-programmatic-capture"></a>프로그래밍 캡처를 사용하도록 앱 준비
앱에서 프로그래밍 방식 캡처를 사용하려면 필요한 헤더를 포함해야 합니다. 이러한 헤더는 Windows 10 SDK의 일부입니다.

##### <a name="to-include-programmatic-capture-headers"></a>프로그래밍 캡처 헤더를 포함하려면

- IDXGraphicsAnalysis 인터페이스를 정의할 소스 파일에 다음 헤더 파일을 포함합니다.

    ```cpp
    #include <DXGItype.h>
    #include <dxgi1_2.h>
    #include <dxgi1_3.h>
    #include <DXProgrammableCapture.h>
    ```

    > [!IMPORTANT]
    > Windows 10 앱에서 프로그래밍 방식 캡처를 수행하기 위해 Windows 8.0 및 이전 버전에서 프로그래밍 방식 캡처를 지원하는 vsgcapture.h 헤더 파일을 포함하지 않습니다. 이 헤더는 DirectX 11.2와 호환되지 않습니다. D3d11_2 헤더를 포함 한 후이 파일이 포함 된 경우 컴파일러에서 경고를 발생 시킵니다. D3d11_2 앞에 vsgcapture가 포함 되어 있으면 앱이 시작 되지 않습니다.

    > [!NOTE]
    > 컴퓨터에 June 2010 DirectX SDK가 설치되어 있고 프로젝트의 포함 경로에 `%DXSDK_DIR%includex86`이 포함되어 있으면 이 부분을 포함 경로의 끝으로 옮깁니다. 라이브러리 경로에 대해서도 동일하게 수행합니다.

### <a name="getting-the-idxgraphicsanalysis-interface"></a>IDXGraphicsAnalysis 인터페이스 가져오기
DirectX 11.2에서 그래픽 정보를 캡처하려면 DXGI 디버그 인터페이스를 가져와야 합니다.

> [!IMPORTANT]
> 프로그래밍 캡처를 사용 하는 경우에도 그래픽 진단 ([!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]의 경우 Alt + F5) 이나 [명령줄 캡처 도구](command-line-capture-tool.md)에서 응용 프로그램을 실행 해야 합니다.

##### <a name="to-get-the-idxgraphicsanalysis-interface"></a>IDXGraphicsAnalysis 인터페이스를 가져오려면

- 다음 코드를 사용하여 IDXGraphicsAnalysis 인터페이스를 DXGI 디버그 인터페이스에 연결합니다.

  ```cpp
  IDXGraphicsAnalysis* pGraphicsAnalysis;
  HRESULT getAnalysis = DXGIGetDebugInterface1(0, __uuidof(pGraphicsAnalysis), reinterpret_cast<void**>(&pGraphicsAnalysis));
  ```

  [DXGIGetDebugInterface1](/windows/desktop/api/dxgi1_3/nf-dxgi1_3-dxgigetdebuginterface1) 에서 반환 된 `HRESULT`를 확인 하 여 사용 하기 전에 유효한 인터페이스를 얻을 수 있도록 해야 합니다.

  ```cpp
  if (FAILED(getAnalysis))
  {
      // Abort program or disable programmatic capture in your app.
  }
  ```

  > [!NOTE]
  > `DXGIGetDebugInterface1` 이 `E_NOINTERFACE` (`error: E_NOINTERFACE No such interface supported`)를 반환하는 경우 앱이 그래픽 진단에서 실행되고 있는지 확인합니다( [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]의 Alt+F5)로 앱을 실행해야 합니다.

### <a name="capturing-graphics-information"></a>그래픽 정보 캡처
이제 유효한 `IDXGraphicsAnalysis` 인터페이스가 있으므로 `BeginCapture` 및 `EndCapture` 를 사용하여 그래픽 정보를 캡처할 수 있습니다.

##### <a name="to-capture-graphics-information"></a>그래픽 정보를 캡처하려면

- 그래픽 정보 캡처를 시작하려면 다음과 같이 `BeginCapture`를 사용합니다.

    ```cpp
    ...
    pGraphicsAnalysis->BeginCapture();
    ...
    ```

    `BeginCapture` 가 호출되면 즉시 캡처가 시작됩니다. 다른 프레임이 시작되도록 기다리지 않습니다. 현재 프레임이 표시되거나 다음과 같이 `EndCapture`를 호출하면 캡처가 중지됩니다.

    ```cpp
    ...
    pGraphicsAnalysis->EndCapture();
    ...
    ```

- @No__t_0 호출 후 graphics 개체를 해제 합니다.

## <a name="next-steps"></a>다음 단계
이 연습에서는 그래픽 정보를 프로그래밍 방식으로 캡처하는 방법을 보여주었습니다. 다음 단계로 아래 옵션을 고려해 보세요.

- 그래픽 진단 도구를 사용하여 캡처한 그래픽 정보를 분석하는 방법에 대해 알아봅니다. [개요](overview-of-visual-studio-graphics-diagnostics.md)를 참조 하세요.

## <a name="see-also"></a>참조
- [연습: 그래픽 정보 캡처](walkthrough-capturing-graphics-information.md)
- [Capturing Graphics Information](capturing-graphics-information.md)
- [명령줄 캡처 도구](command-line-capture-tool.md)
