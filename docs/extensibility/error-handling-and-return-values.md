---
title: 오류 처리 및 반환 값 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- errors [Visual Studio SDK], handling
- error handling
- return values
ms.assetid: b2d9079d-39a6-438a-8010-290056694b5c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e3120302de007c9d2b454a0ba7cb5c58e7c7db7b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66309888"
---
# <a name="error-handling-and-return-values"></a>오류 처리 및 반환 값
Vspackage 및 COM 오류에 대 한 동일한 아키텍처를 사용 합니다. 합니다 `SetErrorInfo` 및 `GetErrorInfo` 함수는 Win32 API (응용 프로그래밍 인터페이스)의 일부인 합니다. 모든 VSPackage 통합된 개발 환경 (IDE)에서 호출할 수 있습니다 이러한 다양 한 오류 정보를 기록 하려면 전역 Win32 Api는 오류 알림의 받을 때. [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] 오류 정보를 관리 하는 interop 어셈블리를 제공 합니다.

## <a name="interop-methods"></a>Interop 메서드
 편의 IDE 메서드를 제공 하 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>Win32 Api를 호출 하는 대신 사용 하도록 합니다. 관리 코드 사용에서 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>합니다. 때 오류가 `HRESULT` 오류 메시지를 표시할 수준에서 도착 (이 개체는 종종 구현를 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 명령 처리기), IDE의 다른 방법을 사용 하 여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>, 적절 한 메시지 상자를 표시 하려면. 관리 코드 사용에서을 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> 메서드.

 VSPackage 구현자, COM 개체 일반적으로 구현 `ISupportErrorInfo`합니다. `ISupportErrorInfo` 인터페이스를 사용 하면 다양 한 오류 정보 호출 체인 세로 방향으로 이동할 수 있습니다. 스레드 또는 프로세스에 걸쳐 사용할 수 있는 개체를 지원 해야 합니다 `ISupportErrorInfo` 다양 한 오류 정보를 다시 호출자에 게 제대로 마샬링됩니다 되도록 합니다.

 Vspackage에 관련 된 및 관련 편집기 팩터리, 편집기, 계층 구조를 포함 하 여 IDE를 확장 하 여 서비스를 제공 하는 모든 개체는 다양 한 오류 정보를 지원 해야 합니다. IDE 하지 않아도 이러한 VSPackage 개체를 구현 하는 동안 `ISupportErrorInfo`에 항상 것이 좋습니다.

 IDE가 오류 정보를 보고 하 고의 사용자에 게 표시 하는 일을 담당 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 때마다는 `HRESULT` IDE에 전파 됩니다. IDE를 만들기 위한 메커니즘 이기도 `ErrorInfo` 개체입니다.

## <a name="general-guidelines"></a>일반 지침
 사용할 수는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> 및 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> 메서드를 설정 하 고 내부도 VSPackage 구현에 있는 오류를 보고 합니다. 그러나 일반적으로 VSPackage의 오류 메시지를 처리 하기 위한 다음이 지침을 따르세요.

- 구현 `ISupportErrorInfo` VSPackage COM 개체에 있습니다.

- 오류 보고를 호출 하는 메커니즘을 만들기는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> 메서드를 구현 하는 개체의 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>합니다.

- IDE를 통해 사용자에 게 오류를 표시할 수는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> 메서드.

## <a name="error-information-in-the-ide"></a>IDE에서 오류 정보
 다음 규칙에 오류 정보를 처리 하는 방법에 표시 된 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE:

- 사용자에 게 오래 된 오류 정보 보고 되지 않습니다 보장 하기 위해 방어 전략을 호출 하는 함수 처럼 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> 메서드가 먼저 호출 해야 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> 메서드. 전달 `null` 새 오류 정보를 설정할 수는 아무 것도 호출 하려면 먼저 캐시 된 오류 메시지를 지워야 합니다.

- 오류 메시지를 직접 보고 하지 않는 함수 호출 에서만 수는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> 메서드는 오류를 반환 하는 이러한 경우 `HRESULT`합니다. 선택을 허용 되는 것은 `ErrorInfo` 함수 또는 반환할 때 항목 <xref:Microsoft.VisualStudio.VSConstants.S_OK>합니다. 이 규칙의 유일한 예외는 호출 오류를 반환 하는 경우 `HRESULT` 여자에 게는 수신 파티 수 복구 명시적으로 무시 해도 괜찮습니다.

- 명시적으로 오류를 무시 하는 모든 파티 `HRESULT` 호출 해야 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> 메서드를 <xref:Microsoft.VisualStudio.VSConstants.S_OK>합니다. 그렇지 않은 경우는 `ErrorInfo` 다른 당사자가 자신의 제공 하지 않고 오류를 생성 하는 경우 개체 실수로 사용할 수 있습니다 `ErrorInfo`합니다.

- 오류가 발생 하는 모든 메서드에 `HRESULT` 를 호출 하는 것이 좋습니다는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> 다양 한 오류 정보를 제공 하는 방법입니다. 하는 경우 반환 된 `HRESULT` 특수 `FACILITY_ITF` 오류를 다음 메서드를 제공 해야 적절 한 `ErrorInfo`개체입니다. 반환 된 오류는 표준 시스템 오류가 발생 하는 경우 (예를 들어 <xref:Microsoft.VisualStudio.VSConstants.E_OUTOFMEMORY>, <xref:Microsoft.VisualStudio.VSConstants.E_ABORT>, <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG>, <xref:Microsoft.VisualStudio.VSConstants.E_UNEXPECTED>, 및 등입니다.)를 명시적으로 호출 하지 않고 오류 코드를 반환 하는 것이 좋습니다는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> 메서드. 코딩 하려는 방어 전략에서 오류가 발생 하는 경우로 `HRESULT` 항상 호출 (시스템 오류)를 포함 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> 메서드를 사용 하 여 `ErrorInfo` 더 자세히 설명에서 실패를 설명 하는 또는 `null`합니다.

- 실패에서 수신 된 정보에 전달 해야 다른 호출에서 발생 하는 오류를 반환 하는 모든 함수에서 호출 된 `HRESULT` 수정 하지 않고는 `ErrorInfo` 개체입니다.

## <a name="see-also"></a>참고자료
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [SetErrorInfo (구성 요소 자동화)](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-seterrorinfo)
- [GetErrorInfo](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-geterrorinfo)
- [ISupportErrorInfo 인터페이스](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-isupporterrorinfo)
