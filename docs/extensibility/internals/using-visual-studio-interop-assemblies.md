---
title: Visual Studio Interop 어셈블리 사용 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, interop assemblies
- interop assemblies, Visual Studio
- managed VSPackages, interop assemblies
ms.assetid: 1043eb95-4f0d-4861-be21-2a25395b3b3c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d0db6e0e0d5014f09a84316143af40f410bc1b10
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722110"
---
# <a name="using-visual-studio-interop-assemblies"></a>Visual Studio Interop 어셈블리 사용
Visual Studio interop 어셈블리를 사용 하면 관리 되는 응용 프로그램에서 Visual Studio 확장성을 제공 하는 COM 인터페이스에 액세스할 수 있습니다. 직선 COM 인터페이스와 해당 interop 버전 간에는 몇 가지 차이점이 있습니다. 예를 들어 Hresult는 일반적으로 int 값으로 표시 되 고 예외와 동일한 방식으로 처리 되어야 하며 매개 변수 (특히 out 매개 변수)는 다르게 처리 됩니다.

## <a name="handling-hresults-returned-to-managed-code-from-com"></a>COM에서 관리 코드로 반환되는 HRESULT 처리
 관리 코드에서 COM 인터페이스를 호출하는 경우 HRESULT 값을 검사하고 필요에 따라 예외를 발생시킵니다. <xref:Microsoft.VisualStudio.ErrorHandler> 클래스에는 전달된 HRESULT의 값에 따라 COM 예외를 발생시키는 <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> 메서드가 포함되어 있습니다.

 기본적으로 <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>는 0보다 작은 값을 가진 HRESULT가 전달될 때마다 예외를 발생시킵니다. 이러한 HRESULT가 허용되는 값이며 예외가 발생하지 않아야 하는 경우 값이 테스트된 후에 추가 HRESULT 값을 <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>에 전달해야 합니다. 테스트되는 HRESULT가 <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>에 명시적으로 전달된 HRESULT 값과 일치하는 경우 예외가 발생하지 않습니다.

> [!NOTE]
> @No__t_0 클래스에는 일반적인 HRESULT에 대 한 상수 (예: <xref:Microsoft.VisualStudio.VSConstants.S_OK> 및 <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> 및 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] HRESULT (예: <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> 및 <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>)가 포함 되어 있습니다. 또한 <xref:Microsoft.VisualStudio.VSConstants>는 COM의 SUCCEEDED 및 FAILED 매크로에 해당하는 <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A> 및 <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A> 메서드를 제공합니다.

 예를 들어 <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>은 허용되는 반환 값이지만 0보다 작은 다른 HRESULT는 오류를 나타내는 다음 함수 호출을 고려해 보세요.

 [!code-vb[VSSDKHRESULTInformation#1](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_1.vb)]
 [!code-csharp[VSSDKHRESULTInformation#1](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_1.cs)]

 허용되는 반환 값이 둘 이상 있는 경우 <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> 호출의 목록에 다른 HRESULT 값을 추가하면 됩니다.

 [!code-vb[VSSDKHRESULTInformation#2](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_2.vb)]
 [!code-csharp[VSSDKHRESULTInformation#2](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_2.cs)]

## <a name="returning-hresults-to-com-from-managed-code"></a>관리 코드에서 COM으로 HRESULT 반환
 예외가 발생하지 않는 경우 관리 코드가 호출한 COM 함수에 <xref:Microsoft.VisualStudio.VSConstants.S_OK>를 반환합니다. COM interop는 관리 코드에서 강력한 형식의 일반적인 예외를 지원합니다. 예를 들어 허용되지 않는 `null` 인수를 받은 메서드는 <xref:System.ArgumentNullException>을 발생시킵니다.

 어떤 예외를 발생시켜야 하는지 모르지만 COM에 반환하려는 HRESULT를 알고 있는 경우 <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> 메서드를 사용하여 적절한 예외를 발생시킬 수 있습니다. 이는 비표준 오류(예: <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>)에도 적용됩니다. <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>이 전달된 HRESULT를 강력한 형식의 예외에 매핑하려고 합니다. 매핑할 수 없는 경우 대신 일반 COM 예외를 발생시킵니다. 최종 결과로, 관리 코드에서 <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>에 전달하는 HRESULT가 호출한 COM 함수에 반환됩니다.

> [!NOTE]
> 예외가 발생하면 성능이 저하되며 비정상적인 프로그램 상태를 나타냅니다. 자주 발생하는 상태는 예외를 발생시키는 대신 인라인으로 처리해야 합니다.

## <a name="iunknown-parameters-passed-as-type-void"></a>IUnknown 매개 변수가 void 형식으로 전달 되었습니다. * *
 COM 인터페이스에서 형식 `void **` 정의 된 [out] 매개 변수를 찾습니다 .이 매개 변수는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interop 어셈블리 메서드 프로토타입에서 `[``iid_is``]` 정의 됩니다.

 경우에 따라 COM 인터페이스는 `IUnknown` 개체를 생성 하 고 COM 인터페이스는 `void **` 형식으로 전달 합니다. 이러한 인터페이스는 변수가 IDL에서 [out]으로 정의 된 경우 `IUnknown` 개체가 `AddRef` 메서드를 사용 하 여 참조 횟수가 계산 되기 때문에 특히 중요 합니다. 개체가 올바르게 처리 되지 않으면 메모리 누수가 발생 합니다.

> [!NOTE]
> COM 인터페이스에 의해 생성 되 고 [out] 변수에 반환 된 `IUnknown` 개체는 명시적으로 해제 되지 않은 경우 메모리 누수가 발생 합니다.

 이러한 개체를 처리 하는 관리 되는 메서드는 <xref:System.IntPtr>를 `IUnknown` 개체에 대 한 포인터로 처리 하 고 <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> 메서드를 호출 하 여 개체를 가져와야 합니다. 그런 다음 호출자는 적절 한 형식으로 반환 값을 캐스팅 해야 합니다. 개체가 더 이상 필요 하지 않은 경우 <xref:System.Runtime.InteropServices.Marshal.Release%2A>를 호출 하 여 릴리스 합니다.

 다음은 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A> 메서드를 호출 하 고 `IUnknown` 개체를 올바르게 처리 하는 예제입니다.

```
MyClass myclass;
Object object;
IntPtr pObj;
Guid iid = Typeof(MyClass).Guid;
int hr = windowFrame.QueryViewInterface(ref iid, out pObj);
if (NativeMethods.Succeeded(hr))
{
    try
    {
        object = Marshal.GetObjectForIUnknown(pObj);
        myclass = object;
    }
    finally
    {
        Marshal.Release(pObj);
    }
}
else
{
    // error calling QueryViewInterface
}
```

> [!NOTE]
> 다음 메서드는 <xref:System.IntPtr> 형식으로 `IUnknown` 개체 포인터를 전달 하는 것으로 알려져 있습니다. 이 섹션에 설명 된 대로 처리 합니다.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>

## <a name="optional-out-parameters"></a>선택적 [out] 매개 변수
 COM 인터페이스에서 [out] 데이터 형식 (`int`, `object` 등)으로 정의 된 매개 변수를 찾습니다. 하지만이 매개 변수는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interop 어셈블리 메서드 프로토타입에서 동일한 데이터 형식의 배열로 정의 됩니다.

 @No__t_0와 같은 일부 COM 인터페이스는 [out] 매개 변수를 선택적으로 처리 합니다. 개체가 필요 하지 않은 경우 이러한 COM 인터페이스는 [out] 개체를 만드는 대신 해당 매개 변수의 값으로 `null` 포인터를 반환 합니다. 이것은 의도적인 것입니다. 이러한 인터페이스의 경우 `null` 포인터는 VSPackage의 올바른 동작의 일부로 간주 되며 오류가 반환 되지 않습니다.

 CLR에서는 [out] 매개 변수의 값을 `null` 수 없으므로 이러한 인터페이스의 디자인 된 동작 부분은 관리 코드 내에서 직접 사용할 수 없습니다. 영향을 받는 인터페이스에 대 한 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interop 어셈블리 메서드는 CLR에서 `null` 배열을 전달할 수 있기 때문에 관련 매개 변수를 배열로 정의 하 여 문제를 해결 합니다.

 이러한 메서드의 관리 되는 구현은 반환 될 항목이 없을 때 매개 변수에 `null` 배열을 배치 해야 합니다. 그렇지 않으면 올바른 형식의 요소가 하나인 배열을 만들고 반환 값을 배열에 배치 합니다.

 선택적 [out] 매개 변수가 있는 인터페이스에서 정보를 수신 하는 관리 되는 메서드는 매개 변수를 배열로 받습니다. 배열의 첫 번째 요소 값을 검사 하면 됩니다. @No__t_0 되지 않은 경우 첫 번째 요소를 원래 매개 변수로 처리 합니다.

## <a name="passing-constants-in-pointer-parameters"></a>포인터 매개 변수에서 상수 전달
 COM 인터페이스에서 [in] 포인터로 정의 된 매개 변수를 찾습니다 .이 매개 변수는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interop 어셈블리 메서드 프로토타입에서 <xref:System.IntPtr> 형식으로 정의 됩니다.

 COM 인터페이스가 개체 포인터가 아닌 0,-1 또는-2와 같은 특수 값을 전달 하는 경우에도 유사한 문제가 발생 합니다. @No__t_0와 달리 CLR에서는 상수를 개체로 캐스팅 하는 것을 허용 하지 않습니다. 대신 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interop 어셈블리는 매개 변수를 <xref:System.IntPtr> 형식으로 정의 합니다.

 이러한 메서드의 관리 되는 구현에서는 <xref:System.IntPtr> 클래스가 `int` 및 `void *` 생성자를 사용 하 여 개체 또는 정수 상수에서 적절 하 게 <xref:System.IntPtr>를 만들도록 하는 이점을 활용 해야 합니다.

 이 형식의 <xref:System.IntPtr> 매개 변수를 받는 관리 되는 메서드는 <xref:System.IntPtr> 형식 변환 연산자를 사용 하 여 결과를 처리 해야 합니다. 먼저 <xref:System.IntPtr>를 `int`으로 변환 하 고 관련 정수 상수에 대해 테스트 합니다. 일치 하는 값이 없으면 필요한 형식의 개체로 변환 하 고 계속 합니다.

 이에 대 한 예제는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 및 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>를 참조 하세요.

## <a name="ole-return-values-passed-as-out-parameters"></a>[Out] 매개 변수로 전달 된 OLE 반환 값
 COM 인터페이스에 `retval` 반환 값이 있지만 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interop 어셈블리 메서드 프로토타입의 `int` 반환 값 및 추가 [out] 배열 매개 변수가 있는 메서드를 찾습니다. @No__t_0 interop 어셈블리 메서드 프로토타입의 COM 인터페이스 메서드 보다 하나 이상의 매개 변수가 있기 때문에 이러한 메서드는 특수 하 게 처리 해야 합니다.

 OLE 작업을 처리 하는 많은 COM 인터페이스는 인터페이스의 `retval` 반환 값에 저장 된 호출 프로그램에 대 한 OLE 상태 정보를 다시 보냅니다. 반환 값을 사용 하는 대신 해당 하는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interop 어셈블리 메서드는 [out] 배열 매개 변수에 저장 된 호출 프로그램으로 정보를 다시 보냅니다.

 이러한 메서드의 관리 되는 구현에서는 [out] 매개 변수와 동일한 형식의 단일 요소 배열을 만들고 매개 변수에 넣습니다. 배열 요소의 값은 적절 한 COM `retval`와 동일 해야 합니다.

 이 형식의 인터페이스를 호출 하는 관리 되는 메서드는 [out] 배열에서 첫 번째 요소를 가져와야 합니다. 이 요소는 해당 COM 인터페이스의 `retval` 반환 값인 것 처럼 처리할 수 있습니다.

## <a name="see-also"></a>참조
- [비관리 코드와의 상호 운용](/dotnet/framework/interop/index)