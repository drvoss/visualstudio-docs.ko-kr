---
title: '연습: 시작 페이지에 사용자 설정 저장 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 754b9bf3-8681-4c77-b0a4-09146a4e1d2d
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8976d329f6303d60cc00609bc9ed9471456c1b63
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63408750"
---
# <a name="walkthrough-saving-user-settings-on-a-start-page"></a>연습: 시작 페이지에 사용자 설정 저장
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

시작 페이지에 대 한 사용자 설정을 유지할 수 있습니다. 이 연습을 수행 하 여 사용자가 단추를 클릭 하 고 다음 시작 페이지가 로드 될 때마다이 설정으로 검색 하는 경우 레지스트리 설정을 저장 하는 컨트롤을 만들 수 있습니다. 시작 페이지 프로젝트 템플릿을 사용자 지정 가능한 사용자 컨트롤을 포함 하 고 해당 컨트롤을 호출 하는 기본 시작 페이지 XAML 때문에 자체 시작 페이지를 수정할 필요가 없습니다.  
  
 이 연습에서 인스턴스화되는 설정 저장소의 인스턴스가 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore> 인터페이스를 읽고 호출 되는 경우 다음 레지스트리 위치에 씁니다. HKCU\Software\Microsoft\VisualStudio\14.0\\*CollectionName*  
  
 Visual Studio의 실험적 인스턴스에서 실행 중인 경우 설정 저장소에 읽고 쓰는 HKCU\Software\Microsoft\VisualStudio\14.0Exp\\*CollectionName입니다.*  
  
 설정을 유지 하는 방법에 대 한 자세한 내용은 참조 하세요. [Extending User Settings and 옵션](../extensibility/extending-user-settings-and-options.md)합니다.  
  
## <a name="prerequisites"></a>전제 조건  
  
> [!NOTE]
> 이 연습을 수행하려면 Visual Studio SDK를 설치해야 합니다. 자세한 내용은 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)합니다.  
>   
> 시작 페이지 프로젝트 템플릿을 사용 하 여 다운로드할 수 있습니다 **확장 관리자**합니다.  
  
## <a name="setting-up-the-project"></a>프로젝트 설정  
  
#### <a name="to-configure-the-project-for-this-walkthrough"></a>이 연습에 대 한 프로젝트를 구성 하려면  
  
1. 에 설명 된 대로 시작 페이지 프로젝트 템플릿을 사용 하 여 시작 페이지 프로젝트를 만듭니다 [만들기 사용자 고유의 시작 페이지](../misc/creating-your-own-start-page.md)합니다. 프로젝트 이름을 **SaveMySettings**합니다.  
  
2. **솔루션 탐색기**, StartPageControl 프로젝트에 다음 어셈블리 참조를 추가 합니다.  
  
    - EnvDTE  
  
    - EnvDTE80  
  
    - Microsoft.VisualStudio.OLE.Interop  
  
    - Microsoft.VisualStudio.Shell.Interop.11.0  
  
3. MyControl.xaml을 엽니다.  
  
4. XAML 창에서 최상위에서 <xref:System.Windows.Controls.UserControl> 요소 정의입니다. 네임 스페이스 선언 후 다음 이벤트 선언을 추가 합니다.  
  
    ```  
    Loaded="OnLoaded"  
    ```  
  
5. 디자인 창에서 컨트롤의 주요 영역을 클릭 하 고 DELETE 키를 누릅니다.  
  
     이 제거 합니다 <xref:System.Windows.Controls.Border> 요소와 모든 및 최상위 리프 <xref:System.Windows.Controls.Grid> 요소.  
  
6. **도구 상자**, 끌어는 <xref:System.Windows.Controls.StackPanel> 그리드 컨트롤입니다.  
  
7. 끕니다를 <xref:System.Windows.Controls.TextBlock>, <xref:System.Windows.Controls.TextBox>, 및 단추는 <xref:System.Windows.Controls.StackPanel>합니다.  
  
8. 추가 **X:name** 특성에 대 한는 <xref:System.Windows.Controls.TextBox>, 및 `Click` 에 대 한 이벤트는 <xref:System.Windows.Controls.Button>다음 예제에서와 같이 합니다.  
  
    ```xml  
    <StackPanel Width="300" HorizontalAlignment="Center" VerticalAlignment="Center">  
        <TextBlock Width="140" FontSize="14">Enter your setting</TextBlock>  
        <TextBox x:Name="txtblk" Margin="0, 5, 0, 10" Width="140" />  
        <Button Click="Button_Click" Width="100">Save My Setting</Button>  
    </StackPanel>  
    ```  
  
## <a name="implementing-the-user-control"></a>사용자 정의 컨트롤 구현  
  
#### <a name="to-implement-the-user-control"></a>사용자 컨트롤을 구현 하려면  
  
1. XAML 창에서 마우스 오른쪽 단추로 클릭 합니다 `Click` 특성을 <xref:System.Windows.Controls.Button> 요소와 클릭 한 다음 **이벤트 처리기로 이동**.  
  
     MyControl.xaml.cs, 열리고에 대 한 스텁 처리기를 만들고이 `Button_Click` 이벤트입니다.  
  
2. 다음 추가 `using` 문을 파일의 맨 위로 이동 합니다.  
  
     [!code-csharp[StartPageDTE#11](../snippets/csharp/VS_Snippets_VSSDK/startpagedte/cs/startpagecontrol/mycontrol.xaml.cs#11)]  
  
3. 개인 추가 `SettingsStore` 속성을 다음 예와에서 같이 합니다.  
  
    ```csharp  
    private IVsWritableSettingsStore _settingsStore = null;  
    private IVsWritableSettingsStore SettingsStore  
    {  
        get  
        {  
            if (_settingsStore == null)  
            {  
                // Get a reference to the DTE from the DataContext.   
                var typeDescriptor = DataContext as ICustomTypeDescriptor;  
                var propertyCollection = typeDescriptor.GetProperties();  
                var dte = propertyCollection.Find("DTE", false).GetValue(  
                    DataContext) as DTE2;  
  
                // Get the settings manager from the DTE.   
                var serviceProvider = new ServiceProvider(  
                    (Microsoft.VisualStudio.OLE.Interop.IServiceProvider)dte);  
                var settingsManager = serviceProvider.GetService(  
                    typeof(SVsSettingsManager)) as IVsSettingsManager;  
  
                // Write the user settings to _settingsStore.  
                settingsManager.GetWritableSettingsStore(  
                    (uint)__VsSettingsScope.SettingsScope_UserSettings,  
                    out _settingsStore);  
            }  
            return _settingsStore;  
        }  
    }  
    ```  
  
     이 속성에 대 한 참조를 먼저 가져옵니다는 <xref:EnvDTE80.DTE2> 에서 자동화 개체 모델을 포함 하는 인터페이스를 <xref:System.Windows.FrameworkElement.DataContext%2A> 는 사용자 정의 컨트롤을 사용 하 여 다음의 인스턴스를 가져오려면 DTE의는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> 인터페이스. 그런 다음 현재 사용자 설정을 반환 하려면 해당 인스턴스를 사용 합니다.  
  
4. 입력 된 `Button_Click` 다음과 같은 이벤트입니다.  
  
    ```csharp  
    private void Button_Click(object sender, RoutedEventArgs e)  
    {  
        int exists = 0;  
        SettingsStore.CollectionExists("MySettings", out exists);  
        if (exists != 1)  
        {  
            SettingsStore.CreateCollection("MySettings");  
        }  
        SettingsStore.SetString("MySettings", "MySetting", txtblk.Text);  
    }  
    ```  
  
     레지스트리에 "MySettings" 컬렉션의 "MySetting" 필드에 텍스트 상자의 콘텐츠를 기록 합니다. 컬렉션에 없으면 자동으로 만들어집니다.  
  
5. 에 대 한 다음 처리기를 추가 합니다 `OnLoaded` 사용자 컨트롤의 이벤트입니다.  
  
    ```csharp  
    private void OnLoaded(Object sender, RoutedEventArgs e)  
    {  
        string value;  
        SettingsStore.GetStringOrDefault(  
            "MySettings", "MySetting", "", out value);  
        txtblk.Text = value;  
    }  
    ```  
  
     입력란의 텍스트 "MySetting"의 현재 값으로 설정합니다.  
  
6. 사용자 정의 컨트롤을 빌드하십시오.  
  
7. **솔루션 탐색기**, source.extension.vsixmanifest를 엽니다.  
  
8. 매니페스트 편집기에서 설정 **Product Name** 하 **내 설정 시작 페이지 저장**합니다.  
  
     에 표시 하는 것 만큼 시작 페이지의 이름을 설정 합니다 **시작 페이지 사용자 지정** 목록에 **옵션** 대화 상자.  
  
9. StartPage.xaml을 빌드하십시오.  
  
## <a name="testing-the-control"></a>컨트롤 테스트  
  
#### <a name="to-test-the-user-control"></a>사용자 컨트롤을 테스트 하려면  
  
1. F5 키를 누릅니다.  
  
     Visual Studio의 실험적 인스턴스가 열립니다.  
  
2. 실험적 인스턴스에서는 **도구** 메뉴에서 클릭 **옵션**합니다.  
  
3. 에 **환경** 노드를 클릭 **시작**를 선택한 후는 **시작 페이지 사용자 지정** 목록에서 **[설치 된 확장] 저장 내 설정 시작 페이지** .  
  
     **확인**을 클릭합니다.  
  
4. 에 열려 있는 경우 한 후 시작 페이지를 닫습니다 합니다 **뷰** 메뉴에서 클릭 **시작 페이지**합니다.  
  
5. 시작 페이지를 클릭 합니다 **MyControl** 탭 합니다.  
  
6. 텍스트 상자에 입력 **Cat**를 클릭 하 고 **내 설정 저장**합니다.  
  
7. 시작 페이지를 닫고 다시 여십시오.  
  
     텍스트 상자에 "Cat" 단어를 표시 합니다.  
  
8. Word "Dog"를 사용 하 여 "Cat" 단어를 대체 합니다. 단추를 클릭 하지 마세요.  
  
9. 시작 페이지를 닫고 다시 여십시오.  
  
     설정이 저장 되지 않았습니다 하는 경우에 word "Dog" 텍스트 상자에 표시 합니다. Visual Studio 자체를 닫을 때까지 닫혀 있는 경우에 Visual Studio 도구 창 메모리에 유지 하기 때문에 발생 합니다.  
  
10. Visual Studio의 실험적 인스턴스를 닫습니다.  
  
11. F5 키를 눌러 실험적 인스턴스를 다시 엽니다.  
  
12. 텍스트 상자에 "Cat" 단어를 표시 합니다.  
  
## <a name="next-steps"></a>다음 단계  
 저장 하 고 가져오기 및 설정에 다른 이벤트 처리기에서 다른 값을 사용 하 여 개수에 관계 없이 사용자 지정 설정 검색할이 사용자 정의 컨트롤을 수정할 수는 `SettingsStore` 속성입니다. 사용 하는 다른 `propertyName` 각 호출에 매개 변수 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore.SetString%2A>, 레지스트리에서 서로 값은 덮어쓰지 않습니다.  
  
## <a name="see-also"></a>참고 항목  
 <xref:EnvDTE80.DTE2?displayProperty=fullName>   
 [사용자 고유의 시작 페이지 만들기](../misc/creating-your-own-start-page.md)   
 [시작 페이지에 Visual Studio 명령 추가](../extensibility/adding-visual-studio-commands-to-a-start-page.md)
