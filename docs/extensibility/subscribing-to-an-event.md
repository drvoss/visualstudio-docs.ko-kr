---
title: 이벤트 구독 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- running document table (RDT), responding to events
- running document table (RDT), subscribing to events
ms.assetid: e94a4fea-94df-488e-8560-9538413422bc
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5c0466d5b8644ddeae60df24b8b980ee9da0f820
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66331677"
---
# <a name="subscribing-to-an-event"></a>이벤트 구독
이 연습에는 실행 중인 문서 테이블 (RDT)의 이벤트에 응답 하는 도구 창을 만드는 방법을 설명 합니다. 도구 창을 구현 하는 사용자 정의 컨트롤을 호스트 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>합니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> 메서드는 이벤트 인터페이스를 연결 합니다.

## <a name="prerequisites"></a>전제 조건
 Visual Studio 2015부터 수행 설치 하면 Visual Studio SDK 다운로드 센터에서. Visual Studio 설치에서 선택적 기능으로 포함 됩니다. 또한 VS SDK를 나중에 설치할 수 있습니다. 자세한 내용은 [Visual Studio SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)합니다.

## <a name="subscribing-to-rdt-events"></a>RDT 이벤트 구독

#### <a name="to-create-an-extension-with-a-tool-window"></a>도구 창으로 확장 프로그램을 만들려면

1. 라는 프로젝트를 만듭니다 **RDTExplorer** 라는 사용자 지정 도구 창 항목 템플릿을 VSIX 템플릿을 사용 하 여 추가한 **RDTExplorerWindow**합니다.

     도구 창을 사용 하 여 확장을 만드는 방법에 대 한 자세한 내용은 참조 하세요. [도구 창으로 확장을 만드는](../extensibility/creating-an-extension-with-a-tool-window.md)합니다.

#### <a name="to-subscribe-to-rdt-events"></a>RDT 이벤트를 구독할 수

1. RDTExplorerWindowControl.xaml 파일을 열고 라는 단추를 삭제할 `button1`합니다. 추가 된 <xref:System.Windows.Forms.ListBox> 제어 하 고 기본 이름을 적용 합니다. Grid 요소는 다음과 같습니다.

    ```xml
    <Grid>
        <StackPanel Orientation="Vertical" Margin="-10,10,10,0">
            <TextBlock Margin="10" HorizontalAlignment="Center">RDTExplorerWindow</TextBlock>
            <ListBox x:Name="listBox" Height="100" />
        </StackPanel>
    </Grid>
    ```

2. 코드 뷰에서 RDTExplorerWindow.cs 파일을 엽니다. 다음 추가 using 문을 파일의 시작에 있습니다.

    ```csharp
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Shell;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

3. 수정 합니다 `RDTExplorerWindow` 있으므로 클래스에서 파생 하는 것 외에도 있는 <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> 구현 클래스는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> 인터페이스.

    ```csharp
    public class RDTExplorerWindow : ToolWindowPane, IVsRunningDocTableEvents
    {. . .}
    ```

4. <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>를 구현해야 합니다.

    - 인터페이스를 구현 합니다. IVsRunningDocTableEvents 이름에 커서를 놓습니다. 전구가 왼쪽된 여백에 표시 됩니다. 전구는 오른쪽에 있는 아래쪽 화살표를 클릭 하 고 선택 **인터페이스 구현**합니다.

5. 인터페이스의 각 메서드에서 줄을 바꿀 `throw new NotImplementedException();` 이 사용 하 여:

    ```csharp
    return VSConstants.S_OK;
    ```

6. 쿠키 필드 RDTExplorerWindow 클래스를 추가 합니다.

    ```csharp
    private uint rdtCookie;
    ```

     반환 되는 쿠키를 포함 하는이 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> 메서드.

7. RDT 이벤트에 등록 하려면 RDTExplorerWindow의 initialize () 메서드를 재정의 합니다. 항상 생성자에 없는 ToolWindowPane의 initialize () 메서드에서 서비스를 가져와야 합니다.

    ```csharp
    protected override void Initialize()
    {
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)
        this.GetService(typeof(SVsRunningDocumentTable));
        rdt.AdviseRunningDocTableEvents(this, out rdtCookie);
    }
    ```

     <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> 서비스를 가져오기 위해 호출 되는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> 인터페이스입니다. 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> RDT 이벤트를 구현 하는 개체에 연결 하는 메서드 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>,이 경우 RDTExplorer 개체입니다.

8. RDTExplorerWindow의 dispose () 메서드를 업데이트 합니다.

    ```csharp
    protected override void Dispose(bool disposing)
    {
        // Release the RDT cookie.
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)
            Package.GetGlobalService(typeof(SVsRunningDocumentTable));
        rdt.UnadviseRunningDocTableEvents(rdtCookie);

        base.Dispose(disposing);
    }
    ```

     합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnadviseRunningDocTableEvents%2A> 메서드 간의 연결을 삭제 `RDTExplorer` 및 RDT 이벤트 알림.

9. 본문에 다음 줄을 추가 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnBeforeLastDocumentUnlock%2A> 처리기 직전는 `return` 문.

    ```csharp
    public int OnBeforeLastDocumentUnlock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)
    {
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnBeforeLastDocumentUnlock");
        return VSConstants.S_OK;
    }
    ```

10. 본문에도 유사한 줄을 추가 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterFirstDocumentLock%2A> 처리기 및 목록 상자에 표시 하려는 다른 이벤트입니다.

    ```csharp
    public int OnAfterFirstDocumentLock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)
    {
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnAfterFirstDocumentLock");
        return VSConstants.S_OK;
    }
    ```

11. 프로젝트를 빌드하고 디버깅을 시작합니다. Visual Studio 실험적 인스턴스가 표시 됩니다.

12. 엽니다는 **RDTExplorerWindow** (**보기 / 다른 Windows / RDTExplorerWindow**).

     합니다 **RDTExplorerWindow** 빈 이벤트 목록을 사용 하 여 창이 열립니다.

13. 페이지를 열거나 솔루션을 만듭니다.

     로 `OnBeforeLastDocument` 고 `OnAfterFirstDocument` 이벤트가, 각 이벤트에 대 한 알림을 표시 이벤트 목록입니다.