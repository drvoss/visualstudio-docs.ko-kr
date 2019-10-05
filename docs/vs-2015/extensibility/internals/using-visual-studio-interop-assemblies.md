---
title: Interop 어셈블리를 사용 하 여 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, interop assemblies
- interop assemblies, Visual Studio
- managed VSPackages, interop assemblies
ms.assetid: 1043eb95-4f0d-4861-be21-2a25395b3b3c
caps.latest.revision: 34
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7df241773d06574f8d070285c2b45b662ccd6403
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65675195"
---
# <a name="using-visual-studio-interop-assemblies"></a>Visual Studio Interop 어셈블리 사용
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio interop 어셈블리는 Visual Studio 확장성을 제공 하는 COM 인터페이스에 액세스 하는 관리 되는 응용 프로그램을 허용 합니다. 가지 직선 COM 인터페이스 및 해당 interop 버전 간의 일부 차이점이 있습니다. 예를 들어 Hresult int 값으로 표현 일반적으로 동일한 방식으로 예외를 처리 해야 및 (특히 out 매개 변수) 매개 변수를 다르게 처리 됩니다.

## <a name="handling-hresults-returned-to-managed-code-from-com"></a>COM에서 관리 코드로 반환되는 HRESULT 처리
 관리 코드에서 COM 인터페이스를 호출하는 경우 HRESULT 값을 검사하고 필요에 따라 예외를 발생시킵니다. <xref:Microsoft.VisualStudio.ErrorHandler> 클래스에는 전달된 HRESULT의 값에 따라 COM 예외를 발생시키는 <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> 메서드가 포함되어 있습니다.

 기본적으로 <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>는 0보다 작은 값을 가진 HRESULT가 전달될 때마다 예외를 발생시킵니다. 이러한 HRESULT가 허용되는 값이며 예외가 발생하지 않아야 하는 경우 값이 테스트된 후에 추가 HRESULT 값을 <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>에 전달해야 합니다. 테스트되는 HRESULT가 <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>에 명시적으로 전달된 HRESULT 값과 일치하는 경우 예외가 발생하지 않습니다.

> [!NOTE]
> <xref:Microsoft.VisualStudio.VSConstants> 클래스 일반적인 HRESULT에 대 한 예를 들어 상수를 포함 <xref:Microsoft.VisualStudio.VSConstants.S_OK> 하 고 <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>, 및 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] HRESULT, 예를 들어 <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> 및 <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>합니다. 또한 <xref:Microsoft.VisualStudio.VSConstants>는 COM의 SUCCEEDED 및 FAILED 매크로에 해당하는 <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A> 및 <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A> 메서드를 제공합니다.

 예를 들어 <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>은 허용되는 반환 값이지만 0보다 작은 다른 HRESULT는 오류를 나타내는 다음 함수 호출을 고려해 보세요.

 [!code-csharp[VSSDKHRESULTInformation#1](../../snippets/csharp/VS_Snippets_VSSDK/vssdkhresultinformation/cs/vssdkhresultinformationpackage.cs#1)]
 [!code-vb[VSSDKHRESULTInformation#1](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdkhresultinformation/vb/vssdkhresultinformationpackage.vb#1)]

 허용되는 반환 값이 둘 이상 있는 경우 <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> 호출의 목록에 다른 HRESULT 값을 추가하면 됩니다.

 [!code-csharp[VSSDKHRESULTInformation#2](../../snippets/csharp/VS_Snippets_VSSDK/vssdkhresultinformation/cs/vssdkhresultinformationpackage.cs#2)]
 [!code-vb[VSSDKHRESULTInformation#2](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdkhresultinformation/vb/vssdkhresultinformationpackage.vb#2)]

## <a name="returning-hresults-to-com-from-managed-code"></a>관리 코드에서 COM으로 HRESULT 반환
 예외가 발생하지 않는 경우 관리 코드가 호출한 COM 함수에 <xref:Microsoft.VisualStudio.VSConstants.S_OK>를 반환합니다. COM interop는 관리 코드에서 강력한 형식의 일반적인 예외를 지원합니다. 예를 들어 허용되지 않는 `null` 인수를 받은 메서드는 <xref:System.ArgumentNullException>을 발생시킵니다.

 어떤 예외를 발생시켜야 하는지 모르지만 COM에 반환하려는 HRESULT를 알고 있는 경우 <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> 메서드를 사용하여 적절한 예외를 발생시킬 수 있습니다. 이는 비표준 오류(예: <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>)에도 적용됩니다. <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>이 전달된 HRESULT를 강력한 형식의 예외에 매핑하려고 합니다. 매핑할 수 없는 경우 대신 일반 COM 예외를 발생시킵니다. 최종 결과로, 관리 코드에서 <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>에 전달하는 HRESULT가 호출한 COM 함수에 반환됩니다.

> [!NOTE]
> 예외가 발생하면 성능이 저하되며 비정상적인 프로그램 상태를 나타냅니다. 자주 발생하는 상태는 예외를 발생시키는 대신 인라인으로 처리해야 합니다.

## <a name="iunknown-parameters-passed-as-type-void"></a>IUnknown 매개 변수 형식 void * *으로 전달
 [Out] 형식으로 정의 된 매개 변수에 검색할 `void **` COM 인터페이스, 있지만로 정의 됩니다 `[``iid_is``]` 에 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] interop 어셈블리 메서드 프로토타입을 합니다.

 COM 인터페이스를 생성 하는 경우에 따라 프로그램 `IUnknown` 개체 및 COM 인터페이스를 전달 형식으로 `void **`입니다. 이러한 인터페이스는 특히 중요 하기 때문에 변수의로 정의 된 경우 [out]의 IDL에 해당 `IUnknown` 개체가 사용 하 여 참조 횟수가 계산는 `AddRef` 메서드. 메모리 누수 개체가 제대로 처리 되지 않은 경우 발생 합니다.

> [!NOTE]
> `IUnknown` COM 인터페이스에 의해 생성 되 고 [out] 변수에 반환 개체는 명시적으로 해제 되지 않습니다 하는 경우 메모리 누수가 발생 합니다.

 이러한 개체를 처리 하는 관리 되는 메서드를 처리 해야 <xref:System.IntPtr> 포인터로 `IUnknown` 개체를 호출 합니다 <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> 개체를 가져오는 방법입니다. 호출자에 게 적합 한 형식에 관계 없이 반환 값을 캐스팅 한 다음 해야 합니다. 개체가 더 이상 필요 하면 호출 <xref:System.Runtime.InteropServices.Marshal.Release%2A> 해제 합니다.

 다음은 호출의 예는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A> 메서드 및 처리는 `IUnknown` 올바르게 개체:

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
> 다음 방법 전달할 알려져 `IUnknown` 형식으로 포인터를 개체 <xref:System.IntPtr>합니다. 이 섹션에 설명 된 대로 처리 합니다.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>

## <a name="optional-out-parameters"></a>[Out] 매개 변수는 선택 사항
 [Out]로 정의 된 매개 변수를 검색할 데이터 형식 (`int`, `object`등)에서 동일한 데이터 형식의 배열로 사용 되는 하지만 인터페이스를 COM에 정의 된 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] interop 어셈블리 메서드 프로토타입.

 와 같은 일부 COM 인터페이스를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>, [out] 매개 변수 선택 사항으로 처리 합니다. 이러한 COM 인터페이스를 반환 하는 경우 개체 필수는 `null` [out] 개체를 만드는 대신 해당 매개 변수의 값으로 포인터입니다. 이것은 의도적인 것입니다. 이러한 인터페이스에 대 한 `null` 포인터는 VSPackage의 올바른 동작의 일부로 간주 됩니다 하 고 오류가 반환 되지 않습니다.

 CLR에서 되도록 [out] 매개 변수 값을 허용 하지 않으므로 `null`, 이러한 인터페이스의 디자인 하는 동작 파트를 관리 코드 내에서 직접 사용할 수 없는 경우. 합니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 영향을 받는 인터페이스에 대 한 interop 어셈블리 메서드 CLR의 통과 허용 하기 때문에 배열로 관련 매개 변수를 정의 하 여 문제를 해결 `null` 배열입니다.

 이러한 메서드의 관리 되는 구현 넣어야를 `null` 항목이 반환 될 때 매개 변수 배열입니다. 이 고, 그렇지 올바른 형식의 요소가 하나인 배열 만들기 및 반환 값은 배열에 배치 합니다.

 관리 되는 선택적 [out]를 사용 하 여 인터페이스에서 정보를 수신 하는 메서드 매개 변수 배열로 매개 변수를 수신 합니다. 배열의 첫 번째 요소의 값을 조사 하면 됩니다. 없는 경우 `null`, 원래 매개 변수 처럼 첫 번째 요소를 처리 합니다.

## <a name="passing-constants-in-pointer-parameters"></a>포인터 매개 변수에서 전달 상수
 으로 [in] COM 인터페이스에 대 한 포인터 정의 되어 있지만으로 정의 된 매개 변수를 검색할를 <xref:System.IntPtr> 입력을 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] interop 어셈블리 메서드 프로토타입을 합니다.

 유사한 문제는 COM 인터페이스에는 0,-1 또는-2는 개체 포인터 대신 같은 특수 값을 전달 하는 경우에 발생 합니다. 와 달리 [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)]를 CLR 개체로 캐스팅 하는 상수를 허용 하지 않습니다. 대신 합니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 로 매개 변수를 정의 하는 interop 어셈블리를 <xref:System.IntPtr> 형식입니다.

 이러한 메서드에 대 한 관리 되는 구현을 활용 합니다 되기 때문에 발생 하는 <xref:System.IntPtr> 클래스에는 둘 다 `int` 및 `void *` 만들려면 생성자를 <xref:System.IntPtr> 개체 또는 정수 상수에서 적절 하 게 합니다.

 관리 되는 수신 하는 메서드 <xref:System.IntPtr> 이 형식의 매개 변수를 사용 해야는 <xref:System.IntPtr> 결과 처리 하는 변환 연산자를 입력 합니다. 먼저 변환 합니다 <xref:System.IntPtr> 에 `int` 및 관련 정수 상수에 대해 테스트 합니다. 값이 없는 일치 필요한 형식의 개체로 변환 하 고 계속 합니다.

 이 예제를 참조 하세요 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 고 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>입니다.

## <a name="ole-return-values-passed-as-out-parameters"></a>OLE 반환 값이 전달 [out] 매개 변수
 있는 메서드를 `retval` COM 인터페이스에는 반환 값을 `int` 반환 값 및 [out] 배열 매개 변수에 추가 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] interop 어셈블리 메서드 프로토타입. 때문에 특별 한 처리가 필요는 명확 해야 합니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 메서드 프로토타입을 interop 어셈블리에는 COM 인터페이스 메서드를 보다 자세한 매개 변수가 하나 있어야 합니다.

 에 저장 된 호출 프로그램으로 다시 OLE 상태에 대 한 정보를 송신 하는 OLE 활동을 처리 하는 많은 COM 인터페이스는 `retval` 인터페이스의 값을 반환 합니다. 해당 반환 값을 사용 하는 대신 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] interop 어셈블리 메서드는 [out]에 저장 된 호출 프로그램에 다시 정보를 보낼 배열 매개 변수입니다.

 이러한 메서드의 관리 되는 구현 [out] 매개 변수로 동일한 형식의 단일 요소 배열을 만들고 매개 변수에 배치 해야 합니다. 배열 요소의 값으로 적절 한 COM 동일 해야 `retval`합니다.

 이 형식의 인터페이스를 호출 하는 관리 되는 메서드는 [out] 배열에서 첫 번째 요소를 끌어옵니다. 이 요소는 것 처럼 처리할 수 있습니다는 `retval` 해당 COM 인터페이스에서 값을 반환 합니다.

## <a name="see-also"></a>참고 항목
 [비관리 코드와의 상호 운용](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
