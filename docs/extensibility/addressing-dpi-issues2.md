---
title: DPI Issues2 주소 지정 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 359184aa-f5b6-4b6c-99fe-104655b3a494
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e2b440ff34a5c1f2c60b8874ba56266b636afde3
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352257"
---
# <a name="address-dpi-issues"></a>DPI 문제
장치 수가 증가 "고해상도" 화면을 사용 하 여 전달 됩니다. 이 화면에는 일반적으로 200 개가 넘는 인치 당 픽셀 수 (가) 있습니다. 이러한 컴퓨터에서 응용 프로그램을 사용 하 여 작업 콘텐츠를 장치에 대 한 일반 보기로 거리에 있는 콘텐츠를 표시 하는 요구를 충족 하도록 확장 해야 합니다. 2014 년을 기준으로 기본 고밀도 디스플레이 대 한 대상이 모바일 컴퓨팅 장치 (태블릿, 랩톱 클램쉘 및 휴대폰)입니다.

Windows 8.1 이상 컴퓨터 고밀도 둘 다에 연결 된 표준 밀도 동시에 표시 하는 환경 및 표시를 사용 하 여 작동 하도록 이러한 컴퓨터를 사용 하도록 설정 하려면 몇 가지 기능이 포함 되어 있습니다.

- Windows의 "텍스트 및 기타 항목 크게 또는 작게 만들려면"을 사용 하 여 장치로 콘텐츠 조정 수 설정 (Windows XP부터 사용할 수 있음).

- Windows 8.1 이상 자동으로 서로 다른 픽셀 밀도의 표시를 이동할 때 일관 되도록 대부분의 응용 프로그램에 대 한 콘텐츠 확장 됩니다. 기본 디스플레이 고밀도 (200%까지 크기 조정) 이며 보조 디스플레이 표준 밀도 (100%)을 하는 경우 Windows는 자동으로 축소 응용 프로그램 창 내용 보조 디스플레이에서 (1 픽셀에서 렌더링 되는 모든 4 픽셀에 대해 표시 되는 응용 프로그램)입니다.

- Windows 픽셀 밀도 대 한 크기 조정 및 표시 (Windows 7 이상 OEM 구성 가능)에 대 한 거리 보기 오른쪽 기본값으로 설정 됩니다.

- Windows 수 280 ppi (기준으로 Windows 8.1 S14)를 초과 하는 새 장치 250% 콘텐츠를 자동으로 조정 됩니다.

  Windows는이 ui 확장을 처리 하는 향상 된 픽셀 수를 활용 하 합니다. 응용 프로그램 자체 "시스템 DPI를 인식 합니다."를 선언 하 여이 시스템에 옵트인 이 수행 하는 응용 프로그램 시스템에 의해 조정 됩니다. 이 전체 응용 프로그램은 픽셀을 균일 하 게 확장 하는 위치는 "유사" 사용자 환경에서 발생할 수 있습니다. 예를 들어:

  ![DPI 문제 퍼지](../extensibility/media/dpi-issues-fuzzy.png "DPI 문제 퍼지")

  Visual Studio 확장에서 인식 되는 DPI에 옵트인 및 따라서가 가상화 되지 않음"."

  Windows (및 Visual Studio)에 여러 가지 배율 시스템으로 설정 하는 인수를 처리 하는 여러 가지 UI 기술을 활용 합니다. 예를 들어:

- WPF (단위, 픽셀이 아닌) 장치 독립적인 방식으로 컨트롤을 측정합니다. WPF UI 현재 DPI에 대해 자동으로 조정 합니다.

- UI 프레임 워크에 관계 없이 모든 텍스트 크기는 포인트 단위로 표현 됩니다 및 하므로 시스템에 의해 DPI 독립적으로 처리 됩니다. Win32, WinForms 및 WPF에서 텍스트 이미 확장할 올바르게 디스플레이 장치에 그리는 경우.

- Win32/WinForms 대화 상자 및 windows 텍스트 (예를 들어를 통해 표, flow 및 테이블 레이아웃 패널)를 사용 하 여 크기를 조정 하는 레이아웃을 사용 하도록 설정 하는 방법에 있습니다. 이 통해 글꼴 크기는 증가 하는 경우 배율이 조정 되지 않으므로 하드 코드 된 픽셀 위치를 방지 합니다.

- 시스템에서 제공 하는 아이콘 또는 시스템 메트릭 (예: SM_CXICON 및 SM_CXSMICON)에 따라 리소스 이미 조정 됩니다.

## <a name="older-win32-gdi-gdi-and-winforms-based-ui"></a>이전 Win32 (GDI, GDI +) 및 WinForms 기반 UI
WPF는 이미 높은 DPI를 인식 하지만 염두에서 DPI 인식으로 원래 작성 되는 Win32/GDI 기반 코드의 대부분 되었습니다 없습니다. Windows는 DPI 조정 Api를 제공 합니다. Win32 문제 수정에는 이러한 제품 전체에서 일관 되 게 사용 해야 합니다. Visual Studio는 도우미를 제공 하는 기능을 복제 및 제품 전체에서 일관성을 유지 하지 않으려면 클래스 라이브러리입니다.

## <a name="high-resolution-images"></a>고해상도 이미지
이 섹션은 주로 Visual Studio 2013을 확장 하는 개발자가 됩니다. Visual Studio 2015 용 Visual Studio에 기본 제공 되는 이미지 서비스를 사용 합니다. Visual Studio의 여러 버전을 대상/지원 해야 하 고 따라서 이미지 서비스를 사용 하 여 2015에서 불가능 한 이전 버전에 없기 때문에 알 수 있습니다. 이 섹션에서는 이면도 있습니다.

## <a name="scaling-up-images-that-are-too-small"></a>작은 이미지를 크기 조정
작은 이미지 확장 하 고 GDI 및 일부 공용 메서드를 사용 하 여 WPF에서 렌더링할 수 있습니다. 관리 되는 DPI 도우미 클래스는 내부 및 외부 Visual Studio 통합 업체 주소 아이콘, 비트맵, imagestrips, 및 imagelists 크기 조정에 사용할 수 있습니다. Win32 기반 네이티브 C / C + + 도우미 HICON, HBITMAP, HIMAGELIST, 및 VsUI::GdiplusImage 크기 조정에 사용할 수 있습니다. 일반적으로 비트맵의 크기 조정 도우미 라이브러리에 대 한 참조를 포함 한 후 한 줄 변경만 필요 합니다. 예를 들어:

```cpp
(Unmanaged) VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);
```

```csharp
(WinForms) DpiHelper.LogicalToDeviceUnits(ref image);
```

Imagelist 확장 아니면 했는지에 따라 다릅니다 imagelist 로드 시간, 완료를 런타임에 추가 됩니다. 로드 시 완료 하는 경우 호출 `LogicalToDeviceUnits()` 때 imagelist를 사용 하 여 비트맵을 것입니다. 코드를 imagelist 작성 하기 전에 개별 비트맵을 로드 해야 하는 경우의 imagelist 이미지 크기를 조정할 수 있는지 확인 합니다.

```csharp
imagelist.ImageSize = DpiHelper.LogicalToDeviceUnits(imagelist.ImageSize);
```

네이티브 코드에서 다음과 같이 imagelist를 만들 때 크기를 확장할 수 있습니다.

```cpp
ImageList_Create(VsUI::DpiHelper::LogicalToDeviceUnitsX(16),VsUI::DpiHelper::LogicalToDeviceUnitsY(16), ILC_COLOR32|ILC_MASK, nCount, 1);
```

라이브러리의 함수 크기 조정 알고리즘을 지정할 수 있습니다. 경우 imagelists에 배치할 크기 조정 이미지 투명도에 사용 되는 배경색을 지정 해야 합니다. 또는 NearestNeighbor 배율 (그러면 125%, 150%에서 왜곡이) 사용 합니다.

참조 된 <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> MSDN에 대 한 설명서입니다.

다음 표에서 배율 인수 해당 DPI에서 이미지 배율 조정 방법을의 예를 보여 줍니다. 주황색에 설명 된 이미지 (100-200 %DPI 배율)는 Visual Studio 2013이 모범 사례를 나타냅니다.

![DPI 문제 배율](../extensibility/media/dpi-issues-scaling.png "DPI 문제 배율")

## <a name="layout-issues"></a>레이아웃 문제
절대 위치 (특히 픽셀 단위)를 사용 하지 않고 크기를 조정 하는 UI에 서로 기준으로 요소를 유지 하 여 주로 일반적인 레이아웃 문제를 방지할 수 있습니다. 예를 들어:

- 레이아웃/텍스트 위치는 확장 된 이미지에 대 한 계정으로 조정 해야 합니다.

- 표에서 열 너비가 강화 텍스트에 대 한 조정 해야 합니다.

- 하드 코드 된 크기나 요소 사이 공백을 강화 해야 합니다. 텍스트 크기에만 기반 하는 크기는 글꼴 자동으로 조정 되므로 일반적으로 세밀 하 게 합니다.

  도우미 함수에서 사용할 수는 <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> X 및 Y 축에 확장을 허용 하려면 클래스:

- LogicalToDeviceUnitsX/LogicalToDeviceUnitsY (함수 X에서 크기 조정을 허용 / Y 축)

- int space = DpiHelper.LogicalToDeviceUnitsX (10);

- int height = VsUI::DpiHelper::LogicalToDeviceUnitsY(5);

  Rect, 지점 및 크기와 같은 개체 확장을 허용 하려면 LogicalToDeviceUnits 오버 로드가 있습니다.

## <a name="using-the-dpihelper-libraryclass-to-scale-images-and-layout"></a>이미지 배율을 조정 및 레이아웃을 DPIHelper 라이브러리/클래스를 사용 하 여
Visual Studio DPI 도우미 라이브러리를 네이티브 및 관리 되는 형태로 사용할 수 있으며 다른 응용 프로그램에서 Visual Studio shell을 외부에서 사용할 수 있습니다.

라이브러리를 사용 하려면로 이동 합니다 [Visual Studio VSSDK 확장성 샘플](https://github.com/Microsoft/VSSDK-Extensibility-Samples) 및 높은 DPI_Images_Icons 샘플을 복제 합니다.

원본 파일에에서 포함 *VsUIDpiHelper.h* 의 정적 함수를 호출 하 고 `VsUI::DpiHelper` 클래스:

```cpp
#include "VsUIDpiHelper.h"

int cxScaled = VsUI::DpiHelper::LogicalToDeviceUnitsX(cx);
VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);

```

> [!NOTE]
> 모듈 수준 또는 클래스 수준 정적 변수에서 도우미 함수를 사용 하지 마세요. 스레드 동기화에 대 한 라이브러리도 사용 하 여 정적 및 순서 초기화 문제를 발생할 수 있습니다. 비정적 멤버 변수를 해당 정적 변환 하거나 (따라서 첫 번째 액세스에서 생성 되는) 함수를 래핑하십시오.

Visual Studio 환경 내에서 실행 되는 관리 되는 코드에서 DPI 도우미 함수에 액세스 합니다.

- 사용 하는 프로젝트 셸을 MPF의 최신 버전을 참조 해야 합니다. 예를 들어:

    ```csharp
    <Reference Include="Microsoft.VisualStudio.Shell.14.0.dll" />
    ```

- 프로젝트에 대 한 참조를 확인 하십시오 **System.Windows.Forms**를 **PresentationCore**, 및 **PresentationUI**합니다.

- 코드를 사용 합니다 **Microsoft.VisualStudio.PlatformUI** DpiHelper 클래스의 정적 함수 네임 스페이스를 호출 합니다. 지원 되는 형식 (점, 크기, 사각형 및 등)에 새 반환 하는 확장 함수 개체를 확장 제공. 예를 들어:

    ```csharp
    using Microsoft.VisualStudio.PlatformUI;
    double x = DpiHelper.LogicalToDeviceUnitsX(posX);
    Point ptScaled = ptOriginal.LogicalToDeviceUnits();
    DpiHelper.LogicalToDeviceUnits(ref bitmap);

    ```

## <a name="dealing-with-wpf-image-fuzziness-in-zoomable-ui"></a>WPF 이미지 허용량 가능한 ui를 사용 하 여 처리
Wpf에서 비트맵은 자동으로 크기가 조정 WPF에서 사진 또는 큰 스크린샷, 잘 작동 하지만 아니므로 메뉴 항목 아이콘에 대 한 적절 한 인식된 허용량을 소개 하는 고품질 이중 큐빅 알고리즘 (기본값) 사용 하 여 현재 DPI 확대/축소 수준에 대 한 .

권장 사항:

- 로고 이미지 및 배너 아트 워크, 기본값에 대 한 <xref:System.Windows.Media.BitmapScalingMode> 크기 모드를 사용할 수 있습니다.

- 메뉴 항목과도 해 이미지에 대 한는 <xref:System.Windows.Media.BitmapScalingMode> 기타 왜곡 아티팩트 허용량 (%200 및 300%)에서 제거를 수행 해도 해당 하는 경우에 사용 해야 합니다.

- 큰 확대/축소 수준을 100% (예를 들어 250% 또는 %350)의 배수로 청구 되지 않습니다,에 대 한 유사 항목 바랜 UI에 결과 이중 큐빅을 사용 하 여의 해 이미지 크기를 조정 합니다. 첫 번째 100% (예: 200% 또는 300%)의 가장 큰 배수로 NearestNeighbor 사용 하 여 이미지를 확장 하 여 더 나은 결과 가져옵니다. 및 여기에서 이중 큐빅을 사용 하 여 크기 조정 합니다. 특수 한 사례를 참조 하세요: 자세한 수준 큰 DPI에 대 한 WPF 이미지 prescaling 합니다.

  Microsoft.VisualStudio.PlatformUI 네임 스페이스의 DpiHelper 클래스 멤버를 제공 <xref:System.Windows.Media.BitmapScalingMode> 바인딩에 사용할 수 있습니다. Visual Studio shell은 비트맵 배율 조정을 제품 전체에서 일관 되 게 DPI 배율에 따라 제어 하는 허용 됩니다.

  XAML에서 사용 하려면 다음을 추가 합니다.

```xaml
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"

<Setter Property="RenderOptions.BitmapScalingMode" Value="{x:Static vs:DpiHelper.BitmapScalingMode}" />

```

이미 Visual Studio shell을 최상위 창 및 대화 상자에서이 속성을 설정합니다. 이미 Visual Studio에서 실행 하는 WPF 기반 UI 것을 상속 합니다. 설정에 특정 UI 부분을 전파 하지 않습니다, 경우에 XAML/WPF UI의 루트 요소에서 설정할 수 있습니다. Blend와 같은 디자이너 창 개를 실행 하는 처리 및이 이루어지는 곳에 팝업 Win32 부모 요소에 포함 됩니다.

일부 UI는 Visual Studio 텍스트 편집기 및 디자이너 WPF 기반 (WPF 데스크톱 및 Windows 스토어)와 같은 시스템 집합 DPI 확대/축소 수준을 독립적으로 확장할 수 있습니다. 이러한 경우 DpiHelper.BitmapScalingMode 해야 사용할 수 없습니다. 편집기에서이 문제를 해결 하려면 사용자 지정 속성을 생성 하는 IDE 팀 RenderOptions.BitmapScalingMode 제목 있습니다. 시스템 및 UI의 결합 된 확대/축소 수준에 따라 HighQuality 또는 NearestNeighbor 해당 속성 값을 설정 합니다.

## <a name="special-case-prescaling-wpf-images-for-large-dpi-levels"></a>특별 한 경우: prescaling 큰 DPI 수준에 대 한 WPF 이미지
100% (예를 들어 250%, 350%, 및 등)의 배수로 청구 되지 않는 매우 큰 확대/축소 수준에 대 한 유사 항목 바랜 UI에서 이중 큐빅 결과로도 해 이미지 크기를 조정 합니다. 선명한 텍스트와 함께 이러한 이미지 중 인상을 광학 감을의 거의 경우 텍스트와 관련 하 여 포커스 눈에 가깝게 이미지가 나타납니다. 첫 번째 100% (예: 200% 또는 300%)의 가장 큰 배수로 NearestNeighbor 사용 하 여 이미지를 확장 하 여이 확대 크기로 크기 조정 결과 향상 시킬 수 있습니다. 및 이중 큐빅 나머지 (추가 50%)를 사용 하 여 크기 조정 합니다.

다음은 결과의 차이점에 대 한 예로 첫 번째 이미지 크기가 조정 되는 100%-> 향상 된 double 크기 조정 알고리즘을 사용 하 여 200% 250%->. 및-> 250% 이중 큐빅 100%가 포함 된 두 번째입니다.

![DPI 문제 Double 크기 조정 예제](../extensibility/media/dpi-issues-double-scaling-example.png "DPI 문제 Double 크기 조정 예제")

각 이미지 요소를 표시 하는 것에 대 한이 이중 확장, XAML 태그를 사용 하는 UI를 사용 하도록 설정 하려면 할 수정할 수 있습니다. 다음 예제에서는 Shell.12/14 고 DpiHelper 라이브러리를 사용 하 여 Visual Studio에서 WPF에서 이중 확장을 사용 하는 방법을 보여 줍니다.

1단계: 200%, 300% 등에 NearestNeighbor를 사용 하 여 이미지를 prescale입니다.

바인딩 또는 XAML 태그 확장을 사용 하 여 적용할 변환기를 사용 하 여 이미지를 prescale입니다. 예를 들어:

```xaml
<vsui:DpiPrescaleImageSourceConverter x:Key="DpiPrescaleImageSourceConverter" />

<Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />

<Image Source="{vsui:DpiPrescaledImage Images/Help.png}" Width="16" Height="16" />

```

이미지도 해야 테마가 지정 된 경우 (대부분 경우 항상 그렇지는 않지만 해야) 태그 이미지 및 다음 미리 확장의 테마를 먼저 수행 하는 다양 한 변환기를 사용할 수 있습니다. 태그를 사용할 수 있습니다 <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageConverter> 또는 <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageSourceConverter>원하는 변환 출력에 따라 합니다.

```xaml
<vsui:DpiPrescaleThemedImageSourceConverter x:Key="DpiPrescaleThemedImageSourceConverter" />

<Image Width="16" Height="16">
  <Image.Source>
    <MultiBinding Converter="{StaticResource DpiPrescaleThemedImageSourceConverter}">
      <Binding Path="Icon" />
      <Binding Path="(vsui:ImageThemingUtilities.ImageBackgroundColor)"
               RelativeSource="{RelativeSource Self}" />
      <Binding Source="{x:Static vsui:Boxes.BooleanTrue}" />
    </MultiBinding>
  </Image.Source>
</Image>
```

2단계: 현재 DPI에 최종 크기가 올바른지 확인 하십시오.

WPF UI UIElement 설정 BitmapScalingMode 속성을 사용 하 여 현재 dpi를 확장 하기 때문에 해당 소스 2-3 배 보다 크게 보입니다 prescaled 이미지를 사용 하 여 이미지 컨트롤을 해야 합니다. 다음은이 효과 대처 하는 몇 가지 방법입니다.

- 100%에 원본 이미지의 치수를 알고 있는 경우 이미지 컨트롤의 정확한 크기를 지정할 수 있습니다. 이러한 크기 확장 하기 전에 UI의 크기를 적용 하는 내용을 반영 합니다.

    ```xaml
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />
    ```

- 원본 이미지의 크기를 알 수 없는 경우는 LayoutTransform 최종 이미지 개체 축소를 사용할 수 있습니다. 예를 들어:

    ```xaml
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" >
        <Image.LayoutTransform>
            <ScaleTransform
                ScaleX="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}"
                ScaleY="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}" />
        </Image.LayoutTransform>
    </Image>
    ```

## <a name="enabling-hdpi-support-to-the-weboc"></a>WebOC HDPI 지원을 사용 하도록 설정
기본적으로 WebOC 컨트롤 (예: WPF 또는 IWebBrowser2 인터페이스에서 WebBrowser 컨트롤) HDPI 검색 및 지원을 사용 하도록 설정 하지 않습니다. 결과 고해상도 디스플레이에 너무 작으면 콘텐츠 표시를 사용 하 여 포함 된 컨트롤 됩니다. 다음 특정 웹 WebOC 인스턴스에서 높은 DPI 지원을 사용 하도록 설정 하는 방법을 설명 합니다.

IDocHostUIHandler 인터페이스 구현 (MSDN 문서를 참조 합니다 [IDocHostUIHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753260(v=vs.85)):

```idl
[ComImport, InterfaceType(ComInterfaceType.InterfaceIsIUnknown),
 Guid("BD3F23C0-D43E-11CF-893B-00AA00BDCE1A")]
public interface IDocHostUIHandler
{
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int ShowContextMenu(
        [In, MarshalAs(UnmanagedType.U4)] int dwID,
        [In] POINT pt,
        [In, MarshalAs(UnmanagedType.Interface)] object pcmdtReserved,
        [In, MarshalAs(UnmanagedType.IDispatch)] object pdispReserved);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int GetHostInfo([In, Out] DOCHOSTUIINFO info);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int ShowUI(
        [In, MarshalAs(UnmanagedType.I4)] int dwID,
        [In, MarshalAs(UnmanagedType.Interface)] object activeObject,
        [In, MarshalAs(UnmanagedType.Interface)] object commandTarget,
        [In, MarshalAs(UnmanagedType.Interface)] object frame,
        [In, MarshalAs(UnmanagedType.Interface)] object doc);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int HideUI();
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int UpdateUI();
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int EnableModeless([In, MarshalAs(UnmanagedType.Bool)] bool fEnable);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int OnDocWindowActivate([In, MarshalAs(UnmanagedType.Bool)] bool fActivate);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int OnFrameWindowActivate([In, MarshalAs(UnmanagedType.Bool)] bool fActivate);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int ResizeBorder(
        [In] COMRECT rect,
        [In, MarshalAs(UnmanagedType.Interface)] object doc,
        bool fFrameWindow);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int TranslateAccelerator(
        [In] ref MSG msg,
        [In] ref Guid group,
        [In, MarshalAs(UnmanagedType.I4)] int nCmdID);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int GetOptionKeyPath(
        [Out, MarshalAs(UnmanagedType.LPArray)] string[] pbstrKey,
        [In, MarshalAs(UnmanagedType.U4)] int dw);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int GetDropTarget(
        [In, MarshalAs(UnmanagedType.Interface)] IOleDropTarget pDropTarget,
        [MarshalAs(UnmanagedType.Interface)] out IOleDropTarget ppDropTarget);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int GetExternal([MarshalAs(UnmanagedType.IDispatch)] out object ppDispatch);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int TranslateUrl(
        [In, MarshalAs(UnmanagedType.U4)] int dwTranslate,
        [In, MarshalAs(UnmanagedType.LPWStr)] string strURLIn,
        [MarshalAs(UnmanagedType.LPWStr)] out string pstrURLOut);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int FilterDataObject(
        IDataObject pDO,
        out IDataObject ppDORet);
    }
```

필요에 따라 ICustomDoc 인터페이스를 구현 (MSDN 문서를 참조 합니다 [ICustomDoc](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753272(v=vs.85)):

```idl
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown),
 Guid("3050F3F0-98B5-11CF-BB82-00AA00BDCE0B")]
public interface ICustomDoc
{
    void SetUIHandler(IDocHostUIHandler pUIHandler);
}
```

IDocHostUIHandler WebOC의 문서를 사용 하 여 구현 하는 클래스를 연결 합니다. 위의 ICustomDoc 인터페이스를 구현 하는 경우 WebOC의 문서 속성이 유효한 지, 즉시는 ICustomDoc에 캐스팅을 IDocHostUIHandler를 구현 하는 클래스를 전달 하 여 SetUIHandler 메서드를 호출 합니다.

```csharp
// "this" references that class that owns the WebOC control and in this case also implements the IDocHostUIHandler interface
ICustomDoc customDoc = (ICustomDoc)webBrowser.Document;
customDoc.SetUIHandler(this);

```

ICustomDoc 인터페이스를 구현 하지 않은 경우 IOleObject, 및 호출 캐스팅 해야 WebOC의 문서 속성 유효 즉시는 `SetClientSite` IDocHostUIHandler를 구현 하는 클래스에 전달 하는 메서드를 합니다. 전달할 DOCHOSTUIINFO DOCHOSTUIFLAG_DPI_AWARE 플래그를 설정 합니다 `GetHostInfo` 메서드를 호출 합니다.

```csharp
public int GetHostInfo(DOCHOSTUIINFO info)
{
    // This is what the default site provides.
    info.dwFlags = (DOCHOSTUIFLAG)0x5a74012;
    // Add the DPI flag to the defaults
    info.dwFlags |=.DOCHOSTUIFLAG.DOCHOSTUIFLAG_DPI_AWARE;
    return S_OK;
}
```

WebOC 컨트롤 HPDI를 지원 하도록 준비 해야 하는 모든 이어야 합니다.

## <a name="tips"></a>팁

1. WebOC 컨트롤에 문서 속성이 변경 되 면 IDocHostUIHandler 클래스를 사용 하 여 문서를 다시 연결 해야 합니다.

2. 위의 작동 하지 않는 경우 변경 된 DPI 플래그를 가져오지 WebOC의 알려진된 문제가 있습니다. 이 문제를 해결 하는 가장 안정적인 방법은 확대/축소 비율에 대 한 서로 다른 두 값을 사용 하 여 두 개의 호출을 의미 하 고 WebOC의 광학 확대/축소를 설정/해제 방법은입니다. 또한이 해결 방법은 필요한 경우 탐색 호출할 때마다 수행 해야 할 수 있습니다.

    ```csharp
    // browser2 is a SHDocVw.IWebBrowser2 in this case
    // EX: Call the Exec twice with DPI%-1 and then DPI% as the zoomPercent values
    IOleCommandTarget cmdTarget = browser2.Document as IOleCommandTarget;
    if (cmdTarget != null)
    {
        object commandInput = zoomPercent;
        cmdTarget.Exec(IntPtr.Zero,
                       OLECMDID_OPTICAL_ZOOM,
                       OLECMDEXECOPT_DONTPROMPTUSER,
                       ref commandInput,
                       ref commandOutput);
    }
    ```
