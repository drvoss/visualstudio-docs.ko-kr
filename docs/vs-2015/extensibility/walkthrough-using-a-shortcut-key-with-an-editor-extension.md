---
title: '연습: 편집기 확장에서 바로 가기 키 사용 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link keystrokes to commands
ms.assetid: cf6cc6c6-5a65-4f90-8f14-663decf74672
caps.latest.revision: 33
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5c9cb20bafa552c47a2f599d12e6b66fdb2bde59
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68201951"
---
# <a name="walkthrough-using-a-shortcut-key-with-an-editor-extension"></a>연습: 편집기 확장에서 바로 가기 키 사용
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

편집기 확장에서 바로 가기 키에 대응할 수 있습니다. 다음 연습에는 바로 가기 키를 사용 하 여 보기 장식 텍스트 뷰를 추가 하는 방법을 보여 줍니다. 이 연습에서는 뷰포트 adornment 편집기 템플릿을 기준으로 하며 장식을 사용 하 여 추가할 수 있도록는 + 문자입니다.  
  
## <a name="prerequisites"></a>전제 조건  
 Visual Studio 2015부터 수행 설치 하면 Visual Studio SDK 다운로드 센터에서. Visual Studio 설치에서 선택적 기능으로 포함 됩니다. 또한 VS SDK를 나중에 설치할 수 있습니다. 자세한 내용은 [Visual Studio SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)합니다.  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>MEF(Managed Extensibility Framework) 프로젝트 만들기  
  
1. C# VSIX 프로젝트를 만듭니다. (에 **새 프로젝트** 대화 상자에서 **Visual C# / 확장성**, 한 다음 **VSIX 프로젝트**.) 솔루션의 이름을 `KeyBindingTest`로 지정합니다.  
  
2. 편집기 텍스트 장식 항목 템플릿을 프로젝트에 추가 하 고 이름을 `KeyBindingTest`입니다. 자세한 내용은 [편집기 항목 템플릿을 사용 하 여 확장을 만드는](../extensibility/creating-an-extension-with-an-editor-item-template.md)합니다.  
  
3. 다음 참조를 추가 하 고 설정 **CopyLocal** 에 `false`:  
  
    Microsoft.VisualStudio.Editor  
  
    Microsoft.VisualStudio.OLE.Interop  
  
    Microsoft.VisualStudio.Shell.14.0  
  
    Microsoft.VisualStudio.TextManager.Interop  
  
   KeyBindingTest 클래스 파일에서 클래스 이름을 PurpleCornerBox를 변경 합니다. 왼쪽된 여백에 표시 되는 전구를 사용 하 여 적절 하 게 다른 변경. 생성자 내부 adornment 계층의 이름을 변경할 **KeyBindingTest** 하 **PurpleCornerBox**:  
  
```csharp  
this.layer = view.GetAdornmentLayer("PurpleCornerBox");  
```  
  
## <a name="defining-the-command-filter"></a>명령 필터를 정의합니다.  
 명령 필터는의 구현 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>, 장식 인스턴스화하여 명령을 처리 합니다.  
  
1. 클래스 파일을 추가하고 이름을 `KeyBindingCommandFilter`로 지정합니다.  
  
2. 다음 using 문을 추가합니다.  
  
    ```csharp  
    using System;  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.OLE.Interop;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Text.Editor;  
  
    ```  
  
3. KeyBindingCommandFilter 이라는 클래스에서 상속 해야 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>합니다.  
  
    ```csharp  
    internal class KeyBindingCommandFilter : IOleCommandTarget  
    ```  
  
4. 텍스트 보기에 대 한 전용 필드, 다음 명령을 명령 체인 및 명령 필터가 이미 추가 되어 있는지 여부를 나타내는 플래그를 추가 합니다.  
  
    ```csharp  
    private IWpfTextView m_textView;  
    internal IOleCommandTarget m_nextTarget;  
    internal bool m_added;  
    internal bool m_adorned;  
    ```  
  
5. 텍스트 뷰를 설정 하는 생성자를 추가 합니다.  
  
    ```csharp  
    public KeyBindingCommandFilter(IWpfTextView textView)  
    {  
        m_textView = textView;  
        m_adorned = false;  
    }  
    ```  
  
6. 구현 된 `QueryStatus()` 같이 메서드.  
  
    ```vb  
    int IOleCommandTarget.QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)  
    {  
        return m_nextTarget.QueryStatus(ref pguidCmdGroup, cCmds, prgCmds, pCmdText);  
    }  
    ```  
  
7. 구현 된 `Exec()` 한다는 자주색 상자를 뷰에 추가 하는 경우 메서드는 문자가 입력 된 +.  
  
    ```csharp  
    int IOleCommandTarget.Exec(ref Guid pguidCmdGroup, uint nCmdID, uint nCmdexecopt, IntPtr pvaIn, IntPtr pvaOut)  
    {  
        if (m_adorned == false)  
        {  
            char typedChar = char.MinValue;  
  
            if (pguidCmdGroup == VSConstants.VSStd2K && nCmdID == (uint)VSConstants.VSStd2KCmdID.TYPECHAR)  
            {  
                typedChar = (char)(ushort)Marshal.GetObjectForNativeVariant(pvaIn);  
                if (typedChar.Equals('+'))  
                {  
                    new PurpleCornerBox(m_textView);  
                    m_adorned = true;  
                }  
            }  
        }  
        return m_nextTarget.Exec(ref pguidCmdGroup, nCmdID, nCmdexecopt, pvaIn, pvaOut);  
    }  
  
    ```  
  
## <a name="adding-the-command-filter"></a>명령 필터를 추가합니다.  
 Adornment 공급자 명령 필터 텍스트 보기에 추가 해야 합니다. 이 예제에서는 공급자 구현 <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> 텍스트 뷰 생성 이벤트를 수신 대기 하도록 합니다. 또한이 adornment 공급자 장식의 Z 순서를 정의 하는 장식 계층을 내보냅니다.  
  
1. KeyBindingTestTextViewCreationListener 파일에 다음 추가 문을 사용 하 여:  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.OLE.Interop;  
    using Microsoft.VisualStudio.Utilities;  
    using Microsoft.VisualStudio.Editor;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.TextManager.Interop;  
  
    ```  
  
2. Adornment 계층 정의에서 AdornmentLayer의 이름을 변경할 **KeyBindingTest** 하 **PurpleCornerBox**합니다.  
  
    ```csharp  
    [Export(typeof(AdornmentLayerDefinition))]  
    [Name("PurpleCornerBox")]  
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
    public AdornmentLayerDefinition editorAdornmentLayer;  
    ```  
  
3. 텍스트 뷰 어댑터를 가져오려면 가져와야는 <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>합니다.  
  
    ```csharp  
    [Import(typeof(IVsEditorAdaptersFactoryService))]  
    internal IVsEditorAdaptersFactoryService editorFactory = null;  
  
    ```  
  
4. 변경 된 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> 메서드를 추가 하도록는 `KeyBindingCommandFilter`합니다.  
  
    ```csharp  
    public void TextViewCreated(IWpfTextView textView)  
    {  
        AddCommandFilter(textView, new KeyBindingCommandFilter(textView));  
    }  
    ```  
  
5. `AddCommandFilter` 처리기가 텍스트 뷰 어댑터를 가져와 명령 필터를 추가 합니다.  
  
    ```csharp  
    void AddCommandFilter(IWpfTextView textView, KeyBindingCommandFilter commandFilter)  
    {  
        if (commandFilter.m_added == false)  
        {  
            //get the view adapter from the editor factory  
            IOleCommandTarget next;   
            IVsTextView view = editorFactory.GetViewAdapter(textView);  
  
            int hr = view.AddCommandFilter(commandFilter, out next);  
  
            if (hr == VSConstants.S_OK)  
            {      
                commandFilter.m_added = true;  
                 //you'll need the next target for Exec and QueryStatus   
                if (next != null)  
                commandFilter.m_nextTarget = next;  
            }  
        }  
    }  
    ```  
  
## <a name="making-the-adornment-appear-on-every-line"></a>장식 만드는 모든 줄에 표시  
 모든 문자에 표시 되는 원래 장식 텍스트 파일에 ' a'입니다. 장식 줄에만 추가 장식 '+' 문자에 대 한 응답에 추가 하는 코드를 변경 했습니다 했으므로 여기서는 '+'를 입력 합니다. 한 번 더 장식에 나타나도록 adornment 코드를 변경할 수 있습니다 모든 'a'입니다.  
  
 KeyBindingTest.cs 파일에서 'a' 문자를 데코 레이트 하는 뷰에서 모든 줄을 반복 하 CreateVisuals() 방법을 변경 합니다.  
  
```csharp  
private void CreateVisuals(ITextViewLine line)  
{  
    IWpfTextViewLineCollection textViewLines = this.view.TextViewLines;  
  
    foreach (ITextViewLine textViewLine in textViewLines)  
    {  
        if (textViewLine.ToString().Contains("a"))  
        {  
            // Loop through each character, and place a box around any 'a'   
            for (int charIndex = textViewLine.Start; charIndex < textViewLine.End; charIndex++)  
            {  
                if (this.view.TextSnapshot[charIndex] == 'a')  
                {  
                    SnapshotSpan span = new SnapshotSpan(this.view.TextSnapshot, Span.FromBounds(charIndex, charIndex + 1));  
                    Geometry geometry = textViewLines.GetMarkerGeometry(span);  
                    if (geometry != null)  
                    {  
                        var drawing = new GeometryDrawing(this.brush, this.pen, geometry);  
                        drawing.Freeze();  
  
                        var drawingImage = new DrawingImage(drawing);  
                        drawingImage.Freeze();  
  
                        var image = new Image  
                        {  
                            Source = drawingImage,  
                        };  
  
                        // Align the image with the top of the bounds of the text geometry  
                        Canvas.SetLeft(image, geometry.Bounds.Left);  
                        Canvas.SetTop(image, geometry.Bounds.Top);  
  
                        this.layer.AddAdornment(AdornmentPositioningBehavior.TextRelative, span, null, image, null);  
                    }  
                }  
            }  
        }  
    }  
}  
```  
  
## <a name="building-and-testing-the-code"></a>코드 빌드 및 테스트  
  
1. KeyBindingTest 솔루션을 빌드하고 실험적 인스턴스에서 실행 합니다.  
  
2. 텍스트 파일을 열거나 만듭니다. 입력 문자를 포함 하는 몇 가지 단어 'a', 입력 및 + 텍스트 보기에서 아무 곳 이나 합니다.  
  
     자주색 사각형 파일에서 'a' 모든 문자에 표시 됩니다.
