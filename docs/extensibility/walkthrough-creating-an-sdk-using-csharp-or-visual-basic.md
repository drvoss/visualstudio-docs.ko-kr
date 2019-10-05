---
title: '연습: 사용 하 여 SDK 만들기 C# 또는 Visual Basic | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ef96a249-5eef-402a-a8d5-d74cb49239bd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CSharp
- VB
ms.openlocfilehash: 6bb9ae53dfb2e849c35c05fe5187cddcf301622c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66312637"
---
# <a name="walkthrough-create-an-sdk-using-c-or-visual-basic"></a>연습: 사용 하 여 SDK 만들기 C# 또는 Visual Basic
이 연습에서는 Visual C#을 사용 하 여 간단한 수학 라이브러리 SDK를 만들고 다음 SDK는 Visual Studio 확장 (VSIX)로 패키지 하는 방법에 알아봅니다. 다음 절차를 완료 합니다.

- [SimpleMath Windows 런타임 구성 요소를 만들려면](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createClassLibrary)

- [SimpleMathVSIX 확장 프로젝트를 만들려면](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createVSIX)
- [클래스 라이브러리를 사용 하는 샘플 앱을 만들려면](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createSample)

## <a name="prerequisites"></a>전제 조건
 이 연습을 수행하려면 Visual Studio SDK를 설치해야 합니다. 자세한 내용은 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)합니다.

## <a name="createClassLibrary"></a> SimpleMath Windows 런타임 구성 요소를 만들려면

1. 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 선택합니다.

2. 템플릿 목록에서 확장 **Visual C#** 또는 **Visual Basic**를 선택 합니다 **Windows 스토어** 노드를 선택한 후는 **Windows 런타임 구성 요소** 템플릿.

3. 에 **이름** 상자에서 지정 **SimpleMath**를 선택한 후는 **확인** 단추입니다.

4. **솔루션 탐색기**에 대 한 바로 가기 메뉴를 열고 합니다 **SimpleMath** 프로젝트 노드를 선택한 후 **속성**합니다.

5. 이름 바꾸기 **Class1.cs** 하 **Arithmetic.cs** 다음 코드와 일치 하도록 업데이트 합니다.

    [!code-csharp[CreatingAnSDKUsingWinRT#3](../extensibility/codesnippet/CSharp/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_1.cs)]
    [!code-vb[CreatingAnSDKUsingWinRT#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_1.vb)]

6. **솔루션 탐색기**에 대 한 바로 가기 메뉴를 열고 합니다 **솔루션 'SimpleMath'** 노드를 선택한 후 **Configuration Manager**합니다.

    합니다 **Configuration Manager** 대화 상자가 열립니다.

7. 에 **활성 솔루션 구성** 목록에서 선택 **릴리스**합니다.

8. 에 **구성** 열 되어 있는지 확인 **SimpleMath** 행으로 설정 됩니다 **릴리스**를 선택한 후는 **닫기** 단추를는 변경 내용입니다.

   > [!IMPORTANT]
   > SimpleMath 구성 요소에 대 한 SDK에는 하나의 구성만 포함 됩니다. 이 구성은 릴리스 빌드의 경우 해야 합니다. 또는 구성 요소를 사용 하는 앱에 대 한 인증을 전달 하지는 [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)]합니다.

9. **솔루션 탐색기**에 대 한 바로 가기 메뉴를 열고 합니다 **SimpleMath** 프로젝트 노드를 선택한 후 **빌드**합니다.

## <a name="createVSIX"></a> SimpleMathVSIX 확장 프로젝트를 만들려면

1. 에 대 한 바로 가기 메뉴를 **솔루션 'SimpleMath'** 노드를 선택 **추가** > **새 프로젝트**합니다.

2. 템플릿 목록에서 확장 **Visual C#** 또는 **Visual Basic**를 선택 합니다 **확장성** 노드를 선택한 후 합니다 **VSIX 프로젝트** 템플릿입니다.

3. 에 **이름** 상자에서 지정 **SimpleMathVSIX**를 선택한 후는 **확인** 단추입니다.

4. **솔루션 탐색기**를 선택 합니다 **source.extension.vsixmanifest** 항목입니다.

5. 메뉴 모음에서 **보기** > **코드**를 차례로 선택합니다.

6. 다음 XML의 기존 XML로 바꿉니다.

     [!code-xml[CreatingAnSDKUsingWinRT#1](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_2.xml)]

7. **솔루션 탐색기**를 선택 합니다 **SimpleMathVSIX** 프로젝트입니다.

8. 메뉴 모음에서 **프로젝트** > **새 항목 추가**를 선택합니다.

9. 목록의 **공통 항목**를 확장 하 고 **데이터**를 선택한 후 **XML 파일**.

10. 에 **이름** 상자에서 지정 `SDKManifest.xml`를 선택한 후는 **추가** 단추입니다.

11. **솔루션 탐색기**에 대 한 바로 가기 메뉴를 열고 `SDKManifest.xml`, 선택 **속성**의 값을 변경한 후 합니다 **VSIX에 포함** 속성**True**합니다.

12. 파일의 내용을 다음 XML로 바꿉니다.

    **C#**

    ```xml
    <FileList
      DisplayName="WinRT Math Library (CS)"
      MinVSVersion="11.0"
      TargetFramework=".NETCore,version=v4.5"
      AppliesTo="WindowsAppContainer"
      SupportsMultipleVersions="Error"
      MoreInfo="https://msdn.microsoft.com/">
    </FileList>
    ```

    **Visual Basic**

    ```xml
    <FileList
      DisplayName="WinRT Math Library (VB)"
      MinVSVersion="11.0"
      TargetFramework=".NETCore,version=v4.5"
      AppliesTo="WindowsAppContainer"
      SupportsMultipleVersions="Error"
      MoreInfo="https://msdn.microsoft.com/">
    </FileList>
    ```

13. **솔루션 탐색기**에 대 한 바로 가기 메뉴를 열고 합니다 **SimpleMathVSIX** 프로젝트를 선택 **추가**를 선택한 후 **새 폴더**합니다.

14. 폴더 이름 바꾸기 `references`합니다.

15. 바로 가기 메뉴를 열고 합니다 **참조** 폴더 선택 **추가**를 선택한 후 **새 폴더**합니다.

16. 에 하위 폴더 이름 바꾸기 `commonconfiguration`, 하위 폴더를 만들고 하위 폴더의 이름을 `neutral`입니다.

17. 첫 번째 폴더 이름 바꾸기이 이번 이전 네 단계를 반복 `redist`합니다.

     이제 프로젝트에는 다음 폴더 구조가 포함 됩니다.

    ```xml
    references\commonconfiguration\neutral
    redist\commonconfiguration\neutral
    ```

18. **솔루션 탐색기**에 대 한 바로 가기 메뉴를 열고 합니다 **SimpleMath** 프로젝트를 선택한 후 **파일 탐색기에서 폴더 열기**합니다.

19. **파일 탐색기**로 이동 합니다 *bin\Release* 폴더에 대 한 바로 가기 메뉴를 열고는 **SimpleMath.winmd** 파일을 선택한 후 **복사**.

20. **솔루션 탐색기**로 파일을 붙여 넣습니다 합니다 *references\commonconfiguration\neutral* 폴더에는 **SimpleMathVSIX** 프로젝트입니다.

21. 이전 단계를 반복 붙여넣기를 **SimpleMath.pri** 파일을 *redist\commonconfiguration\neutral* 폴더에는 **SimpleMathVSIX** 프로젝트입니다.

22. **솔루션 탐색기**, 선택 **SimpleMath.winmd**합니다.

23. 메뉴 모음에서 선택 **뷰** > **속성** (키보드: 선택 된 **F4** 키).

24. 에 **속성** 창에서를 **빌드 작업** 속성을 **콘텐츠**, 변경한 후를 **VSIX에 포함** 속성 **True**합니다.

25. **솔루션 탐색기**,이 프로세스를 반복 **SimpleMath.pri**합니다.

26. **솔루션 탐색기**를 선택 합니다 **SimpleMathVSIX** 프로젝트입니다.

27. 메뉴 모음에서 **빌드합니다** > **빌드 SimpleMathVSIX**합니다.

28. **솔루션 탐색기**에 대 한 바로 가기 메뉴를 열고 합니다 **SimpleMathVSIX** 프로젝트를 선택한 후 **파일 탐색기에서 폴더 열기**합니다.

29. **파일 탐색기**, 이동할 *\bin\Release* 폴더 및 다음 실행 *SimpleMathVSIX.vsix* 설치 합니다.

30. 선택 된 **설치** 단추, 설치가 완료 되기를 기다린 후 다음 Visual Studio를 다시 시작 합니다.

## <a name="createSample"></a> 클래스 라이브러리를 사용 하는 샘플 앱을 만들려면

1. 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 선택합니다.

2. 템플릿 목록에서 확장 **Visual C#** 또는 **Visual Basic**를 선택한 후는 **Windows 스토어** 노드.

3. 선택 합니다 **비어 있는 앱** 서식 파일을 프로젝트의 이름 **ArithmeticUI**를 선택한 후는 **확인** 단추입니다.

4. **솔루션 탐색기**에 대 한 바로 가기 메뉴를 열고 합니다 **ArithmeticUI** 프로젝트를 선택한 후 **추가** > **참조**.

5. 참조 형식의 목록에서 확장 **Windows**를 선택한 후 **확장**합니다.

6. 세부 정보 창에서 선택 합니다 **WinRT 수학 라이브러리** 확장 합니다.

    SDK에 대 한 추가 정보가 표시 됩니다. 선택할 수 있습니다는 **자세한 정보** 열려면 링크 https://msdn.microsoft.com/처럼이 연습의 앞부분에서 SDKManifest.xml 파일에 지정 합니다.

7. **참조 관리자** 대화 상자를 선택 합니다 **WinRT 수학 라이브러리** 확인란을 선택한 후는 **확인** 단추.

8. 메뉴 모음에서 선택 **뷰** > **개체 브라우저**합니다.

9. 에 **찾아보기** 목록에서 선택 **간단한 수학**합니다.

     이제 SDK의 새로운 기능을 탐색할 수 있습니다.

10. **솔루션 탐색기**오픈 **MainPage.xaml**를 다음 XAML을 사용 하 여 해당 내용을 바꿉니다.

    **C#**

    ```xml
    <Page
        x:Class="ArithmeticUI.MainPage"
        IsTabStop="False"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:SimpleMath"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        mc:Ignorable="d">

        <Grid Background="{StaticResource ApplicationPageBackgroundThemeBrush}">
            <TextBox x:Name="_firstNumber" HorizontalAlignment="Left" Margin="414,370,0,0" TextWrapping="Wrap" Text="First Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <TextBox x:Name="_secondNumber" HorizontalAlignment="Left" Margin="613,370,0,0" TextWrapping="Wrap" Text="Second Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <Button Content="+" HorizontalAlignment="Left" Margin="557,301,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="-" HorizontalAlignment="Left" Margin="557,345,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="*" HorizontalAlignment="Left" Margin="557,389,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="/" HorizontalAlignment="Left" Margin="557,433,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="=" HorizontalAlignment="Left" Margin="755,367,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnResultsClick"/>
            <TextBox x:Name="_result" HorizontalAlignment="Left" Margin="809,370,0,0" TextWrapping="Wrap" Text="Result" VerticalAlignment="Top" Height="32" Width="163" TextAlignment="Center" IsReadOnly="True"/>
        </Grid>
    </Page>
    ```

    **Visual Basic**

    ```xml
    <Page
        x:Class="ArithmeticUI.MainPage"
        IsTabStop="False"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:SimpleMath"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        mc:Ignorable="d">

        <Grid Background="{StaticResource ApplicationPageBackgroundThemeBrush}">
            <TextBox x:Name="_firstNumber" HorizontalAlignment="Left" Margin="414,370,0,0" TextWrapping="Wrap" Text="First Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <TextBox x:Name="_secondNumber" HorizontalAlignment="Left" Margin="613,370,0,0" TextWrapping="Wrap" Text="Second Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <Button Content="+" HorizontalAlignment="Left" Margin="557,301,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="-" HorizontalAlignment="Left" Margin="557,345,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="*" HorizontalAlignment="Left" Margin="557,389,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="/" HorizontalAlignment="Left" Margin="557,433,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="=" HorizontalAlignment="Left" Margin="755,367,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnResultsClick"/>
            <TextBox x:Name="_result" HorizontalAlignment="Left" Margin="809,370,0,0" TextWrapping="Wrap" Text="Result" VerticalAlignment="Top" Height="32" Width="163" TextAlignment="Center" IsReadOnly="True"/>
        </Grid>
    </Page>
    ```

11. 업데이트 **MainPage.xaml.cs** 다음 코드와 일치 하도록 합니다.

     [!code-csharp[CreatingAnSDKUsingWinRTDemoApp#2](../extensibility/codesnippet/CSharp/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_5.cs)]
     [!code-vb[CreatingAnSDKUsingWinRTDemoApp#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_5.vb)]

12. 선택 된 **F5** 키를 눌러 앱을 실행 합니다.

13. 앱에서 임의의 두 숫자로 입력 작업을 선택한 다음 선택 합니다 **=** 단추입니다.

     올바른 결과 표시 합니다.

    성공적으로 만들고 확장명 SDK를 사용 합니다.

## <a name="see-also"></a>참고자료
- [연습: 사용 하 여 SDK 만들기C++](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)
- [연습: JavaScript를 사용 하 여 SDK 만들기](../extensibility/walkthrough-creating-an-sdk-using-javascript.md)
- [소프트웨어 개발 키트 만들기](../extensibility/creating-a-software-development-kit.md)
