---
title: SharePoint 용 OData를 표시 하는 Silverlight 웹 파트 만들기
ms.date: 02/22/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.SPE.SilverlightWebPart
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f248ce4403e771d9ab8b6d13fe55fd5ca1c960d4
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66401127"
---
# <a name="walkthrough-create-a-silverlight-web-part-that-displays-odata-for-sharepoint"></a>연습: SharePoint 용 OData를 표시 하는 Silverlight 웹 파트 만들기
  SharePoint 2010 OData를 사용 하 여 해당 목록 데이터를 노출합니다. SharePoint에서 OData 서비스는 RESTful 서비스 ListData.svc에 의해 구현 됩니다. 이 연습에서는 Silverlight 응용 프로그램을 호스트 하는 SharePoint 웹 파트를 만드는 방법을 보여 줍니다. Silverlight 응용 프로그램 ListData.svc를 사용 하 여 SharePoint 알림 목록 정보를 표시 합니다. 자세한 내용은 [SharePoint Foundation REST 인터페이스](http://go.microsoft.com/fwlink/?LinkId=225999) 하 고 [개방형 데이터 프로토콜](http://go.microsoft.com/fwlink/?LinkId=226000)합니다.

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>전제 조건
 이 연습을 완료하려면 다음 구성 요소가 필요합니다.

- 지원되는 Microsoft Windows 및 SharePoint 버전.

- [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)].

## <a name="create-a-silverlight-application-and-silverlight-web-part"></a>Silverlight 응용 프로그램 및 Silverlight 웹 파트 만들기
 먼저 Visual Studio에서 Silverlight 응용 프로그램을 만듭니다. Silverlight 응용 프로그램 ListData.svc 서비스를 사용 하 여 SharePoint 알림 목록에서 데이터를 검색 합니다.

> [!NOTE]
> Silverlight 4.0 이전 버전 없음 SharePoint 목록 데이터를 참조 하기 위해 필요한 인터페이스를 지원 합니다.

#### <a name="to-create-a-silverlight-application-and-silverlight-web-part"></a>Silverlight 웹 파트를 Silverlight 응용 프로그램을 만들려면

1. 메뉴 모음에서 선택 **파일** > **새로 만들기** > **프로젝트** 표시 하는 **새 프로젝트** 대화 상자.

2. 확장 합니다 **SharePoint** 노드 아래 **Visual C#** 또는 **Visual Basic**를 선택한 후는 **2010** 노드.

3. 템플릿 창에서 선택 합니다 **SharePoint 2010 Silverlight 웹 파트** 템플릿.

4. 에 **이름** 상자에 입력 합니다 **SLWebPartTest** 를 선택한 후는 **확인** 단추입니다.

    합니다 **SharePoint 사용자 지정 마법사** 대화 상자가 나타납니다.

5. 에 **디버깅에 대 한 사이트 및 보안 수준을 지정할** 페이지에서 사이트 정의 디버그 하려는 SharePoint 서버 사이트의 URL을 입력 하거나 기본 위치를 사용 하 여 (http://<em>시스템 이름</em>/) .

6. 에 **이 SharePoint 솔루션의 신뢰 수준을?** 섹션을 선택 합니다 **팜 솔루션으로 배포** 옵션 단추입니다.

    이 예제에서는 팜 솔루션을 팜 또는 샌드박스 솔루션으로 Silverlight 웹 파트 프로젝트를 배포할 수 있습니다. 샌드박스 솔루션과 팜 솔루션에 대 한 자세한 내용은 참조 하세요. [샌드박스 솔루션 고려 사항](../sharepoint/sandboxed-solution-considerations.md)합니다.

7. 에 **Silverlight 웹 파트를 연결 하 시겠습니까** 부분을 **Silverlight 구성 정보를 지정** 페이지를 선택는 **새 Silverlight 프로젝트 만들기 및 웹 파트와 연결할** 옵션 단추입니다.

8. 변경 합니다 **이름** 하 **SLApplication**설정 **언어** 를 **Visual Basic** 또는 **Visual C#** , 설정한 후 **Silverlight 버전** 하 **Silverlight 4.0**합니다.

9. 선택 된 **완료** 단추입니다. 프로젝트에 나타납니다 **솔루션 탐색기**합니다.

     솔루션 프로젝트가 들어 있습니다: Silverlight 응용 프로그램 및 Silverlight 웹 파트를 합니다. Silverlight 응용 프로그램을 검색 하 고 SharePoint에서 목록 데이터를 표시 하 고 Silverlight 웹 파트를 SharePoint에서 볼 수 있도록 Silverlight 응용 프로그램을 호스트 합니다.

## <a name="customize-the-silverlight-application"></a>Silverlight 응용 프로그램을 사용자 지정
 Silverlight 응용 프로그램 코드와 디자인 요소를 추가 합니다.

#### <a name="to-customize-the-silverlight-application"></a>Silverlight 응용 프로그램을 사용자 지정 하려면

1. Silverlight 응용 프로그램에서 System.Windows.Data에 어셈블리 참조를 추가 합니다. 자세한 내용은 [방법: 참조 추가 또는 제거 참조 추가 대화 상자를 사용 하 여](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)입니다.

2. **솔루션 탐색기**에 대 한 바로 가기 메뉴를 열고 **참조**를 선택한 후 **서비스 참조 추가**합니다.

    > [!NOTE]
    > Visual Basic을 사용 하는 경우에 선택 해야 합니다 **모든 파일 표시** 맨 위에 있는 아이콘 **솔루션 탐색기** 표시 하는 **참조** 노드.

3. 주소 상자에는 **서비스 참조 추가** 대화 상자와 같은 SharePoint 사이트의 URL을 입력 합니다 **http://MySPSite** 를 선택한 후는 **이동** 단추입니다.

     Silverlight에서는 ListData.svc SharePoint OData 서비스를 찾고, 전체 서비스 URL로 주소를 대체 합니다. 예를 들어 http://myserver 가 http://myserver/_vti_bin/ListData.svc합니다.

4. 선택 된 **확인** 프로젝트에 서비스 참조 추가 단추 및 ServiceReference1 기본 서비스 이름을 사용 합니다.

5. 메뉴 모음에서 **빌드** > **솔루션 빌드**를 선택합니다.

6. SharePoint 서비스를 기반으로 프로젝트에 새 데이터 원본을 추가 합니다. 이렇게 하려면 메뉴 모음에서 선택할 **뷰** > **기타 Windows** > **데이터 원본**합니다.

     합니다 **데이터 원본** 창에 모든 작업, 알림, 달력 등 사용 가능한 SharePoint 목록 데이터를 표시 합니다.

7. Silverlight 응용 프로그램에 알림 목록 데이터를 추가 합니다. "알림"을 끌 수 있습니다 합니다 **데이터 원본** Silverlight 디자이너 창입니다.

     SharePoint 사이트의 알림 목록에 바인딩된 표 형태 컨트롤을 만듭니다.

8. Silverlight 페이지에 맞게 그리드 컨트롤의 크기를 조정 합니다.

9. MainPage.xaml의 코드 파일에서 (*MainPage.xaml.cs* Visual C# 또는 *MainPage.xaml.vb* Visual basic), 다음 네임 스페이스 참조를 추가 합니다.

    ```vb
    ' Add the following three Imports statements.
    Imports SLApplication.ServiceReference1
    Imports System.Windows.Data
    Imports System.Data.Services.Client
    ```

    ```csharp
    // Add the following three using statements.
    using SLApplication.ServiceReference1;
    using System.Windows.Data;
    using System.Data.Services.Client;
    ```

10. 클래스의 맨 위에 있는 다음 변수 선언을 추가 합니다.

    ```vb
    Private context As TeamSiteDataContext
    Private myCollectionViewSource As CollectionViewSource
    Private announcements As New DataServiceCollection(Of AnnouncementsItem)()
    ```

    ```csharp
    private TeamSiteDataContext context;
    private CollectionViewSource myCollectionViewSource;
    DataServiceCollection<AnnouncementsItem> announcements = new DataServiceCollection<AnnouncementsItem>();
    ```

11. 대체는 `UserControl_Loaded` 다음을 사용 하 여 프로시저입니다.

    ```vb
    Private Sub UserControl_Loaded_1(sender As Object, e As RoutedEventArgs)
        ' The URL for the OData service.
        ' Replace <server name> in the next line with the name of your SharePoint server.
        context = New TeamSiteDataContext(New Uri("http://<server name>/_vti_bin/ListData.svc"))

        ' Do not load your data at design time.
        If Not System.ComponentModel.DesignerProperties.GetIsInDesignMode(Me) Then
            'Load your data here and assign the results to the CollectionViewSource.
            myCollectionViewSource =   DirectCast(Me.Resources("announcementsViewSource"), System.Windows.Data.CollectionViewSource)
            announcements.LoadCompleted += New EventHandler(Of LoadCompletedEventArgs)(AddressOf announcements_LoadCompleted)
            announcements.LoadAsync(context.Announcements)
        End If
    End Sub
    ```

    ```csharp
    private void UserControl_Loaded_1(object sender, RoutedEventArgs e)
    {
        // The URL for the OData service.
        // Replace <server name> in the next line with the name of your
        // SharePoint server.
        context = new TeamSiteDataContext(new Uri("http://ServerName>/_vti_bin/ListData.svc"));

        // Do not load your data at design time.
        if (!System.ComponentModel.DesignerProperties.GetIsInDesignMode(this))
        {
            //Load your data here and assign the results to the CollectionViewSource.
            myCollectionViewSource = (System.Windows.Data.CollectionViewSource)this.Resources["announcementsViewSource"];
            announcements.LoadCompleted += new EventHandler<LoadCompletedEventArgs>(announcements_LoadCompleted);
            announcements.LoadAsync(context.Announcements);
        }
    }
    ```

     로 대체 해야 합니다 *ServerName* 자리 표시자 SharePoint를 실행 하는 서버의 이름입니다.

12. 다음 오류 처리 프로시저를 추가 합니다.

    ```vb
    Private Sub announcements_LoadCompleted(sender As Object, e As LoadCompletedEventArgs)
        ' Handle any errors.
        If e.[Error] Is Nothing Then
            myCollectionViewSource.Source = announcements
        Else
            MessageBox.Show(String.Format("ERROR: {0}", e.[Error].Message))
        End If
    End Sub

    ```

    ```csharp
    void announcements_LoadCompleted(object sender, LoadCompletedEventArgs e)
    {
        // Handle any errors.
        if (e.Error == null)
        {
            myCollectionViewSource.Source = announcements;
        }
        else
        {
            MessageBox.Show(string.Format("ERROR: {0}", e.Error.Message));
        }
    }
    ```

## <a name="modify-the-silverlight-web-part"></a>Silverlight 웹 파트를 수정 합니다.
 Silverlight 디버깅을 사용 하려면 Silverlight 웹 파트 프로젝트 속성을 변경 합니다.

#### <a name="to-modify-the-silverlight-web-part"></a>Silverlight 웹 파트를 수정 하려면

1. Silverlight 웹 파트 프로젝트에 대 한 바로 가기 메뉴를 열고 (**SLWebPartTest**)를 선택한 후 **속성**합니다.

2. 에 **속성** 창에서 선택 합니다 **SharePoint** 탭 합니다.

3. 선택 되어 있지 않은 경우는 **스크립트 디버깅 대신 Silverlight 사용 디버깅** 확인란 합니다.

4. 프로젝트를 저장합니다.

## <a name="test-the-silverlight-web-part"></a>Silverlight 웹 파트 테스트
 SharePoint 목록 데이터를 올바르게 표시 되는지 확인 하려면 SharePoint에서 새 Silverlight 웹 파트를 테스트 합니다.

#### <a name="to-test-the-silverlight-web-part"></a>Silverlight 웹 파트를 테스트 하려면

1. 선택 된 **F5** SharePoint 솔루션 빌드 및 실행 하는 키입니다.

2. SharePoint에서에 **사이트 작업** 메뉴 선택 **새 페이지**합니다.

3. 에 **새 페이지** 대화 상자에서와 같은 제목을 입력 **SL 웹 파트 테스트**를 선택한 후는 **만들기** 단추입니다.

4. 페이지 디자이너에서에 **편집 도구** 탭을 선택 **삽입**합니다.

5. 탭 스트립에서 선택 **웹 파트**합니다.

6. 에 **범주** 상자를 선택 합니다 **사용자 지정** 폴더입니다.

7. 에 **웹 파트** 목록, Silverlight 웹 파트를 선택한 다음 선택 합니다 **추가** 디자이너에 웹 파트를 추가 하려면 단추.

8. 변경한 모든 추가 하려는 웹 페이지를 선택 합니다 **페이지** 탭을 선택한 다음는 **저장 후 닫기** 도구 모음에서 단추입니다.

     Silverlight 웹 파트는 SharePoint 사이트에서 알림 데이터 이제 표시 해야 합니다. 기본적으로 페이지는 SharePoint 사이트 페이지 목록에 저장 됩니다.

    > [!NOTE]
    > 도메인에 걸쳐 Silverlight에서의 데이터에 액세스할 때 Silverlight 웹 응용 프로그램을 악용 하는 보안 취약점 으로부터 보호 합니다. Silverlight에서의 원격 데이터에 액세스할 때 문제가 발생 하면 참조 [는 서비스 사용 가능한 도메인 경계를 넘어 수행](http://go.microsoft.com/fwlink/?LinkId=223276)합니다.

## <a name="see-also"></a>참고자료
- [SharePoint 용 웹 파트 만들기](../sharepoint/creating-web-parts-for-sharepoint.md)
- [배포, 게시 및 SharePoint 솔루션 패키지를 업그레이드 합니다.](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)
