---
title: VSIX 색 편집기 | Microsoft Docs
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 70879c5d-e0f0-4845-993c-2f4229869706
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fe8e54876f5b2ab3eda5c1bd8d35f0b0d0c788b2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68197214"
---
# <a name="vsix-color-editor"></a>VSIX 색 편집기
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio 확장명 색 편집기 도구를 만들고 Visual Studio에 대 한 사용자 지정 색을 편집할 수 있습니다. 도구는 코드에서 색을 사용할 수 있도록 테마 리소스 키를 생성할 수도 있습니다. 이 도구는 색 테마를 지 원하는 Visual Studio 확장을 만드는 데 유용 합니다. 이 도구는.pkgdef 및.xml 파일을 열 수 있습니다. Visual Studio 테마 (.vstheme 파일)를.xml으로 파일 확장명을 변경 하 여 Visual Studio 확장명 색 편집기 사용 하 여 사용할 수 있습니다. 또한 현재.xml 파일로.vstheme 파일을 가져올 수 있습니다.  
  
 ![VSIX 색 편집기 Hero](../../extensibility/internals/media/vsix-color-editor-hero.png "VSIX 색 편집기 Hero")  
  
 **패키지 정의 파일**  
  
 패키지 정의 (.pkgdef) 파일은 테마를 정의 하는 파일입니다. 색 자체가.pkgdef 파일로 컴파일되는 테마 색.xml 파일에 저장 됩니다. .Pkgdef 파일 Visual Studio 검색할 수 있는 위치에 배포, 런타임 시 처리 되 고 병합 테마를 정의할 수 있습니다.  
  
 **색 토큰**  
  
 색 토큰은 네 가지 요소로 구성 됩니다.  
  
- **범주 이름:** 색 집합에 대 한 논리적 그룹화입니다. 원하는 UI 요소 또는 UI 요소의 그룹에 관련 된 색 이미 있는 경우 기존 범주 이름을 사용 합니다.  
  
- **토큰 이름:** 토큰 및 토큰 색에 대해 설명 하는 이름이 설정합니다. 이러한 쌍은 및에 적용 되는 상태를 쉽게 식별할 수 있도록 이름은 및 배경 및 전경 (텍스트) 토큰 이름 뿐만 아니라 해당 모든 상태 집합이 포함 됩니다.  
  
- **색 값 (또는 색상):** 각 색이 지정 된 테마에 필요합니다. 항상 만들기 배경색과 텍스트 색 값 쌍에서입니다. 색은 텍스트 (전경) 색은 항상 그리기는 배경 색에 대해 읽을 수 있도록 배경/전경에 대 한 쌍을 이룹니다. 이러한 색에 연결 되 고 UI에서 함께 사용할 수 있습니다. 텍스트를 사용 하 여 사용 하기 위해 백그라운드 없는 경우에 전경색을 정의 하지 않습니다.  
  
- **시스템 색 이름:** 고대비 디스플레이에서 사용할 수 있습니다.  
  
## <a name="how-to-use-the-tool"></a>이 도구를 사용 하는 방법  
 가능한 만큼 적절 한 경우 새로 만드는 대신 기존 Visual Studio 색을 재사용할 수 해야 합니다. 그러나 없는 적절 한 색 정의 되어 있는 경우에 대 한 사용자 지정 색 만들어야 확장 테마는 호환 되도록 합니다.  
  
 **새 색 토큰 만들기**  
  
 Visual Studio 확장명 색 편집기를 사용 하 여 사용자 지정 색을 만들려면 다음이 단계를 수행 합니다.  
  
1. 새 색 토큰에 대 한 범주 및 토큰 이름을 결정 합니다.  
  
2. UI 요소에서 고대비 시스템 색과 각 테마에 사용할 색상을 선택 합니다.  
  
3. 새 색 토큰을 만들려면 색 편집기를 사용 합니다.  
  
4. Visual Studio 확장에서 색을 사용 합니다.  
  
5. Visual Studio에서 변경 내용을 테스트 합니다.  
  
   **1단계: 새 색 토큰에 대 한 범주 및 토큰 이름을 결정 합니다.**  
  
   VSColor에 대 한 스키마 기본 명명 **[Category] [UI 유형] [State]** 합니다. 중복 이므로 VSColor 이름에 "color" 라는 단어를 사용 하지 마세요.  
  
   범주 이름 논리적 그룹화를 제공 및 좁은 최대한으로 정의 해야 합니다. 예를 들어 단일 도구 창의 이름, 범주 이름을 변경할 수 있지만 전체 비즈니스 단위 또는 프로젝트 팀의 이름은 아닙니다. 항목 범주로 그룹화 색 동일한 이름의 혼동을 방지할 수 있습니다.  
  
   요소 형식이 된 경우 또는 "상태를" 색을 적용할 토큰 이름을 명확 하 게 나타내야 합니다. 예를 들어는 활성 데이터 팁의 **[UI 형식]** 이름을 지정할 수 있습니다 "**DataTip**" 하며 **[State]** 이름을 지정할 수 있습니다 "**Active**," 결과 색 이름이 "**DataTipActive**." 데이터 팁 텍스트 없으므로 전경색과 배경색을 모두 정의 해야 합니다. 배경/전경 쌍을 사용 하 여 색 편집기에서 자동으로 만듭니다 색 "**DataTipActive**" 배경에 대 한 및 "**DataTipActiveText**" 전경색입니다.  
  
   UI 부분 하나만 상태를 사용 하는 경우는 **[State]** 이름 부분을 생략할 수 있습니다. 예를 들어, 검색 상자에 테두리가 영향을 미치는 테두리의 색 상태 변경 사항이 없는 경우 다음 테두리의 색 토큰에 대 한 이름을 간단히 호출할 수 있습니다 "**SearchBoxBorder**."  
  
   몇 가지 일반적인 상태 이름은 다음과 같습니다.  
  
- 활성  
  
- 비활성  
  
- MouseOver  
  
- MouseDown  
  
- 선택  
  
- 포커스 있음  
  
  목록 항목 컨트롤의 부분에 대 한 몇 가지 토큰 이름 예:  
  
- ListItem  
  
- ListItemBorder  
  
- ListItemMouseOver  
  
- ListItemMouseOverBorder  
  
- ListItemSelected  
  
- ListItemSelectedBorder  
  
- ListItemDisabled  
  
- ListItemDisabledBorder  
  
  **2단계: UI 요소에서 고대비 시스템 색과 각 테마에 사용할 색상을 선택 합니다.**  
  
  UI에 대 한 사용자 지정 색을 선택할 때 유사한 기존 UI 요소를 선택 하 고 기준으로 해당 색을 사용 합니다. 상자에서 UI 요소에 대 한 색은 적절 한 보이고 모든 테마에서 올바르게 작동 하므로 검토 및 테스트를 거쳤지만 합니다.  
  
  **3단계: 새 색 토큰을 만들려면 색 편집기를 사용 합니다.**  
  
  색 편집기를 시작 하 고 열거나 새 사용자 지정 테마 색.xml 파일을 만듭니다. 선택 **편집 > 새 색** 합니다. 이 범주를 지정 하기 위한 대화 상자 및 해당 범주 내의 색 항목에 대 한 하나 이상의 이름 열립니다.  
  
  ![VSIX 색 편집기 새 색](../../extensibility/internals/media/vsix-color-editor-new-color.png "VSIX 색 편집기 새 색")  
  
  기존 범주를 선택 하거나 선택 **새 범주** 새 범주를 만들 수 있습니다. 새 범주 이름을 만드는 다른 대화가 열립니다.  
  
  ![VSIX 색 편집기 새 범주](../../extensibility/internals/media/vsix-color-editor-new-category.png "VSIX 색 편집기 새 범주")  
  
  새 범주에 사용한 다음 합니다 **새 색** 범주 드롭다운 메뉴입니다. 범주를 선택한 후 각 새 색 토큰에 대 한 줄당 하나의 이름을 입력 하 고 완료 되 면 "만들기"를 선택 합니다.  
  
  ![VSIX 색 편집기 새 색 등치](../../extensibility/internals/media/vsix-color-editor-new-color-filled.png "채워진 VSIX 색 편집기 새 색")  
  
  색 값은 "없음"으로 나타내는 색 정의 되지 않았습니다. 배경/전경 쌍으로 표시 됩니다. 참고: 색을 텍스트 색/배경 색 쌍이 없는 경우 다음 백그라운드만 정의 해야 합니다.  
  
  ![VSIX 색 편집기 색 값](../../extensibility/internals/media/vsix-color-editor-color-values.png "VSIX 색 편집기 색 값")  
  
  색 토큰을 편집 하려면 해당 토큰의 테마 (열)에 대 한 색 항목을 선택 합니다. ARGB 형식으로 8 자리 16 진수 색 값을 입력, 셀에 시스템 색 이름을 입력 하거나 색 슬라이더 또는 시스템 색 목록을 통해 원하는 색을 선택 하려면 드롭다운 메뉴를 사용 하 여 색 값을 추가 합니다.  
  
  ![VSIX 색 편집기 색 편집](../../extensibility/internals/media/vsix-color-editor-edit-color.png "VSIX 색 편집기 색 편집")  
  
  ![VSIX 색 편집기 배경](../../extensibility/internals/media/vsix-color-editor-background.png "VSIX 색 편집기 배경")  
  
  텍스트를 표시 하는 필요 하지 않은 구성 요소에 대 한 하나의 색 값을 입력 합니다: 배경색입니다. 그렇지 않은 경우 슬래시를 구분 배경색과 텍스트 색에 대 한 값을 입력 합니다.  
  
  고대비에 대 한 값을 입력 하는 경우에 유효한 Windows 시스템 색 이름을 입력 합니다. 하드 코드 된 ARGB 값을 입력 하지 마세요. 선택 하 여 올바른 시스템 색 이름 목록을 보면 "배경: 시스템"또는" 전경: 시스템 색 값 드롭다운 메뉴에서 "입니다. 텍스트 구성 요소가 있는 요소를 만들 때 올바른 배경/텍스트 시스템 색 쌍을 사용 하거나 텍스트를 읽을 수 없습니다.  
  
  만들기, 설정 및 색 토큰을 편집을 완료 하면 원하는.xml 또는.pkgdef 형식으로 저장 합니다. 모두 배경의 색 토큰 또는 포그라운드 집합은.xml 형식으로 빈 색으로 저장 되지만.pkgdef 형식을 삭제 합니다. 대화 상자를 빈 색.pkgdef 파일에 저장 하려고 하면 색 손실 하는 경우에 표시 됩니다.  
  
  **4단계: Visual Studio 확장에서 색을 사용 합니다.**  
  
  새 색을 정의한 후 토큰을 "빌드 동작" "콘텐츠"로 설정 된 프로젝트 파일에는.pkgdef를 포함 하 고 "VSIX에 포함" 설정 "True"를 선택 합니다.  
  
  ![VSIX 색 편집기 pkgdef](../../extensibility/internals/media/vsix-color-editor-pkgdef.png "VSIX 색 편집기 pkgdef")  
  
  Visual Studio 확장명 색 편집기에서 파일을 선택 합니다 > 사용자 지정 액세스에 사용 되는 코드를 보려면 리소스 코드 보기 WPF 기반 UI에서 색입니다.  
  
  ![VSIX 색 편집기 리소스 코드 뷰어](../../extensibility/internals/media/vsix-color-editor-resource-code-viewer.png "VSIX 색 편집기 리소스 코드 뷰어")  
  
  프로젝트에서 정적 클래스에이 코드를 포함 합니다. 에 대 한 참조가 **Microsoft.VisualStudio.Shell.\< VSVersion >.0.dll** 를 사용 하도록 프로젝트를 추가 해야 합니다 **ThemeResourceKey** 형식입니다.  
  
```csharp  
namespace MyCustomColors  
{  
    public static class MyCategory  
    {  
        #region Autogenerated resource keys  
        // These resource keys are generated by Visual Studio Extension Color Editor, and should be replaced when new colors are added to this category.  
        public static readonly Guid Category = new Guid("faf7f3f9-9fe5-4dd3-9350-59679617dfbe");  
  
        private static ThemeResourceKey _MyColor1ColorKey;  
        private static ThemeResourceKey _MyColor1BrushKey;  
        private static ThemeResourceKey _MyColor1TextColorKey;  
        private static ThemeResourceKey _MyColor1TextBrushKey;  
        public static ThemeResourceKey MyColor1ColorKey { get { return _MyColor1ColorKey ?? (_MyColor1ColorKey = new ThemeResourceKey(Category, "MyColor1", ThemeResourceKeyType.BackgroundColor)); } }  
        public static ThemeResourceKey MyColor1BrushKey { get { return _MyColor1BrushKey ?? (_MyColor1BrushKey = new ThemeResourceKey(Category, "MyColor1", ThemeResourceKeyType.BackgroundBrush)); } }  
        public static ThemeResourceKey MyColor1TextColorKey { get { return _MyColor1TextColorKey ?? (_MyColor1TextColorKey = new ThemeResourceKey(Category, "MyColor1", ThemeResourceKeyType.ForegroundColor)); } }  
        public static ThemeResourceKey MyColor1TextBrushKey { get { return _MyColor1TextBrushKey ?? (_MyColor1TextBrushKey = new ThemeResourceKey(Category, "MyColor1", ThemeResourceKeyType.ForegroundBrush)); } }  
        #endregion  
    }  
}  
```  
  
 이 XAML 코드의 색상에 대 한 액세스를 사용 하도록 설정 하 고 UI 테마 변경에 응답할 수 있습니다.  
  
```xaml  
<UserControl x:Class="NewTestProject.TestPackageControl" Name="MyToolWindow"  
             xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
             xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
             xmlns:ns="clr-namespace:MyCustomColors">  
  <Grid>  
    <TextBlock Background="{DynamicResource {x:Static ns:MyCategory.MyColor1BrushKey}}"  
               Foreground="{DynamicResource {x:Static ns:MyCategory.MyColor1TextBrushKey}}"  
      >Sample Text</TextBlock>  
  
  </Grid>  
</UserControl>  
```  
  
 **5단계: Visual Studio에서 변경 내용을 테스트 합니다.**  
  
 일시적으로 색 편집기 확장 패키지를 다시 작성 하지 않고 라이브 색 변경 내용을 보려면 Visual Studio의 실행 중인 인스턴스에 색 토큰을 적용할 수 있습니다. 이렇게 하려면 각 테마 열의 머리글에 있는 "Visual Studio windows를 실행이 테마 적용" 단추를 클릭 합니다. VSIX 색 편집기를 닫을 때이 임시 테마 위치로 이동 합니다.  
  
 ![VSIX 색 편집기 적용](../../extensibility/internals/media/vsix-color-editor-apply.png "VSIX 색 편집기 적용")  
  
 변경 내용을 영구적으로 유지 되도록를 다시 빌드하고.pkgdef 파일에 새 색을 추가 하 고 해당 색을 사용할지는 코드를 작성 한 후 Visual Studio 확장을 다시 배포 합니다. Visual Studio 확장을 다시 작성 테마의 나머지 부분에 새 색에 대 한 레지스트리 값을 병합 합니다. 그런 다음 Visual Studio를 다시 시작 하 고 UI를 보고 새 색 예상 대로 나타나는지 확인 합니다.  
  
## <a name="notes"></a>참고  
 이 도구는 Visual Studio 테마를 사용자 지정 색 편집 또는 기존 Visual Studio 테마에 대 한 사용자 지정 색 만들기에 사용 되는 것입니다. 사용자 지정 하는 전체 Visual Studio 테마를 만들려면 다음을 다운로드 합니다 [Visual Studio 색 테마 편집기 확장](http://visualstudiogallery.msdn.microsoft.com/6f4b51b6-5c6b-4a81-9cb5-f2daa560430b) Visual Studio 확장 갤러리에서.  
  
## <a name="sample-output"></a>샘플 출력  
 **XML 색 출력**  
  
 도구에서 생성 된.xml 파일은 다음과 유사 하 게 됩니다.  
  
```xml  
<Themes>  
  <Theme Name="Light" GUID="{de3dbbcd-f642-433c-8353-8f1df4370aba}">  
    <Category Name="CategoryName" GUID="{eee9d521-dac2-48d9-9a5e-5c625ba2040c}">  
      <Color Name="ColorName1">  
        <Background Type="CT_RAW" Source="FFFFFFFF" />  
      </Color>  
      <Color Name="ColorName2">  
        <Background Type="CT_RAW" Source="FFFFFFFF" />  
        <Foreground Type="CT_RAW" Source="FF000000" />  
      </Color>  
      <Color Name="ColorName3">  
        <Background Type="CT_RAW" Source="FFFF0000" />  
      </Color>  
      <Color Name="ColorName4">  
        <Background Type="CT_RAW" Source="FF000088" />  
        <Foreground Type="CT_RAW" Source="FFFFFFFF" />  
      </Color>  
    </Category>  
  </Theme>  
  <Theme Name="Dark" GUID="{1ded0138-47ce-435e-84ef-9ec1f439b749}">...</Theme>  
  <Theme Name="Blue" GUID="{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}">...</Theme>  
  <Theme Name="HighContrast" GUID="{a5c004b4-2d4b-494e-bf01-45fc492522c7}">...</Theme>  
</Themes>  
  
```  
  
 **PKGDEF 색 출력**  
  
 도구에서 생성 한.pkgdef 파일은 다음과 유사 하 게 됩니다.  
  
```  
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\CategoryName]  
"Data"=hex:78,00,00,00,0b,00,00,00,01,00,00,00,21,d5,e9,ee,c2,da,d9,48,9a,5e,5c,62,5b,a2,04,0c,04,00,00,00,0a,00,00,00,43,6f,6c,6f,72,4e,61,6d,65,31,01,ff,ff,ff,ff,00,0a,00,00,00,43,6f,6c,6f,72,4e,61,6d,65,32,01,ff,ff,ff,ff,01,00,00,00,ff,0a,00,00,00,43,6f,6c,6f,72,4e,61,6d,65,33,01,ff,00,00,ff,00,0a,00,00,00,43,6f,6c,6f,72,4e,61,6d,65,34,01,00,00,88,ff,01,ff,ff,ff,ff  
[$RootKey$\Themes\{1ded0138-47ce-435e-84ef-9ec1f439b749}\CategoryName]  
"Data"=hex:...  
[$RootKey$\Themes\{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}\CategoryName]  
"Data"=hex:...  
[$RootKey$\Themes\{a5c004b4-2d4b-494e-bf01-45fc492522c7}\CategoryName]  
"Data"=hex:...  
  
```  
  
 **C# 리소스 키 래퍼**  
  
 도구에서 생성 된 색 리소스 키 다음과 유사 하 게 됩니다.  
  
```csharp  
namespace MyNamespace  
{  
    public static class MyColors  
    {  
        #region Autogenerated resource keys  
        // These resource keys are generated by Visual Studio Extension Color Editor, and should be replaced when new colors are added to this category.  
  
        public static string ColorName1ColorKey { get { return "ColorName1ColorKey"; } }  
        public static string ColorName1BrushKey { get { return "ColorName1BrushKey"; } }  
  
        public static string ColorName2ColorKey { get { return "ColorName2ColorKey"; } }  
        public static string ColorName2BrushKey { get { return "ColorName2BrushKey"; } }  
        public static string ColorName2TextColorKey { get { return "ColorName2TextColorKey"; } }  
        public static string ColorName2TextBrushKey { get { return "ColorName2TextBrushKey"; } }  
  
        public static string ColorName3ColorKey { get { return "ColorName4ColorKey"; } }  
        public static string ColorName3BrushKey { get { return "ColorName4BrushKey"; } }  
        public static string ColorName3TextColorKey { get { return "ColorName4TextColorKey"; } }  
        public static string ColorName3TextBrushKey { get { return "ColorName4TextBrushKey"; } }  
        #endregion  
    }  
}  
```  
  
 **WPF 리소스 사전 래퍼**  
  
 색 **ResourceDictionary** 도구에서 생성 된 키 다음과 유사 하 게 됩니다.  
  
```xaml  
<ResourceDictionary xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
        xmlns:colors="clr-namespace:MyNamespace">  
  
  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName1BrushKey}" Color="#FFFFFFFF" />  
  <Color x:Key="{x:Static colors:MyColors.ColorName1ColorKey}" A="255" R="255" G="255" B="255" />  
  
  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName2BrushKey}" Color="#FFFFFFFF" />  
  <Color x:Key="{x:Static colors:MyColors.ColorName2ColorKey}" A="255" R="255" G="255" B="255" />  
  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName2TextBrushKey}" Color="#FF000000" />  
  <Color x:Key="{x:Static colors:MyColors.ColorName2TextColorKey}" A="255" R="0" G="0" B="0" />  
  
  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName3BrushKey}" Color="#FFFF0000" />  
  <Color x:Key="{x:Static colors:MyColors.ColorName3ColorKey}" A="255" R="255" G="0" B="0" />  
  
  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName4BrushKey}" Color="#FF000088" />  
  <Color x:Key="{x:Static colors:MyColors.ColorName4ColorKey}" A="255" R="0" G="0" B="136" />  
  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName4TextBrushKey}" Color="#FFFFFFFF" />  
  <Color x:Key="{x:Static colors:MyColors.ColorName4TextColorKey}" A="255" R="255" G="255" B="255" />  
</ResourceDictionary>  
```
