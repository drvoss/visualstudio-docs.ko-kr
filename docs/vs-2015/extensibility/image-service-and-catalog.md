---
title: 이미지 서비스 및 카탈로그 | Microsoft Docs
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 34990c37-ae98-4140-9b1e-a91c192220d9
caps.latest.revision: 38
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1cc402792f39cbbebb6e7804e7406be4f06658a4
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67824678"
---
# <a name="image-service-and-catalog"></a>이미지 서비스 및 카탈로그
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 cookbook 지침 및 Visual Studio 이미지 서비스 및 Visual Studio 2015에 도입 된 이미지 카탈로그에 대 한 모범 사례를 포함 합니다.  

 Visual Studio 2015에 도입 된 이미지 서비스 개발자를 장치 및 사용자의 표시 되는 상황에 맞는 올바른 테마를 포함 하 여 이미지를 표시 하려면 선택한 테마에 대 한 최상의 이미지를 가져올 수 있습니다. 이미지 서비스를 채택 자산 유지 관리, HDPI 확장 및 테마와 관련 된 주요 고충을 없애는 데 도움이 됩니다.  

|||  
|-|-|  
|**현재 문제**|**솔루션**|  
|배경 색 혼합|기본 제공 알파 혼합|  
|(일부) 테마 설정 이미지|테마 메타 데이터|  
|고대비 모드|대체 고대비 리소스|  
|서로 다른 DPI 모드에 대 한 여러 리소스 필요|벡터 기반 대체 (fallback) 사용 하 여 선택할 수 있는 리소스|  
|중복 된 이미지|이미지 개념 당 한 개의 식별자|  

 이미지 서비스를 채택 하는 이유  

- Visual Studio에서 최신 "완벽 한 픽셀" 이미지를 항상 가져오기  

- 제출 하 고 사용자 고유의 이미지를 사용할 수 있습니다.  

- 새 DPI 배율 Windows을 추가 하는 경우 아웃 이미지를 테스트할 필요가 없습니다  

- 구현에서 이전 아키텍처 문제를 해결 합니다.  

  Visual Studio shell 도구 모음에서 이전 및 이후 이미지를 사용 하 여:  

  ![이미지 서비스 이전 및 이후](../extensibility/media/image-service-before-and-after.png "이전 및 이후 이미지 서비스")  

## <a name="how-it-works"></a>작동 방법  
 이미지 서비스는 모든 지원 되는 UI 프레임 워크에 대 한 적절 한 비트맵 이미지를 제공할 수 있습니다.  

- WPF: BitmapSource  

- WinForms: System.Drawing.Bitmap  

- Win32: HBITMAP  

  이미지 서비스 흐름 다이어그램  

  ![이미지 서비스 흐름 다이어그램](../extensibility/media/image-service-flow-diagram.png "이미지 서비스 흐름 다이어그램")  

  **이미지 모니커**  

  이미지 모니커 (또는 줄여서 모니커)는 고유 하 게 이미지 자산 또는 이미지 라이브러리에서 이미지 목록 자산을 식별 하는 GUID/i D 쌍입니다.  

  **알려진된 모니커**  

  Visual Studio 이미지 카탈로그 및 공개적으로 사용할 수 있는 모든 Visual Studio 구성 요소 또는 확장에 의해 포함 된 이미지 모니커 집합이 있습니다.  

  **이미지 매니페스트 파일**  

  이미지 매니페스트 (.imagemanifest) 파일은 이미지 자산, 자산 및 실제 이미지 또는 각 자산을 나타내는 이미지를 나타내는 모니커 집합을 정의 하는 XML 파일입니다. 이미지 매니페스트 독립 실행형 이미지를 정의할 수 있습니다 또는 레거시 UI 지원에 대 한 이미지를 나열 합니다. 또한, 시기 및 해당 자산을 표시 하는 방법을 변경 하려면 각각의 자산 뒤 개별 이미지 또는 자산에서 설정할 수 있는 속성이 있습니다.  

  **이미지 매니페스트 스키마**  

  이미지 완료 매니페스트는 다음과 같습니다.  

```xml  
<ImageManifest>  
      <!-- zero or one Symbols elements -->  
      <Symbols>  
        <!-- zero or more Import, Guid, ID, or String elements -->  
      </Symbols>  
      <!-- zero or one Images elements -->  
      <Images>  
        <!-- zero or more Image elements -->  
      </Images>  
      <!-- zero or one ImageLists elements -->  
      <ImageLists>  
        <!-- zero or more ImageList elements -->  
      </ImageLists>  
</ImageManifest>  
```  

 **Symbols**  

 가독성 및 유지 관리를 지 원하는 대로 이미지 매니페스트 특성 값에 대 한 기호를 사용할 수 있습니다. 기호는 다음과 같이 정의 됩니다.  

```xml  
<Symbols>  
      <Import Manifest="manifest" />  
      <Guid Name="ShellCommandGuid" Value="8ee4f65d-bab4-4cde-b8e7-ac412abbda8a" />  
      <ID Name="cmdidSaveAll" Value="1000" />  
      <String Name="AssemblyName" Value="Microsoft.VisualStudio.Shell.UI.Internal" />  
</Symbols>  
```  

|||  
|-|-|  
|**하위 요소**|**정의**|  
|가져오기|현재 매니페스트에서 사용 하기 위해 지정된 된 매니페스트 파일의 기호를 가져옵니다.|  
|Guid|GUID를 나타내는 기호와 GUID 서식 지정과 일치 해야 합니다.|  
|ID|기호 ID를 나타내며 음수가 아닌 정수 여야 합니다.|  
|String|기호를 나타내는 임의의 문자열 값|  

 기호는 대/소문자 구분, 및 $(symbol-name) 구문을 사용 하 여 참조입니다.  

```xml  
<Image Guid="$(ShellCommandGuid)" ID="$(cmdidSaveAll)" >  
      <Source Uri="/$(AssemblyName);Component/Resources/image.xaml" />  
</Image>  
```  

 일부 기호는 모든 매니페스트에 대 한 미리 정의 됩니다. 이러한 Uri 특성에 사용할 수 있습니다 합니다 \<소스 > 또는 \<가져오기 > 로컬 컴퓨터의 참조 경로 요소입니다.  

|||  
|-|-|  
|**Symbol**|**설명**|  
|CommonProgramFiles|% CommonProgramFiles % 환경 변수 값|  
|LocalAppData|% LocalAppData % 환경 변수 값|  
|ManifestFolder|매니페스트 파일을 포함 하는 폴더|  
|MyDocuments|현재 사용자의 내 문서 폴더의 전체 경로|  
|ProgramFiles|% ProgramFiles % 환경 변수 값|  
|시스템|Windows\System32 폴더|  
|WinDir|% WinDir % 환경 변수 값|  

 **Image**  

 \<이미지 > 요소는 모니커를 참조할 수 있는 이미지를 정의 합니다. GUID 및 ID 종합해 이미지 모니커를 형성 합니다. 이미지에 대 한 모니커는 전체 이미지 갤러리에서 고유 해야 합니다. 라이브러리를 빌드하는 동안 발생 한 첫 번째 지정 된 모니커를 갖도록 하는 둘 이상의 이미지를 경우 유지 되는 것입니다.  

 소스가 하나 이상 있어야 합니다. 크기와 무관 원본 최상의 결과 다양 한 범위의 크기에서 지지만 필요 하지 않습니다. 서비스에서 정의 되지 않은 크기의 이미지에 대 한 요청을 \<이미지 > 요소 및 크기와 무관 원본이 없는, 서비스는 가장 좋은 크기 관련 소스를 선택 하 고 요청 된 크기 조정 합니다.  

```xml  
<Image Guid="guid" ID="int" AllowColorInversion="true/false">  
      <Source ... />  
      <!-- optional additional Source elements -->  
</Image>  
```  

|||  
|-|-|  
|**특성**|**정의**|  
|Guid|[필수] 이미지 모니커의 GUID 부분|  
|ID|[필수] 이미지 모니커 ID 부분|  
|AllowColorInversion|[선택 사항, 기본값은 true] 이미지를 프로그래밍 방식으로 어두운 배경을 사용 하는 경우 반전 된 색을 가질 수 있는지 여부를 나타냅니다.|  

 **원본**  

 \<소스 > 요소 (XAML 및 PNG)을 단일 이미지 원본 자산을 정의 합니다.  

```xml  
<Source Uri="uri" Background="background">  
      <!-- optional NativeResource element -->  
 </Source>  
```  

|               |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|---------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **특성** |                                                                                                                                                                                                                                                                                                                                                                                                                                                                            **정의**                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|      URI      |                                                                                                                                                                                                                                                                                                               [필수] 이미지를 로드할 수 있는 정의 하는 URI입니다. 다음 중 하나일 수 있습니다.<br /><br /> -A [Pack URI](https://msdn.microsoft.com/library/aa970069\(v=vs.100\).aspx) 응용 프로그램을 사용 하 여: / / / 기관<br />-절대 구성 요소 리소스 참조<br />-네이티브 리소스를 포함 하는 파일 경로                                                                                                                                                                                                                                                                                                               |
|  배경   | [선택 사항] 어떤 종류의 원본으로 사용할 목적이 백그라운드에서 나타냅니다.<br /><br /> 다음 중 하나일 수 있습니다.<br /><br /> *조명:* 밝은 배경에 소스를 사용할 수 있습니다.<br /><br /> <em>진한:</em>어두운 배경을에서 소스를 사용할 수 있습니다.<br /><br /> *HighContrast:* 고대비 모드에서 백그라운드에서 소스를 사용할 수 있습니다.<br /><br /> *HighContrastLight:* 고대비 모드에서 밝은 배경에 소스를 사용할 수 있습니다.<br /><br /> *HighContrastDark:* 고대비 모드에서 어두운 배경을에서 소스를 사용할 수 있습니다.<br /><br /> 배경 특성을 생략 하는 경우 백그라운드에서 소스를 사용할 수 있습니다.<br /><br /> 배경이 *Light*를 *어두운*를 *HighContrastLight*, 또는 *HighContrastDark*, 소스의 색 반전 되지 않습니다. 백그라운드 생략 되거나로 설정 하는 경우 *고 대비*, 소스의 색 반전을 이미지의 의해 제어 됩니다 **AllowColorInversion** 특성입니다. |
|               |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |

 \<소스 > 요소는 다음 선택적 하위 요소 중 하나만 포함할 수 있습니다.  

||||  
|-|-|-|  
|**요소**|**특성 (모두 필요)**|**정의**|  
|\<크기 >|값|원본 장치 단위로 지정된 된 크기의 이미지에 대 한 사용 됩니다. 이미지는 사각형 됩니다.|  
|\<SizeRange>|MinSize, MaxSize|원본 장치 단위로 최대 크기로 MinSize에서 이미지에 대 한 포괄적 사용 됩니다. 이미지는 사각형 됩니다.|  
|\<크기 >|Width, Height|원본은 이미지의 지정 된 너비와 높이 (장치 단위)에 대 한 사용 됩니다.|  
|\<DimensionRange>|MinWidth, MinHeight,<br /><br /> MaxWidth, MaxHeight|원본 장치 단위로 최대 너비/높이에 최소 너비/높이의 이미지에 대 한 포괄적 사용 됩니다.|  

 A \<소스 > 요소는 선택적 수도 있습니다 \<NativeResource > 하위 요소를 정의 하는 \<원본 > 관리 되는 어셈블리 대신 네이티브 어셈블리에서 로드 되는 합니다.  

```xml  
<NativeResource Type="type" ID="int" />  
```  

|||  
|-|-|  
|**특성**|**정의**|  
|형식|[필수] 네이티브 리소스를 XAML 또는 PNG 형식|  
|ID|[필수] 네이티브 리소스의 정수 ID 부분|  

 **ImageList**  

 \<ImageList > 요소를 단일 줄에에서 반환 될 수 있는 이미지의 컬렉션을 정의 합니다. 줄 필요에 따라 주문형으로 빌드됩니다.  

```xml  
<ImageList>  
      <ContainedImage Guid="guid" ID="int" External="true/false" />  
      <!-- optional additional ContainedImage elements -->  
 </ImageList>  
```  

|||  
|-|-|  
|**특성**|**정의**|  
|Guid|[필수] 이미지 모니커의 GUID 부분|  
|ID|[필수] 이미지 모니커 ID 부분|  
|외부|[선택 사항, 기본값: false] 이미지 모니커를 사용 하 여 현재 매니페스트에서 이미지를 참조 하는지 여부를 나타냅니다.|  

 포함 된 이미지에 대 한 모니커 현재 매니페스트에 정의 된 이미지를 참조할 필요가 없습니다. 이미지 라이브러리에 포함 된 이미지를 찾지 못하면 빈 자리 표시자 이미지를 해당 위치에 됩니다.  

## <a name="using-the-image-service"></a>이미지 서비스 사용  

### <a name="first-steps-managed"></a>첫 번째 단계 (관리)  
 이미지 서비스를 사용 하려면 프로젝트에 다음 어셈블리의 일부 또는 전부에 대 한 참조를 추가 해야 합니다.  

- **Microsoft.VisualStudio.ImageCatalog.dll**  

  - 기본 제공 이미지 카탈로그 KnownMonikers를 사용 하는 경우 필요  

- **Microsoft.VisualStudio.Imaging.dll**  

  - 사용 하는 경우 필요 **CrispImage** 하 고 **ImageThemingUtilities** WPF UI에서  

- **Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll**  

  - 사용 하는 경우 필요 합니다 **ImageMoniker** 하 고 **ImageAttributes** 형식  

  - **EmbedInteropTypes** 설정 해야 true로  

- **Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime**  

  - 사용 하는 경우 필요 합니다 **IVsImageService2** 형식  

  - **EmbedInteropTypes** 설정 해야 true로  

- **Microsoft.VisualStudio.Utilities.dll**  

  - 사용 하는 경우 필요 합니다 **BrushToColorConverter** 는 ImageThemingUtilities에 대 한. **ImageBackgroundColor** WPF UI에서  

- **Microsoft.VisualStudio.Shell.\<VSVersion>.0**  

  - 사용 하는 경우 필요 합니다 **IVsUIObject** 형식  

- **Microsoft.VisualStudio.Shell.Interop.10.0.dll**  

  - UI WinForms 관련 도우미를 사용 하는 경우 필요  

  - **EmbedInteropTypes** 설정 해야 true로  

### <a name="first-steps-native"></a>첫 번째 단계 (네이티브)  
 이미지 서비스를 사용 하려면 일부 또는 모든 프로젝트에 다음 헤더를 포함 해야 합니다.  

- **KnownImageIds.h**  

  - 기본 제공 이미지 카탈로그를 사용 하는 경우 필요 **KnownMonikers**, 하지만 사용할 수 없습니다는 **ImageMoniker** 면에서 값 반환 등의 형식 **IVsHierarchy GetGuidProperty**나 **GetProperty** 호출 합니다.  

- **KnownMonikers.h**  

  - 기본 제공 이미지 카탈로그를 사용 하는 경우 필요 **KnownMonikers**합니다.  

- **ImageParameters140.h**  

  - 사용 하는 경우 필요 합니다 **ImageMoniker** 하 고 **ImageAttributes** 형식입니다.  

- **VSShell140.h**  

  - 사용 하는 경우 필요 합니다 **IVsImageService2** 형식입니다.  

- **ImageThemingUtilities.h**  

  - 이미지를 테마를 처리할 수 없는 경우 필요 합니다.  

  - 이미지 서비스에 이미지 테마를 처리할 수 있는 경우에이 헤더를 사용 하지 마세요.  

- **VSUIDPIHelper.h**  

  - DPI 도우미를 사용 하 여 현재 DPI를 가져오려는 경우 필요 합니다.  

## <a name="how-do-i-write-new-wpf-ui"></a>새 WPF UI를 작성 하는 방법  

1. 위의 필요한 어셈블리 참조를 추가 하 여 시작 프로젝트에 섹션을 첫 번째 단계입니다. 모두 추가 해야 하는 참조만 추가 필요가 없습니다. (참고: 사용 하는 경우에 대 한 액세스 권한이 **색** of **브러시**에 대 한 참조를 건너뛸 수 있습니다 **유틸리티**변환기가 필요 하지 않으므로,.)  

2. 원하는 이미지를 선택 하 고 해당 모니커를 가져옵니다. 사용 하 여는 **KnownMoniker**, 하거나 사용자 고유의 사용자 지정 이미지 및 모니커 경우 직접 사용 합니다.  

3. 추가 **CrispImages** 에 XAML을 합니다. (아래 예제 참조).  

4. 설정 된 **ImageThemingUtilities.ImageBackgroundColor** UI 계층의 속성입니다. (배경색 알려져 없는 반드시에 하지 위치에 설정 해야 합니다 **CrispImage**.) (아래 예제 참조).  

```xaml  
<Window  
  x:Class="WpfApplication.MainWindow"  
  xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
  xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
  xmlns:imaging="clr-namespace:Microsoft.VisualStudio.Imaging;assembly=Microsoft.VisualStudio.Imaging"  
  xmlns:theming="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Imaging"  
  xmlns:utilities="clr-namespace:Microsoft.Internal.VisualStudio.Imaging;assembly=Microsoft.VisualStudio.Imaging"  
  xmlns:catalog="clr-namespace:Microsoft.VisualStudio.Imaging;assembly=Microsoft.VisualStudio.ImageCatalog"  
  Title="MainWindow" Height="350" Width="525" UseLayoutRounding="True">  
  <Window.Resources>  
    <utilities:BrushToColorConverter x:Key="BrushToColorConverter"/>  
  </Window.Resources>  
  <StackPanel Background="White" VerticalAlignment="Center"   
    theming:ImageThemingUtilities.ImageBackgroundColor="{Binding Background, RelativeSource={RelativeSource Self}, Converter={StaticResource BrushToColorConverter}}">  
    <imaging:CrispImage Width="16" Height="16" Moniker="{x:Static catalog:KnownMonikers.MoveUp}" />  
  </StackPanel>  
</Window>  
```  

 **기존 WPF UI를 업데이트 하려면 어떻게 해야 하나요?**  

 기존 WPF UI 업데이트는 세 단계로 구성 된 비교적 간단한 프로세스입니다.  

1. 모두 바꾸기 \<이미지 > 요소를 사용 하 여 UI에서 \<CrispImage > 요소  

2. 모니커 특성에 모든 원본 특성을 변경 합니다.  

    - 이미지는 변경 되지 않습니다 하 고 사용 하는 경우 **KnownMonikers**, 한 다음 해당 속성을 정적으로 바인딩할 합니다 **KnownMoniker**합니다. (위의 예제 참조).  

    - 이미지는 변경 되지 않습니다 사용자 고유의 사용자 지정 이미지를 사용 하는 경우 다음 정적으로 바인딩할 사용자 고유의 모니커.  

    - 이미지를 변경할 수 있으면 모니커 특성을 속성 변경 내용에 알리는 코드 속성에 바인딩하십시오.  

3. 어딘가에 UI 계층 구조를 설정 **ImageThemingUtilities.ImageBackgroundColor** 있는지 색 반전 되도록 제대로 적용 됩니다.  

    - 사용 해야 합니다 **BrushToColorConverter** 클래스입니다. (위의 예제 참조).  

## <a name="how-do-i-update-win32-ui"></a>Win32 UI를 업데이트 하려면 어떻게 해야 하나요?  
 로드 하는 원시 이미지의 이름을 바꾸려면 해당 되는 경우 다음 코드를 추가 합니다. 필요에 따라 HICONs HIMAGELIST 비교와 이러한 방식으로 반환 하는 것에 대 한 값을 전환 합니다.  

 **이미지 서비스**  

```cpp  
CComPtr<IVsImageService2> spImgSvc;  
CGlobalServiceProvider::HrQueryService(SID_SVsImageService, &spImgSvc);  
```  

 **이미지를 요청합니다.**  

```cpp  
ImageAttributes attr = { 0 };  
attr.StructSize      = sizeof(attributes);  
attr.Format          = DF_Win32;  
// IT_Bitmap for HBITMAP, IT_Icon for HICON, IT_ImageList for HIMAGELIST  
attr.ImageType       = IT_Bitmap;  
attr.LogicalWidth    = 16;  
attr.LogicalHeight   = 16;  
attr.Dpi             = VsUI::DpiHelper::GetDeviceDpiX();  
attr.Background      = 0xFFFFFFFF;  
// Desired RGBA color, if you don't use this, don't set IAF_Background below  
attr.Flags           = IAF_RequiredFlags | IAF_Background;  

CComPtr<IVsUIObject> spImg;  
// Replace this KnownMoniker with your desired ImageMoniker  
spImgSvc->GetImage(KnownMonikers::Blank, attributes, &spImg);  

```  

## <a name="how-do-i-update-winforms-ui"></a>WinForms UI를 업데이트 하려면 어떻게 해야 하나요?  
 로드 하는 원시 이미지의 이름을 바꾸려면 해당 되는 경우 다음 코드를 추가 합니다. 필요에 따라 비트맵 및 아이콘을 반환 하는 것에 대 한 값을 전환 합니다.  

 **문을 사용 하 여 도움이**  

```csharp  
using GelUtilities = Microsoft.Internal.VisualStudio.PlatformUI.Utilities;  
```  

 **이미지 서비스**  

```csharp  
// This or your preferred way of querying for Visual Studio services  
IVsImageService2 imageService = (IVsImageService2)Package.GetGlobalService(typeof(SVsImageService));  

```  

 **이미지를 요청 합니다.**  

```csharp  
ImageAttributes attributes = new ImageAttributes  
{  
    StructSize    = Marshal.SizeOf(typeof(ImageAttributes)),  
    // IT_Bitmap for Bitmap, IT_Icon for Icon  
    ImageType     = (uint)_UIImageType.IT_Bitmap,  
    Format        = (uint)_UIDataFormat.DF_WinForms,  
    LogicalWidth  = 16,  
    LogicalHeight = 16,  
    // Desired RGBA color, if you don't use this, don't set IAF_Background below  
    Background    = 0xFFFFFFFF,  
    Flags = (uint)_ImageAttributesFlags.IAF_RequiredFlags | _ImageAttributesFlags.IAF_Background,  
};  

// Replace this KnownMoniker with your desired ImageMoniker  
IVsUIObject uIObj = imageService.GetImage(KnownMonikers.Blank, attributes);  

Bitmap bitmap = (Bitmap)GelUtilities.GetObjectData(uiObj); // Use this if you need a bitmap  
// Icon icon = (Icon)GelUtilities.GetObjectData(uiObj); // Use this if you need an icon  

```  

## <a name="how-do-i-use-image-monikers-in-a-new-tool-window"></a>새 도구 창에서 이미지 모니커를 사용 하는 방법  
 VSIX 패키지 프로젝트 템플릿은 Visual Studio 2015에 대 한 업데이트 되었습니다. 새 도구 창을 만들려면 VSIX 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 "새 항목... 추가" 선택 (Ctrl+Shift+A). 프로젝트 언어에 대 한 확장성 노드 아래의 "사용자 지정 도구 창," 선택 "추가" 단추를 누르고 도구 창에 이름을 지정 합니다.  

 이들은 도구 창에서 모니커를 사용 하는 키 위치입니다. 각각에 대 한 지침을 따르세요.  

1. 도구 창 탭 탭 작은 경우 (Ctrl + Tab 창 전환기에도 사용)에 충분 합니다.  

    파생 된 클래스의 생성자에이 줄을 추가 합니다 **ToolWindowPane** 형식:  

   ```csharp  
   // Replace this KnownMoniker with your desired ImageMoniker  
   this.BitmapImageMoniker = KnownMonikers.Blank;  
   ```  

2. 도구 창을 열려면 명령입니다.  

    패키지에 대 한.vsct 파일에서 도구 창의 명령 단추를 편집 합니다.  

   ```xml  
   <Button guid="guidPackageCmdSet" id="CommandId" priority="0x0100" type="Button">  
     <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>  
     <!-- Replace this KnownMoniker with your desired ImageMoniker -->  
     <Icon guid="ImageCatalogGuid" id="Blank" />  
     <!-- Add this -->  
     <CommandFlag>IconIsMoniker</CommandFlag>  
     <Strings>  
       <ButtonText>MyToolWindow</ButtonText>  
     </Strings>  
   </Button>  
   ```  

   **기존 도구 창에서 이미지 모니커를 사용 하는 방법**  

   이미지 모니커를 사용 하는 기존 도구 창을 업데이트 하는 것은 새 도구 창을 만드는 단계와 비슷합니다.  

   이들은 도구 창에서 모니커를 사용 하는 키 위치입니다. 각각에 대 한 지침을 따르세요.  

3. 도구 창 탭 탭 작은 경우 (Ctrl + Tab 창 전환기에도 사용)에 충분 합니다.  

   1. 파생 된 클래스의 생성자에서 (있는 경우) 다음이 줄을 제거 합니다 **ToolWindowPane** 형식:  

       ```csharp  
       this.BitmapResourceID = <Value>;  
       this.BitmapIndex = <Value>;  
       ```  

   2. 단계 # 1의 참조는 "어떻게 할까요 새 도구 창에서 사용 하 여 이미지 모니커?" 위의 섹션입니다.  

4. 도구 창을 열려면 명령입니다.  

   - 2 단계가 표시 된 "작업 방법에 새 도구 창 사용 하 여 이미지 모니커?" 위의 섹션입니다.  

## <a name="how-do-i-use-image-monikers-in-a-vsct-file"></a>.Vsct 파일에서 이미지 모니커를 사용 하는 방법  
 주석 처리 된 줄 아래에 표시 된 대로.vsct 파일을 업데이트 합니다.  

```xml  
<?xml version="1.0" encoding="utf-8"?>  
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <!--  Include the definitions for images included in the VS image catalog -->  
  <Include href="KnownImageIds.vsct"/>  
  <Commands package="guidMyPackage">  
    <Buttons>  
      <Button guid="guidMyCommandSet" id="cmdidMyCommand" priority="0x0000" type="Button">  
        <!-- Add an Icon element, changing the attributes to match the image moniker you want to use.  
             In this case, we’re using the Guid for the VS image catalog.  
             Change the id attribute to be the ID of the desired image moniker. -->  
        <Icon guid="ImageCatalogGuid" id="OpenFolder" />  
        <CommandFlag>DynamicVisibility</CommandFlag>  
        <CommandFlag>DefaultInvisible</CommandFlag>  
        <CommandFlag>DefaultDisabled</CommandFlag>  
        <CommandFlag>CommandWellOnly</CommandFlag>  
        <CommandFlag>IconAndText</CommandFlag>  
        <!-- Add the IconIsMoniker CommandFlag -->  
        <CommandFlag>IconIsMoniker</CommandFlag>  
        <Strings>  
          <ButtonText>Quick Fixes...</ButtonText>  
          <CommandName>Show Quick Fixes</CommandName>  
          <CanonicalName>ShowQuickFixes</CanonicalName>  
          <LocCanonicalName>ShowQuickFixes</LocCanonicalName>  
        </Strings>  
      </Button>  
    </Buttons>  
  </Commands>  
  <!-- It is recommended that you remove <Bitmap> elements that are no longer used in the vsct file -->  
  <Symbols>  
    <GuidSymbol name="guidMyPackage"    value="{1491e936-6ffe-474e-8371-30e5920d8fdd}" />  
    <GuidSymbol name="guidMyCommandSet" value="{10347de4-69a9-47f4-a950-d3301f6d2bc7}">  
      <IDSymbol name="cmdidMyCommand" value="0x9437" />  
    </GuidSymbol>  
  </Symbols>  
</CommandTable>  
```  

 **그렇다면 이전 버전의 Visual Studio에서 읽을 수 있도록 내.vsct 파일 해야?**  

 이전 버전의 Visual Studio를 인식 하지 못하는 합니다 **IconIsMoniker** 명령 플래그입니다. 이미지 서비스에서 이미지를 지원 하지만 계속 이전 버전의 Visual Studio에서 이전 스타일 이미지를 사용 하는 버전의 Visual Studio에서 사용할 수 있습니다. 이 위해 변경 되지 않은 (및 이전 버전의 Visual Studio와 호환 되므로).vsct 파일을 유지 하는.vsct 파일에 정의 된 GUID/i D 쌍에서 매핑하는 CSV (쉼표로 구분 된 값) 파일 만들기 \<비트맵 > 이미지 요소 모니커 GUID/ID 쌍입니다.  

 매핑 CSV 파일의 형식은 다음과 같습니다.  

```  
Icon guid, Icon id, Moniker guid, Moniker id  
b714fcf7-855e-4e4c-802a-1fd87144ccad,1,fda30684-682d-421c-8be4-650a2967058e,100  
b714fcf7-855e-4e4c-802a-1fd87144ccad,2,fda30684-682d-421c-8be4-650a2967058e,200  
```  

 패키지를 사용 하 여 CSV 파일을 배포 하 고 해당 위치를 지정 하 여는 **IconMappingFilename** 의 속성을 **ProvideMenuResource** 패키지 특성:  

```csharp  
[ProvideMenuResource("MyPackage.ctmenu", 1, IconMappingFilename="IconMappings.csv")]  
```  

 합니다 **IconMappingFilename** @"%UserProfile%\ 같은 환경 변수를 정의한 디렉터리에서 명시적으로 시작 하는 절대 경로 또는 상대 경로 암시적으로 루 팅 (예에서 같이 위의) $PackageFolder $ dir1\dir2\MyMappingFile.csv "입니다.  

## <a name="how-do-i-port-a-project-system"></a>프로젝트 시스템을 포트 수행는 방법  
 **프로젝트에 대해 ImageMonikers를 제공 하는 방법**  

1. 구현 **VSHPROPID_SupportsIconMonikers** 프로젝트의 **IVsHierarchy**, true를 반환 합니다.  

2. 구현 **VSHPROPID_IconMonikerImageList** (원래 프로젝트를 사용 하는 경우 **VSHPROPID_IconImgList**) 또는 **VSHPROPID_IconMonikerGuid**,  **VSHPROPID_IconMonikerId**하십시오 **VSHPROPID_OpenFolderIconMonikerGuid**합니다 **VSHPROPID_OpenFolderIconMonikerId** (원래 프로젝트를 사용 하는 경우  **VSHPROPID_IconHandle** 하 고 **VSHPROPID_OpenFolderIconHandle**).  

3. "레거시"의 버전을 만드는 아이콘 확장점 요청 하는 경우 아이콘에 대 한 원래 VSHPROPIDs의 구현을 변경 합니다. **IVsImageService2** 아이콘에 해당 하는 데 필요한 기능을 제공 합니다.  

   **VB에 대 한 추가 요구 사항이 C# 프로젝트 특성 /**  

   만 구현 **VSHPROPID_SupportsIconMonikers** 프로젝트가 것을 감지 하는 경우를 **바깥쪽 flavor**합니다. 이 고, 그렇지 실제 가장 바깥쪽 버전을 실제로 이미지 모니커를 지원 하지 않을 수 및 기본 버전에 효과적으로 "숨어서 실행" 사용자 지정된 이미지입니다.  

   **CPS에서 이미지 모니커를 사용 하는 방법**  

   CPS (공통 프로젝트 시스템)에서 사용자 지정 이미지를 설정 수동으로 또는 프로젝트 시스템 확장 SDK를 사용 하 여 제공 되는 항목 템플릿을 통해 수행할 수 있습니다.  

   **프로젝트 시스템 확장 SDK를 사용 하 여**  

   지침을 따르세요 [프로젝트 형식/항목 형식에 대 한 사용자 지정 아이콘을 제공](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/scenario/provide_custom_icons_for_the_project_or_item_type.md) CPS 이미지를 사용자 지정할 수 있습니다. 자세한 내용은 CPS에서 찾을 수 있습니다 [Visual Studio 프로젝트 시스템 확장 설명서](https://github.com/Microsoft/VSProjectSystem)  

   **수동으로 ImageMonikers 사용**  

4. 구현 및 내보내기 합니다 **IProjectTreeModifier** 프로젝트 시스템의 인터페이스입니다.  

5. 결정 **KnownMoniker** 또는 사용자 지정 이미지 모니커를 사용 하려면.  

6. 에 **ApplyModifications** 메서드를 다음을 수행 비슷하게 새 트리를 반환 하기 전에 메서드 내의 아래 예제:  

   ```csharp  
   // Replace this KnownMoniker with your desired ImageMoniker  
   tree = tree.SetIcon(KnownMonikers.Blank.ToProjectSystemType());  
   ```  

7. 새 트리를 만드는 경우 원하는 모니커 비슷합니다 NewTree 메서드를 전달 하 여 사용자 지정 이미지를 설정할 수 있습니다는 아래 예제:  

   ```csharp  
   // Replace this KnownMoniker with your desired ImageMoniker  
   ProjectImageMoniker icon         = KnownMonikers.FolderClosed.ToProjectSystemType();  
   ProjectImageMoniker expandedIcon = KnownMonikers.FolderOpened.ToProjectSystemType();  

   return this.ProjectTreeFactory.Value.NewTree(/*caption*/<value>,  
                                                /*filePath*/<value>,  
                                                /*browseObjectProperties*/<value>,  
                                                icon,  
                                                expandedIcon);  
   ```  

## <a name="how-do-i-convert-from-a-real-image-strip-to-a-moniker-based-image-strip"></a>변환 하는 방법 실제 이미지 스트립에서 모니커 기반 이미지 스트립에?  
 **HIMAGELISTs를 지원 해야 하는 경우**  

 이미지 서비스를 사용 하 여 업데이트 하려는 하지만 이미지 목록 전달 해야 하는 Api에 의해 제한 되는 코드에 대 한 기존 이미지 스트립의 경우 여전히 이미지 서비스의 이점을 얻을 수 있습니다. 모니커 기반 이미지 스트립을 만들려면 기존 모니커에서 매니페스트를 만들려면 다음 단계를 수행 합니다.  

1. 실행 합니다 **ManifestFromResources** 도구인 이미지 스트립을 전달 합니다. 이 줄에 대 한 매니페스트를 생성 됩니다.  

   - 권장: 용도 맞게 매니페스트에 대 한 기본이 아닌 이름을 제공 합니다.  

2. 만 사용 하는 경우 **KnownMonikers**, 다음을 수행 합니다.  

   - 대체는 \<이미지 > 섹션으로 매니페스트에 \<이미지 / >입니다.  

   - 모든 subimage Id를 제거 (개 \<imagestrip 이름 > _ # #).  

   - 권장: AssetsGuid 기호 및 용도 맞게 이미지 스트립 기호 이름을 바꿉니다.  

   - 각 대체 **ContainedImage**의 각 $(ImageCatalogGuid)를 사용 하 여 GUID 바꿀 **ContainedImage**의 $를 사용 하 여 ID (\<모니커 >), 각 외부="true"특성추가**ContainedImage**  

       - \<모니커 > 바꿔야 합니다 **KnownMoniker** 이미지와 일치 하는 같지만 "KnownMonikers" 이름에서 제거 합니다.  

   - 추가 < 가져오기 Manifest="$(ManifestFolder)\\< 디렉터리 경로 설치 하는 상대\>\Microsoft.VisualStudio.ImageCatalog.imagemanifest" /\> 의 맨 위에 \<기호 > 섹션.  

       - 상대 경로 매니페스트에 대 한 제작 설치에 정의 된 배포 위치에 따라 결정 됩니다.  

3. 실행 합니다 **ManifestToCode** 기존 코드에는 모니커 이미지 스트립에 대 한 이미지 서비스를 쿼리 하는 데 사용할 수 있도록 래퍼를 생성 하는 도구입니다.  

   - 권장: 래퍼 및 용도 맞게 네임 스페이스에 대 한 기본이 아닌 이름을 제공 합니다.  

4. 모든 작업을 수행 합니다 추가 설치 작성/배포 및 다른 코드 변경은 이미지 서비스 및 새 파일을 사용 하 합니다.  

   샘플 매니페스트를 내부 및 외부 이미지 처럼 보여야 합니다 참조를 포함 합니다.  

```xml  
<?xml version="1.0"?>  
<ImageManifest  
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"  
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
  xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014">  

  <Symbols>  
    <!-- This needs to be the relative path from your manifest to the ImageCatalog's manifest  
         where $(ManifestFolder) is the deployed location of this manifest. -->  
    <Import Manifest="$(ManifestFolder)\<RelPath>\Microsoft.VisualStudio.ImageCatalog.imagemanifest" />  

    <String Name="Resources" Value="/My.Assembly.Name;Component/Resources/ImageStrip" />  
    <Guid Name="ImageGuid" Value="{fb41b7ef-6587-480c-aa27-5b559d42cfc9}" />  
    <Guid Name="ImageStripGuid" Value="{9c84a570-d9a7-4052-a340-188fb276f973}" />  
    <ID Name="MyImage_0" Value="100" />  
    <ID Name="MyImage_1" Value="101" />  
    <ID Name="InternalList" Value="1001" />  
    <ID Name="ExternalList" Value="1002" />  
  </Symbols>  

  <Images>  
    <Image Guid="$(ImageGuid)" ID="$(MyImage_0)">  
      <Source Uri="$(Resources)/MyImage_0.png">  
        <Size Value="16" />  
      </Source>  
    </Image>  
    <Image Guid="$(ImageGuid)" ID="$(MyImage_1)">  
      <Source Uri="$(Resources)/MyImage_1.png">  
        <Size Value="16" />  
      </Source>  
    </Image>  
  </Images>  

  <ImageLists>  
    <ImageList Guid="$(ImageStripGuid)" ID="$(InternalList)">  
      <ContainedImage Guid="$(ImageGuid)" ID="$(MyImage_0)" />  
      <ContainedImage Guid="$(ImageGuid)" ID="$(MyImage_1)" />  
    </ImageList>  
    <ImageList Guid="$(ImageStripGuid)" ID="$(ExternalList)">  
      <ContainedImage Guid="$(ImageCatalogGuid)" ID="$(StatusError)" External="true" />  
      <ContainedImage Guid="$(ImageCatalogGuid)" ID="$(StatusWarning)" External="true" />  
      <ContainedImage Guid="$(ImageCatalogGuid)" ID="$(StatusInformation)" External="true" />  
    </ImageList>  
  </ImageLists>  

</ImageManifest>  
```  

 **HIMAGELISTs 지원할 필요가 없습니다.**  

1. 집합을 결정 **KnownMonikers** 프로그램 이미지 스트립에 있는 이미지와 일치는 또는 사용자 이미지 스트립에서 이미지에 대 한 고유한 모니커를 만듭니다.  

2. 필요한 인덱스 대신 모니커를 사용 하도록 이미지 스트립에 있는 이미지를 가져오는 데 모든 매핑을 업데이트 합니다.  

3. 이미지 서비스 요청을 통해 업데이트 되는 매핑의 모니커를 사용 하도록 코드를 업데이트 합니다. (업데이트를 의미할 수 있습니다 **CrispImages** 관리 코드 또는 이러한 방식으로 또는 HICONs 이미지 서비스에서 요청 및 네이티브 코드에 대 한 관련 전달 합니다.)  

## <a name="testing-your-images"></a>이미지를 테스트합니다.  
 이미지 라이브러리 뷰어 도구를 사용 하 여 모든 것이 제대로 작성 되었는지 확인 하 여 이미지 매니페스트를 테스트할 수 있습니다. 도구를 [Visual Studio 2015 SDK](https://msdn.microsoft.com/library/bb166441.aspx)합니다. 이 도구 및 기타 도구에 대 한 설명서를 찾을 수 있습니다 [여기](https://aka.ms/VSImageThemeTools)합니다.  

## <a name="additional-resources"></a>추가 자료  

### <a name="samples"></a>샘플  
 GitHub에서 Visual Studio 샘플의 여러 다양 한 Visual Studio 확장성 지점의 일환으로 이미지 서비스를 사용 하는 방법을 보여 주는 업데이트 되었습니다.  

 확인할 [ http://github.com/Microsoft/VSSDK-Extensibility-Samples ](http://github.com/Microsoft/VSSDK-Extensibility-Samples) 최신 샘플에 대 한 합니다.  

### <a name="tooling"></a>도구  
 이미지 서비스와 작동 하는 UI를 작성/업데이트 지원 하기 위해 이미지 서비스에 대 한 지원 도구 집합을 만들었습니다. 각 도구에 대 한 자세한 내용은 도구와 함께 제공 되는 설명서를 확인 합니다. 도구는의 일부분으로 포함 된 [Visual Studio 2015 SDK.](https://msdn.microsoft.com/library/bb166441.aspx)  

 **ManifestFromResources**  

 매니페스트 리소스 도구에서 이미지 리소스 (PNG 또는 XAML)의 목록을 사용 하 고 이미지 서비스를 사용 하 여 해당 이미지를 사용 하 여 이미지 매니페스트 파일을 생성 합니다.  

 **ManifestToCode**  

 매니페스트 코드 도구를 이미지 매니페스트 파일을 사용 하 고 코드에서 매니페스트 값 참조에 대 한 래퍼 파일을 생성 (C++, C#, 또는 VB) 또는.vsct 파일입니다.  

 **ImageLibraryViewer**  

 이미지 라이브러리 뷰어 도구 이미지 매니페스트를 로드할 수 있습니다 및 Visual Studio 매니페스트가 제대로 작성 되었는지 확인 하는 동일한 방식으로 조작할 수 있습니다. 백그라운드, 크기, DPI 설정, 고대비 등 및 기타 설정을 변경할 수 있습니다. 또한 매니페스트에서 오류를 찾을 수 로드 정보를 표시 하 고 매니페스트에 각 이미지에 대 한 소스 정보를 표시 합니다.  

## <a name="faq"></a>FAQ  

- 로드할 때 포함 해야 하는 종속성이 있습니까 \<Include="Microsoft.VisualStudio.* 참조 합니다. Interop.14.0.DesignTime"/ >?  

  - EmbedInteropTypes 설정 = "true" 모든 interop Dll에 있습니다.  

- 이미지 매니페스트는 my 확장을 사용 하 여 배포 하려면 어떻게 해야 하나요?  

  - 프로젝트에.imagemanifest 파일을 추가 합니다.  

  - "VSIX에 포함"을 true로 설정 합니다.  

- CPS 프로젝트 시스템 내를 업데이트 합니다. 변경 내용 **ImageName** 하 고 **StockIconService**?  

  - 이러한 CPS 모니커를 사용 하도록 업데이트 되었을 때 제거 되었습니다. 더 이상 호출 해야 합니다 **StockIconService**, 원하는 전달 하기만 하면 됩니다 **KnownMoniker** 메서드를 사용 하 여 속성에는 **ToProjectSystemType()** 확장 메서드 CPS 유틸리티입니다. 매핑을 찾을 수 있습니다 **ImageName** 하 **KnownMonikers** 아래:  

    |||  
    |-|-|  
    |**ImageName**|**KnownMoniker**|  
    |ImageName.OfflineWebApp|KnownImageIds.Web|  
    |ImageName.WebReferencesFolder|KnownImageIds.Web|  
    |ImageName.OpenReferenceFolder|KnownImageIds.FolderOpened|  
    |ImageName.ReferenceFolder|KnownImageIds.Reference|  
    |ImageName.Reference|KnownImageIds.Reference|  
    |ImageName.SdlWebReference|KnownImageIds.WebReferenceFolder|  
    |ImageName.DiscoWebReference|KnownImageIds.DynamicDiscoveryDocument|  
    |ImageName.Folder|KnownImageIds.FolderClosed|  
    |ImageName.OpenFolder|KnownImageIds.FolderOpened|  
    |ImageName.ExcludedFolder|KnownImageIds.HiddenFolderClosed|  
    |ImageName.OpenExcludedFolder|KnownImageIds.HiddenFolderOpened|  
    |ImageName.ExcludedFile|KnownImageIds.HiddenFile|  
    |ImageName.DependentFile|KnownImageIds.GenerateFile|  
    |ImageName.MissingFile|KnownImageIds.DocumentWarning|  
    |ImageName.WindowsForm|KnownImageIds.WindowsForm|  
    |ImageName.WindowsUserControl|KnownImageIds.UserControl|  
    |ImageName.WindowsComponent|KnownImageIds.ComponentFile|  
    |ImageName.XmlSchema|KnownImageIds.XMLSchema|  
    |ImageName.XmlFile|KnownImageIds.XMLFile|  
    |ImageName.WebForm|KnownImageIds.Web|  
    |ImageName.WebService|KnownImageIds.WebService|  
    |ImageName.WebUserControl|KnownImageIds.WebUserControl|  
    |ImageName.WebCustomUserControl|KnownImageIds.WebCustomControl|  
    |ImageName.AspPage|KnownImageIds.ASPFile|  
    |ImageName.GlobalApplicationClass|KnownImageIds.SettingsFile|  
    |ImageName.WebConfig|KnownImageIds.ConfigurationFile|  
    |ImageName.HtmlPage|KnownImageIds.HTMLFile|  
    |ImageName.StyleSheet|KnownImageIds.StyleSheet|  
    |ImageName.ScriptFile|KnownImageIds.JSScript|  
    |ImageName.TextFile|KnownImageIds.Document|  
    |ImageName.SettingsFile|KnownImageIds.Settings|  
    |ImageName.Resources|KnownImageIds.DocumentGroup|  
    |ImageName.Bitmap|KnownImageIds.Image|  
    |ImageName.Icon|KnownImageIds.IconFile|  
    |ImageName.Image|KnownImageIds.Image|  
    |ImageName.ImageMap|KnownImageIds.ImageMapFile|  
    |ImageName.XWorld|KnownImageIds.XWorldFile|  
    |ImageName.Audio|KnownImageIds.Sound|  
    |ImageName.Video|KnownImageIds.Media|  
    |ImageName.Cab|KnownImageIds.CABProject|  
    |ImageName.Jar|KnownImageIds.JARFile|  
    |ImageName.DataEnvironment|KnownImageIds.DataTable|  
    |ImageName.PreviewFile|KnownImageIds.Report|  
    |ImageName.DanglingReference|KnownImageIds.ReferenceWarning|  
    |ImageName.XsltFile|KnownImageIds.XSLTransform|  
    |ImageName.Cursor|KnownImageIds.CursorFile|  
    |ImageName.AppDesignerFolder|KnownImageIds.Property|  
    |ImageName.Data|KnownImageIds.Database|  
    |ImageName.Application|KnownImageIds.Application|  
    |ImageName.DataSet|KnownImageIds.DatabaseGroup|  
    |ImageName.Pfx|KnownImageIds.Certificate|  
    |ImageName.Snk|KnownImageIds.Rule|  
    |ImageName.VisualBasicProject|KnownImageIds.VBProjectNode|  
    |ImageName.CSharpProject|KnownImageIds.CSProjectNode|  
    |ImageName.Empty|KnownImageIds.Blank|  
    |ImageName.MissingFolder|KnownImageIds.FolderOffline|  
    |ImageName.SharedImportReference|KnownImageIds.SharedProject|  
    |ImageName.SharedProjectCs|KnownImageIds.CSSharedProject|  
    |ImageName.SharedProjectVc|KnownImageIds.CPPSharedProject|  
    |ImageName.SharedProjectJs|KnownImageIds.JSSharedProject|  
    |ImageName.CSharpCodeFile|KnownImageIds.CSFileNode|  
    |ImageName.VisualBasicCodeFile|KnownImageIds.VBFileNode|  

  - 내 완료 목록 공급자를 업데이트 합니다. 어떤 **KnownMonikers** 이전 일치 **StandardGlyphGroup** 하 고 **StandardGlyph** 값?  

    ||||  
    |-|-|-|  
    |GlyphGroupClass|GlyphItemPublic|ClassPublic|  
    |GlyphGroupClass|GlyphItemInternal|ClassInternal|  
    |GlyphGroupClass|GlyphItemFriend|ClassInternal|  
    |GlyphGroupClass|GlyphItemProtected|ClassProtected|  
    |GlyphGroupClass|GlyphItemPrivate|ClassPrivate|  
    |GlyphGroupClass|GlyphItemShortcut|ClassShortcut|  
    |GlyphGroupConstant|GlyphItemPublic|ClassPublic|  
    |GlyphGroupConstant|GlyphItemInternal|ClassInternal|  
    |GlyphGroupConstant|GlyphItemFriend|ClassInternal|  
    |GlyphGroupConstant|GlyphItemProtected|ClassProtected|  
    |GlyphGroupConstant|GlyphItemPrivate|ClassPrivate|  
    |GlyphGroupConstant|GlyphItemShortcut|ClassShortcut|  
    |GlyphGroupDelegate|GlyphItemPublic|DelegatePublic|  
    |GlyphGroupDelegate|GlyphItemInternal|DelegateInternal|  
    |GlyphGroupDelegate|GlyphItemFriend|DelegateInternal|  
    |GlyphGroupDelegate|GlyphItemProtected|DelegateProtected|  
    |GlyphGroupDelegate|GlyphItemPrivate|DelegatePrivate|  
    |GlyphGroupDelegate|GlyphItemShortcut|DelegateShortcut|  
    |GlyphGroupEnum|GlyphItemPublic|EnumerationPublic|  
    |GlyphGroupEnum|GlyphItemInternal|EnumerationInternal|  
    |GlyphGroupEnum|GlyphItemFriend|EnumerationInternal|  
    |GlyphGroupEnum|GlyphItemProtected|EnumerationProtected|  
    |GlyphGroupEnum|GlyphItemPrivate|EnumerationPrivate|  
    |GlyphGroupEnum|GlyphItemShortcut|EnumerationShortcut|  
    |GlyphGroupEnumMember|GlyphItemPublic|EnumerationMemberPublic|  
    |GlyphGroupEnumMember|GlyphItemInternal|EnumerationMemberInternal|  
    |GlyphGroupEnumMember|GlyphItemFriend|EnumerationMemberInternal|  
    |GlyphGroupEnumMember|GlyphItemProtected|EnumerationMemberProtected|  
    |GlyphGroupEnumMember|GlyphItemPrivate|EnumerationMemberPrivate|  
    |GlyphGroupEnumMember|GlyphItemShortcut|EnumerationMemberShortcut|  
    |GlyphGroupEvent|GlyphItemPublic|EventPublic|  
    |GlyphGroupEvent|GlyphItemInternal|EventInternal|  
    |GlyphGroupEvent|GlyphItemFriend|EventInternal|  
    |GlyphGroupEvent|GlyphItemProtected|EventProtected|  
    |GlyphGroupEvent|GlyphItemPrivate|EventPrivate|  
    |GlyphGroupEvent|GlyphItemShortcut|EventShortcut|  
    |GlyphGroupException|GlyphItemPublic|ExceptionPublic|  
    |GlyphGroupException|GlyphItemInternal|ExceptionInternal|  
    |GlyphGroupException|GlyphItemFriend|ExceptionInternal|  
    |GlyphGroupException|GlyphItemProtected|ExceptionProtected|  
    |GlyphGroupException|GlyphItemPrivate|ExceptionPrivate|  
    |GlyphGroupException|GlyphItemShortcut|ExceptionShortcut|  
    |GlyphGroupField|GlyphItemPublic|FieldPublic|  
    |GlyphGroupField|GlyphItemInternal|FieldInternal|  
    |GlyphGroupField|GlyphItemFriend|FieldInternal|  
    |GlyphGroupField|GlyphItemProtected|FieldProtected|  
    |GlyphGroupField|GlyphItemPrivate|FieldPrivate|  
    |GlyphGroupField|GlyphItemShortcut|FieldShortcut|  
    |GlyphGroupInterface|GlyphItemPublic|InterfacePublic|  
    |GlyphGroupInterface|GlyphItemInternal|InterfaceInternal|  
    |GlyphGroupInterface|GlyphItemFriend|InterfaceInternal|  
    |GlyphGroupInterface|GlyphItemProtected|InterfaceProtected|  
    |GlyphGroupInterface|GlyphItemPrivate|InterfacePrivate|  
    |GlyphGroupInterface|GlyphItemShortcut|InterfaceShortcut|  
    |GlyphGroupMacro|GlyphItemPublic|MacroPublic|  
    |GlyphGroupMacro|GlyphItemInternal|MacroInternal|  
    |GlyphGroupMacro|GlyphItemFriend|MacroInternal|  
    |GlyphGroupMacro|GlyphItemProtected|MacroProtected|  
    |GlyphGroupMacro|GlyphItemPrivate|MacroPrivate|  
    |GlyphGroupMacro|GlyphItemShortcut|MacroShortcut|  
    |GlyphGroupMap|GlyphItemPublic|MapPublic|  
    |GlyphGroupMap|GlyphItemInternal|MapInternal|  
    |GlyphGroupMap|GlyphItemFriend|MapInternal|  
    |GlyphGroupMap|GlyphItemProtected|MapProtected|  
    |GlyphGroupMap|GlyphItemPrivate|MapPrivate|  
    |GlyphGroupMap|GlyphItemShortcut|MapShortcut|  
    |GlyphGroupMapItem|GlyphItemPublic|MapItemPublic|  
    |GlyphGroupMapItem|GlyphItemInternal|MapItemInternal|  
    |GlyphGroupMapItem|GlyphItemFriend|MapItemInternal|  
    |GlyphGroupMapItem|GlyphItemProtected|MapItemProtected|  
    |GlyphGroupMapItem|GlyphItemPrivate|MapItemPrivate|  
    |GlyphGroupMapItem|GlyphItemShortcut|MapItemShortcut|  
    |GlyphGroupMethod|GlyphItemPublic|MethodPublic|  
    |GlyphGroupMethod|GlyphItemInternal|MethodInternal|  
    |GlyphGroupMethod|GlyphItemFriend|MethodInternal|  
    |GlyphGroupMethod|GlyphItemProtected|MethodProtected|  
    |GlyphGroupMethod|GlyphItemPrivate|MethodPrivate|  
    |GlyphGroupMethod|GlyphItemShortcut|MethodShortcut|  
    |GlyphGroupOverload|GlyphItemPublic|MethodPublic|  
    |GlyphGroupOverload|GlyphItemInternal|MethodInternal|  
    |GlyphGroupOverload|GlyphItemFriend|MethodInternal|  
    |GlyphGroupOverload|GlyphItemProtected|MethodProtected|  
    |GlyphGroupOverload|GlyphItemPrivate|MethodPrivate|  
    |GlyphGroupOverload|GlyphItemShortcut|MethodShortcut|  
    |GlyphGroupModule|GlyphItemPublic|ModulePublic|  
    |GlyphGroupModule|GlyphItemInternal|ModuleInternal|  
    |GlyphGroupModule|GlyphItemFriend|ModuleInternal|  
    |GlyphGroupModule|GlyphItemProtected|ModuleProtected|  
    |GlyphGroupModule|GlyphItemPrivate|ModulePrivate|  
    |GlyphGroupModule|GlyphItemShortcut|ModuleShortcut|  
    |GlyphGroupNamespace|GlyphItemPublic|NamespacePublic|  
    |GlyphGroupNamespace|GlyphItemInternal|NamespaceInternal|  
    |GlyphGroupNamespace|GlyphItemFriend|NamespaceInternal|  
    |GlyphGroupNamespace|GlyphItemProtected|NamespaceProtected|  
    |GlyphGroupNamespace|GlyphItemPrivate|NamespacePrivate|  
    |GlyphGroupNamespace|GlyphItemShortcut|NamespaceShortcut|  
    |GlyphGroupOperator|GlyphItemPublic|OperatorPublic|  
    |GlyphGroupOperator|GlyphItemInternal|OperatorInternal|  
    |GlyphGroupOperator|GlyphItemFriend|OperatorInternal|  
    |GlyphGroupOperator|GlyphItemProtected|OperatorProtected|  
    |GlyphGroupOperator|GlyphItemPrivate|OperatorPrivate|  
    |GlyphGroupOperator|GlyphItemShortcut|OperatorShortcut|  
    |GlyphGroupProperty|GlyphItemPublic|PropertyPublic|  
    |GlyphGroupProperty|GlyphItemInternal|PropertyInternal|  
    |GlyphGroupProperty|GlyphItemFriend|PropertyInternal|  
    |GlyphGroupProperty|GlyphItemProtected|PropertyProtected|  
    |GlyphGroupProperty|GlyphItemPrivate|PropertyPrivate|  
    |GlyphGroupProperty|GlyphItemShortcut|PropertyShortcut|  
    |GlyphGroupStruct|GlyphItemPublic|StructurePublic|  
    |GlyphGroupStruct|GlyphItemInternal|StructureInternal|  
    |GlyphGroupStruct|GlyphItemFriend|StructureInternal|  
    |GlyphGroupStruct|GlyphItemProtected|StructureProtected|  
    |GlyphGroupStruct|GlyphItemPrivate|StructurePrivate|  
    |GlyphGroupStruct|GlyphItemShortcut|StructureShortcut|  
    |GlyphGroupTemplate|GlyphItemPublic|TemplatePublic|  
    |GlyphGroupTemplate|GlyphItemInternal|TemplateInternal|  
    |GlyphGroupTemplate|GlyphItemFriend|TemplateInternal|  
    |GlyphGroupTemplate|GlyphItemProtected|TemplateProtected|  
    |GlyphGroupTemplate|GlyphItemPrivate|TemplatePrivate|  
    |GlyphGroupTemplate|GlyphItemShortcut|TemplateShortcut|  
    |GlyphGroupTypedef|GlyphItemPublic|TypeDefinitionPublic|  
    |GlyphGroupTypedef|GlyphItemInternal|TypeDefinitionInternal|  
    |GlyphGroupTypedef|GlyphItemFriend|TypeDefinitionInternal|  
    |GlyphGroupTypedef|GlyphItemProtected|TypeDefinitionProtected|  
    |GlyphGroupTypedef|GlyphItemPrivate|TypeDefinitionPrivate|  
    |GlyphGroupTypedef|GlyphItemShortcut|TypeDefinitionShortcut|  
    |GlyphGroupType|GlyphItemPublic|TypePublic|  
    |GlyphGroupType|GlyphItemInternal|TypeInternal|  
    |GlyphGroupType|GlyphItemFriend|TypeInternal|  
    |GlyphGroupType|GlyphItemProtected|TypeProtected|  
    |GlyphGroupType|GlyphItemPrivate|TypePrivate|  
    |GlyphGroupType|GlyphItemShortcut|TypeShortcut|  
    |GlyphGroupUnion|GlyphItemPublic|UnionPublic|  
    |GlyphGroupUnion|GlyphItemInternal|UnionInternal|  
    |GlyphGroupUnion|GlyphItemFriend|UnionInternal|  
    |GlyphGroupUnion|GlyphItemProtected|UnionProtected|  
    |GlyphGroupUnion|GlyphItemPrivate|UnionPrivate|  
    |GlyphGroupUnion|GlyphItemShortcut|UnionShortcut|  
    |GlyphGroupVariable|GlyphItemPublic|FieldPublic|  
    |GlyphGroupVariable|GlyphItemInternal|FieldInternal|  
    |GlyphGroupVariable|GlyphItemFriend|FieldInternal|  
    |GlyphGroupVariable|GlyphItemProtected|FieldProtected|  
    |GlyphGroupVariable|GlyphItemPrivate|FieldPrivate|  
    |GlyphGroupVariable|GlyphItemShortcut|FieldShortcut|  
    |GlyphGroupValueType|GlyphItemPublic|ValueTypePublic|  
    |GlyphGroupValueType|GlyphItemInternal|ValueTypeInternal|  
    |GlyphGroupValueType|GlyphItemFriend|ValueTypeInternal|  
    |GlyphGroupValueType|GlyphItemProtected|ValueTypeProtected|  
    |GlyphGroupValueType|GlyphItemPrivate|ValueTypePrivate|  
    |GlyphGroupValueType|GlyphItemShortcut|ValueTypeShortcut|  
    |GlyphGroupIntrinsic|GlyphItemPublic|ObjectPublic|  
    |GlyphGroupIntrinsic|GlyphItemInternal|ObjectInternal|  
    |GlyphGroupIntrinsic|GlyphItemFriend|ObjectInternal|  
    |GlyphGroupIntrinsic|GlyphItemProtected|ObjectProtected|  
    |GlyphGroupIntrinsic|GlyphItemPrivate|ObjectPrivate|  
    |GlyphGroupIntrinsic|GlyphItemShortcut|ObjectShortcut|  
    |GlyphGroupJSharpMethod|GlyphItemPublic|MethodPublic|  
    |GlyphGroupJSharpMethod|GlyphItemInternal|MethodInternal|  
    |GlyphGroupJSharpMethod|GlyphItemFriend|MethodInternal|  
    |GlyphGroupJSharpMethod|GlyphItemProtected|MethodProtected|  
    |GlyphGroupJSharpMethod|GlyphItemPrivate|MethodPrivate|  
    |GlyphGroupJSharpMethod|GlyphItemShortcut|MethodShortcut|  
    |GlyphGroupJSharpField|GlyphItemPublic|FieldPublic|  
    |GlyphGroupJSharpField|GlyphItemInternal|FieldInternal|  
    |GlyphGroupJSharpField|GlyphItemFriend|FieldInternal|  
    |GlyphGroupJSharpField|GlyphItemProtected|FieldProtected|  
    |GlyphGroupJSharpField|GlyphItemPrivate|FieldPrivate|  
    |GlyphGroupJSharpField|GlyphItemShortcut|FieldShortcut|  
    |GlyphGroupJSharpClass|GlyphItemPublic|ClassPublic|  
    |GlyphGroupJSharpClass|GlyphItemInternal|ClassInternal|  
    |GlyphGroupJSharpClass|GlyphItemFriend|ClassInternal|  
    |GlyphGroupJSharpClass|GlyphItemProtected|ClassProtected|  
    |GlyphGroupJSharpClass|GlyphItemPrivate|ClassPrivate|  
    |GlyphGroupJSharpClass|GlyphItemShortcut|ClassShortcut|  
    |GlyphGroupJSharpNamespace|GlyphItemPublic|NamespacePublic|  
    |GlyphGroupJSharpNamespace|GlyphItemInternal|NamespaceInternal|  
    |GlyphGroupJSharpNamespace|GlyphItemFriend|NamespaceInternal|  
    |GlyphGroupJSharpNamespace|GlyphItemProtected|NamespaceProtected|  
    |GlyphGroupJSharpNamespace|GlyphItemPrivate|NamespacePrivate|  
    |GlyphGroupJSharpNamespace|GlyphItemShortcut|NamespaceShortcut|  
    |GlyphGroupJSharpInterface|GlyphItemPublic|InterfacePublic|  
    |GlyphGroupJSharpInterface|GlyphItemInternal|InterfaceInternal|  
    |GlyphGroupJSharpInterface|GlyphItemFriend|InterfaceInternal|  
    |GlyphGroupJSharpInterface|GlyphItemProtected|InterfaceProtected|  
    |GlyphGroupJSharpInterface|GlyphItemPrivate|InterfacePrivate|  
    |GlyphGroupJSharpInterface|GlyphItemShortcut|InterfaceShortcut|  
    |GlyphGroupError||StatusError|  
    |GlyphBscFile||ClassFile|  
    |GlyphAssembly||참조|  
    |GlyphLibrary||Library|  
    |GlyphVBProject||VBProjectNode|  
    |GlyphCoolProject||CSProjectNode|  
    |GlyphCppProject||CPPProjectNode|  
    |GlyphDialogId||대화 상자|  
    |GlyphOpenFolder||FolderOpened|  
    |GlyphClosedFolder||FolderClosed|  
    |GlyphArrow||GoToNext|  
    |GlyphCSharpFile||CSFileNode|  
    |GlyphCSharpExpansion||코드 조각|  
    |GlyphKeyword||IntellisenseKeyword|  
    |GlyphInformation||StatusInformation|  
    |GlyphReference||ClassMethodReference|  
    |GlyphRecursion||재귀|  
    |GlyphXmlItem||Tag|  
    |GlyphJSharpProject||DocumentCollection|  
    |GlyphJSharpDocument||문서|  
    |GlyphForwardType||GoToNext|  
    |GlyphCallersGraph||CallTo|  
    |GlyphCallGraph||CallFrom|  
    |GlyphWarning||StatusWarning|  
    |GlyphMaybeReference||QuestionMark|  
    |GlyphMaybeCaller||CallTo|  
    |GlyphMaybeCall||CallFrom|  
    |GlyphExtensionMethod||ExtensionMethod|  
    |GlyphExtensionMethodInternal||ExtensionMethod|  
    |GlyphExtensionMethodFriend||ExtensionMethod|  
    |GlyphExtensionMethodProtected||ExtensionMethod|  
    |GlyphExtensionMethodPrivate||ExtensionMethod|  
    |GlyphExtensionMethodShortcut||ExtensionMethod|  
    |GlyphXmlAttribute||XmlAttribute|  
    |GlyphXmlChild||XmlElement|  
    |GlyphXmlDescendant||XmlDescendant|  
    |GlyphXmlNamespace||XmlNamespace|  
    |GlyphXmlAttributeQuestion||XmlAttributeLowConfidence|  
    |GlyphXmlAttributeCheck||XmlAttributeHighConfidence|  
    |GlyphXmlChildQuestion||XmlElementLowConfidence|  
    |GlyphXmlChildCheck||XmlElementHighConfidence|  
    |GlyphXmlDescendantQuestion||XmlDescendantLowConfidence|  
    |GlyphXmlDescendantCheck||XmlDescendantHighConfidence|  
    |GlyphCompletionWarning||IntellisenseWarning|
