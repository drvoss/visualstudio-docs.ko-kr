---
title: 속성 창에 속성 노출 | Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- properties [Visual Studio SDK], exposing in Property Browser
- properties [Visual Studio SDK]
- Property Browser, exposing properties
ms.assetid: 47f295b5-1ca5-4e7b-bb52-7b926b136622
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2cd1f44342199c26506cceb4c77378b13aefd566
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66341221"
---
# <a name="expose-properties-to-the-properties-window"></a>속성 창에 속성 노출

이 연습에서는 개체의 공용 속성을 노출 합니다 **속성** 창입니다. 이러한 속성에 변경 내용이 반영 합니다 **속성** 창입니다.

## <a name="prerequisites"></a>전제 조건

Visual Studio 2015부터 수행 설치 하면 Visual Studio SDK 다운로드 센터에서. Visual Studio 설치에서 선택적 기능으로 포함 됩니다. 또한 VS SDK를 나중에 설치할 수 있습니다. 자세한 내용은 [Visual Studio SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)합니다.

## <a name="expose-properties-to-the-properties-window"></a>속성 창에 속성 노출

이 섹션에서는 사용자 지정 도구 창을 만들고 창과 연결된 창 개체의 공용 속성을 표시 합니다 **속성** 창입니다.

### <a name="to-expose-properties-to-the-properties-window"></a>속성 창에 속성을 노출 하려면

1. 모든 Visual Studio 확장 확장 자산을 포함 하는 VSIX 배포 프로젝트를 시작 합니다. 만들기는 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 라는 VSIX 프로젝트 `MyObjectPropertiesExtension`합니다. VSIX 프로젝트 템플릿을 찾을 수 있습니다 합니다 **새 프로젝트** "vsix"를 검색 하 여 대화 상자.

2. 명명 된 사용자 지정 도구 창을 항목 템플릿을 추가 하 여 도구 창을 추가 `MyToolWindow`합니다. 에 **솔루션 탐색기**, 프로젝트 노드를 마우스 오른쪽 단추로 **추가** > **새 항목**합니다. 에 **새 항목 추가 대화 상자**로 이동 하세요 **Visual C# 항목** > **확장성** 선택한 **사용자 지정 도구 창을**합니다. 에 **이름을** 대화 상자의 맨 아래에 있는 필드에 파일 이름을 *MyToolWindow.cs*합니다. 사용자 지정 도구 창을 만드는 방법에 대 한 자세한 내용은 참조 하세요. [도구 창으로 확장 프로그램을 만들려면](../extensibility/creating-an-extension-with-a-tool-window.md)합니다.

3. 오픈 *MyToolWindow.cs* 추가한 다음 문을 사용 하 여:

   ```csharp
   using System.Collections;
   using System.ComponentModel;
   using Microsoft.VisualStudio.Shell.Interop;
   ```

4. 이제 다음 필드를 추가 합니다 `MyToolWindow` 클래스입니다.

   ```csharp
   private ITrackSelection trackSel;
   private SelectionContainer selContainer;

   ```

5. `MyToolWindow` 클래스에 다음 코드를 추가합니다.

   ```csharp
   private ITrackSelection TrackSelection
   {
       get
       {
           if (trackSel == null)
               trackSel =
                  GetService(typeof(STrackSelection)) as ITrackSelection;
           return trackSel;
       }
   }

   public void UpdateSelection()
   {
       ITrackSelection track = TrackSelection;
       if (track != null)
           track.OnSelectChange((ISelectionContainer)selContainer);
   }

   public void SelectList(ArrayList list)
   {
       selContainer = new SelectionContainer(true, false);
       selContainer.SelectableObjects = list;
       selContainer.SelectedObjects = list;
       UpdateSelection();
   }

   public override void OnToolWindowCreated()
   {
       ArrayList listObjects = new ArrayList();
       listObjects.Add(this);
       SelectList(listObjects);
   }
   ```

    합니다 `TrackSelection` 속성에서 사용 하 `GetService` 가져오려고는 `STrackSelection` 제공 하는 서비스는 <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> 인터페이스입니다. 합니다 `OnToolWindowCreated` 이벤트 처리기 및 `SelectList` 메서드는 함께 도구 창 창 개체 자체를 포함 하는 선택한 개체의 목록을 만듭니다. 합니다 `UpdateSelection` 메서드의 지시에 따라 합니다 **속성** 창에 도구 창의 공용 속성을 표시 합니다.

6. 프로젝트를 빌드하고 디버깅을 시작합니다. Visual Studio의 실험적 인스턴스가 표시 됩니다.

7. 경우는 **속성** 창이 표시 되지 않으면, 키를 눌러 엽니다 **F4**합니다.

8. 엽니다는 **MyToolWindow** 창입니다. 찾을 수 있습니다 **뷰** > **기타 Windows**합니다.

    창이 열리고에서 창의 공용 속성에 표시 된 **속성** 창입니다.

9. 변경 합니다 **캡션** 속성에는 **속성** 창을 **내 개체 속성**합니다.

     MyToolWindow 창 캡션에 적절 하 게 변경 합니다.

## <a name="expose-tool-window-properties"></a>도구 창 속성 표시

이 섹션에서는 도구 창을 추가 하 고 해당 속성을 노출 합니다. 속성에 변경 내용이 반영 합니다 **속성** 창입니다.

### <a name="to-expose-tool-window-properties"></a>도구 창 속성 노출

1. 열기 *MyToolWindow.cs*, IsChecked 공용 부울 속성을 추가 하는 `MyToolWindow` 클래스.

    ```csharp
    [Category("My Properties")]
    [Description("MyToolWindowControl properties")]
    public bool IsChecked
    {
        get {
            if (base.Content == null)  return false;
            return (bool)(( MyToolWindowControl) base.Content).checkBox.IsChecked;
        }
        set {
            ((MyToolWindowControl) base.Content).checkBox.IsChecked = value;
        }
    }
    ```

     이 속성 나중에 만들 WPF 확인란에서의 상태를 가져옵니다.

2. 오픈 *MyToolWindowControl.xaml.cs* MyToolWindowControl 생성자를 다음 코드로 바꿉니다.

    ```vb
    private MyToolWindow pane;
    public MyToolWindowControl(MyToolWindow pane)
    {
        InitializeComponent();
        this.pane = pane;
        checkBox.IsChecked = false;
    }
    ```

     이렇게 `MyToolWindowControl` 에 대 한 액세스는 `MyToolWindow` 창입니다.

3. *MyToolWindow.cs*를 변경 합니다 `MyToolWindow` 같이 생성자:

    ```csharp
    base.Content = new MyToolWindowControl(this);
    ```

4. MyToolWindowControl의 디자인 뷰로 변경 합니다.

5. 단추를 삭제 하 고에서 확인란을 추가 합니다 **도구 상자** 왼쪽된 위 모퉁이에 있습니다.

6. Checked 및 Unchecked 이벤트를 추가 합니다. 디자인 뷰에서 확인란을 선택 합니다. 에 **속성** 창에서 이벤트 처리기 단추를 클릭 (맨 위에 있는 오른쪽를 **속성** 창). 찾을 **Checked** 형식과 **checkbox_Checked** 텍스트 상자에서 찾을 **Unchecked** 형식과 **checkbox_Unchecked** 텍스트 상자에.

7. 확인란 이벤트 처리기를 추가 합니다.

    ```csharp
    private void checkbox_Checked(object sender, RoutedEventArgs e)
    {
        pane.IsChecked = true;
        pane.UpdateSelection();
    }
    private void checkbox_Unchecked(object sender, RoutedEventArgs e)
    {
        pane.IsChecked = false;
        pane.UpdateSelection();
    }
    ```

8. 프로젝트를 빌드하고 디버깅을 시작합니다.

9. 실험적 인스턴스를 엽니다는 **MyToolWindow** 창입니다.

     창의 속성에 대 한 확인 합니다 **속성** 창입니다. **IsChecked** 속성 아래에 있는 창의 맨 아래에 표시 되는 **내 속성** 범주.

10. 확인 상자를 선택 합니다 **MyToolWindow** 창입니다. **IsChecked** 에 **속성** 창으로 변경 **True**합니다. 확인란의 선택을 취소 합니다 **MyToolWindow** 창입니다. **IsChecked** 에 **속성** 창으로 변경 **False**합니다. 값을 변경 **IsChecked** 에 **속성** 창입니다. 확인란 합니다 **MyToolWindow** 창의 내용이 변경 된 새 값과 일치 하도록 합니다.

    > [!NOTE]
    > 경우에 표시 되는 개체의 삭제 해야 합니다는 **속성** 창, 호출 `OnSelectChange` 사용 하 여는 `null` 선택 컨테이너 첫 번째입니다. 속성 또는 개체를 삭제 한 후 업데이트 된 선택 컨테이너에 변경할 수 있습니다 <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectableObjects%2A> 고 <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectedObjects%2A> 나열 합니다.

## <a name="change-selection-lists"></a>선택 목록 변경

 이 섹션에서는 기본 속성 클래스에 대 한 선택 목록을 추가 하 고 도구 창 인터페이스를 사용 하 여 선택 목록을 표시 하려면 선택 합니다.

### <a name="to-change-selection-lists"></a>선택 목록 변경 하려면

1. 오픈 *MyToolWindow.cs* 라는 공용 클래스를 추가 하 고 `Simple`입니다.

    ```csharp
    public class Simple
    {
        private string someText = "";

        [Category("My Properties")]
        [Description("Simple Properties")]
        [DisplayName("My Text")]
        public string SomeText
        {
            get { return someText; }
            set { someText = value; }
        }

        [Category("My Properties")]
        [Description("Read-only property")]
        public bool ReadOnly
        {
            get { return false; }
        }
    }
    ```

2. 추가 `SimpleObject` 속성을를 `MyToolWindow` 전환 하는 두 가지 방법 및 클래스에는 **속성** 창 선택 영역 창 창 사이 및 `Simple` 개체.

    ```csharp
    private Simple simpleObject = null;
    public Simple SimpleObject
    {
        get
        {
            if (simpleObject == null) simpleObject = new Simple();
            return simpleObject;
        }
    }

    public void SelectSimpleList()
    {
        ArrayList listObjects = new ArrayList();
        listObjects.Add(SimpleObject);
        SelectList(listObjects);
    }

    public void SelectThisList()
    {
        ArrayList listObjects = new ArrayList();
        listObjects.Add(this);
        SelectList(listObjects);
    }
    ```

3. *MyToolWindowControl.cs*, 확인란 처리기는 이러한 코드 줄을 바꿉니다.

    ```csharp
    private void checkbox_Checked(object sender, RoutedEventArgs e)
     {
        pane.IsChecked = true;
        pane.SelectSimpleList();
        pane.UpdateSelection();
    }
    private void checkbox_Unchecked(object sender, RoutedEventArgs e)
    {
        pane.IsChecked = false;
        pane.SelectThisList();
        pane.UpdateSelection();
    }
    ```

4. 프로젝트를 빌드하고 디버깅을 시작합니다.

5. 실험적 인스턴스를 엽니다는 **MyToolWindow** 창입니다.

6. 확인란을 선택 합니다 **MyToolWindow** 창입니다. **속성** 창에 표시 됩니다는 `Simple` 개체의 속성을 **SomeText** 및 **ReadOnly**합니다. 확인란의 선택을 취소 합니다. 공용 속성 창에 표시 된 **속성** 창입니다.

    > [!NOTE]
    > 표시 이름 **SomeText** 됩니다 **내 텍스트**합니다.

## <a name="best-practice"></a>모범 사례

이 연습에서는 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 되도록 선택할 수 있는 개체 컬렉션 및 선택한 개체 컬렉션은 동일한 컬렉션에 구현 됩니다. 속성 브라우저 목록에서 선택한 개체에만 표시 됩니다. 더 완전 한 ISelectionContainer 구현 Reference.ToolWindow 샘플을 참조 하세요.

Visual Studio 도구 창은 Visual Studio 세션 간에 유지 합니다. 도구 창 상태를 유지 하는 방법은 참조 하세요. <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>합니다.

## <a name="see-also"></a>참고자료

- [속성 및 속성 창 확장](../extensibility/extending-properties-and-the-property-window.md)