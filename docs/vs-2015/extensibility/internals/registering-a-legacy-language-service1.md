---
title: 레거시 언어 Service1 등록 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], registering
ms.assetid: d33b08af-09e0-4c79-87b2-5536b27fbacf
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9d78050f455e83b43dc114ad80fc084dc5604103
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68188862"
---
# <a name="registering-a-legacy-language-service"></a>레거시 언어 서비스 등록
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

VSPackage에서 제공 되는 언어 서비스에서 관리 되는 패키지 프레임 워크에 MPF (), (참조 [Vspackage](../../extensibility/internals/vspackages.md))으로 등록 됩니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 레지스트리 키 및 항목을 추가 하 여 합니다. 이 등록 프로세스는 부분적으로 설치 하는 동안 및 런타임 시 일부에서 수행 됩니다.  
  
## <a name="register-the-language-service-by-using-attributes"></a>특성을 사용 하 여 언어 서비스 등록  
 언어 서비스를 등록 하는 다음과 같은 특성이 사용 됩니다.  
  
- <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>  
  
- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>  
  
- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute>  
  
- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute>  
  
- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageEditorOptionPageAttribute>  
  
  이러한 특성은 아래에서 설명  
  
### <a name="provideserviceattribute"></a>ProvideServiceAttribute  
 이 특성을 서비스로 언어 서비스를 등록합니다.  
  
### <a name="example"></a>예제  
  
```csharp  
using Microsoft.VisualStudio.Shell;  
  
namespace TestLanguagePackage  
{  
    [ProvideServiceAttribute(typeof(TestLanguageService),  
                             ServiceName = "Test Language Service")]  
  
    public class TestLanguagePackage : Package  
    {  
    }  
}  
```  
  
### <a name="providelanguageserviceattribute"></a>ProvideLanguageServiceAttribute  
 이 특성을 언어 서비스로 특히 언어 서비스를 등록합니다. 언어 서비스를 제공 하는 기능을 지정 하는 옵션을 설정할 수 있습니다. 이 예제에서는 언어 서비스가 제공할 수 있는 옵션의 하위 집합을 보여 줍니다. 언어 서비스 옵션의 전체 집합을 참조 하세요. <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>합니다.  
  
### <a name="example"></a>예제  
  
```csharp  
using Microsoft.VisualStudio.Shell;  
  
namespace TestLanguagePackage  
{  
    [ProvideLanguageServiceAttribute(typeof(TestLanguageService),  
                             "Test Language",  
                             106,             // resource ID of localized language name  
                             CodeSense = true,             // Supports IntelliSense  
                             RequestStockColors = false,   // Supplies custom colors  
                             EnableCommenting = true,      // Supports commenting out code  
                             EnableAsyncCompletion = true  // Supports background parsing  
                             )]  
  
    public class TestLanguagePackage : Package  
    {  
    }  
}  
```  
  
### <a name="providelanguageextensionattribute"></a>ProvideLanguageExtensionAttribute  
 이 특성 파일 확장명이 언어 서비스를 연결합니다. 모든 프로젝트에서 해당 확장을 사용 하 여 파일을 로드 될 때마다 언어 서비스가 시작 되 고 파일의 내용을 표시 하는 데 사용 합니다.  
  
### <a name="example"></a>예제  
  
```csharp  
using Microsoft.VisualStudio.Shell;  
  
namespace TestLanguagePackage  
{  
    [ProvideLanguageExtensionAttribute(typeof(TestLanguageService),  
                                       ".Testext")]  
  
    public class TestLanguagePackage : Package  
    {  
    }  
}  
```  
  
### <a name="providelanguagecodeexpansionattribute"></a>ProvideLanguageCodeExpansionAttribute  
 이 특성 확장 또는 코드 조각 템플릿 코드에서 가져온 위치에 등록 합니다. 이 정보를 사용 합니다 **코드 조각을 브라우저** 및 소스 파일에 코드 조각을 삽입할 때 편집기에서.  
  
### <a name="example"></a>예제  
  
```csharp  
using Microsoft.VisualStudio.Shell;  
  
namespace TestLanguagePackage  
{  
    [ProvideLanguageCodeExpansionAttribute(  
             typeof(TestLanguageService),  
             "Test Language", // Name of language used as registry key.  
             106,           // Resource ID of localized name of language service.  
             "testlanguage",  // language key used in snippet templates.  
             @"%InstallRoot%\Test Language\SnippetsIndex.xml",  // Path to snippets index  
             SearchPaths = @"%InstallRoot%\Test Language\Snippets\%LCID%\Snippets\;" +  
                           @"%TestDocs%\Code Snippets\Test Language\Test Code Snippets"  
             )]  
  
    public class TestLanguagePackage : Package  
    {  
    }  
}  
```  
  
### <a name="providelanguageeditoroptionpageattribute"></a>ProvideLanguageEditorOptionPageAttribute  
 이 특성에 표시 되는 속성 페이지를 등록 합니다 **옵션** 대화 상자의 합니다 **텍스트 편집기** 범주입니다. 각 페이지에 대 한 이러한 특성 중 하나를 사용 하 여 언어 서비스에 대해 표시할 수 있습니다. 트리 구조에서 페이지를 구성 해야 할 경우 트리의 각 노드를 정의 하려면 추가 특성을 사용 합니다.  
  
### <a name="example"></a>예제  
 이 예제에서는 두 개의 속성 페이지를 보여 줍니다 **옵션** 하 고 **Indenting**, 및 두 번째 속성 페이지를 포함 하는 하나의 노드.  
  
```csharp  
using Microsoft.VisualStudio.Shell;  
  
namespace TestLanguagePackage  
{  
    [ProvideLanguageEditorOptionPageAttribute(  
             "Test Language",  // Registry key name for language  
             "Options",      // Registry key name for property page  
             "#242",         // Localized name of property page  
             OptionPageGuid = "{A2FE74E1-FFFF-3311-4342-123052450768}"  // GUID of property page  
             )]  
    [ProvideLanguageEditorOptionPageAttribute(  
             "Test Language",  // Registry key name for language  
             "Advanced",     // Registry key name for node  
             "#243",         // Localized name of node  
             )]  
    [ProvideLanguageEditorOptionPageAttribute(  
             "Test Language",  // Registry key name for language  
             @"Advanced\Indenting",     // Registry key name for property page  
             "#244",         // Localized name of property page  
             OptionPageGuid = "{A2FE74E2-FFFF-3311-4342-123052450768}"  // GUID of property page  
             )]  
  
    public class TestLanguagePackage : Package  
    {  
    }  
}  
```  
  
## <a name="proffer-the-language-service-at-runtime"></a>런타임 시 언어 서비스를 제공 합니다.  
 알려야 언어 패키지 로드 되 면 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 언어 서비스를 준비 합니다. 서비스 proffering 하 여이 작업을 수행 합니다. 이 수행 된 <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> 메서드. 또한 백그라운드 구문 분석을 수행할 수 있습니다 있도록 유휴 기간 동안 언어 서비스를 호출 하는 타이머를 시작 해야 합니다. 이 유휴 타이머가 또한 문서 속성을 통해 모든 구현한 경우 업데이트 된 <xref:Microsoft.VisualStudio.Package.DocumentProperties> 클래스입니다. 타이머를 지원 하기 위해 패키지를 구현 해야 합니다는 <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponent> 인터페이스 (만 <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponent.FDoIdle%2A> 완벽 하 게 구현 해야 하는 메서드, 나머지 메서드는 기본 값을 반환할 수 있습니다).  
  
### <a name="example"></a>예제  
 이 예제에서는 서비스 proffering 유휴 타이머가 제공 하는 일반적인 방법을 보여 줍니다.  
  
```csharp  
  
using System;  
using System.Runtime.InteropServices;  
using System.ComponentModel.Design;  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.Shell;  
using Microsoft.VisualStudio.OLE.Interop;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    [Microsoft.VisualStudio.Shell.ProvideService(typeof(TestLanguageService))]  
    [Microsoft.VisualStudio.Shell.ProvideLanguageExtension(typeof(TestLanguageService), ".testext")]  
    [Microsoft.VisualStudio.Shell.ProvideLanguageService(typeof(TestLanguageService), "Test Language", 0,  
        AutoOutlining = true,  
        EnableCommenting = true,  
        MatchBraces = true,  
        ShowMatchingBrace = true)]  
    [Guid("00000000-0000-0000-0000-00000000000")] //provide a unique GUID for the package  
  
    public class TestLanguagePackage : Package, IOleComponent  
    {  
        private uint m_componentID;  
  
        protected override void Initialize()  
        {  
            base.Initialize();  // required  
  
            // Proffer the service.  
            IServiceContainer serviceContainer = this as IServiceContainer;  
            TestLanguageService langService      = new TestLanguageService();  
            langService.SetSite(this);  
            serviceContainer.AddService(typeof(TestLanguageService),  
                                        langService,  
                                        true);  
  
            // Register a timer to call our language service during  
            // idle periods.  
            IOleComponentManager mgr = GetService(typeof(SOleComponentManager))  
                                       as IOleComponentManager;  
            if (m_componentID == 0 && mgr != null)  
            {  
                OLECRINFO[] crinfo = new OLECRINFO[1];  
                crinfo[0].cbSize            = (uint)Marshal.SizeOf(typeof(OLECRINFO));  
                crinfo[0].grfcrf            = (uint)_OLECRF.olecrfNeedIdleTime |  
                                              (uint)_OLECRF.olecrfNeedPeriodicIdleTime;  
                crinfo[0].grfcadvf          = (uint)_OLECADVF.olecadvfModal     |  
                                              (uint)_OLECADVF.olecadvfRedrawOff |  
                                              (uint)_OLECADVF.olecadvfWarningsOff;  
                crinfo[0].uIdleTimeInterval = 1000;  
                int hr = mgr.FRegisterComponent(this, crinfo, out m_componentID);  
            }  
        }  
  
        protected override void Dispose(bool disposing)  
        {  
            if (m_componentID != 0)  
            {  
                IOleComponentManager mgr = GetService(typeof(SOleComponentManager))  
                                           as IOleComponentManager;  
                if (mgr != null)  
                {  
                    int hr = mgr.FRevokeComponent(m_componentID);  
                }  
                m_componentID = 0;  
            }  
  
            base.Dispose(disposing);  
        }  
  
        #region IOleComponent Members  
  
        public int FDoIdle(uint grfidlef)  
        {  
            bool bPeriodic = (grfidlef & (uint)_OLEIDLEF.oleidlefPeriodic) != 0;  
            // Use typeof(TestLanguageService) because we need to  
            // reference the GUID for our language service.  
            LanguageService service = GetService(typeof(TestLanguageService))  
                                      as LanguageService;  
            if (service != null)  
            {  
                service.OnIdle(bPeriodic);  
            }  
            return 0;  
        }  
  
        public int FContinueMessageLoop(uint uReason,  
                                        IntPtr pvLoopData,  
                                        MSG[] pMsgPeeked)  
        {  
            return 1;  
        }  
  
        public int FPreTranslateMessage(MSG[] pMsg)  
        {  
            return 0;  
        }  
  
        public int FQueryTerminate(int fPromptUser)  
        {  
            return 1;  
        }  
  
        public int FReserved1(uint dwReserved,  
                              uint message,  
                              IntPtr wParam,  
                              IntPtr lParam)  
        {  
            return 1;  
        }  
  
        public IntPtr HwndGetWindow(uint dwWhich, uint dwReserved)  
        {  
            return IntPtr.Zero;  
        }  
  
        public void OnActivationChange(IOleComponent pic,  
                                       int fSameComponent,  
                                       OLECRINFO[] pcrinfo,  
                                       int fHostIsActivating,  
                                       OLECHOSTINFO[] pchostinfo,  
                                       uint dwReserved)  
        {  
        }  
  
        public void OnAppActivate(int fActive, uint dwOtherThreadID)  
        {  
        }  
  
        public void OnEnterState(uint uStateID, int fEnter)  
        {  
        }  
  
        public void OnLoseActivation()  
        {  
        }  
  
        public void Terminate()  
        {  
        }  
  
        #endregion  
    }  
}   
```
