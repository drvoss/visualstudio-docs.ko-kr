---
title: 편집기 확장에서 DTE 개체에 액세스 합니다.
ms.date: 04/24/2019
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d023359412b423c9c12d7c7d8a37e79571cbc11a
ms.sourcegitcommit: e3c3d2b185b689c5e32ab4e595abc1ac60b6b9a8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/18/2020
ms.locfileid: "76269082"
---
# <a name="walkthrough-access-the-dte-object-from-an-editor-extension"></a>연습: 편집기 확장에서 DTE 개체에 액세스

Vspackage에서 DTE 개체의 형식을 사용 하 여 <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> 메서드를 호출 하 여 DTE 개체를 가져올 수 있습니다. MEF (Managed Extensibility Framework) 확장에서 <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> 가져온 다음 <xref:EnvDTE.DTE>형식의 <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> 메서드를 호출할 수 있습니다.

## <a name="prerequisites"></a>전제 조건

이 연습을 수행하려면 Visual Studio SDK를 설치해야 합니다. 자세한 내용은 [Visual STUDIO SDK](../extensibility/visual-studio-sdk.md)를 참조 하세요.

## <a name="get-the-dte-object"></a>DTE 개체 가져오기

1. VSIX 프로젝트 C# 를 만들고 이름을 **DTETest**로 만듭니다. **편집기 분류자** 항목 템플릿을 추가 하 고 이름을 **DTETest**로 추가 합니다.

   자세한 내용은 [편집기 항목 템플릿을 사용 하 여 확장 만들기](../extensibility/creating-an-extension-with-an-editor-item-template.md)를 참조 하세요.

::: moniker range=">=vs-2019"

2. 프로젝트에 다음 어셈블리 참조를 추가 합니다.

    - Microsoft.VisualStudio.Shell.Framework
    - Microsoft.VisualStudio.Shell.Immutable.10.0

3. *DTETestProvider.cs* 파일에서 다음 `using` 지시문을 추가 합니다.

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. `DTETestProvider` 클래스에서 <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>를 가져옵니다.

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. `GetClassifier()` 메서드에서 `return` 문 앞에 다음 코드를 추가 합니다.

    ```csharp
   ThreadHelper.ThrowIfNotOnUIThread();
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

::: moniker range="vs-2017"

2. 프로젝트에 다음 어셈블리 참조를 추가 합니다.

   - EnvDTE
   - Microsoft.VisualStudio.Shell.Framework

3. *DTETestProvider.cs* 파일에서 다음 `using` 지시문을 추가 합니다.

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. `DTETestProvider` 클래스에서 <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>를 가져옵니다.

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. `GetClassifier()` 메서드에서 `return` 문 앞에 다음 코드를 추가 합니다.

    ```csharp
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

## <a name="see-also"></a>참조

- [언어 서비스 및 편집기 확장 위치](../extensibility/language-service-and-editor-extension-points.md)
- [DTE를 사용 하 여 Visual Studio 시작](launch-visual-studio-dte.md)
