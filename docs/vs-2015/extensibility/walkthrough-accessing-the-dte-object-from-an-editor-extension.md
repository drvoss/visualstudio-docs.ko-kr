---
title: '연습: 편집기 확장에서 DTE 개체 액세스 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4b14b59465b94ddd0a09748f0e309166bf3d4114
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68148884"
---
# <a name="walkthrough-accessing-the-dte-object-from-an-editor-extension"></a>연습: 편집기 확장에서 DTE 개체 액세스
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vspackage에서 DTE 개체를 호출 하 여 가져올 수 있습니다는 <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> DTE 개체의 유형과 메서드. Framework MEF (Managed Extensibility) 확장을 가져올 수 있습니다 <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> 호출을 <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> 형식의 메서드 <xref:EnvDTE.DTE>합니다.  
  
## <a name="prerequisites"></a>필수 구성 요소  
 이 연습을 수행하려면 Visual Studio SDK를 설치해야 합니다. 자세한 내용은 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)합니다.  
  
## <a name="getting-the-dte-object"></a>DTE 개체를 가져오는 중  
  
#### <a name="to-get-the-dte-object-from-the-serviceprovider"></a>ServiceProvider에서 DTE 개체를 가져와  
  
1. 라는 C# VSIX 프로젝트를 만듭니다 `DTETest`합니다. 편집기 분류자 항목 템플릿을 추가 하 고 이름을 `DTETest`입니다. 자세한 내용은 [편집기 항목 템플릿을 사용 하 여 확장을 만드는](../extensibility/creating-an-extension-with-an-editor-item-template.md)합니다.  
  
2. 프로젝트에 다음 어셈블리 참조를 추가 합니다.  
  
    - EnvDTE  
  
    - EnvDTE80  
  
    - Microsoft.VisualStudio.Shell.Immutable.10.0  
  
3. DTETest.cs 파일로 이동한 다음 추가 `using` 지시문:  
  
    ```csharp  
    using EnvDTE;  
    using EnvDTE80;  
    using Microsoft.VisualStudio.Shell;  
  
    ```  
  
4. 에 `GetDTEProvider` 클래스, 가져오기는 <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>합니다.  
  
    ```csharp  
    [Import]  
    internal SVsServiceProvider ServiceProvider = null;  
  
    ```  
  
5. `GetClassifier()` 메서드에 다음 코드를 추가합니다.  
  
    ```csharp  
    DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));  
  
    ```  
  
6. 사용 해야 하는 경우는 <xref:EnvDTE80.DTE2> 인터페이스를 DTE 개체를 캐스팅할 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [언어 서비스 및 편집기 확장 지점](../extensibility/language-service-and-editor-extension-points.md)
