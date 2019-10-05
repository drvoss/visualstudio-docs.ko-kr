---
title: 구현 하 고 포트 공급자 등록 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], registering port suppliers
- port suppliers, registering
ms.assetid: fb057052-ee16-4272-8e16-a4da5dda0ad4
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 26767193c4489405432054ee94beb195ce8448d7
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66344265"
---
# <a name="implement-and-register-a-port-supplier"></a>구현 하 고 포트 공급자 등록
포트 공급자의 역할 추적에 프로세스를 관리 하는 포트를 제공 하는 것입니다. 포트를 만들 수 해야 하는 경우 포트 공급자 CoCreate를 사용 하 여 포트 공급자의 GUID (세션 디버그 관리자 [SDM] 사용 프로젝트 시스템에서 지정 하는 사용자가 선택한 또는 포트 공급자 포트 공급자)를 사용 하 여 인스턴스화됩니다. SDM 호출 [CanAddPort](../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) 모든 포트를 추가할 수 있는지 확인 합니다. 새 포트를 호출 하 여 요청 된 경우 포트를 추가할 수 있습니다 [포트 추가](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) 전달 하는 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) 는 포트에 설명 합니다. `AddPort` 나타내는 새 포트를 반환 합니다는 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) 인터페이스입니다.

## <a name="discussion"></a>토론
 포트를 컴퓨터 또는 디버그 서버와 연결 된 포트 공급자에 의해 생성 됩니다. 서버 열거를 통해 그 포트 공급자는[EnumPortSuppliers](../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) 메서드와 포트 공급자를 통해 해당 포트를 열거 합니다 [EnumPorts](../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) 메서드.

 일반적인 COM 등록, 외에도 포트 공급자 등록 해야 자체 Visual Studio를 사용 하 여 특정 레지스트리 위치에서 이름과 CLSID를 배치 하 여 합니다. Debugging SDK 도우미 함수가 호출 `SetMetric` 이 번거로운 작업이 처리: 등록, 따라서 각 항목에 대해 한 번씩 호출 됩니다.

```cpp
SetMetric(metrictypePortSupplier,
          <GUID of your port supplier>,
          metricCLSID,
          <CLSID of your port supplier>,
          false,
          NULL)
SetMetric(metrictypePortSupplier,
          <GUID of your port supplier>,
          metricName,
          <name of your port supplier>,
          false,
          NULL);
```

 포트 공급자를 호출 하 여 자체를 등록 취소 `RemoveMetric` (또 다른 디버깅 SDK 도우미 함수가) 따라서 등록 된 각 항목에 한 번씩:

```cpp
RemoveMetric(metrictypePortSupplier,
             <GUID of your port supplier>,
             metricCLSID,
             NULL);
RemoveMetric(metrictypePortSupplier,
             <GUID of your port supplier>,
             metricName,
             NULL);
```

> [!NOTE]
> [디버깅을 위한 SDK 도우미](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric` 하 고 `RemoveMetric` 에 정의 된 정적 함수 *dbgmetric.h* 및로 컴파일된 *ad2de.lib*합니다. 합니다 `metrictypePortSupplier`, `metricCLSID`, 및 `metricName` 도우미에도 정의 되어 *dbgmetric.h*합니다.

 포트 공급자 메서드를 통해 해당 이름 및 GUID를 제공할 수 있습니다 [GetPortSupplierName](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md) 하 고 [GetPortSupplierId](../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md), 각각.

## <a name="see-also"></a>참고자료
- [포트 공급자 구현](../../extensibility/debugger/implementing-a-port-supplier.md)
- [디버깅을 위한 SDK 도우미](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [포트 공급자](../../extensibility/debugger/port-suppliers.md)