---
title: 다중 인스턴스 도구 창 만들기 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- multi
- tool windows
ms.assetid: 4a7872f1-acc9-4f43-8932-5a526b36adea
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a9c31f1c439db69b3795d789758b0604a539ef81
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66341622"
---
# <a name="create-a-multi-instance-tool-window"></a>다중 인스턴스 도구 창을 만들려면
여러 인스턴스가 동시에 열릴 수 있도록 도구 창을 프로그래밍할 수 있습니다. 기본적으로 도구 창을 열고 하나의 인스턴스만을 가질 수 있습니다.

다중 인스턴스 도구 창을 사용 하는 경우에 몇 가지 관련된 정보 소스를 동시에 표시할 수 있습니다. 예를 들어, 여러 줄에 배치할 수 있습니다 <xref:System.Windows.Forms.TextBox> 프로그래밍 세션 중 몇 가지 코드 조각을 동시에 사용할 수 있도록 다중 인스턴스 도구 창에서 제어 합니다. 또한 예를 들어 배치할 수 있습니다는 <xref:System.Windows.Forms.DataGrid> 컨트롤 및 드롭다운 목록 상자에 다중 인스턴스 도구 창 여러 실시간 데이터 소스를 동시에 추적할 수 있도록 합니다.

## <a name="create-a-basic-single-instance-tool-window"></a>기본 (인스턴스) 도구 창을 만듭니다.

1. 라는 프로젝트를 만듭니다 **MultiInstanceToolWindow** 라는 사용자 지정 도구 창 항목 템플릿을 VSIX 템플릿을 사용 하 여 추가한 **MIToolWindow**합니다.

    > [!NOTE]
    > 도구 창을 사용 하 여 확장을 만드는 방법에 대 한 자세한 내용은 참조 하세요. [도구 창으로 확장 프로그램을 만들려면](../extensibility/creating-an-extension-with-a-tool-window.md)합니다.

## <a name="make-a-tool-window-multi-instance"></a>다중 인스턴스 도구 창 확인

1. 엽니다는 *MIToolWindowPackage.cs* 파일을 찾을 `ProvideToolWindow` 특성입니다. 및 `MultiInstances=true` 다음 예와에서 같이 매개 변수:

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
        [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About
        [ProvideMenuResource("Menus.ctmenu", 1)]
        [ProvideToolWindow(typeof(MultiInstanceToolWindow.MIToolWindow), MultiInstances = true)]
        [Guid(MIToolWindowPackage.PackageGuidString)]
        public sealed class MIToolWindowPackage : Package
    {. . .}
    ```

2. 에 *MIToolWindowCommand.cs* 파일에서 찾기는 `ShowToolWindos()` 메서드. 이 메서드를 호출 합니다 <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> 메서드 집합과 해당 `create` 플래그를 `false` 일까 지 사용할 수 있는 기존 도구 창의 인스턴스를 통해 반복 됩니다 있도록 `id` 가 합니다.

3. 도구 창의 인스턴스를 만들려면 다음을 호출 합니다 <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> 메서드 집합과 해당 `id` 사용 가능한 값 및 해당 `create` 플래그를 `true`.

    기본적으로 값을 `id` 의 매개 변수를 <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> 메서드는 `0`합니다. 이 값은 단일 인스턴스 도구 창입니다. 호스팅 되도록 둘 이상의 인스턴스에 대 한 모든 인스턴스는 자체 고유 있어야 `id`합니다.

4. 호출를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> 메서드를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> 에서 반환 되는 개체는 <xref:Microsoft.VisualStudio.Shell.ToolWindowPane.Frame%2A> 도구 창 인스턴스의 속성입니다.

5. 기본적으로 `ShowToolWindow` 도구 창 항목 템플릿에 의해 생성 되는 메서드는 단일 인스턴스 도구 창을 만듭니다. 다음 예제에서는 수정 하는 방법의 `ShowToolWindow` 여러 인스턴스를 만드는 방법.

    ```csharp
    private void ShowToolWindow(object sender, EventArgs e)
    {
        for (int i = 0; i < 10; i++)
        {
            ToolWindowPane window = this.package.FindToolWindow(typeof(MIToolWindow), i, false);
            if (window == null)
            {
                // Create the window with the first free ID.
                window = (ToolWindowPane)this.package.FindToolWindow(typeof(MIToolWindow), i, true);
                if ((null == window) || (null == window.Frame))
                {
                    throw new NotSupportedException("Cannot create tool window");
                }

            IVsWindowFrame windowFrame = (IVsWindowFrame)window.Frame;
            Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(windowFrame.Show());
            break;
            }
        }
    }
    ```
