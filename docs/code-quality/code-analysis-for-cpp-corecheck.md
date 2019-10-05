---
title: C++ Core Guidelines에 대한 정보
ms.date: 03/22/2018
ms.topic: reference
helpviewer_keywords:
- code analysis, C++ core check
ms.assetid: f1429463-136e-41ed-8a75-a8dbf0b4fd89
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: 0b725d0ee49590062ebdde9a1ef27f838678ccf5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62540796"
---
# <a name="c-core-guidelines-checker-reference"></a>C++ Core Guidelines에 대한 정보

이 섹션에서는 C++ 핵심 지침 검사기 경고를 나열합니다. 코드 분석에 대 한 자세한 내용은 [/analyze (코드 분석)](/cpp/build/reference/analyze-code-analysis) 고 [빠른 시작: C 용 코드 분석 /C++](../code-quality/quick-start-code-analysis-for-c-cpp.md)합니다.

> [!NOTE]
> 일부 경고 둘 이상의 그룹에 속하고 모든 경고의 경우에 완전 한 참조 항목입니다.

## <a name="ownerpointer-group"></a>OWNER_POINTER 그룹

[C26402 DONT_HEAP_ALLOCATE_MOVABLE_RESULT](C26402.md) 는 이동 생성자가 하는 경우 힙 할당 하는 대신 범위 개체를 반환 합니다. 참조 [C++ Core Guidelines R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr)합니다.

[C26403 RESET_OR_DELETE_OWNER](C26403.md) 다시 설정 하거나 소유자를 명시적으로 삭제\<T > 포인터 '% 변수 %'. 참조 [C++ Core Guidelines R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr)합니다.

[C26404 DONT_DELETE_INVALID](C26404.md) 소유자를 삭제 하지 마십시오\<T >는 잘못 된 상태일에서 수 있습니다. 참조 [C++ Core Guidelines R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr)합니다.

[C26405 DONT_ASSIGN_TO_VALID](C26405.md) 소유자에 할당 하지 않으면\<T >는 유효한 상태일 수 있습니다. 참조 [C++ Core Guidelines R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr)합니다.

[C26406 DONT_ASSIGN_RAW_TO_OWNER](C26406.md) 소유자에 대 한 원시 포인터를 할당 하지 마십시오\<T >입니다. 참조 [C++ Core Guidelines R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr)합니다.

[C26407 DONT_HEAP_ALLOCATE_UNNECESSARILY](C26407.md) 범위 개체, 하지 힙 할당 불필요 하 게 합니다. 참조 [C++ Core Guidelines R.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped)합니다.

[C26429 USE_NOTNULL](C26429.md) '% 기호 %' 기호는 nullness에 대해 테스트 되지, not_null로 표시할 수 있습니다. 참조 [C++ Core Guidelines F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value)합니다.

[C26430 TEST_ON_ALL_PATHS](C26430.md) 기호 '% 기호 %'은 모든 경로에서 nullness에 대해 테스트 되지 않았습니다. 참조 [C++ Core Guidelines F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value)합니다.

[C26431 DONT_TEST_NOTNULL](C26431.md) 식 '%expr% '의 형식은 이미 gsl:: not_null입니다. Nullness에 대해 테스트 하지 마십시오. 참조 [C++ Core Guidelines F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value)합니다.

## <a name="rawpointer-group"></a>RAW_POINTER 그룹

[C26400 NO_RAW_POINTER_ASSIGNMENT](c26400.md) 소유자를 사용 하 여 함수 호출 또는 할당의 결과 할당 하지 마세요\<T >를 원시 포인터 값을 반환; 소유자를 사용 하 여\<T > 대신 합니다. 참조 [C++ Core Guidelines I.11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Ri-raw)합니다.

[C26401 DONT_DELETE_NON_OWNER](c26401.md) 소유자가 아닌 원시 포인터를 삭제 하지 마십시오\<T >입니다. 참조 [C++ Core Guidelines I.11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Ri-raw)합니다.

[C26402 DONT_HEAP_ALLOCATE_MOVABLE_RESULT](C26402.md)  는 이동 생성자가 하는 경우 힙 할당 하는 대신 범위 개체를 반환 합니다. 참조 [C++ Core Guidelines R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr)합니다.

[C26408 NO_MALLOC_FREE](C26408.md) malloc () 및 free () 방지, 삭제 함께 new의 nothrow 버전을 선호 합니다. 참조 [C++ Core Guidelines R.10](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-mallocfree)합니다.

[C26409 NO_NEW_DELETE](C26409.md) 새 호출을 방지 하 고 명시적으로 삭제 않고\<T > 대신 합니다. 참조 [C++ Core Guidelines 합니다 (r.11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-newdelete)합니다.

[C26429 USE_NOTNULL](C26429.md) '% 기호 %' 기호는 nullness에 대해 테스트 되지, not_null로 표시할 수 있습니다. 참조 [C++ Core Guidelines F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value)합니다.

[C26430 TEST_ON_ALL_PATHS](C26430.md) 기호 '% 기호 %'은 모든 경로에서 nullness에 대해 테스트 되지 않았습니다. 참조 [C++ Core Guidelines F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value)합니다.

[C26431 DONT_TEST_NOTNULL](C26431.md) 식 '%expr% '의 형식은 이미 gsl:: not_null입니다. Nullness에 대해 테스트 하지 마십시오. 참조 [C++ Core Guidelines F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value)합니다.

[C26481 NO_POINTER_ARITHMETIC](C26481.md) 포인터 산술 연산을 사용 하지 마세요. 범위를 대신 사용 합니다. 참조 [C++ 핵심 지침 합니다 (bounds.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)합니다.

[C26485 NO_ARRAY_TO_POINTER_DECAY](C26485.md)합니다.
식 '%expr% '. 없는 배열에서 포인터로 감소 합니다. 참조 [C++ 핵심 지침 Bounds.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)합니다.

## <a name="uniquepointer-group"></a>UNIQUE_POINTER 그룹

[C26410 NO_REF_TO_CONST_UNIQUE_PTR](C26410.md) 매개 변수 '% 매개 변수 %'에 대 한 참조는 `const` 고유 포인터 대신 const T * 또는 const T &를 사용 합니다. 참조 [C++ Core Guidelines R.32](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-uniqueptrparam)합니다.

[C26411 NO_REF_TO_UNIQUE_PTR](C26411.md) '매개 변수 % %' 매개 변수는 고유 포인터에 대 한 참조 이며 다시 할당 되거나 다시 설정, 대신 T * 또는 T &를 사용 합니다. 참조 [C++ Core Guidelines R.33](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-reseat)합니다.

[C26414 RESET_LOCAL_SMART_PTR](C26414.md) 이동, 복사, 다시 할당 또는 '% 기호 %'와 같은 로컬 스마트 포인터 다시 설정 합니다. 참조 [C++ Core Guidelines R.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped)합니다.

[C26415 SMART_PTR_NOT_NEEDED](C26415.md) 스마트 포인터 매개 변수 '% 기호 %'는 포함 된 포인터를 액세스할 때만 사용 합니다. 대신 T \* 또는 T &를 사용 합니다. 참조 [C++ Core Guidelines 합니다 r.30](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-smartptrparam)합니다.

## <a name="sharedpointer-group"></a>SHARED_POINTER 그룹

[C26414 RESET_LOCAL_SMART_PTR](C26414.md) 이동, 복사, 다시 할당 또는 '% 기호 %'와 같은 로컬 스마트 포인터 다시 설정 합니다. 참조 [C++ Core Guidelines R.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped)합니다.

[C26415 SMART_PTR_NOT_NEEDED](C26415.md) 스마트 포인터 매개 변수 '% 기호 %'는 포함 된 포인터를 액세스할 때만 사용 합니다. 대신 T \* 또는 T &를 사용 합니다. 참조 [C++ Core Guidelines 합니다 r.30](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-smartptrparam)합니다.

[C26416 NO_RVALUE_REF_SHARED_PTR](C26416.md) 공유 포인터 매개 변수 '% 기호 %'는 rvalue 참조로 전달 됩니다. 대신 값으로 전달 합니다. 참조 [C++ Core Guidelines 하세요 (r.34](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam-owner)합니다.

[C26417 NO_LVALUE_REF_SHARED_PTR](C26417.md) 공유 포인터 매개 변수 '% 있는 기호' 참조로 전달 하 고 다시 설정 되지 않습니다 또는 다시 할당 합니다. 대신 T \* 또는 T &를 사용 합니다. 참조 [C++ Core Guidelines 하세요 (r.35](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam)합니다.

[C26418 NO_VALUE_OR_CONST_REF_SHARED_PTR](C26418.md) 공유 포인터 매개 변수 '% 기호 %'을 복사 하거나 이동 하지 않습니다. 대신 T \* 또는 T &를 사용 합니다. 참조 [C++ Core Guidelines 하세요 (r.36](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam-const)합니다.

## <a name="declaration-group"></a>선언 그룹

[C26426 NO_GLOBAL_INIT_CALLS](C26426.md) 전역 이니셜라이저가 constexpr이 아닌 함수 '% 기호 %'를 호출 합니다. 참조 [C++ Core Guidelines I.22](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i22-avoid-complex-initialization-of-global-objects)합니다.

[C26427 NO_GLOBAL_INIT_EXTERNS](C26427.md) 전역 이니셜라이저가 extern 개체 '% 기호 %'에 액세스 합니다. 참조 [C++ Core Guidelines I.22](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i22-avoid-complex-initialization-of-global-objects)합니다.

[C26444 NO_UNNAMED_RAII_OBJECTS](c26444.md) 사용자 지정 생성 및 소멸을 사용 하 여 개체를 명명 되지 않은 하지 마십시오. 참조 [않습니다 (es.84: 안 함 (시도) 이름이 없는 지역 변수 선언](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md)합니다.

## <a name="class-group"></a>클래스 그룹

[C26432 DEFINE_OR_DELETE_SPECIAL_OPS](C26432.md) 을 정의 하거나 기본 작업 형식 '% 기호 %'를 삭제 하는 경우 정의 또는 모두를 삭제 합니다. 참조 [C++ Core Guidelines C.21](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c21-if-you-define-or-delete-any-default-operation-define-or-delete-them-all)합니다.

[C26433 OVERRIDE_EXPLICITLY](c26433.md) 함수 '% 기호 %'는 'override'으로 표시 되어야 합니다. 참조 [C.128: 가상 함수는 정확히 하나의 가상, 재정의 또는 최종 지정 해야](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c128-virtual-functions-should-specify-exactly-one-of-virtual-override-or-final)합니다.

[C26434 DONT_HIDE_METHODS](C26434.md) 함수 '%symbol_1% '는 비가상 함수 '%symbol_2% '를 숨깁니다. 참조 [C++ Core Guidelines C.128](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c128-virtual-functions-should-specify-exactly-one-of-virtual-override-or-final)합니다.

[C26435 SINGLE_VIRTUAL_SPECIFICATION](c26435.md) 함수 '% 기호 %'는 'virtual', 'override' 또는 '최종' 중 하나만 지정 해야 합니다. 참조 [C.128: 가상 함수는 정확히 하나의 가상, 재정의 또는 최종 지정 해야](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md)합니다.

[C26436 NEED_VIRTUAL_DTOR](C26436.md) 가상 함수를 사용 하 여 ' % 기호 %' 형식에는 두 공용 가상 또는 보호 된 비가상 소멸자 필요 합니다. 참조 [C++ Core Guidelines가 필요 합니다 (c.35](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c35-a-base-class-destructor-should-be-either-public-and-virtual-or-protected-and-nonvirtual)합니다.

[C26443 NO_EXPLICIT_DTOR_OVERRIDE](c26443.md) 재정의 소멸자 명시적인 'override' 또는 'virtual' 지정자를 사용 하지 않아야 합니다. 참조 [C.128: 가상 함수는 정확히 하나의 가상, 재정의 또는 최종 지정 해야](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md)합니다.

## <a name="type-group"></a>형식 그룹

[C26437 DONT_SLICE](C26437.md) 조각화 하지 않습니다. 참조 [C++ Core Guidelines ES.63](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es63-dont-slice)합니다.

## <a name="style-group"></a>스타일 그룹

[C26438 NO_GOTO](C26438.md) 방지 `goto`합니다. 참조 [C++ Core Guidelines ES.76](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es76-avoid-goto)합니다.

## <a name="function-group"></a>함수 그룹

[C26439 SPECIAL_NOEXCEPT](C26439.md) 이 종류의 함수가 throw 할 수 있습니다. 선언 `noexcept`합니다. 참조 [C++ Core Guidelines F.6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept)합니다.

[C26440 DECLARE_NOEXCEPT](C26440.md) '기호 % %' 함수를 선언할 수 있습니다 `noexcept`합니다. 참조 [C++ Core Guidelines F.6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept)합니다.

[C26447 DONT_THROW_IN_NOEXCEPT](c26447.md) 선언 **noexcept** 하지만 예외를 throw 할 수 있는 함수를 호출 합니다.
참조 [ C++ 핵심 지침:  F.6: 함수가 throw 할 수 있으면 선언 noexcept](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept)합니다.

## <a name="concurrency-group"></a>동시성 그룹

[C26441 NO_UNNAMED_GUARDS](C26441.md) 가드 개체 이름을 지정 해야 합니다. 참조 [C++ 핵심 지침 cp.44](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#cp44-remember-to-name-your-lock_guards-and-unique_locks)합니다.

## <a name="const-group"></a>CONST 그룹

[C26460 USE_CONST_REFERENCE_ARGUMENTS](c26460.md) 함수 '% 함수 %'에 대 한 참조 인수 '% 인수 %'로 표시할 수 있습니다 `const`합니다. 참조 [C++ 핵심 지침 con.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-ref)합니다.

[C26461 USE_CONST_POINTER_ARGUMENTS](c26461.md): 함수 '% 함수 %'에 대 한 포인터 인수 '% 인수 %'에 대 한 포인터로 표시할 수 있습니다 `const`합니다. 참조 [C++ 핵심 지침 con.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-ref)합니다.

[C26462 USE_CONST_POINTER_FOR_VARIABLE](c26462.md) '% 변수 %'에서 가리키는 값은 한 번만 할당에 대 한 포인터로 표시 `const`합니다. 참조 [C++ 핵심 지침 con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction)합니다.

[C26463 USE_CONST_FOR_ELEMENTS](c26463.md) 배열 '% 배열 %'의 요소를 한 번만 표시 요소 할당 된 `const`합니다. 참조 [C++ 핵심 지침 con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction)합니다.

[C26464 USE_CONST_POINTER_FOR_ELEMENTS](c26464.md) '% 있는 배열' 배열의 요소로 가리킨 값은 한 번만 표시 요소에 대 한 포인터를 할당 됩니다 `const`합니다. 참조 [C++ 핵심 지침 con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction)합니다.

[C26496 USE_CONST_FOR_VARIABLE](c26496.md) 변수가 '% 변수 %' 한 번만 할당, 표시로 `const`합니다. 참조 [C++ 핵심 지침 con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction)합니다.

[C26497 USE_CONSTEXPR_FOR_FUNCTION](c26497.md) 이 함수가 함수 %로 표시할 수 있습니다 `constexpr` 컴파일 시간 계산이 필요한 경우. 참조 [C++ Core Guidelines F.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rf-constexpr)합니다.

[C26498 USE_CONSTEXPR_FOR_FUNCTIONCALL](c26498.md) 이 함수 호출 함수 % 따르면 `constexpr` 컴파일 시간 계산이 필요한 경우. 참조 [C++ 핵심 지침 con.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-constexpr)합니다.

## <a name="type-group"></a>형식 그룹

[C26465 NO_CONST_CAST_UNNECESSARY](c26465.md) 사용 하지 마세요 `const_cast` 캐스팅 하 `const`합니다. `const_cast` 필요 없음. 상수 성 또는 변동성이이 변환으로 제거 되지 않습니다. 참조 [C++ 핵심 지침 Type.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-constcast)합니다.

[C26466 NO_STATIC_DOWNCAST_POLYMORPHIC](c26466.md) 사용 하지 않는 `static_cast` 다운 캐스트 합니다. 다형 형식에서 캐스팅은 dynamic_cast을 사용 해야 합니다. 참조 [C++ 핵심 지침 Type.2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-downcast)합니다.

[C26471 NO_REINTERPRET_CAST_FROM_VOID_PTR](c26471.md) 사용 하지 않는 `reinterpret_cast`합니다. Void *에서 캐스트를 사용 하 여 수 `static_cast`입니다. 참조 [C++ 핵심 지침 Type.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast)합니다.

[C26472 NO_CASTS_FOR_ARITHMETIC_CONVERSION](C26472.md) 사용 하지 않는 한 `static_cast` 산술 변환에 대 한 합니다. 중괄호 초기화, gsl:: narrow_cast를 사용 합니다. 참조 [C++ 핵심 지침 Type.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast)합니다.

[C26473 NO_IDENTITY_CAST](C26473.md) 소스 형식과 대상 형식이 있는 동일한 포인터 형식 간에 캐스트 하지 않습니다. 참조 [C++ 핵심 지침 Type.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast)합니다.

[C26474 NO_IMPLICIT_CAST](C26474.md) 변환이 암시적 일 수 있습니다 있을 때는 포인터 형식 간에 캐스트 하지 않습니다. 참조 [C++ 핵심 지침 Type.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast)합니다.

[C26475 NO_FUNCTION_STYLE_CASTS](C26475.md) 함수 스타일 C 캐스트를 사용 하지 마세요. 참조 [C++ Core Guidelines ES.49](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es49-if-you-must-use-a-cast-use-a-named-cast)합니다.

[C26490 NO_REINTERPRET_CAST](c26490.md) 사용 하지 않는 `reinterpret_cast`합니다. 참조 [C++ 핵심 지침 Type.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type)합니다.

[C26491 NO_STATIC_DOWNCAST](c26490.md) 사용 하지 않는 `static_cast` 다운 캐스트 합니다. 참조 [C++ 핵심 지침 Type.2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type)합니다.

[C26492 NO_CONST_CAST](c26492.md) 사용 하지 마세요 `const_cast` 캐스팅 하 `const`합니다. 참조 [C++ 핵심 지침 Type.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type)합니다.

[C26493 NO_CSTYLE_CAST](c26493.md) C 스타일 캐스트를 사용 하지 마세요. 참조 [C++ 핵심 지침 않습니다 (type.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type)합니다.

[C26494 VAR_USE_BEFORE_INIT](c26494.md) 변수 '% 변수 %'가 초기화 되지 않습니다. 항상 개체를 초기화 합니다. 참조 [C++ 핵심 지침 하세요 (type.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type)합니다.

[C26495 MEMBER_UNINIT](c26495.md) 변수 '% 변수 %'가 초기화 되지 않습니다. 항상 멤버 변수를 초기화 합니다. 참조 [C++ 핵심 지침 Type.6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type)합니다.

## <a name="bounds-group"></a>범위 그룹

[C26446 USE_GSL_AT](c26446.md) 사용을 선호 `gsl::at()` 검사 되지 않은 아래 첨자 연산자 대신 합니다. 참조 [ C++ 핵심 지침:  Bounds.4: 표준 라이브러리 함수 및 범위 선택 되지 않은 형식을 사용 하지 않는](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile)합니다.

[C26481 NO_POINTER_ARITHMETIC](C26481.md)합니다.
포인터 산술 연산을 사용 하지 마세요. 범위를 대신 사용 합니다. 참조 [C++ Core 지침 합니다 (bounds.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26482 NO_DYNAMIC_ARRAY_INDEXING](c26482.md) 상수 식을 사용 하는 배열로 인덱스입니다. 참조 [C++ Core 지침 Bounds.2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26483 STATIC_INDEX_OUT_OF_RANGE](c26483.md) 값 % 값 범위를 벗어납니다 (0, 바인딩된 %) 변수 '% 변수 %'. 배열 범위 내에 있는 상수 식을 사용 하는 배열로 인덱싱. 참조 [C++ Core 지침 Bounds.2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26485 NO_ARRAY_TO_POINTER_DECAY](C26485.md) 식 '%expr% '. 없는 배열에서 포인터로 감소 합니다. 참조 [C++ Core 지침 Bounds.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

## <a name="gsl-group"></a>GSL 그룹

[C26445 NO_SPAN_REF](c26445.md) 에 대 한 참조가 `gsl::span` 또는 `std::string_view` 수명 문제를 나타낼 수 있습니다.
참조 [ C++ 지침 GSL.view 핵심: 레이아웃](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#gslview-views)

[C26446 USE_GSL_AT](c26446.md) 사용을 선호 `gsl::at()` 검사 되지 않은 아래 첨자 연산자 대신 합니다. 참조 [ C++ 핵심 지침:  Bounds.4: 표준 라이브러리 함수 및 범위 선택 되지 않은 형식을 사용 하지 않는](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile)합니다.

[C26448 USE_GSL_FINALLY](c26448.md) 사용해 보세요 `gsl::finally` 사용 되는 최종 동작 합니다. 참조 [ C++ 핵심 지침:  GSL.util: 유틸리티](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-utilities)합니다.

[C26449 NO_SPAN_FROM_TEMPORARY](c26449.md) 
 `gsl::span` 또는 `std::string_view` 임시에서 만든 유효 하지 않게 됩니다 때 임시 무효화 됩니다. 참조 [ C++ 핵심 지침: GSL.view: 뷰](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#gslview-views)합니다.

## <a name="deprecated-warnings"></a>사용 되지 않는 경고

다음 경고 핵심 지침 검사기는 초기 실험적 규칙 집합에 있는 있지만 이제 되지 않으며 무시 해도 됩니다. 경고는 위의 목록에서 경고로 대체 됩니다.

- 26412 DEREF_INVALID_POINTER
- 26413 DEREF_NULLPTR
- 26420 ASSIGN_NONOWNER_TO_EXPLICIT_OWNER
- 26421 ASSIGN_VALID_OWNER
- 26422 VALID_OWNER_LEAVING_SCOPE
- 26423 ALLOCATION_NOT_ASSIGNED_TO_OWNER
- 26424 VALID_ALLOCATION_LEAVING_SCOPE
- 26425 ASSIGNING_TO_STATIC
- 26499 NO_LIFETIME_TRACKING

## <a name="see-also"></a>참고 항목
[C++ Core Guidelines 이용한 코드검사 사용](using-the-cpp-core-guidelines-checkers.md)
