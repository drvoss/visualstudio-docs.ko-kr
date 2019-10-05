---
title: IntelliTrace를 사용 하 여 SharePoint 응용 프로그램 디버그
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- IntelliTrace [SharePoint development in Visual Studio]
- standalone data collector
- SharePoint development in Visual Studio, IntelliTrace
- data collector
- IntelliTrace
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 59407696743b15262db83f915feb075a10e22225
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66401038"
---
# <a name="walkthrough-debug-a-sharepoint-application-by-using-intellitrace"></a>연습: IntelliTrace를 사용 하 여 SharePoint 응용 프로그램 디버그

IntelliTrace를 사용 하 여 SharePoint 솔루션을 보다 쉽게 디버깅할 수 있습니다. 기존 디버거는 현재 시점에서 솔루션의 스냅숏만을 제공합니다. 그러나 솔루션에서 발생 한 이전 이벤트 및 컨텍스트는 발생 하며 코드로 이동 하려면를 검토 하려면 IntelliTrace를 사용할 수 있습니다.

 이 연습에는 Microsoft Monitoring Agent를 사용 하 여 배포 된 응용 프로그램에서 IntelliTrace 데이터를 수집 하 여 Visual Studio에서 SharePoint 2010 또는 SharePoint 2013 프로젝트를 디버그 하는 방법을 보여 줍니다. 해당 데이터를 분석 하려면 Visual Studio Enterprise를 사용 해야 합니다. 이 프로젝트는 기능이 활성화 되 면 작업 목록 및 알림 목록에 공지에 작업을 추가 하는 기능 수신기를 통합 합니다. 기능이 비활성화 되 면 작업은 완료 표시 하 고 두 번째 알림이 알림 목록에 추가 됩니다. 그러나 프로시저 프로젝트 올바르게 실행 하지 못하도록 하는 논리 오류를 포함 합니다. IntelliTrace를 사용 하 여 찾습니다 하 고 오류를 수정 합니다.

 **적용 대상:** 이 항목의 정보는 Visual Studio에서 생성 된 SharePoint 2010 및 SharePoint 2013 솔루션에 적용 됩니다.

 이 연습에서는 다음 작업을 수행합니다.

- [기능 수신기 만들기](#create-a-feature-receiver)

- [기능 수신기에 코드 추가](#add-code-to-the-feature-receiver)

- [프로젝트 테스트](#test-the-project)

- [Microsoft Monitoring Agent를 사용 하 여 IntelliTrace 데이터 수집](#collect-intellitrace-data-by-using-microsoft-monitoring-agent)

- [디버깅 하 고 SharePoint 솔루션 수정](#debug-and-fix-the-sharepoint-solution)

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>전제 조건

이 연습을 완료하려면 다음 구성 요소가 필요합니다.

- Windows 및 SharePoint 버전을 지원 합니다.

- Visual Studio Enterprise.

## <a name="create-a-feature-receiver"></a>기능 수신기 만들기

먼저, 기능 수신기에 있는 빈 SharePoint 프로젝트를 만듭니다.

1. SharePoint 2010 또는 SharePoint 2013 솔루션 프로젝트를 만들고 이름을 **IntelliTraceTest**합니다.

     합니다 **SharePoint 사용자 지정 마법사** 표시 되는 프로젝트 및 솔루션의 신뢰 수준에 대 한 SharePoint 사이트를 지정할 수 있습니다.

2. 선택 된 **팜 솔루션으로 배포** 옵션 단추를 선택한 후는 **마침** 단추입니다.

     IntelliTrace는 팜 솔루션 에서만 작동합니다.

3. **솔루션 탐색기**에 대 한 바로 가기 메뉴를 열고 합니다 **기능** 노드를 선택한 후 **기능 추가**합니다.

     *Feature1.feature* 나타납니다.

4. Feature1.feature에 대 한 바로 가기 메뉴를 열고 선택한 **이벤트 수신기 추가** 기능에는 코드 모듈을 추가 합니다.

## <a name="add-code-to-the-feature-receiver"></a>기능 수신기에 코드 추가

다음 코드를 추가 기능 수신기의 두 가지 방법: `FeatureActivated` 고 `FeatureDeactivating`입니다. 이러한 메서드는 기능을 활성화 또는 SharePoint에서 각각 비활성화 될 때마다 트리거합니다.

1. 맨 위에 있는 `Feature1EventReceiver` 클래스, SharePoint 사이트와 하위 사이트를 지정 하는 변수를 선언 하는 다음 코드를 추가 합니다.

    ```vb
    ' SharePoint site and subsite.
    Private siteUrl As String = "http://localhost"
    Private webUrl As String = "/"
    ```

    ```csharp
    // SharePoint site and subsite.
    private string siteUrl = "http://localhost";
    private string webUrl = "/";
    ```

2. `FeatureActivated` 메서드를 다음 코드로 바꿉니다.

    ```vb
    Public Overrides Sub FeatureActivated(ByVal properties As SPFeatureReceiverProperties)
        Try
            Using site As New SPSite(siteUrl)
                Using web As SPWeb = site.OpenWeb(webUrl)
                    ' Reference the lists.
                    Dim announcementsList As SPList = web.Lists("Announcements")
                    Dim taskList As SPList = web.Lists("Tasks")

                    ' Add an announcement to the Announcements list.
                    Dim listItem As SPListItem = announcementsList.Items.Add()
                    listItem("Title") = "Activated Feature: " & Convert.ToString(properties.Definition.DisplayName)
                    listItem("Body") = Convert.ToString(properties.Definition.DisplayName) & " was activated on: " & DateTime.Now.ToString()
                    listItem.Update()

                    ' Add a task to the Task list.
                    Dim newTask As SPListItem = taskList.Items.Add()
                    newTask("Title") = "Deactivate feature: " & Convert.ToString(properties.Definition.DisplayName)
                    newTask.Update()
                End Using
            End Using

        Catch e As Exception
            Console.WriteLine("Error: " & e.ToString())
        End Try

    End Sub
    ```

    ```csharp
    public override void FeatureActivated(SPFeatureReceiverProperties properties)
    {
        try
        {
            using (SPSite site = new SPSite(siteUrl))
            {
                using (SPWeb web = site.OpenWeb(webUrl))
                {
                    // Reference the lists.
                    SPList announcementsList = web.Lists["Announcements"];
                    SPList taskList = web.Lists["Tasks"];

                    // Add an announcement to the Announcements list.
                    SPListItem listItem = announcementsList.Items.Add();
                    listItem["Title"] = "Activated Feature: " + properties.Definition.DisplayName;
                    listItem["Body"] = properties.Definition.DisplayName + " was activated on: " + DateTime.Now.ToString();
                    listItem.Update();

                    // Add a task to the Task list.
                    SPListItem newTask = taskList.Items.Add();
                    newTask["Title"] = "Deactivate feature: " + properties.Definition.DisplayName;
                    newTask.Update();
                }
            }
        }

        catch (Exception e)
        {
            Console.WriteLine("Error: " + e.ToString());
        }

    }
    ```

3. `FeatureDeactivating` 메서드를 다음 코드로 바꿉니다.

    ```vb
    Public Overrides Sub FeatureDeactivating(ByVal properties As SPFeatureReceiverProperties)
        ' The following line induces an error to demonstrate debugging.
        ' Remove this line later for proper operation.
        Throw New System.InvalidOperationException("Serious error occurred!")
        Try
            Using site As New SPSite(siteUrl)
                Using web As SPWeb = site.OpenWeb(webUrl)
                    ' Reference the lists.
                    Dim taskList As SPList = web.Lists("Tasks")
                    Dim announcementsList As SPList = web.Lists("Announcements")

                    ' Add an announcement that the feature was deactivated.
                    Dim listItem As SPListItem = announcementsList.Items.Add()
                    listItem("Title") = "Deactivated Feature: " & Convert.ToString(properties.Definition.DisplayName)
                    listItem("Body") = Convert.ToString(properties.Definition.DisplayName) & " was deactivated on: " & DateTime.Now.ToString()
                    listItem.Update()

                    ' Find the task that the feature receiver added to the Task list when the
                    ' feature was activated.
                    Dim qry As New SPQuery()
                    qry.Query = "<Where><Contains><FieldRef Name='Title' /><Value Type='Text'>Deactivate</Value></Contains></Where>"
                    Dim taskItems As SPListItemCollection = taskList.GetItems(qry)

                    For Each taskItem As SPListItem In taskItems
                        ' Mark the task as complete.
                        taskItem("PercentComplete") = 1
                        taskItem("Status") = "Completed"
                        taskItem.Update()
                    Next
                End Using

            End Using

        Catch e As Exception
            Console.WriteLine("Error: " & e.ToString())
        End Try

    End Sub
    ```

    ```csharp
    public override void FeatureDeactivating(SPFeatureReceiverProperties properties)
    {
        // The following line induces an error to demonstrate debugging.
        // Remove this line later for proper operation.
        throw new System.InvalidOperationException("A serious error occurred!");
        try
        {
            using (SPSite site = new SPSite(siteUrl))
            {
                using (SPWeb web = site.OpenWeb(webUrl))
                {
                    // Reference the lists.
                    SPList taskList = web.Lists["Tasks"];
                    SPList announcementsList = web.Lists["Announcements"];

                    // Add an announcement that the feature was deactivated.
                    SPListItem listItem = announcementsList.Items.Add();
                    listItem["Title"] = "Deactivated Feature: " + properties.Definition.DisplayName;
                    listItem["Body"] = properties.Definition.DisplayName + " was deactivated on: " + DateTime.Now.ToString();
                    listItem.Update();

                    // Find the task that the feature receiver added to the Task list when the
                    // feature was activated.
                    SPQuery qry = new SPQuery();
                    qry.Query = "<Where><Contains><FieldRef Name='Title' /><Value Type='Text'>Deactivate</Value></Contains></Where>";
                    SPListItemCollection taskItems = taskList.GetItems(qry);

                    foreach (SPListItem taskItem in taskItems)
                    {
                        // Mark the task as complete.
                        taskItem["PercentComplete"] = 1;
                        taskItem["Status"] = "Completed";
                        taskItem.Update();
                    }
                }
            }

        }

        catch (Exception e)
        {
            Console.WriteLine("Error: " + e.ToString());
        }
    }
    ```

## <a name="test-the-project"></a>프로젝트 테스트

코드가 기능 수신기에 추가 하 고 데이터 수집기가 실행을 배포 하 고 올바르게 작동 하는지 여부를 테스트 하려면 SharePoint 솔루션을 실행 합니다.

> [!IMPORTANT]
> 예를 들어 FeatureDeactivating 이벤트 처리기에서 오류가 throw 됩니다. 이 연습의 뒷부분에서 생성 하는 데이터 수집기.iTrace 파일을 사용 하 여이 오류를 찾습니다.

1. SharePoint에 솔루션을 배포 하 고 그런 다음 브라우저에서 SharePoint 사이트를 엽니다.

     기능을 자동으로 활성화 되어 공지 사항 및 태스크를 추가 하려면 해당 기능 수신기입니다.

2. 공지 사항 및 작업 목록의 내용을 표시 합니다.

     알림 목록 이라고 하는 새 공지 사항이 있어야 **Activated 기능: IntelliTraceTest_Feature1**, 작업 목록 이라고 하는 새 작업을 해야 했으며 **비활성화 기능: IntelliTraceTest_Feature1**. 이러한 항목 중 하나가 없는 경우 기능이 활성화 되어 있는지 여부를 확인 합니다. 이 활성화 되지 않은 경우이 활성화 합니다.

3. 다음 단계를 수행 하 여 기능을 비활성화 합니다.

   1. 에 **사이트 작업** SharePoint에서 메뉴 **사이트 설정**합니다.

   2. 아래 **사이트 작업**를 선택 합니다 **사이트 기능 관리** 링크 합니다.

   3. 옆에 **IntelliTraceTest Feature1**를 선택 합니다 **비활성화** 단추입니다.

   4. 경고 페이지에서 선택 합니다 **이 기능을 비활성화** 링크 합니다.

      FeatureDeactivating() 이벤트 처리기에서 오류를 throw 합니다.

## <a name="collect-intellitrace-data-by-using-microsoft-monitoring-agent"></a>Microsoft Monitoring Agent를 사용 하 여 IntelliTrace 데이터 수집

SharePoint를 실행 하는 시스템에서 Microsoft Monitoring Agent를 설치 하는 경우에 IntelliTrace 반환 하는 제네릭 정보 보다 더 관련 된 데이터를 사용 하 여 SharePoint 솔루션을 디버깅할 수 있습니다. 에이전트에 SharePoint 솔루션 실행 하는 동안 디버그 정보를 캡처하려면 PowerShell cmdlet을 사용 하 여 Visual Studio 외부에서 작동 합니다.

> [!NOTE]
> 이 섹션의 구성 정보는이 예제와 관련이 있습니다. 다른 구성 옵션에 대 한 자세한 내용은 참조 하세요. [IntelliTrace 독립 실행형 수집기를 사용 하 여](../debugger/using-the-intellitrace-stand-alone-collector.md)입니다.

1. SharePoint를 실행 하는 컴퓨터의 [Microsoft Monitoring Agent를 설정 하 고 솔루션을 모니터링 하려면](../debugger/using-the-intellitrace-stand-alone-collector.md)합니다.

2. 기능을 비활성화 합니다.

   1. 에 **사이트 작업** SharePoint에서 메뉴 **사이트 설정**합니다.

   2. 아래 **사이트 작업**를 선택 합니다 **사이트 기능 관리** 링크 합니다.

   3. 옆에 **IntelliTraceTest Feature1**를 선택 합니다 **비활성화** 단추입니다.

   4. 경고 페이지에서 선택 합니다 **이 기능을 비활성화** 링크 합니다.

      (이 예제의 경우 FeatureDeactivating() 이벤트 처리기에서 throw 되는 오류)으로 인해 오류가 발생 했습니다.

3. PowerShell 창에서 실행 합니다 [Stop-webapplicationmonitoring](http://go.microsoft.com/fwlink/?LinkID=313687) .iTrace 파일을 만들고, 모니터링을 중지, SharePoint 솔루션을 다시 시작 하는 명령입니다.

     **Stop-WebApplicationMonitoring**  *"\<SharePointSite>\\<SharePointAppName\>"*

## <a name="debug-and-fix-the-sharepoint-solution"></a>디버깅 하 고 SharePoint 솔루션 수정

이제 찾기 및 SharePoint 솔루션에서 오류를 해결 하려면 Visual Studio에서 IntelliTrace 로그 파일을 볼 수 있습니다.

1. \IntelliTraceLogs 폴더에서 Visual Studio에서.iTrace 파일을 엽니다.

     합니다 **IntelliTrace 요약** 페이지가 나타납니다. SharePoint 상관 관계 ID (GUID)의 처리 되지 않은 예외가 영역에 나타나는 오류 처리 되지 않았습니다. 때문에 합니다 **분석** 섹션입니다. 선택 된 **호출 스택** 오류가 발생 하 고 호출 스택을 보고 하려는 경우 단추입니다.

2. 선택 된 **예외 디버그** 단추입니다.

     메시지가 표시 되 면 기호 파일을 로드 합니다. 에 **IntelliTrace** 예외 강조 표시 됩니다 창 "throw 됨: 심각한 오류가 발생 했습니다! ".

     IntelliTrace 창에서 실패 한 코드를 표시 하는 예외를 선택 합니다.

3. SharePoint 솔루션 열기 및 다음 주석으로 처리 하거나 제거 하 여 오류를 해결 합니다 **throw** FeatureDeactivating() 프로시저의 맨 위에 있는 문.

4. Visual Studio에서 솔루션을 다시 빌드하고 SharePoint에 다시 배포 합니다.

5. 다음 단계를 수행 하 여 기능을 비활성화 합니다.

    1. 에 **사이트 작업** SharePoint에서 메뉴 **사이트 설정**합니다.

    2. 아래 **사이트 작업**를 선택 합니다 **사이트 기능 관리** 링크 합니다.

    3. 옆에 **IntelliTraceTest Feature1**를 선택 합니다 **비활성화** 단추입니다.

    4. 경고 페이지에서 선택 합니다 **이 기능을 비활성화** 링크 합니다.

6. 태스크 목록을 열고 있는지 확인 합니다 **상태** 비활성화 작업의 값은 "완료" 및 해당 **% 완료** 값이 100%입니다.

     코드는 이제 제대로 실행 됩니다.

## <a name="see-also"></a>참고자료

- [확인 하 고 SharePoint 코드 디버그](../sharepoint/verifying-and-debugging-sharepoint-code.md)
- [IntelliTrace](../debugger/intellitrace.md)
- [연습: 단위 테스트를 사용 하 여 SharePoint 코드 확인](/previous-versions/visualstudio/visual-studio-2010/gg599006\(v\=vs.100\))