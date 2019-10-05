---
title: '연습: 핵심 편집기 만들기 및 등록 하는 편집기 파일 형식 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - walkthrough
ms.assetid: 24d2bffd-a35c-46db-8515-fd60b884b7fb
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 14296aa335ba6710d4d9eac8e5338af7463c0aac
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65687642"
---
# <a name="walkthrough-creating-a-core-editor-and-registering-an-editor-file-type"></a>연습: 핵심 편집기 만들기 및 등록 하는 편집기 파일 형식
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 연습에는 시작 하는 VSPackage를 만드는 방법을 보여 줍니다는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .myext 파일 이름 확장명을 가진 파일의 핵심 편집기가 로드 됩니다.  
  
## <a name="prerequisites"></a>전제 조건  
 이 연습을 수행하려면 Visual Studio SDK를 설치해야 합니다. 자세한 내용은 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)합니다.  
  
## <a name="locations-for-the-visual-studio-package-project-template"></a>Visual Studio 패키지 프로젝트 템플릿 위치  
 Visual Studio 패키지 프로젝트 템플릿은 **새 프로젝트** 대화 상자의 세 가지 서로 다른 위치에 있습니다.  
  
1. Visual Basic 확장성에 위치한 템플릿 프로젝트의 기본 언어는 Visual Basic입니다.  
  
2. C# 확장성에 위치한 템플릿 프로젝트의 기본 언어는 C#입니다.  
  
3. 다른 프로젝트 형식 확장성에 위치한 템플릿 프로젝트의 기본 언어는 C++입니다.  
  
### <a name="to-create-the-vspackage"></a>VSPackage를 만들려면  
  
- 시작 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 만들고는 [!INCLUDE[csprcs](../includes/csprcs-md.md)] 라는 VSPackage `MyPackage`에 설명 된 대로, [연습: 메뉴 명령 VSPackage를 만드는](https://msdn.microsoft.com/d699c149-5d1e-47ff-94c7-e1222af02c32)합니다.  
  
### <a name="to-add-the-editor-factory"></a>편집기 팩터리를 추가 하려면  
  
1. 마우스 오른쪽 단추로 클릭 합니다 **MyPackage** 프로젝트를 가리키도록 **추가** 을 클릭 한 다음 **클래스**.  
  
2. 에 **새 항목 추가** 대화 상자를 **클래스** 서식 파일을 선택 하면 형식 `EditorFactory.cs` 클릭 한 다음 확인 하 고 이름에 대 한 **추가** 프로젝트에 클래스를 추가 하려면.  
  
     EditorFactory.cs 파일을 자동으로 열 수 있습니다.  
  
3. 코드에서 다음 어셈블리를 참조 합니다.  
  
    ```vb  
    Imports System.Runtime.InteropServices  
    Imports Microsoft.VisualStudio  
    Imports Microsoft.VisualStudio.Shell  
    Imports Microsoft.VisualStudio.Shell.Interop  
    Imports Microsoft.VisualStudio.OLE.Interop  
    Imports Microsoft.VisualStudio.TextManager.Interop  
    Imports IOleServiceProvider = Microsoft.VisualStudio.OLE.Interop.IServiceProvider  
    ```  
  
    ```csharp  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.Shell.Interop;  
    using Microsoft.VisualStudio.OLE.Interop;  
    using Microsoft.VisualStudio.TextManager.Interop;  
    using IOleServiceProvider = Microsoft.VisualStudio.OLE.Interop.IServiceProvider;  
  
    ```  
  
4. GUID를 추가 합니다 `EditorFactory` 클래스를 추가 하 여는 `Guid` 특성 클래스 선언 바로 앞입니다.  
  
     Guidgen.exe 프로그램에 사용 하 여 새 GUID를 생성할 수 있습니다 합니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 명령 프롬프트를 또는 클릭 하 여 **GUID 만들기** 에 **도구** 메뉴. 여기에 사용 하는 GUID은 예 시일 뿐임; 프로젝트에서 사용 하지 마세요.  
  
    ```vb  
    <Guid("0eea3187-c5fa-48d4-aa72-b5eecd3b17b1")> _  
    ```  
  
    ```csharp  
    [Guid("0eea3187-c5fa-48d4-aa72-b5eecd3b17b1")]   
    ```  
  
5. 클래스 정의에서 부모 패키지 및 서비스 공급자를 포함 하는 두 전용 변수를 추가 합니다.  
  
    ```vb  
    Class EditorFactory  
        Private parentPackage As Package  
        Private serviceProvider As IOleServiceProvider  
    ```  
  
    ```csharp  
    class EditorFactory  
    {  
        private Package parentPackage;  
        private IOleServiceProvider serviceProvider;  
    }  
  
    ```  
  
6. 형식의 매개 변수 하나를 사용 하는 공용 클래스 생성자를 추가 <xref:Microsoft.VisualStudio.Shell.Package>:  
  
    ```vb  
    Public Sub New(ByVal parentPackage As Package)  
        Me.parentPackage = parentPackage  
    End Sub  
    ```  
  
    ```csharp  
    public EditorFactory(Package parentPackage)  
    {  
        this.parentPackage = parentPackage;  
    }  
    ```  
  
7. 수정 된 `EditorFactory` 클래스에서 파생 하는 선언을 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> 인터페이스입니다.  
  
    ```vb  
    Class EditorFactory Implements IVsEditorFacto  
    ```  
  
    ```csharp  
    class EditorFactory : IVsEditorFactory  
  
    ```  
  
8. 마우스 오른쪽 단추로 클릭 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>, 클릭 **인터페이스 구현**를 클릭 하 고 **명시적으로 인터페이스 구현**합니다.  
  
     구현 해야 하는 4 개의 메서드를 추가 하는이 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> 인터페이스입니다.  
  
9. `IVsEditorFactory.Close` 메서드의 내용을 다음 코드로 대체합니다.  
  
    ```vb  
    Return VSConstants.S_OK  
    ```  
  
    ```csharp  
    return VSConstants.S_OK;  
    ```  
  
10. 내용을 바꿉니다는 `IVsEditorFactory.SetSite` 다음 코드를 사용 합니다.  
  
    ```vb  
    Me.serviceProvider = psp  
    Return VSConstants.S_OK  
    ```  
  
    ```csharp  
    this.serviceProvider = psp;  
    return VSConstants.S_OK;  
    ```  
  
11. `IVsEditorFactory.MapLogicalView` 메서드의 내용을 다음 코드로 대체합니다.  
  
    ```vb  
    Dim retval As Integer = VSConstants.E_NOTIMPL  
    pbstrPhysicalView = Nothing ' We support only one view.  
    If rguidLogicalView.Equals(VSConstants.LOGVIEWID_Designer)OrElse _  
    rguidLogicalView.Equals(VSConstants.LOGVIEWID_Primary) Then  
        retval = VSConstants.S_OK  
    End If  
    Return retval  
    ```  
  
    ```csharp  
    int retval = VSConstants.E_NOTIMPL;  
    pbstrPhysicalView = null;   // We support only one view.  
    if (rguidLogicalView.Equals(VSConstants.LOGVIEWID_Designer) ||  
    rguidLogicalView.Equals(VSConstants.LOGVIEWID_Primary))  
    {  
        retval = VSConstants.S_OK;  
    }  
    return retval;  
    ```  
  
12. `IVsEditorFactory.CreateEditorInstance` 메서드의 내용을 다음 코드로 대체합니다.  
  
    ```vb  
    Dim retval As Integer = VSConstants.E_FAIL          
  
    ' Initialize these to empty to start with   
    ppunkDocView = IntPtr.Zero  
    ppunkDocData = IntPtr.Zero  
    pbstrEditorCaption = ""  
    pguidCmdUI = Guid.Empty  
    pgrfCDW = 0  
  
    If (grfCreateDoc And (VSConstants.CEF_OPENFILE Or _  
    VSConstants.CEF_SILENT)) = 0 Then  
        Throw New ArgumentException("Only Open or Silent is valid")  
    End If  
    If punkDocDataExisting <> IntPtr.Zero Then  
        Return VSConstants.VS_E_INCOMPATIBLEDOCDATA  
    End If  
  
    ' Instantiate a text buffer of type VsTextBuffer.   
    ' Note: we only need an IUnknown (object) interface for   
    ' this invocation.   
    Dim clsidTextBuffer As Guid = GetType(VsTextBufferClass).GUID  
    Dim iidTextBuffer As Guid = VSConstants.IID_IUnknown  
    Dim pTextBuffer As Object = pTextBuffer = _  
    parentPackage.CreateInstance(clsidTextBuffer, iidTextBuffer, _  
    GetType(Object))  
  
    If Not pTextBuffer Is Nothing Then  
        ' "Site" the text buffer with the service provider we were   
        ' provided.   
        Dim textBufferSite As IObjectWithSite = TryCast(pTextBuffer, _  
        IObjectWithSite)  
        If Not textBufferSite Is Nothing Then  
            textBufferSite.SetSite(Me.serviceProvider)  
        End If  
  
        ' Instantiate a code window of type IVsCodeWindow.   
        Dim clsidCodeWindow As Guid = GetType(VsCodeWindowClass).GUID  
        Dim iidCodeWindow As Guid = GetType(IVsCodeWindow).GUID  
        Dim pCodeWindow As IVsCodeWindow = _  
        CType(Me.parentPackage.CreateInstance(clsidCodeWindow, _  
        iidCodeWindow, GetType(IVsCodeWindow)), IVsCodeWindow)  
        If Not pCodeWindow Is Nothing Then  
            ' Give the text buffer to the code window.   
            ' We are giving up ownership of the text buffer!   
            pCodeWindow.SetBuffer(CType(pTextBuffer, IVsTextLines))  
  
            ' Now tell the caller about all this new stuff   
            ' that has been created.   
            ppunkDocView = Marshal.GetIUnknownForObject(pCodeWindow)  
            ppunkDocData = Marshal.GetIUnknownForObject(pTextBuffer)  
  
            ' Specify the command UI to use so keypresses are   
            ' automatically dealt with.   
            pguidCmdUI = VSConstants.GUID_TextEditorFactory  
  
            ' This caption is appended to the filename and   
            ' lets us know our invocation of the core editor   
            ' is up and running.   
            pbstrEditorCaption = " [MyPackage]"  
  
            retval = VSConstants.S_OK  
        End If  
    End If  
    Return retval  
    ```  
  
    ```csharp  
    int retval = VSConstants.E_FAIL;  
  
    // Initialize these to empty to start with  
    ppunkDocView       = IntPtr.Zero;  
    ppunkDocData       = IntPtr.Zero;  
    pbstrEditorCaption = "";  
    pguidCmdUI         = Guid.Empty;   
    pgrfCDW            = 0;  
  
    if ((grfCreateDoc & (VSConstants.CEF_OPENFILE |   
          VSConstants.CEF_SILENT)) == 0)  
    {   
        throw new ArgumentException("Only Open or Silent is valid");  
    }  
    if (punkDocDataExisting != IntPtr.Zero)  
    {  
        return VSConstants.VS_E_INCOMPATIBLEDOCDATA;  
    }  
  
    // Instantiate a text buffer of type VsTextBuffer.  
    // Note: we only need an IUnknown (object) interface for   
    // this invocation.  
    Guid clsidTextBuffer = typeof(VsTextBufferClass).GUID;  
    Guid iidTextBuffer   = VSConstants.IID_IUnknown;  
    object pTextBuffer   = pTextBuffer = parentPackage.CreateInstance(  
          ref clsidTextBuffer,  
          ref iidTextBuffer,  
          typeof(object));  
  
    if (pTextBuffer != null)  
    {  
        // "Site" the text buffer with the service provider we were  
        // provided.  
        IObjectWithSite textBufferSite = pTextBuffer as IObjectWithSite;  
        if (textBufferSite != null)  
        {  
            textBufferSite.SetSite(this.serviceProvider);  
        }  
  
        // Instantiate a code window of type IVsCodeWindow.  
        Guid clsidCodeWindow = typeof(VsCodeWindowClass).GUID;  
        Guid iidCodeWindow   = typeof(IVsCodeWindow).GUID;  
        IVsCodeWindow pCodeWindow =  
        (IVsCodeWindow)this.parentPackage.CreateInstance(   
              ref clsidCodeWindow,  
              ref iidCodeWindow,  
              typeof(IVsCodeWindow));  
        if (pCodeWindow != null)  
        {  
            // Give the text buffer to the code window.  
            // We are giving up ownership of the text buffer!  
            pCodeWindow.SetBuffer((IVsTextLines)pTextBuffer);  
  
            // Now tell the caller about all this new stuff   
            // that has been created.  
            ppunkDocView = Marshal.GetIUnknownForObject(pCodeWindow);  
            ppunkDocData = Marshal.GetIUnknownForObject(pTextBuffer);  
  
            // Specify the command UI to use so keypresses are   
            // automatically dealt with.  
            pguidCmdUI = VSConstants.GUID_TextEditorFactory;  
  
            // This caption is appended to the filename and  
            // lets us know our invocation of the core editor   
            // is up and running.  
            pbstrEditorCaption = " [MyPackage]";  
  
            retval = VSConstants.S_OK;  
        }   
    }   
    return retval;   
    ```  
  
13. 프로젝트를 컴파일하고 오류가 없는지 확인 합니다.  
  
### <a name="to-register-the-editor-factory"></a>편집기 팩터리를 등록 하려면  
  
1. **솔루션 탐색기**에서 Resources.resx 파일을 문자열 테이블에 있는 열을 두 번 클릭 항목 **String1이** 선택한 합니다.  
  
2. 식별자의 이름을 변경할 `IDS_EDITORNAME` 텍스트를 **MyPackage 편집기입니다.** 이 문자열은 편집기의 이름으로 표시 됩니다.  
  
3. VSPackage.resx 파일을 열고 새 문자열을 이름으로 설정할 **101** 값을 `IDS_EDITORNAME`입니다. 방금 만든 문자열에 액세스 하는 리소스 ID를 사용 하 여 패키지를 제공 합니다.  
  
    > [!NOTE]
    > VSPackage.resx 파일에 있는 경우 다른 문자열입니다 합니다 `name` 특성이로 설정 **101**, 여기에 다음 단계를 다른 숫자를 고유한 값을 대체 합니다.  
  
4. **솔루션 탐색기**, MyPackagePackage.cs 파일을 엽니다.  
  
     주 패키지 파일입니다.  
  
5. 바로 앞에 다음 사용자 특성 추가 `Guid` 특성입니다.  
  
    ```vb  
    <ProvideEditorFactoryAttribute(GetType(EditorFactory), 101)> _  
    <ProvideEditorExtensionAttribute(GetType(EditorFactory), _  
          ".myext", 32, NameResourceID:=101 )> _  
    ```  
  
    ```csharp  
    [ProvideEditorFactory(typeof(EditorFactory), 101)]  
    [ProvideEditorExtension(typeof(EditorFactory),   
          ".myext", 32, NameResourceID = 101)]   
    ```  
  
     <xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute> 특성을 언제 든 지 확장 로드 되 면 편집기 팩터리의 호출 되는 파일 편집기 팩터리와.myext 파일 확장명을 연결 합니다.  
  
6. 개인 변수를 추가 합니다 `MyPackage` 생성자 직전 클래스 및 형식 지정 `EditorFactory`합니다.  
  
    ```vb  
    Private editorFactory As EditorFactory  
    ```  
  
    ```csharp  
    private EditorFactory editorFactory;  
    ```  
  
7. 찾을 합니다 `Initialize` 메서드 (열어야 할 수 있습니다 합니다 `Package Members` 숨겨진된 영역) 호출 후 다음 코드를 추가 하 고 `base.Initialize()`.  
  
    ```vb  
    'Create our editor factory and register it.   
    Me.editorFactory = New EditorFactory(Me)  
    MyBase.RegisterEditorFactory(Me.editorFactory)  
    ```  
  
    ```csharp  
    // Create our editor factory and register it.  
    this.editorFactory = new EditorFactory(this);  
    base.RegisterEditorFactory(this.editorFactory);  
  
    ```  
  
8. 프로그램을 컴파일하고 오류가 없는지 확인합니다.  
  
     이 단계에 대 한 실험적 레지스트리 하이브에 편집기 팩터리를 등록 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]합니다. Resource.h 파일을 재정의 하는 메시지가 누릅니다 **확인**합니다.  
  
9. TextFile1.myext 라는 샘플 파일을 만듭니다.  
  
10. 키를 눌러 **F5** 의 실험적 인스턴스를 열려면 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]합니다.  
  
11. 실험적 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]의 **파일** 메뉴에서 **열기** 클릭 하 고 **파일**.  
  
12. TextFile1.myext를 찾은 다음 클릭 **열려**합니다.  
  
     이제 파일을 로드할 수 해야 합니다.  
  
## <a name="robust-programming"></a>강력한 프로그래밍  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 핵심 편집기 다양 한 범위의 텍스트 기반 파일 형식 및 중괄호 일치, 다양 한 구문 강조 표시 하는 등의 기능을 제공 하기 위해 언어 서비스 및 IntelliSense 단어 완성 및 멤버 완성 목록을 긴밀 한 협력을 처리 합니다. 텍스트 기반 파일을 사용 하는 경우 특정 파일 형식을 지 원하는 사용자 지정 언어 서비스와 함께 핵심 편집기를 사용할 수 있습니다.  
  
 VSPackage를 호출할 수는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 편집기 팩터리를 제공 하 여 핵심 편집기입니다. 이 편집기 팩터리와 연결 된 파일을 로드 하 든 지 사용 됩니다. 파일을 프로젝트의 일부 이면 핵심 편집기 VSPackage에 의해 재정의 되지 않는 호출 자동으로 됩니다. 그러나 파일은 프로젝트 외부에서 로드 되 면 다음 핵심 편집기 호출 되어야 합니다 명시적으로 VSPackage에서.  
  
 핵심 편집기에 대 한 자세한 내용은 참조 하세요. [핵심 편집기 내에서](../extensibility/inside-the-core-editor.md)합니다.  
  
## <a name="see-also"></a>참고 항목  
 [핵심 편집기 내에서](../extensibility/inside-the-core-editor.md)   
 [레거시 API를 사용하여 핵심 편집기 인스턴스화](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)
