---
title: 편집기 확장에서 DTE 개체 액세스
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
ms.openlocfilehash: 1fb22793c3bfa805fae11c8bbea7f07c06fd5a85
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322785"
---
# <a name="walkthrough-access-the-dte-object-from-an-editor-extension"></a>연습: 편집기 확장에서 DTE 개체 액세스

Vspackage에서 DTE 개체를 호출 하 여 가져올 수 있습니다는 <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> DTE 개체의 유형과 메서드. Framework MEF (Managed Extensibility) 확장을 가져올 수 있습니다 <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> 호출을 <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> 형식의 메서드 <xref:EnvDTE.DTE>합니다.

## <a name="prerequisites"></a>전제 조건

이 연습을 수행하려면 Visual Studio SDK를 설치해야 합니다. 자세한 내용은 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)합니다.

## <a name="get-the-dte-object"></a>DTE 개체를 가져옵니다

1. 만들기는 C# VSIX 프로젝트 하 고 이름을 **DTETest**합니다. 추가 된 **편집기 분류자** 항목 템플릿 하 고 이름을 **DTETest**합니다.

   자세한 내용은 [편집기 항목 템플릿을 사용 하 여 확장 프로그램을 만들려면](../extensibility/creating-an-extension-with-an-editor-item-template.md)합니다.

::: moniker range=">=vs-2019"

2. 프로젝트에는 다음 어셈블리 참조를 추가 합니다.

    - Microsoft.VisualStudio.Shell.Immutable.10.0

3. 에 *DTETestProvider.cs* 파일을 다음 추가 `using` 지시문:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. 에 `DTETestProvider` 클래스, 가져오기는 <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>합니다.

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. 에 `GetClassifier()` 메서드를 앞에 다음 코드를 추가 합니다 `return` 문:

    ```csharp
   ThreadHelper.ThrowIfNotOnUIThread();
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

::: moniker range="vs-2017"

2. 프로젝트에 다음 어셈블리 참조를 추가 합니다.

   - EnvDTE
   - Microsoft.VisualStudio.Shell.Framework

3. 에 *DTETestProvider.cs* 파일을 다음 추가 `using` 지시문:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. 에 `DTETestProvider` 클래스, 가져오기는 <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>합니다.

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. 에 `GetClassifier()` 메서드를 앞에 다음 코드를 추가 합니다 `return` 문:

    ```csharp
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

## <a name="see-also"></a>참고자료

- [언어 서비스 및 편집기 확장 지점](../extensibility/language-service-and-editor-extension-points.md)
- [DTE를 사용 하 여 Visual Studio를 시작 합니다.](launch-visual-studio-dte.md)