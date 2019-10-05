---
title: 시작 페이지를 Visual Studio 명령 추가 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- start page commands
- vs:VSCommands
ms.assetid: a8e2765c-cfb5-47b5-a414-6e48b434e0c2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 86fe084d2dab10ed7370f5fc5b99931491b096be
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352292"
---
# <a name="add-visual-studio-commands-to-a-start-page"></a>시작 페이지에 Visual Studio 명령 추가

사용자 지정 시작 페이지를 만들면 Visual Studio 명령에 추가할 수 있습니다. 이 문서에는 Visual Studio 명령 시작 페이지 XAML 개체를 바인딩할 다양 한 방법을 설명 합니다.

XAML에서 명령에 대 한 자세한 내용은 참조 하세요. [직속 상관 개요](/dotnet/framework/wpf/advanced/commanding-overview)

## <a name="add-commands-from-the-command-well"></a>도 명령에서 명령을 추가합니다

시작 페이지에서 만든 [사용자 지정 시작 페이지를 만들](../extensibility/creating-a-custom-start-page.md) 추가 된 <xref:Microsoft.VisualStudio.PlatformUI?displayProperty=fullName> 및 <xref:Microsoft.VisualStudio.Shell?displayProperty=fullName> 같이 네임 스페이스입니다.

```xml
xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"
xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
```

어셈블리에서 Microsoft.VisualStudio.Shell의 다른 네임 스페이스를 추가 *Microsoft.VisualStudio.Shell.Immutable.11.0.dll*합니다. (해야 프로젝트에서이 어셈블리에 대 한 참조를 추가 합니다.)

```xml
xmlns:vscom="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.11.0"
```

사용할 수는 `vscom:` Visual Studio 명령 XAML 바인딩할 별칭을 설정 하 여 페이지에 있는 컨트롤을 <xref:System.Windows.Controls.Primitives.ButtonBase.Command%2A> 컨트롤의 속성 `vscom:VSCommands.ExecuteCommand`합니다. 설정할 수 있습니다는 <xref:System.Windows.Controls.Primitives.ButtonBase.CommandParameter%2A> 속성을 다음 예제에서와 같이 실행할 명령의 이름입니다.

```xml
<Button Name="btnNewProj" Content="New Project"
    Command="{x:Static vscom:VSCommands.ExecuteCommand}"
    CommandParameter="File.NewProject" >
</Button>
```

> [!NOTE]
> `x:` 별칭 XAML 스키마를 참조 하는 모든 명령의 시작 부분에 필요 합니다.

 값을 설정할 수는 `Command` 속성에서 액세스할 수 있는 모든 명령에는 **명령** 창입니다. 사용 가능한 명령 목록을 참조 하세요 [Visual Studio 명령 별칭](../ide/reference/visual-studio-command-aliases.md)합니다.

 추가 하는 명령을 추가 매개 변수를 필요한 경우 값을 추가할 수 있습니다는 `CommandParameter` 속성입니다. 다음 예제에 표시 된 대로 공간을 사용 하 여 명령에서 별도 매개 변수입니다.

```xml
<Button Content="Web Search"
        Command="{x:Static vscom:VSCommands.ExecuteCommand}"
        CommandParameter="View.WebBrowser www.bing.com" />
```

### <a name="call-extensions-from-the-command-well"></a>명령에서 확장을 제대로 호출
 다른 Visual Studio 명령을 호출 하는 데 사용 되는 동일한 구문을 사용 하 여 등록 된 Vspackage에서 명령을 호출할 수 있습니다. 예를 들어, 설치 된 VSPackage를 추가 하는 경우는 **홈 페이지** 명령을 합니다 **보기** 메뉴 명령을 설정 하 여 호출할 수 있습니다 `CommandParameter` 에 `View.HomePage`합니다.

> [!NOTE]
> VSPackage와 사용 하 여 연결된 명령을 호출 하는 경우에 명령이 호출 될 때 패키지 로드 되어야 합니다.

## <a name="add-commands-from-assemblies"></a>어셈블리의 명령 추가
 메뉴 명령과 사용 하 여 연결 되지 않은 VSPackage에서 액세스 코드 또는 어셈블리에서 명령을 호출 하는 어셈블리에 대 한 별칭을 만듭니다 하며 그런 다음 별칭을 호출 합니다.

### <a name="to-call-a-command-from-an-assembly"></a>어셈블리에서 명령을 호출 하려면

1. 솔루션의 어셈블리에 대 한 참조를 추가 합니다.

2. 맨 위에 있는 합니다 *StartPage.xaml* 파일을 어셈블리에 대 한 네임 스페이스 지시문을 추가 합니다. 다음 예제에서와 같이 합니다.

    ```xml
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"
    ```

3. 설정 하 여 명령을 호출 합니다 `Command` 다음 예와에서 같이 XAML 개체의 속성입니다.

     Xaml

    ```
    <vs:Button Text="Hide me" Command="{x:Static vsc:HideControl}" .../>
    ```

> [!NOTE]
> 어셈블리를 복사 하며, 다음에 붙여넣어 *... \\{Visual Studio 설치 폴더} \Common7\IDE\PrivateAssemblies\* 호출 되기 전에 로드 되었는지 확인 합니다.

## <a name="add-commands-with-the-dte-object"></a>DTE 개체를 사용 하 여 명령을 추가 합니다.
 시작 페이지에서 태그와 코드에서 DTE 개체를 액세스할 수 있습니다.

 태그에서 액세스할 수 있습니다 사용 하 여 합니다 [Binding 태그 확장](/dotnet/framework/wpf/advanced/binding-markup-extension) 구문을 호출 하는 <xref:EnvDTE.DTE> 개체입니다. 이 이렇게를 사용 하 여 컬렉션을 반환 하는 것과 같은 간단한 속성에 바인딩할 수 있지만 메서드 또는 서비스에 바인딩할 수 없습니다. 다음 예제와 <xref:System.Windows.Controls.TextBlock> 바인딩되는 컨트롤을 <xref:EnvDTE._DTE.Name%2A> 속성 및 <xref:System.Windows.Controls.ListBox> 열거는 제어를 <xref:EnvDTE.Window.Caption%2A> 속성에서 반환 되는 컬렉션의를 <xref:EnvDTE._DTE.Windows%2A> 속성.

```xml
<TextBlock Text="{Binding Path=DTE.Name}" FontSize="12" HorizontalAlignment="Center"/>
<ListBox ItemsSource="{Binding Path=DTE.Windows}">
    <ListBox.ItemTemplate>
        <DataTemplate>
            <TextBlock Text="{Binding Path=Caption}"/>
        </DataTemplate>
    </ListBox.ItemTemplate>
</ListBox
```

 예제를 보려면 [연습: 시작 페이지에서 사용자 설정 저장](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md)합니다.

## <a name="see-also"></a>참고자료

- [시작 페이지에 사용자 컨트롤 추가](../extensibility/adding-user-control-to-the-start-page.md)