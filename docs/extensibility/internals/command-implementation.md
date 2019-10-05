---
title: 명령을 구현 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, implementation
ms.assetid: c782175c-cce4-4bd0-8374-4a897ceb1b3d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fbd0a9a1886bc1f8743ac8919bcc9cb39559dd19
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67824935"
---
# <a name="command-implementation"></a>명령 구현
명령에서 VSPackage를 구현 하려면 다음 작업을 수행 해야 합니다.

1. 에 *.vsct* 파일, 명령 그룹을 설정 하 고, 다음에 명령을 추가 합니다. 자세한 내용은 [Visual Studio 명령 테이블 (.vsct) 파일](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)합니다.

2. Visual Studio를 사용 하 여 명령을 등록 합니다.

3. 명령을 구현 합니다.

다음 섹션에서는 등록 명령을 구현 하는 방법을 설명 합니다.

## <a name="register-commands-with-visual-studio"></a>Visual Studio를 사용 하 여 등록 명령
 추가 해야 하는 경우에 명령이 메뉴에 표시 되 면는 <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> VSPackage 및 메뉴의 이름 또는 해당 리소스 id입니다. 값으로 사용 하 여

```
[ProvideMenuResource("Menus.ctmenu", 1)]
...
    public sealed class MyPackage : Package
    {.. ..}

```

 또한 사용 하 여 명령을 등록 해야 합니다는 <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService>합니다. 사용 하 여이 서비스를 가져올 수 있습니다 합니다 <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> VSPackage에서 파생 된 경우 메서드 <xref:Microsoft.VisualStudio.Shell.Package>합니다.

```
OleMenuCommandService mcs = GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
if ( null != mcs )
{
    // Create the command for the menu item.
    CommandID menuCommandID = new CommandID(guidCommandGroup, myCommandID);
    MenuCommand menuItem = new MenuCommand(MenuItemCallback, menuCommandID );
    mcs.AddCommand( menuItem );
}

```

## <a name="implement-commands"></a>명령 구현
 명령을 구현 하는 방법의 여러 가지가 있습니다. 항상 표시 되는 동일한 방식으로 및 동일한 메뉴의 명령을 인 정적 메뉴 명령을 원하는 경우 명령을 사용 하 여 만드는 <xref:System.ComponentModel.Design.MenuCommand> 이전 섹션의 예제에 나와 있는 것 처럼 합니다. 정적 명령을 만들려면 명령을 실행 하는 일을 담당 하는 이벤트 처리기를 제공 해야 합니다. 명령을 사용 하도록 설정 하 고 표시 항상 이기 때문에 Visual Studio에 해당 상태를 제공할 필요가 없습니다. 특정 조건에 따라 명령의 상태를 변경 하려는 경우의 인스턴스로 명령을 만들 수 있습니다 합니다 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> 클래스를 해당 생성자에서 명령을 실행 하는 이벤트 처리기를 제공 및 `QueryStatus` 시각적 개체에 알리기 위해 처리기 명령 상태가 변경 될 때 studio입니다. 구현할 수도 있습니다 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 명령 클래스 또는 부분을 구현 수 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 명령을 프로젝트의 일부로 제공 하는 경우. 두 인터페이스 및 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> 클래스 모든 Visual Studio 명령의 상태 변경을 알리는 메서드를 있고 명령의 실행을 제공 하는 다른 방법입니다.

 명령을 명령 서비스에 추가 되 면 명령 체인 중 하나. 해당 특정 명령에 대해서만 제공 하 고 체인에 있는 다른 명령에 다른 모든 경우를 전달 하는 명령에 대 한 상태 알림 및 실행 메서드를 구현할 때 주의 합니다. 명령 전달할 실패 하는 경우 (일반적으로 반환 하 여 <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>), Visual Studio는 제대로 작동 하지 않을 수 있습니다.

## <a name="querystatus-methods"></a>QueryStatus 메서드
 중 하나를 구현 하는 경우는 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 메서드 또는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> 메서드, 명령 명령을 속한 집합의 GUID 확인 및 명령 ID입니다. 다음 지침을 따릅니다.

- GUID 인식 되지 않으면 경우 두 메서드를 구현할 반환 해야 <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_UNKNOWNGROUP>합니다.

- 메서드는 반환 해야 하거나 메서드를 구현할 GUID를 인식 하지만 명령을 구현 되지 않았습니다 경우 <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>합니다.

- GUID와 명령에서 인식 하는 두 메서드를 구현할 경우 메서드는 모든 명령의 명령 플래그 필드를 설정 해야 (에 `prgCmds` 매개 변수) 다음을 사용 하 여 <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> 플래그:

  - `OLECMDF_SUPPORTED`: 명령이 지원 됩니다.

  - `OLECMDF_INVISIBLE`: 명령을 표시 되어야 합니다.

  - `OLECMDF_LATCHED`: 명령에 설정/해제 하 고 확인 한 후에 나타납니다.

  - `OLECMDF_ENABLED`: 명령이 활성화 됩니다.

  - `OLECMDF_DEFHIDEONCTXTMENU`: 바로 가기 메뉴에 표시 되는 경우 명령을 숨겨야 합니다.

  - `OLECMDF_NINCHED`: 명령 메뉴 컨트롤러가 고을 사용 하지 않는 하지만 해당 드롭다운 메뉴 목록을 비어 있지 않고 계속 사용할 수 있습니다. (이 플래그는 거의 사용 합니다.)

- 명령에 정의 된 경우는 *.vsct* 파일을 `TextChanges` 플래그, 다음 매개 변수 설정:

  - 설정 합니다 `rgwz` 의 요소는 `pCmdText` 명령의 새 텍스트로 매개 변수입니다.

  - 설정 합니다 `cwActual` 의 요소를 `pCmdText` 매개 변수를 명령 문자열의 크기입니다.

또한 해야 현재 컨텍스트에 automation 함수 명령을 자동화 기능을 처리 하기 위한 것 하지 않는 한 합니다.

특정 명령 지을 나타내기 위해 반환 <xref:Microsoft.VisualStudio.VSConstants.S_OK>합니다. 다른 모든 명령에 대 한 반환 <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>합니다.

다음 예제에서는 `QueryStatus` 메서드 먼저를 사용 하면 컨텍스트는 automation 함수가 아닙니다는 다음 찾습니다 올바른 명령 집합 GUID 및 명령 id입니다. 명령 자체는 사용 하도록 설정 하 고 지원 되는 수로 설정 됩니다. 다른 명령은 없으면 지원 됩니다.

```csharp
public int QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)
{
    if (!VsShellUtilities.IsInAutomationFunction(m_provider.ServiceProvider))
    {
        if (pguidCmdGroup == VSConstants.VSStd2K && cCmds > 0)
        {
            // make the Right command visible
            if ((uint)prgCmds[0].cmdID == (uint)VSConstants.VSStd2KCmdID.RIGHT)
            {
                prgCmds[0].cmdf = (int)Microsoft.VisualStudio.OLE.Interop.Constants.MSOCMDF_ENABLED | (int)Microsoft.VisualStudio.OLE.Interop.Constants.MSOCMDF_SUPPORTED;
                return VSConstants.S_OK;
            }
        }
        return Constants.OLECMDERR_E_NOTSUPPORTED;
    }
}
```

## <a name="execution-methods"></a>실행 메서드
 구현의 합니다 `Exec` 메서드가 구현의 유사 합니다 `QueryStatus` 메서드. 먼저, 아닌지 컨텍스트 자동화 기능을 확인 합니다. 그런 다음 테스트 GUID 및 명령 id입니다. 경우 GUID 또는 명령 ID를 인식할 수 없습니다, 반환 <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>합니다.

 를 처리 하기 위해 명령을 실행 하 고 반환 <xref:Microsoft.VisualStudio.VSConstants.S_OK> 실행에 성공 합니다. 명령 담당 오류 검색 및 알림. 따라서 실행이 실패 하는 경우에 오류 코드를 반환 합니다. 다음 예제에서는 실행 메서드를 구현 해야 하는 방법을 보여 줍니다.

```csharp
public int Exec(ref Guid pguidCmdGroup, uint nCmdID, uint nCmdexecopt, IntPtr pvaIn, IntPtr pvaOut)
{
    if (!VsShellUtilities.IsInAutomationFunction(m_provider.ServiceProvider))
    {
        if (pguidCmdGroup == VSConstants.GUID_VSStandardCommandSet97)
        {
             if (nCmdID ==(uint) uint)VSConstants.VSStd2KCmdID.RIGHT)
            {
                //execute the command
                return VSConstants.S_OK;
            }
        }
    }
    return Constants.OLECMDERR_E_NOTSUPPORTED;
}
```

## <a name="see-also"></a>참고자료

- [Vspackage에서 사용자 인터페이스 요소를 추가 하는 방법](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
