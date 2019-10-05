---
title: 옵션 페이지 만들기 | Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], creating
ms.assetid: 9f4e210c-4b47-4daa-91fa-1c301c4587f9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b0b8108470d5f9f14c76e422591a536648b5485e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350982"
---
# <a name="create-an-options-page"></a>옵션 페이지 만들기

이 연습을 검토 하 고 속성을 설정 하려면 속성 표를 사용 하는 간단한 도구/옵션 페이지를 만듭니다.

 이러한 속성을 저장 및 설정 파일에서 복원할 다음이 단계를 수행 하 고 확인할 [설정 범주 만들기](../extensibility/creating-a-settings-category.md)합니다.

 MPF 도구 옵션 페이지를 만들 수 있도록 두 개의 클래스를 제공 합니다 <xref:Microsoft.VisualStudio.Shell.Package> 클래스 및 <xref:Microsoft.VisualStudio.Shell.DialogPage> 클래스입니다. 서브클래싱하 여 이러한 페이지에 대 한 컨테이너를 제공 하는 VSPackage를 만든를 `Package` 클래스입니다. 각 도구 옵션 페이지에서 파생 시켜 만들 수는 `DialogPage` 클래스입니다.

## <a name="prerequisites"></a>전제 조건

 Visual Studio 2015부터 수행 설치 하면 Visual Studio SDK 다운로드 센터에서. Visual Studio 설치에서 선택적 기능으로 포함 됩니다. 또한 VS SDK를 나중에 설치할 수 있습니다. 자세한 내용은 [Visual Studio SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)합니다.

## <a name="create-a-tools-options-grid-page"></a>도구 옵션 그리드 페이지 만들기

 이 섹션에서는 간단한 도구 옵션 속성 표를 만들 수 있습니다. 이 표를 사용 하 여 표시 하 고 속성의 값을 변경 합니다.

### <a name="to-create-the-vsix-project-and-add-a-vspackage"></a>VSIX 프로젝트를 만들고 VSPackage를 추가 하려면

1. 모든 Visual Studio 확장 확장 자산을 포함 하는 VSIX 배포 프로젝트를 시작 합니다. 만들기는 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 라는 VSIX 프로젝트 `MyToolsOptionsExtension`합니다. VSIX 프로젝트 템플릿을 찾을 수 있습니다 합니다 **새 프로젝트** "vsix"를 검색 하 여 대화 상자.

2. 라는 이름의 Visual Studio 패키지 항목 템플릿을 추가 하 여 VSPackage를 추가할 `MyToolsOptionsPackage`합니다. 에 **솔루션 탐색기**, 프로젝트 노드를 마우스 오른쪽 단추로 **추가** > **새 항목**합니다. 에 **새 항목 추가 대화 상자**로 이동 하세요 **Visual C# 항목** > **확장성** 선택한 **Visual Studio 패키지**합니다. 에 **이름을** 대화 상자의 맨 아래에 있는 필드에 파일 이름을 `MyToolsOptionsPackage.cs`입니다. VSPackage를 만드는 방법에 대 한 자세한 내용은 참조 하세요. [VSPackage를 사용 하 여 확장 만들기](../extensibility/creating-an-extension-with-a-vspackage.md)합니다.

### <a name="to-create-the-tools-options-property-grid"></a>도구 옵션 속성 표를 만들려면

1. 엽니다는 *MyToolsOptionsPackage* 코드 편집기에서 파일입니다.

2. 다음 추가 문을 사용 하 여 합니다.

   ```csharp
   using System.ComponentModel;
   ```

3. 선언 된 `OptionPageGrid` 클래스에서 파생 되 고 <xref:Microsoft.VisualStudio.Shell.DialogPage>입니다.

   ```csharp
   public class OptionPageGrid : DialogPage
   {  }
   ```

4. 적용을 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> 에 `VSPackage` 를 옵션 범주 옵션 페이지에 대 한 이름과 OptionPageGrid 클래스에 할당 하는 클래스입니다. 결과 다음과 같습니다.

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]
    [ProvideMenuResource("Menus.ctmenu", 1)]
    [Guid(GuidList.guidMyToolsOptionsPkgString)]
    [ProvideOptionPage(typeof(OptionPageGrid),
        "My Category", "My Grid Page", 0, 0, true)]
    public sealed class MyToolsOptionsPackage : Package
    ```

5. 추가 된 `OptionInteger` 속성을는 `OptionPageGrid` 클래스입니다.

    - 적용을 <xref:System.ComponentModel.CategoryAttribute?displayProperty=fullName> 속성 표 범주 속성에 할당 합니다.

    - 적용을 <xref:System.ComponentModel.DisplayNameAttribute?displayProperty=fullName> 이름을 속성에 할당할 수 있습니다.

    - 적용 된 <xref:System.ComponentModel.DescriptionAttribute?displayProperty=fullName> 에 할당할 속성을 설명 합니다.

    ```csharp
    public class OptionPageGrid : DialogPage
    {
        private int optionInt = 256;

        [Category("My Category")]
        [DisplayName("My Integer Option")]
        [Description("My integer option")]
        public int OptionInteger
        {
            get { return optionInt; }
            set { optionInt = value; }
        }
    }
    ```

    > [!NOTE]
    > 기본 구현을 <xref:Microsoft.VisualStudio.Shell.DialogPage> 있는 적절 한 변환기 또는 구조체 또는 배열 속성을 적절 한 변환기를 확장할 수 있는 속성을 지원 합니다. 변환기의 목록에 대 한 참조를 <xref:System.ComponentModel> 네임 스페이스입니다.

6. 프로젝트를 빌드하고 디버깅을 시작합니다.

7. Visual Studio의 실험적 인스턴스에서는 **도구** 메뉴 **옵션**합니다.

     왼쪽된 창에 나타납니다 **My Category**합니다. (옵션 범주는 사전순으로 나열을 목록 아래쪽 중간에 대 한 표시 되어야 하므로.) 오픈 **My Category** 을 클릭 한 다음 **그리드 페이지 내**합니다. 옵션 표의 오른쪽 창에 나타납니다. 속성 범주가 **My Options**, 속성 이름은 **내 정수 옵션**합니다. 속성 설명 **내 정수 옵션**, 창의 아래쪽에 나타납니다. 256의 초기 값에서 다른 값을 변경 합니다. 클릭 **확인**를 닫은 다음 **그리드 페이지 내**합니다. 지속 되 면 새 값을 볼 수 있습니다.

     옵션 페이지에도 Visual Studio의 검색 상자를 통해 제공 됩니다. IDE 위쪽 검색 상자에 입력 **My Category** 를 확인할 수 있습니다 **-> 내 그리드 페이지 내 범주** 결과에 나열 합니다.

## <a name="create-a-tools-options-custom-page"></a>사용자 지정 도구 옵션 페이지 만들기

 이 섹션에서는 도구 옵션 페이지를 사용자 지정 UI를 사용 하 여 만듭니다. 이 페이지를 사용 하 여 표시 하 고 속성의 값을 변경 합니다.

1. 엽니다는 *MyToolsOptionsPackage* 코드 편집기에서 파일입니다.

2. 다음 추가 문을 사용 하 여 합니다.

    ```csharp
    using System.Windows.Forms;
    ```

3. 추가 `OptionPageCustom` 직전 클래스는 `OptionPageGrid` 클래스입니다. 새 클래스를 파생 `DialogPage`합니다.

    ```csharp
    public class OptionPageCustom : DialogPage
    {
        private string optionValue = "alpha";

        public string OptionString
        {
            get { return optionValue; }
            set { optionValue = value; }
        }
    }
    ```

4. GUID 특성을 추가 합니다. OptionString 속성을 추가 합니다.

    ```csharp
    [Guid("00000000-0000-0000-0000-000000000000")]
    public class OptionPageCustom : DialogPage
    {
        private string optionValue = "alpha";

        public string OptionString
        {
            get { return optionValue; }
            set { optionValue = value; }
        }
    }
    ```

5. 두 번째 적용 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> VSPackage 클래스입니다. 이 특성을 옵션 범주 이름과 옵션 페이지 클래스를 할당합니다.

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]
    [ProvideMenuResource("Menus.ctmenu", 1)]
    [Guid(GuidList.guidMyToolsOptionsPkgString)]
    [ProvideOptionPage(typeof(OptionPageGrid),
        "My Category", "My Grid Page", 0, 0, true)]
    [ProvideOptionPage(typeof(OptionPageCustom),
        "My Category", "My Custom Page", 0, 0, true)]
    public sealed class MyToolsOptionsPackage : Package
    ```

6. 새 **사용자 정의 컨트롤** MyUserControl 프로젝트에 이름이 있습니다.

7. 추가 된 **텍스트 상자에 붙여넣습니다** 컨트롤을 사용자 컨트롤입니다.

     에 **속성** 창의 도구 모음에서 클릭를 **이벤트** 단추를 두 번 클릭 하는 **둡니다** 이벤트입니다. 새 이벤트 처리기에 표시 된 *MyUserControl.cs* 코드입니다.

8. 추가 공용 `OptionsPage` 필드는 `Initialize` 컨트롤 클래스 및 옵션을 설정 하는 이벤트 처리기 값 입력란의 내용을 업데이트 방법:

    ```csharp
    public partial class MyUserControl : UserControl
    {
        public MyUserControl()
        {
            InitializeComponent();
        }

        internal OptionPageCustom optionsPage;

        public void Initialize()
        {
            textBox1.Text = optionsPage.OptionString;
        }

        private void textBox1_Leave(object sender, EventArgs e)
        {
            optionsPage.OptionString = textBox1.Text;
        }
    }
    ```

     합니다 `optionsPage` 부모에 대 한 참조를 보유 하는 필드 `OptionPageCustom` 인스턴스. 합니다 `Initialize` 메서드 표시 `OptionString` 에 **텍스트 상자**합니다. 이벤트 처리기의 현재 값을 씁니다를 **텍스트 상자에 붙여넣습니다** 에 `OptionString` 경우 리프를 집중 합니다 **텍스트 상자에 붙여넣습니다**.

9. 패키지 코드 파일에 대 한 재정의 추가 합니다 `OptionPageCustom.Window` 속성을 합니다 `OptionPageCustom` 만들기, 초기화 및 인스턴스를 반환 하는 클래스 `MyUserControl`합니다. 클래스는 이제 다음과 같이 표시 됩니다.

    ```csharp
    [Guid("00000000-0000-0000-0000-000000000000")]
    public class OptionPageCustom : DialogPage
    {
        private string optionValue = "alpha";

        public string OptionString
        {
            get { return optionValue; }
            set { optionValue = value; }
        }

        protected override IWin32Window Window
        {
            get
            {
                MyUserControl page = new MyUserControl();
                page.optionsPage = this;
                page.Initialize();
                return page;
            }
        }
    }
    ```

10. 프로젝트를 빌드하고 실행합니다.

11. 실험적 인스턴스를 클릭 **도구가** > **옵션**합니다.

12. 찾을 **내 범주** 차례로 **내 사용자 지정 페이지**합니다.

13. 값을 변경 **OptionString**합니다. 클릭 **확인**를 닫은 다음 **내 사용자 지정 페이지**합니다. 새 값을 지속에 볼 수 있습니다.

## <a name="access-options"></a>액세스 옵션

 이 섹션에서는 연결 된 도구 옵션 페이지를 호스트 하는 VSPackage에서 옵션의 값을 가져옵니다. Public 속성의 값을 가져오려면 동일한 기술을 사용할 수 있습니다.

1. 패키지 코드 파일에서 이라는 공용 속성을 추가 **OptionInteger** 에 **MyToolsOptionsPackage** 클래스입니다.

    ```csharp
    public int OptionInteger
    {
        get
        {
            OptionPageGrid page = (OptionPageGrid)GetDialogPage(typeof(OptionPageGrid));
            return page.OptionInteger;
        }
    }

    ```

     이 코드는 호출 <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> 만들거나 검색 하는 `OptionPageGrid` 인스턴스. `OptionPageGrid` 호출 <xref:Microsoft.VisualStudio.Shell.DialogPage.LoadSettingsFromStorage%2A> 해당 옵션은 공용 속성을 로드 합니다.

2. 이제 라는 사용자 지정 명령 항목 서식 파일을 추가할 **MyToolsOptionsCommand** 값을 표시 합니다. 에 **새 항목 추가** 대화 상자에서로 이동 **Visual C#**  > **확장성** 선택한 **사용자 지정 명령**입니다. 에 **이름을** 창의 맨 아래에 있는 필드에 명령 파일 이름을 *MyToolsOptionsCommand.cs*합니다.

3. 에 *MyToolsOptionsCommand* 파일에서 명령의의 본문으로 바꿉니다. `ShowMessageBox` 메서드를 다음:

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        MyToolsOptionsPackage myToolsOptionsPackage = this.package as MyToolsOptionsPackage;
        System.Windows.Forms.MessageBox.Show(string.Format(CultureInfo.CurrentCulture, "OptionInteger: {0}", myToolsOptionsPackage.OptionInteger));
    }

    ```

4. 프로젝트를 빌드하고 디버깅을 시작합니다.

5. 실험적 인스턴스에서는 **도구** 메뉴에서 클릭 **MyToolsOptionsCommand 호출**합니다.

     현재 값을 표시 하는 메시지 상자 `OptionInteger`합니다.

## <a name="see-also"></a>참고자료

- [옵션 및 옵션 페이지](../extensibility/internals/options-and-options-pages.md)
