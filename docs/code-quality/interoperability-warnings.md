---
title: 상호 운용성 경고
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.Interoperabilityrules
helpviewer_keywords:
- managed code analysis warnings, interoperability warnings
- interoperability warnings
- warnings, interoperability
ms.assetid: 95de6eb3-40c4-4063-9f59-25cb70e3b2b3
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7a4e8f7bc60704842a8a0e940b336b4bb79093b2
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66745139"
---
# <a name="interoperability-warnings"></a>상호 운용성 경고

상호 운용성 경고 COM 클라이언트와의 상호 작용을 지원합니다.

## <a name="in-this-section"></a>섹션 내용

| 규칙 | 설명 |
| - | - |
| [CA1400: P/Invoke 진입점 있어야 합니다.](../code-quality/ca1400-p-invoke-entry-points-should-exist.md) | public 또는 protected 메서드는 System.Runtime.InteropServices.DllImportAttribute 특성으로 표시됩니다. 관리되지 않는 라이브러리를 찾을 수 없거나 해당 메서드와 라이브러리의 함수가 일치하지 않습니다. |
| [CA1401: P/Invoke을 표시 해야 합니다.](../code-quality/ca1401-p-invokes-should-not-be-visible.md) | 공용 형식에서 public 또는 protected 메서드는 System.Runtime.InteropServices.DllImportAttribute 특성 (Visual Basic에서 Declare 키워드로 구현)에 있습니다. 이러한 메서드는 노출되지 않아야 합니다. |
| [CA1402: COM 노출 인터페이스에서 오버 로드 방지](../code-quality/ca1402-avoid-overloads-in-com-visible-interfaces.md) | 오버로드된 메서드가 COM 클라이언트에 노출되면 첫 번째 메서드 오버로드만 이름이 유지됩니다. 이후의 오버로드는 이름에 밑줄 문자(_)와 오버로드 선언 순서에 해당하는 정수가 추가되어 고유한 이름이 지정됩니다. |
| [CA1403: 자동 레이아웃 형식은 com 노출 이면 안](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md) | COM 노출 값 형식이 LayoutKind.Auto로 설정된 System.Runtime.InteropServices.StructLayoutAttribute 특성을 사용하여 표시되어 있습니다. 이러한 형식의 레이아웃 특정 레이아웃이 필요한 COM 클라이언트는.NET 버전에서는 달라질 수 있습니다. |
| [CA1404: P/Invoke 다음에 바로 GetLastError를 호출 합니다.](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md) | Marshal.GetLastWin32Error 메서드 또는 해당 호출 [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] 즉시 이전 호출 하 고 GetLastError 함수를 플랫폼으로 아닌 메서드를 호출 합니다. |
| [CA1405: COM 노출 형식의 기본 형식은 COM 노출 해야 합니다.](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md) | COM 노출 형식이 COM에 노출되지 않는 형식에서 파생됩니다. |
| [CA1406: Visual Basic 6 클라이언트에서 Int64 인수를 방지 합니다.](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md) | Visual Basic 6 COM 클라이언트는 64 비트 정수를 액세스할 수 없습니다. |
| [CA1407: COM 노출 형식에 정적 멤버를 방지 합니다.](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md) | COM에서는 static 메서드를 지원하지 않습니다. |
| [CA1408: AutoDual ClassInterfaceType을 사용 하지 마십시오](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md) | 이중 인터페이스를 사용하는 형식에서는 클라이언트가 특정 인터페이스 레이아웃에 바인딩할 수 있습니다. 이후 버전에서 해당 형식이나 기본 형식의 레이아웃이 변경되면 인터페이스에 바인딩된 COM 클라이언트의 바인딩이 해제될 수 있습니다. 기본적으로 ClassInterfaceAttribute 특성이 지정되어 있지 않으면 디스패치 전용 인터페이스가 사용됩니다. |
| [CA1409: Com 노출 형식을 만들 수 있어야 합니다.](../code-quality/ca1409-com-visible-types-should-be-creatable.md) | COM에 표시되는 것으로 특별히 표시된 참조 형식에 매개 변수가 있는 public 생성자가 있지만 매개 변수가 없는 public 기본 생성자가 없습니다. COM 클라이언트에서는 public 기본 생성자가 없는 형식을 만들 수 없습니다. |
| [CA1410: COM 등록 메서드는 일치 해야 합니다.](../code-quality/ca1410-com-registration-methods-should-be-matched.md) | 형식을 사용 하 여 표시 된 메서드를 선언 합니다 <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> 하지만 사용 하 여 표시 된 메서드를 선언 하지 않습니다는 <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> 특성 또는 그 반대로 합니다. |
| [CA1411: COM 등록 메서드를 표시 해야 합니다.](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md) | System.Runtime.InteropServices.ComRegisterFunctionAttribute 특성 또는 System.Runtime.InteropServices.ComUnregisterFunctionAttribute 특성을 사용 하 여 표시 된 메서드는 외부에서 볼 수 있습니다. |
| [CA1412: ComSource 인터페이스 IDispatch로 표시](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md) | 형식이 System.Runtime.InteropServices.ComSourceInterfacesAttribute 특성으로 표시되어 있으며 지정된 인터페이스 중 하나 이상이 ComInterfaceType.InterfaceIsIDispatch로 설정된 System.Runtime.InteropServices.InterfaceTypeAttribute 특성으로 표시되어 있지 않습니다. |
| [CA1413: COM 노출 값 형식에 public이 아닌 필드를 방지 합니다.](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md) | public이 아니며 값 형식이 COM에 노출되는 인스턴스 필드는 COM 클라이언트에서 볼 수 있습니다. 필드의 내용을 검토하여 노출되지 않아야 하거나 디자인 또는 보안에 의도하지 않은 영향을 줄 수 있는 정보가 있는지 확인합니다. |
| [CA1414: 부울 P/Invoke 인수를 marshalas로 표시](../code-quality/ca1414-mark-boolean-p-invoke-arguments-with-marshalas.md) | 부울 데이터 형식은 비관리 코드에서 여러 가지로 표현됩니다. |
| [CA1415: P/Invoke를 올바르게 선언 하십시오.](../code-quality/ca1415-declare-p-invokes-correctly.md) | 이 규칙에서는 플랫폼 호출 메서드 선언을 해당 대상에 대 한 [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] OVERLAPPED에 대 한 포인터는 함수 매개 변수 구조체 아니며 해당 관리 되는 매개 변수에 대 한 포인터를 <xref:System.Threading.NativeOverlapped?displayProperty=fullName> 구조입니다. |