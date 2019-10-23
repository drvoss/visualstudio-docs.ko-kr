---
title: UDT | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- SymTagUDT symbol
- user-defined type (UDT) symbol
- unions, as symbols
- UDT symbol
- structs [C++]
ms.assetid: f12459dd-c64d-4cc9-9ee3-a56e19e9e573
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ab301f42891be063ccc6f6ae5476e060497efa21
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738456"
---
# <a name="udt"></a>UDT
각 클래스, 구조체 및 공용 구조체는 `SymTagUDT` 기호로 식별 됩니다. 각 멤버, 함수, 데이터 또는 중첩 형식과 각 기본 클래스는 UDT (사용자 정의 형식)의 클래스 자식으로 표시 됩니다.

## <a name="properties"></a>데이터 액세스
 다음 표에서는이 기호 형식에 대 한 추가 유효한 속성을 보여 줍니다.

|속성|데이터 형식|설명|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|`IDiaSymbol*`|클래스 부모의 기호입니다 (있는 경우).|
|[IDiaSymbol::get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|`DWORD`|클래스 부모 기호의 ID입니다.|
|[IDiaSymbol::get_constructor](../../debugger/debug-interface-access/idiasymbol-get-constructor.md)|`BOOL`|UDT에 생성자가 있는 경우 `TRUE` 합니다.|
|[IDiaSymbol::get_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|UDT가 상수로 표시 되 면 `TRUE` 합니다.|
|[IDiaSymbol::get_hasAssignmentOperator](../../debugger/debug-interface-access/idiasymbol-get-hasassignmentoperator.md)|`BOOL`|UDT에 할당 연산자가 정의 되어 있는지 여부를 `TRUE` 합니다.|
|[IDiaSymbol::get_hasCastOperator](../../debugger/debug-interface-access/idiasymbol-get-hascastoperator.md)|`BOOL`|UDT에 캐스트 연산자가 정의 되어 있는지 여부를 `TRUE` 합니다.|
|[IDiaSymbol::get_hasNestedTypes](../../debugger/debug-interface-access/idiasymbol-get-hasnestedtypes.md)|`BOOL`|UDT에 중첩 된 형식 정의가 있는 경우 `TRUE` 합니다.|
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`LONGLONG`|UDT의 크기 (바이트)입니다.|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|바깥쪽 [Compiland](../../debugger/debug-interface-access/compiland.md)기호입니다.|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|어휘 부모 기호의 ID입니다.|
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|UDT의 이름입니다.|
|[IDiaSymbol::get_nested](../../debugger/debug-interface-access/idiasymbol-get-nested.md)|`BOOL`|UDT가 중첩 되어 있으면 `TRUE` 합니다.|
|[IDiaSymbol::get_overloadedOperator](../../debugger/debug-interface-access/idiasymbol-get-overloadedoperator.md)|`BOOL`|UDT에 대해 오버 로드 된 연산자가 정의 되어 있으면 `TRUE` 합니다.|
|[IDiaSymbol::get_packed](../../debugger/debug-interface-access/idiasymbol-get-packed.md)|`BOOL`|UDT가 압축 된 경우 `TRUE` 합니다.|
|[IDiaSymbol::get_scoped](../../debugger/debug-interface-access/idiasymbol-get-scoped.md)|`BOOL`|UDT가 비전역 어휘 범위에 표시 되는 경우를 `TRUE` 합니다.|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|기호의 인덱스 ID입니다.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|[SymTagEnum 열거형](../../debugger/debug-interface-access/symtagenum.md) 값 중 하나인 `SymTagUDT` 반환 합니다.|
|[IDiaSymbol::get_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)|`DWORD`|구조체, 클래스 또는 공용 구조체 인지 여부를 나타냅니다. 자세한 내용은 [UdtKind 열거형](../../debugger/debug-interface-access/udtkind.md)을 참조 하세요.|
|[IDiaSymbol::get_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|UDT가 정렬 되지 않은 경우 `TRUE` 합니다.|
|[IDiaSymbol::get_virtualTableShape](../../debugger/debug-interface-access/idiasymbol-get-virtualtableshape.md)|`IDiaSymbol*`|가상 테이블의 유형입니다.|
|[IDiaSymbol::get_virtualTableShapeId](../../debugger/debug-interface-access/idiasymbol-get-virtualtableshapeid.md)|`DWORD`|가상 테이블 셰이프 기호의 ID입니다.|
|[IDiaSymbol::get_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|UDT가 volatile로 표시 되 면 `TRUE` 합니다.|

## <a name="see-also"></a>참조
- [기호 형식의 클래스 계층 구조](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)