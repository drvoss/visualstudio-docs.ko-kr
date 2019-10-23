---
title: Typedef (Debug Interface Access SDK) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Typedef symbol [DIA SDK]
ms.assetid: 9ab441b9-cc72-47fa-83e2-87b3c2b891b4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 09aa2cc4554fc877f94b7575a2d67e7b38ad4b5c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738484"
---
# <a name="typedef-debug-interface-access-sdk"></a>Typedef(디버그 인터페이스 액세스 SDK)
@No__t_0 태그가 있는 기호는 다른 형식에 대 한 이름을 제공 합니다.

## <a name="properties"></a>데이터 액세스
 다음 표에서는이 기호 형식에 대 한 추가 유효한 속성을 보여 줍니다.

|속성|데이터 형식|설명|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)|`DWORD`|[Basictype 열거형](../../debugger/debug-interface-access/basictype.md) 값 중 하나입니다.|
|[IDiaSymbol::get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|`IDiaSymbol*`|이 typedef의 클래스 부모입니다 (있는 경우).|
|[IDiaSymbol::get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|`DWORD`|클래스 부모 기호의 ID입니다.|
|[IDiaSymbol::get_constructor](../../debugger/debug-interface-access/idiasymbol-get-constructor.md)|`BOOL`|이 typedef에 생성자가 있는 경우 `TRUE` 합니다.|
|[IDiaSymbol::get_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|이 typedef가 상수로 표시 되 면 `TRUE` 합니다.|
|[IDiaSymbol::get_hasAssignmentOperator](../../debugger/debug-interface-access/idiasymbol-get-hasassignmentoperator.md)|`BOOL`|이 typedef에 대입 연산자가 있는 경우 `TRUE` 합니다.|
|[IDiaSymbol::get_hasCastOperator](../../debugger/debug-interface-access/idiasymbol-get-hascastoperator.md)|`BOOL`|이 typedef에 cast 연산자가 있는 경우 `TRUE` 합니다.|
|[IDiaSymbol::get_hasNestedTypes](../../debugger/debug-interface-access/idiasymbol-get-hasnestedtypes.md)|`BOOL`|이 typedef에 중첩 형식이 있는 경우 `TRUE` 합니다.|
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`ULONGLONG`|이 typedef의 길이 (바이트)입니다.|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|바깥쪽 compiland 기호입니다.|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|어휘 부모 기호의 ID입니다.|
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|typedef의 이름입니다.|
|[IDiaSymbol::get_nested](../../debugger/debug-interface-access/idiasymbol-get-nested.md)|`BOOL`|이 typedef가 어휘 범위에 중첩 되어 있으면 `TRUE` 합니다.|
|[IDiaSymbol::get_overloadedOperator](../../debugger/debug-interface-access/idiasymbol-get-overloadedoperator.md)|`BOOL`|이 typedef에 오버 로드 된 연산자가 있는 경우 `TRUE` 합니다.|
|[IDiaSymbol::get_packed](../../debugger/debug-interface-access/idiasymbol-get-packed.md)|`BOOL`|이 typedef가 압축 되 면 `TRUE` 합니다.|
|[IDiaSymbol::get_reference](../../debugger/debug-interface-access/idiasymbol-get-reference.md)|`BOOL`|이 typedef가 참조 인 경우 `TRUE` 합니다.|
|[IDiaSymbol::get_scoped](../../debugger/debug-interface-access/idiasymbol-get-scoped.md)|`BOOL`|이 typedef가 비전역 어휘 범위에 있는지 여부를 `TRUE` 합니다.|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|기호의 인덱스 ID입니다.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|[SymTagEnum 열거형](../../debugger/debug-interface-access/symtagenum.md) 값 중 하나인 `SymTagTypedef` 반환 합니다.|
|[IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|기본 형식에 대 한 기호입니다.|
|[IDiaSymbol::get_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|형식 기호의 ID입니다.|
|[IDiaSymbol::get_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)|`DWORD`|[UdtKind 열거형](../../debugger/debug-interface-access/udtkind.md) 값 중 하나입니다.|
|[IDiaSymbol::get_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|이 typedef가 정렬 되어 있지 않으면 `TRUE` 합니다.|
|[IDiaSymbol::get_virtualTableShape](../../debugger/debug-interface-access/idiasymbol-get-virtualtableshape.md)|`IDiaSymbol*`|가상 테이블 셰이프를 설명 하는 기호입니다.|
|[IDiaSymbol::get_virtualTableShapeId](../../debugger/debug-interface-access/idiasymbol-get-virtualtableshapeid.md)|`DWORD`|가상 테이블 셰이프 기호의 ID입니다.|
|[IDiaSymbol::get_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|이 typedef가 volatile로 표시 되 면 `TRUE` 합니다.|

## <a name="remarks"></a>주의
 Typedef는 클래스, 포인터 또는 UDT (사용자 정의 형식)를 나타낼 수 있으므로 typedef의 기호는 다른 형식의 기호 중 하 나와 같은 속성을 공유 합니다.

## <a name="see-also"></a>참조
- [기호 형식의 클래스 계층 구조](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)