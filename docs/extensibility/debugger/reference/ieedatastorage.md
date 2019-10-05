---
title: IEEDataStorage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEDataStorage
helpviewer_keywords:
- IEEDataStorage interface
ms.assetid: 704e932d-2325-410e-89c4-ce88c6ec19da
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ab42216df5c7d5f3d2d349ccf07e595ab3fc616c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66335628"
---
# <a name="ieedatastorage"></a>IEEDataStorage
이 인터페이스는 바이트의 배열을 나타냅니다.

## <a name="syntax"></a>구문

```
IEEDataStorage : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 바이트 배열을 나타내는 데이 인터페이스를 구현 하는 식 계산기 (EE) (형식 시각화 도우미에서 사용 하 여 검색을 통해 데이터를 변경 하는 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) 인터페이스). 일반적으로 EE 외부 형식 시각화 도우미를 지원 하기 위해이 인터페이스를 구현 합니다.

## <a name="notes-for-callers"></a>호출자에 대 한 정보
 메서드는 `IPropertyProxyEESide` 모든 인터페이스는이 인터페이스를 반환 합니다. 호출 [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) 가져오려고 합니다 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) 인터페이스입니다. 호출 [QueryInterface](/cpp/atl/queryinterface) 에 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) 얻기 위해 인터페이스의 [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) 인터페이스입니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 `IEEDataStorage` 인터페이스는 다음 메서드를 구현 합니다.

|메서드|설명|
|------------|-----------------|
|[GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)|지정 된 수가 제공 된 버퍼에 데이터 바이트를 검색합니다.|
|[GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)|사용할 수 있는 데이터 바이트 수를 검색 합니다.|

## <a name="remarks"></a>설명
 이 인터페이스는 특정 개체를 소유 하는 데이터에 액세스 하는 형식 시각화 도우미에서 사용 됩니다. 데이터는 사용자에 게 제공 하는 데 필요한 된 방식으로 조작 하는 형식 시각화 도우미를 허용 하는 바이트 배열로 처리 됩니다.

 사용자 지정 뷰어를 이용할 수 있습니다이 인터페이스를 원하는 경우 일반적으로 사용자 지정 뷰어 사용자 지정 인터페이스를 사용 하지만 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) 하거나 [GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md) (데이터용 문자열 기반).

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: Microsoft.VisualStudio.Debugger.Interop

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [형식 시각화 도우미 및 사용자 지정 뷰어](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)