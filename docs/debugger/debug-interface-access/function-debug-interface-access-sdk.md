---
title: 함수 (디버그 인터페이스 액세스 SDK) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Function symbol
ms.assetid: 458dc91c-b78b-4427-84f4-615d89e26760
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4d1e0af87618955c492bef68be45c8c623f41218
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62554520"
---
# <a name="function-debug-interface-access-sdk"></a>함수(디버그 인터페이스 액세스 SDK)
각 함수는으로 식별 되는 `SymTagFunction` 기호입니다.

## <a name="properties"></a>속성
 다음 표에서이 기호 형식에 대 한 잘못 된 속성을 보여 줍니다.

|속성|`Data type`|설명|
|--------------|-----------------|-----------------|
|[IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)|`DWORD`|값 중 하나는 [CV_access_e 열거형](../../debugger/debug-interface-access/cv-access-e.md)이면 함수는 멤버 함수입니다.|
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|위치 오프셋된 부분 자세한 내용은 참조는 [LocationType 열거형](../../debugger/debug-interface-access/locationtype.md)합니다.|
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|위치 섹션 부분 자세한 내용은 참조는 [LocationType 열거형](../../debugger/debug-interface-access/locationtype.md)합니다.|
|[IDiaSymbol::get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|`IDiaSymbol*`|함수는 멤버 함수는 클래스에 대 한 기호입니다.|
|[IDiaSymbol::get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|`DWORD`|ID 클래스 부모 기호입니다.|
|[IDiaSymbol::get_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE` 경우 함수는 상수로 표시 됩니다.|
|[IDiaSymbol::get_customCallingConvention](../../debugger/debug-interface-access/idiasymbol-get-customcallingconvention.md)|`BOOL`|`TRUE` 함수에서 사용자 지정 호출 규칙 (DIA SDK V8.0 이상 에서만)을 사용 하면|
|[IDiaSymbol::get_farReturn](../../debugger/debug-interface-access/idiasymbol-get-farreturn.md)|`BOOL`|`TRUE` 함수 수행 (DIA SDK V8.0 이상 에서만)까지 반환 합니다.|
|[IDiaSymbol::get_hasAlloca](../../debugger/debug-interface-access/idiasymbol-get-hasalloca.md)|`BOOL`|`TRUE` 함수는 할당 된 메모리 함수를 사용 하는 경우 (uinnder DIA SDK V8.0 이상).|
|[IDiaSymbol::get_hasEH](../../debugger/debug-interface-access/idiasymbol-get-haseh.md)|`BOOL`|`TRUE` 함수를 포함 하는 경우 C++-(DIA SDK V8.0 이상 에서만) 스타일 예외를 처리 합니다.|
|[IDiaSymbol::get_hasEHa](../../debugger/debug-interface-access/idiasymbol-get-haseha.md)|`BOOL`|`TRUE` 함수가 포함 된 경우 비동기 예외 처리 (DIA SDK V8.0 이상 에서만).|
|[IDiaSymbol::get_hasInlAsm](../../debugger/debug-interface-access/idiasymbol-get-hasinlasm.md)|`BOOL`|`TRUE` 함수가 포함 되어 있으면 인라인 어셈블리 (DIA SDK V8.0 이상 에서만).|
|[IDiaSymbol::get_hasLongJump](../../debugger/debug-interface-access/idiasymbol-get-haslongjump.md)|`BOOL`|`TRUE` 함수를 포함 하는 경우는 [longjmp](/cpp/c-runtime-library/reference/longjmp) (DIA SDK V8.0 이상 에서만)를 호출 합니다.|
|[IDiaSymbol::get_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|`BOOL`|`TRUE` 함수가 포함 되어 있으면 보안 검사 (DIA SDK V8.0 이상 에서만).|
|[IDiaSymbol::get_hasSEH](../../debugger/debug-interface-access/idiasymbol-get-hasseh.md)|`BOOL`|`TRUE` 함수가 포함 되어 있으면 Win32 스타일 구조적 예외 처리 (DIA SDK V8.0 이상 에서만).|
|[IDiaSymbol::get_hasSetJump](../../debugger/debug-interface-access/idiasymbol-get-hassetjump.md)|`BOOL`|`TRUE` 함수를 포함 하는 경우는 [setjmp](/cpp/c-runtime-library/reference/setjmp) (DIA SDK V8.0 이상 에서만)를 호출 합니다.|
|[IDiaSymbol::get_interruptReturn](../../debugger/debug-interface-access/idiasymbol-get-interruptreturn.md)|`BOOL`|`TRUE` 함수에 인터럽트 (DIA SDK V8.0 이상 에서만)에서 반환 하는 경우|
|[IDiaSymbol::get_intro](../../debugger/debug-interface-access/idiasymbol-get-intro.md)|`BOOL`|`TRUE` 함수를 소개 가상 인 경우|
|[IDiaSymbol::get_InlSpec](../../debugger/debug-interface-access/idiasymbol-get-inlspec.md)|`BOOL`|`TRUE` 함수 중 하나를 사용 하 여 표시 된 경우는 [인라인, __inline \__forceinline](/cpp/cpp/inline-functions-cpp) 특성입니다.|
|[IDiaSymbol::get_isNaked](../../debugger/debug-interface-access/idiasymbol-get-isnaked.md)|`BOOL`|`TRUE` 함수를 사용 하 여 표시 되 면 합니다 [naked](/cpp/cpp/naked-cpp) 특성 (DIA SDK V8.0 이상 에서만).|
|[IDiaSymbol::get_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|`BOOL`|`TRUE` 함수가 경우 정적 (DIA SDK V8.0 이상 에서만).|
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`ULONGLONG`|위치에서 시작 되는 함수 코드의 바이트 수입니다.|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|바깥쪽 compiland의 기호입니다.|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|어휘 부모 기호 ID입니다.|
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|함수는 정적 또는 메타 데이터 위치; 있습니다. 자세한 내용은 참조 하세요 [기호 위치](../../debugger/debug-interface-access/symbol-locations.md)합니다.|
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|함수의 이름입니다.|
|[IDiaSymbol::get_noInline](../../debugger/debug-interface-access/idiasymbol-get-noinline.md)|`BOOL`|`TRUE` 함수는 인라인 함수 없는 경우 (만 n DIA SDK V8.0 이상).|
|[IDiaSymbol::get_notReached](../../debugger/debug-interface-access/idiasymbol-get-notreached.md)|`BOOL`|`TRUE` 함수를 연결할 수 없는 경우 (DIA SDK V8.0 이상 에서만).|
|[IDiaSymbol::get_noReturn](../../debugger/debug-interface-access/idiasymbol-get-noreturn.md)|`BOOL`|`TRUE` 함수 (DIA SDK V8.0 이상 에서만) 값을 반환 하지 않으면.|
|[IDiaSymbol::get_noStackOrdering](../../debugger/debug-interface-access/idiasymbol-get-nostackordering.md)|`BOOL`|`TRUE` 버퍼 보안 검사를 사용 하 여 함수가 컴파일된 경우 스택 순서가 없다는 수행할 수 있습니다.|
|[IDiaSymbol::get_optimizedCodeDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-optimizedcodedebuginfo.md)|`BOOL`|`TRUE` 코드에 최적화 된 코드 (DIA SDK V8.0 이상 에서만)에 대 한 디버그 정보입니다.|
|[IDiaSymbol::get_pure](../../debugger/debug-interface-access/idiasymbol-get-pure.md)|`BOOL`|`TRUE` 함수는 순수 가상입니다.|
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|이 함수는 모듈 내에서 상대 위치입니다.|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|기호 인덱스 ID입니다.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|반환 `SymTagFunction` (중 하나는 [SymTagEnum 열거형](../../debugger/debug-interface-access/symtagenum.md) 값).|
|[IDiaSymbol::get_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)|`DWORD`|함수에 대 한 메타 데이터 토큰입니다.|
|[IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|함수 서명에 대해 기호입니다.|
|[IDiaSymbol::get_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|ID 형식 기호입니다.|
|[IDiaSymbol::get_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE` 함수는 정렬 되지 않습니다.|
|[IDiaSymbol::get_undecoratedName](../../debugger/debug-interface-access/idiasymbol-get-undecoratedname.md)|`BSTR`|데코 레이트 되지 않은 형태의 함수 이름 (DIA SDK v8.0 이상 에서만)|
|[IDiaSymbol::get_undecoratedNameEx](../../debugger/debug-interface-access/idiasymbol-get-undecoratednameex.md)|`BSTR`|일부 또는 전체를 데코 레이트 되지 않은 형태의 함수 이름 (DIA SDK v8.0 이상 에서만).|
|[IDiaSymbol::get_virtual](../../debugger/debug-interface-access/idiasymbol-get-virtual.md)|`BOOL`|`TRUE` 가상 함수입니다.|
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|실행 가능 이미지 내에서이 함수의 위치입니다.|
|[IDiaSymbol::get_virtualBaseOffset](../../debugger/debug-interface-access/idiasymbol-get-virtualbaseoffset.md)|`DWORD`|가상 함수를 다음 가상 함수 테이블의 오프셋입니다.|
|[IDiaSymbol::get_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE` 경우 함수는 volatile로 표시 됩니다.|

## <a name="see-also"></a>참고 항목
- [CV_access_e 열거형](../../debugger/debug-interface-access/cv-access-e.md)
- [기호 형식의 어휘 계층 구조](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
- [LocationType 열거형](../../debugger/debug-interface-access/locationtype.md)
- [기호 위치](../../debugger/debug-interface-access/symbol-locations.md)