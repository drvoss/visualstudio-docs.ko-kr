---
title: IDiaSymbol | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol interface
ms.assetid: 01ad328a-736c-4933-a9f8-c2ded19ddd8c
caps.latest.revision: 33
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7c9b267893bacef8c9126b1a17b4eb444af6a1dd
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/12/2019
ms.locfileid: "65692894"
---
# <a name="idiasymbol"></a>IDiaSymbol
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

기호 인스턴스의 속성을 설명합니다.  
  
## <a name="syntax"></a>구문  
  
```  
IDiaSymbol : IUnknown  
```  
  
## <a name="methods-in-alphabetical-order"></a>알파벳 순서로 메서드  
 다음 표에서의 메서드를 보여 줍니다. `IDiaSymbol`합니다.  
  
> [!NOTE]
> 기호는 형식 기호에 따라 다음이 방법 중 일부에 대 한 의미 있는 데이터를 반환 합니다. 메서드가 반환 하는 경우 `S_OK`, 해당 메서드는 의미 있는 데이터를 반환 합니다.  
  
|메서드|Description|  
|------------|-----------------|  
|[IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)|기호의 모든 자식을 검색합니다.|  
|[IDiaSymbol::findChildrenEx](../../debugger/debug-interface-access/idiasymbol-findchildrenex.md)|기호의 자식을 검색합니다. 이 메서드는 확장 된 버전의 [idiasymbol:: Findchildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)합니다.|  
|[IDiaSymbol::findChildrenExByAddr](../../debugger/debug-interface-access/idiasymbol-findchildrenexbyaddr.md)|지정된 된 주소에서 사용할 수 있는 기호 자식을 검색 합니다.|  
|[IDiaSymbol::findChildrenExByRVA](../../debugger/debug-interface-access/idiasymbol-findchildrenexbyrva.md)|지정 된 상대 가상 주소 (RVA)에서 사용할 수 있는 기호 자식을 검색 합니다.|  
|[IDiaSymbol::findChildrenExByVA](../../debugger/debug-interface-access/idiasymbol-findchildrenexbyva.md)|지정된 된 가상 주소에서 사용할 수 있는 기호 자식을 검색 합니다.|  
|[IDiaSymbol::findInlineFramesByAddr](../../debugger/debug-interface-access/idiasymbol-findinlineframesbyaddr.md)|주어진된 주소에 있는 인라인 프레임의 모든 반복에 대 한 클라이언트를 허용 하는 열거자를 검색 합니다.|  
|[IDiaSymbol::findInlineFramesByRVA](../../debugger/debug-interface-access/idiasymbol-findinlineframesbyrva.md)|클라이언트가 지정 된 상대 가상 주소 (RVA)에 있는 인라인 프레임의 모든 반복 하는 데 사용 하는 열거형을 검색 합니다.|  
|[IDiaSymbol::findInlineFramesByVA](../../debugger/debug-interface-access/idiasymbol-findinlineframesbyva.md)|클라이언트가 지정된 된 가상 주소 (VA)에 있는 인라인 프레임의 모든 반복 하는 데 사용 하는 열거형을 검색 합니다.|  
|[IDiaSymbol::findInlineeLines](../../debugger/debug-interface-access/idiasymbol-findinlineelines.md)|클라이언트가 모든 없는 함수를 인라인 처리를 직접 또는 간접적으로이 기호는 줄 번호 정보를 반복 하는 데 사용 하는 열거형을 검색 합니다.|  
|[IDiaSymbol::findInlineeLinesByAddr](../../debugger/debug-interface-access/idiasymbol-findinlineelinesbyaddr.md)|클라이언트가 없는 인라인을 직접 또는 간접적으로이 기호를 지정 된 주소 범위 내에서 모든 함수의 줄 번호 정보를 반복 하는 데 사용 하는 열거형을 검색 합니다.|  
|[IDiaSymbol::findInlineeLinesByRVA](../../debugger/debug-interface-access/idiasymbol-findinlineelinesbyrva.md)|클라이언트가 없는 인라인을 직접 또는 간접적으로이 기호는 지정 된 가상 RVA (상대 주소) 내에서 모든 함수의 줄 번호 정보를 반복 하는 데 사용 하는 열거형을 검색 합니다.|  
|[IDiaSymbol::findInlineeLinesByVA](../../debugger/debug-interface-access/idiasymbol-findinlineelinesbyva.md)|클라이언트가 없는 인라인을 직접 또는 간접적으로이 기호는 지정 된 가상 주소 (VA) 내에서 모든 함수의 줄 번호 정보를 반복 하는 데 사용 하는 열거형을 검색 합니다.|  
|[IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasymbol-findsymbolsbyrvaforacceleratorpointertag.md)|이 메서드 해당 태그 값을 지정 합니다 지정된 된 상대 가상 주소에서이 스텁 함수에 포함 된 기호의 열거형을 반환 합니다.|  
|[IDiaSymbol::findSymbolsForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasymbol-findsymbolsforacceleratorpointertag.md)|Accelerator 포인터 태그의 수를 반환 합니다는 C++ AMP 스텁 함수입니다.|  
|[IDiaSymbol::get_acceleratorPointerTags](../../debugger/debug-interface-access/idiasymbol-get-acceleratorpointertags.md)|에 해당 하는 모든 가속기 포인터 태그 값을 반환 된 C++ AMP 액셀러레이터 스텁 함수입니다.|  
|[IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)|클래스 멤버의 액세스 한정자를 검색합니다.|  
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|주소 위치 오프셋된 부분을 검색합니다.|  
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|섹션에 대 한 부분 주소 위치를 검색합니다.|  
|[IDiaSymbol::get_addressTaken](../../debugger/debug-interface-access/idiasymbol-get-addresstaken.md)|다른 기호가이 주소를 참조 하는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_age](../../debugger/debug-interface-access/idiasymbol-get-age.md)|프로그램 데이터베이스의 보존 기간 값을 검색합니다.|  
|[IDiaSymbol::get_arrayIndexType](../../debugger/debug-interface-access/idiasymbol-get-arrayindextype.md)|배열 인덱스 유형의 기호 식별자를 검색합니다.|  
|[IDiaSymbol::get_arrayIndexTypeId](../../debugger/debug-interface-access/idiasymbol-get-arrayindextypeid.md)|기호의 배열 인덱스 형식 식별자를 검색합니다.|  
|[IDiaSymbol::get_backEndMajor](../../debugger/debug-interface-access/idiasymbol-get-backendmajor.md)|백 엔드 주 버전 번호를 검색합니다.|  
|[IDiaSymbol::get_backEndMinor](../../debugger/debug-interface-access/idiasymbol-get-backendminor.md)|백 엔드 부 버전 번호를 검색합니다.|  
|[IDiaSymbol::get_backEndBuild](../../debugger/debug-interface-access/idiasymbol-get-backendbuild.md)|백 엔드 빌드 번호를 검색합니다.|  
|[IDiaSymbol::get_baseDataOffset](../../debugger/debug-interface-access/idiasymbol-get-basedataoffset.md)|기본 데이터 오프셋을 검색합니다.|  
|[IDiaSymbol::get_baseDataSlot](../../debugger/debug-interface-access/idiasymbol-get-basedataslot.md)|기본 데이터 슬롯을 검색합니다.|  
|[IDiaSymbol::get_baseSymbol](../../debugger/debug-interface-access/idiasymbol-get-basesymbol.md)|포인터 기반 기호를 검색 합니다.|  
|[IDiaSymbol::get_baseSymbolId](../../debugger/debug-interface-access/idiasymbol-get-basesymbolid.md)|포인터 기반 기호 ID를 검색 합니다.|  
|[IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)|단순 형식의 형식 태그를 검색합니다.|  
|[IDiaSymbol::get_bitPosition](../../debugger/debug-interface-access/idiasymbol-get-bitposition.md)|위치의 비트 위치를 검색합니다.|  
|[IDiaSymbol::get_builtInKind](../../debugger/debug-interface-access/idiasymbol-get-builtinkind.md)|HLSL 형식의 기본 종류를 검색합니다.|  
|[IDiaSymbol::get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)|메서드의 호출 규칙의 표시기를 반환합니다.|  
|[IDiaSymbol::get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|기호의 클래스 부모에 대 한 참조를 검색합니다.|  
|[IDiaSymbol::get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|기호의 클래스 부모 식별자를 검색합니다.|  
|[IDiaSymbol::get_code](../../debugger/debug-interface-access/idiasymbol-get-code.md)|기호 코드 주소를 참조 하는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_compilerGenerated](../../debugger/debug-interface-access/idiasymbol-get-compilergenerated.md)|기호 컴파일러에서 생성 되었는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_compilerName](../../debugger/debug-interface-access/idiasymbol-get-compilername.md)|만드는 데 사용 하는 컴파일러의 이름을 검색 합니다 [Compiland](../../debugger/debug-interface-access/compiland.md)합니다.|  
|[IDiaSymbol::get_constructor](../../debugger/debug-interface-access/idiasymbol-get-constructor.md)|사용자 정의 데이터 형식에 생성자가 있는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_container](../../debugger/debug-interface-access/idiasymbol-get-container.md)|이 기호의 기호를 포함 하 여 검색합니다.|  
|[IDiaSymbol::get_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|사용자 정의 데이터 형식이 상수 인지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_count](../../debugger/debug-interface-access/idiasymbol-get-count.md)|목록 또는 배열에 있는 항목의 수를 검색 합니다.|  
|[IDiaSymbol::get_countLiveRanges](../../debugger/debug-interface-access/idiasymbol-get-countliveranges.md)|로컬 기호를 사용 하 여 연결 하는 유효한 주소 범위 수를 검색 합니다.|  
|[IDiaSymbol::get_customCallingConvention](../../debugger/debug-interface-access/idiasymbol-get-customcallingconvention.md)|함수는 사용자 지정 호출 규칙을 사용 하는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_dataBytes](../../debugger/debug-interface-access/idiasymbol-get-databytes.md)|OEM 기호의 데이터 바이트를 검색합니다.|  
|[IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)|데이터 기호 변수 분류를 검색합니다.|  
|[IDiaSymbol::get_editAndContinueEnabled](../../debugger/debug-interface-access/idiasymbol-get-editandcontinueenabled.md)|단위는 컴파일된 프로그램의 편집 하며 계속 하기 기능을 설명 하는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_farReturn](../../debugger/debug-interface-access/idiasymbol-get-farreturn.md)|함수 사용을 훨씬 반환 하는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_frontEndMajor](../../debugger/debug-interface-access/idiasymbol-get-frontendmajor.md)|프런트 엔드 주 버전 번호를 검색합니다.|  
|[IDiaSymbol::get_frontEndMinor](../../debugger/debug-interface-access/idiasymbol-get-frontendminor.md)|프런트 엔드 부 버전 번호를 검색합니다.|  
|[IDiaSymbol::get_frontEndBuild](../../debugger/debug-interface-access/idiasymbol-get-frontendbuild.md)|프런트 엔드 빌드 번호를 검색합니다.|  
|[IDiaSymbol::get_function](../../debugger/debug-interface-access/idiasymbol-get-function.md)|공용 기호 함수를 참조 하는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_guid](../../debugger/debug-interface-access/idiasymbol-get-guid.md)|기호 GUID를 검색 합니다.|  
|[IDiaSymbol::get_hasAlloca](../../debugger/debug-interface-access/idiasymbol-get-hasalloca.md)|함수 호출을 포함 하는지 여부를 나타내는 플래그를 검색 `alloca`합니다.|  
|[IDiaSymbol::get_hasAssignmentOperator](../../debugger/debug-interface-access/idiasymbol-get-hasassignmentoperator.md)|사용자 정의 데이터 형식에 정의 된 모든 할당 연산자에 있는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_hasCastOperator](../../debugger/debug-interface-access/idiasymbol-get-hascastoperator.md)|사용자 정의 데이터 형식에 정의 된 모든 캐스트 연산자에 있는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_hasDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-hasdebuginfo.md)|컴파일 대상 디버깅 정보를 포함 하는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_hasEH](../../debugger/debug-interface-access/idiasymbol-get-haseh.md)|검색 함수에 있는지 여부를 나타내는 플래그를 C++-스타일 예외 처리기입니다.|  
|[IDiaSymbol::get_hasEHa](../../debugger/debug-interface-access/idiasymbol-get-haseha.md)|함수는 비동기 예외 처리기에 있는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_hasInlAsm](../../debugger/debug-interface-access/idiasymbol-get-hasinlasm.md)|함수를 인라인 어셈블리에 있는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_hasLongJump](../../debugger/debug-interface-access/idiasymbol-get-haslongjump.md)|함수 (C 스타일 예외 처리의 일부) longjmp 명령을 포함 되는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_hasManagedCode](../../debugger/debug-interface-access/idiasymbol-get-hasmanagedcode.md)|관리 코드 모듈에 포함 되는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_hasNestedTypes](../../debugger/debug-interface-access/idiasymbol-get-hasnestedtypes.md)|사용자 정의 데이터 형식에 중첩 된 형식을 정의 하는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|함수 또는 compiland에서 컴파일된 보안 검사에 있는지 여부를 나타내는 플래그를 검색 합니다 (통해 합니다 [/GS (버퍼 보안 검사)](https://msdn.microsoft.com/library/8d8a5ea1-cd5e-42e1-bc36-66e1cd7e731e) 컴파일러 스위치).|  
|[IDiaSymbol::get_hasSEH](../../debugger/debug-interface-access/idiasymbol-get-hasseh.md)|함수 스타일 Win32 구조적 예외 처리에 있는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_hasSetJump](../../debugger/debug-interface-access/idiasymbol-get-hassetjump.md)|Setjmp 명령 함수에 포함 되는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_indirectVirtualBaseClass](../../debugger/debug-interface-access/idiasymbol-get-indirectvirtualbaseclass.md)|사용자 정의 데이터 형식에는 간접 가상 기본 클래스 인지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_InlSpec](../../debugger/debug-interface-access/idiasymbol-get-inlspec.md)|인라인 특성을 사용 하 여 함수를 표시 되었는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_interruptReturn](../../debugger/debug-interface-access/idiasymbol-get-interruptreturn.md)|함수는 인터럽트 명령에서 반환 하는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_intro](../../debugger/debug-interface-access/idiasymbol-get-intro.md)|함수가 기본 클래스 가상 함수와 되는지를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_isAcceleratorGroupSharedLocal](../../debugger/debug-interface-access/idiasymbol-get-isacceleratorgroupsharedlocal.md)|기호에 대해 컴파일된 코드의 그룹 공유 지역 변수에 해당 하는지 여부를 나타내는 플래그를 검색 한 C++ AMP 액셀러레이터입니다.|  
|[IDiaSymbol::get_isAcceleratorPointerTagLiveRange](../../debugger/debug-interface-access/idiasymbol-get-isacceleratorpointertagliverange.md)|기호에 해당 하는지 여부를 나타내는 플래그를 검색 합니다 *정의 범위 기호* 에 대해 컴파일된 코드에서 변수 대 한 포인터의 태그 구성 요소를 C++ AMP 액셀러레이터입니다. 정의 범위 기호는 주소 범위에 대 한 변수의 위치입니다.|  
|[IDiaSymbol::get_isAcceleratorStubFunction](../../debugger/debug-interface-access/idiasymbol-get-isacceleratorstubfunction.md)|기호에 해당 하는 액셀러레이터 키에 대 한 컴파일된 셰이더에 대 한 최상위 함수 기호에 해당 하는지 여부를 나타냅니다는 `parallel_for_each` 호출 합니다.|  
|[IDiaSymbol::get_isAggregated](../../debugger/debug-interface-access/idiasymbol-get-isaggregated.md)|데이터 집계 많은 기호의 일부 인지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_isCTypes](../../debugger/debug-interface-access/idiasymbol-get-isctypes.md)|C 형식 기호 파일에 포함 되는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_isCVTCIL](../../debugger/debug-interface-access/idiasymbol-get-iscvtcil.md)|모듈에서 중간 언어 (CIL (공용)를 네이티브 코드로 변환 되었는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_isDataAligned](../../debugger/debug-interface-access/idiasymbol-get-isdataaligned.md)|사용자 정의 데이터 형식 요소의 특정 경계에 정렬 되는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_isHLSLData](../../debugger/debug-interface-access/idiasymbol-get-ishlsldata.md)|이 기호 셰이더 언어 HLSL (High Level) 데이터를 나타내는지 여부를 지정 합니다.|  
|[IDiaSymbol::get_isHotpatchable](../../debugger/debug-interface-access/idiasymbol-get-ishotpatchable.md)|모듈을 사용 하 여 컴파일된 여부를 나타내는 플래그를 검색 합니다 [/hotpatch (핫 패치 가능 이미지 만들기)](https://msdn.microsoft.com/library/aad539b6-c053-4c78-8682-853d98327798) 컴파일러 스위치입니다.|  
|[IDiaSymbol::get_isLTCG](../../debugger/debug-interface-access/idiasymbol-get-isltcg.md)|관리 되는 compiland 링커의 LTCG를 사용 하 여 연결 된 있는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_isMatrixRowMajor](../../debugger/debug-interface-access/idiasymbol-get-ismatrixrowmajor.md)|행렬 행 주요 인지 여부를 지정 합니다.|  
|[IDiaSymbol::get_isMSILNetmodule](../../debugger/debug-interface-access/idiasymbol-get-ismsilnetmodule.md)|관리 되는 컴파일 대상 (메타 데이터만 포함)에.netmodule 인지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_isMultipleInheritance](../../debugger/debug-interface-access/idiasymbol-get-ismultipleinheritance.md)|지정 여부는 `this` 다중 상속을 사용 하 여 데이터 멤버를 가리킵니다.|  
|[IDiaSymbol::get_isNaked](../../debugger/debug-interface-access/idiasymbol-get-isnaked.md)|함수에 있는지 여부를 나타내는 플래그를 검색 합니다 [naked](https://msdn.microsoft.com/library/69723241-05e1-439b-868e-20a83a16ab6d) 특성입니다.|  
|[IDiaSymbol::get_isOptimizedAway](../../debugger/debug-interface-access/idiasymbol-get-isoptimizedaway.md)|변수의 지금 최적화 되었는지 여부를 지정 합니다.|  
|[IDiaSymbol::get_isPointerBasedOnSymbolValue](../../debugger/debug-interface-access/idiasymbol-get-ispointerbasedonsymbolvalue.md)|지정 여부는 `this` 포인터 기호 값을 기반 합니다.|  
|[IDiaSymbol::get_isPointerToDataMember](../../debugger/debug-interface-access/idiasymbol-get-ispointertodatamember.md)|이 기호 데이터 멤버에 대 한 포인터 인지 여부를 지정 합니다.|  
|[IDiaSymbol::get_isPointerToMemberFunction](../../debugger/debug-interface-access/idiasymbol-get-ispointertomemberfunction.md)|이 기호는 멤버 함수에 대 한 포인터 인지 여부를 지정 합니다.|  
|[IDiaSymbol::get_isReturnValue](../../debugger/debug-interface-access/idiasymbol-get-isreturnvalue.md)|변수의 반환 값을 전달 하는지 여부를 지정 합니다.|  
|[IDiaSymbol::get_isSdl](../../debugger/debug-interface-access/idiasymbol-get-issdl.md)|모듈 /SDL 옵션을 사용 하 여 컴파일 되었는지 여부를 지정 합니다.|  
|[IDiaSymbol::get_isSingleInheritance](../../debugger/debug-interface-access/idiasymbol-get-issingleinheritance.md)|지정 여부는 `this` 단일 상속을 사용 하 여 데이터 멤버를 가리킵니다.|  
|[IDiaSymbol::get_isSplitted](../../debugger/debug-interface-access/idiasymbol-get-issplitted.md)|데이터를 별도 기호의 집계로 분할 되어 있습니다 있는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|함수 또는 썽크 레이어를 정적 인지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_isStripped](../../debugger/debug-interface-access/idiasymbol-get-isstripped.md)|기호 파일에서 전용 기호 제거 된 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_isVirtualInheritance](../../debugger/debug-interface-access/idiasymbol-get-isvirtualinheritance.md)|지정 여부는 `this` 가상 상속을 사용 하 여 데이터 멤버를 가리킵니다.|  
|[IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)|원본 언어를 검색합니다.|  
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|이 기호를 나타내는 개체에 의해 사용 된 메모리의 바이트 수를 검색 합니다.|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|기호의 어휘 부모에 대 한 참조를 검색합니다.|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|기호의 어휘 부모 식별자를 검색합니다.|  
|[IDiaSymbol::get_libraryName](../../debugger/debug-interface-access/idiasymbol-get-libraryname.md)|개체가 로드 된 라이브러리 또는 개체 파일의 파일 이름을 검색 합니다.|  
|[IDiaSymbol::get_liveRangeLength](../../debugger/debug-interface-access/idiasymbol-get-liverangelength.md)|로컬 기호 유효 주소 범위의 길이 반환 합니다.|  
|[IDiaSymbol::get_liveRangeStartAddressSection](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddresssection.md)|로컬 기호의 유효 시작 주소 범위의 섹션 부분을 반환 합니다.|  
|[IDiaSymbol::get_liveRangeStartAddressOffset](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddressoffset.md)|로컬 기호의 유효 시작 주소 범위의 오프셋된 부분을 반환 합니다.|  
|[IDiaSymbol::get_liveRangeStartRelativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-liverangestartrelativevirtualaddress.md)|로컬 기호 유효 주소 범위의 시작을 반환 합니다.|  
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|데이터 기호 위치 형식을 검색합니다.|  
|[IDiaSymbol::get_lowerBound](../../debugger/debug-interface-access/idiasymbol-get-lowerbound.md)|FORTRAN 배열 차원의 하한값을 검색합니다.|  
|[IDiaSymbol::get_lowerBoundId](../../debugger/debug-interface-access/idiasymbol-get-lowerboundid.md)|FORTRAN 배열 차원의 하한값의 기호 식별자를 검색합니다.|  
|[IDiaSymbol::get_machineType](../../debugger/debug-interface-access/idiasymbol-get-machinetype.md)|대상 CPU의 형식을 검색 합니다.|  
|[IDiaSymbol::get_managed](../../debugger/debug-interface-access/idiasymbol-get-managed.md)|기호 참조 하는지 여부를 나타내는 관리 코드는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_memorySpaceKind](../../debugger/debug-interface-access/idiasymbol-get-memoryspacekind.md)|메모리 공간 종류를 검색합니다.|  
|[IDiaSymbol::get_msil](../../debugger/debug-interface-access/idiasymbol-get-msil.md)|Microsoft MSIL (Intermediate Language) 코드 기호 참조 하는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|기호의 이름을 검색합니다.|  
|[IDiaSymbol::get_nested](../../debugger/debug-interface-access/idiasymbol-get-nested.md)|사용자 정의 데이터 형식에 중첩 되어 있는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_noInline](../../debugger/debug-interface-access/idiasymbol-get-noinline.md)|함수를 사용 하 여 표시 되는지 여부를 나타내는 플래그를 검색 합니다 [noinline](https://msdn.microsoft.com/library/f259d55b-dec7-4bde-8cf9-14521e4fdc42) 특성입니다.|  
|[IDiaSymbol::get_noReturn](../../debugger/debug-interface-access/idiasymbol-get-noreturn.md)|함수를 사용 하 여 선언 된 여부를 나타내는 플래그를 검색 합니다 [noreturn](https://msdn.microsoft.com/library/9c6517e5-22d7-4051-9974-3d2200ae4d1d) 특성입니다.|  
|[IDiaSymbol::get_noStackOrdering](../../debugger/debug-interface-access/idiasymbol-get-nostackordering.md)|스택 버퍼 검사의 일부로 스택 순서가 없다는 수행할 수 있는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_notReached](../../debugger/debug-interface-access/idiasymbol-get-notreached.md)|함수 또는 레이블은 달성 하지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_numberOfAcceleratorPointerTags](../../debugger/debug-interface-access/idiasymbol-get-numberofacceleratorpointertags.md)|Accelerator 포인터 태그의 수를 반환 합니다는 C++ AMP 스텁 함수입니다.|  
|[IDiaSymbol::get_numberOfModifiers](../../debugger/debug-interface-access/idiasymbol-get-numberofmodifiers.md)|원본 형식에 적용 되는 한정자의 수를 검색 합니다.|  
|[IDiaSymbol::get_numberOfRegisterIndices](../../debugger/debug-interface-access/idiasymbol-get-numberofregisterindices.md)|등록 하는 인덱스 수를 검색 합니다.|  
|[IDiaSymbol::get_numberOfRows](../../debugger/debug-interface-access/idiasymbol-get-numberofrows.md)|행렬의 행을 검색합니다.|  
|[IDiaSymbol::get_numberOfColumns](../../debugger/debug-interface-access/idiasymbol-get-numberofcolumns.md)|행렬의 열 개수를 검색합니다.|  
|[IDiaSymbol::get_objectFileName](../../debugger/debug-interface-access/idiasymbol-get-objectfilename.md)|개체 파일 이름을 검색합니다.|  
|[IDiaSymbol::get_objectPointerType](../../debugger/debug-interface-access/idiasymbol-get-objectpointertype.md)|클래스 메서드에 대 한 개체 포인터의 형식을 검색합니다.|  
|[IDiaSymbol::get_oemId](../../debugger/debug-interface-access/idiasymbol-get-oemid.md)|기호 검색 `oemId` 값입니다.|  
|[IDiaSymbol::get_oemSymbolId](../../debugger/debug-interface-access/idiasymbol-get-oemsymbolid.md)|기호 검색 `oemSymbolId` 값입니다.|  
|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|기호 위치 오프셋을 검색합니다.|  
|[IDiaSymbol::get_optimizedCodeDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-optimizedcodedebuginfo.md)|함수 또는 레이블 최적화 된 코드를 포함 되는지 여부를 나타내는 플래그를 검색 합니다. 구성 파일 뿐만 아니라 디버그 정보입니다.|  
|[IDiaSymbol::get_overloadedOperator](../../debugger/debug-interface-access/idiasymbol-get-overloadedoperator.md)|사용자 정의 데이터 형식에 연산자가 오버 로드 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_packed](../../debugger/debug-interface-access/idiasymbol-get-packed.md)|이 사용자 정의 데이터 형식으로 압축 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_platform](../../debugger/debug-interface-access/idiasymbol-get-platform.md)|프로그램 또는 compiland 컴파일된 플랫폼 형식을 검색 합니다.|  
|[IDiaSymbol::get_pure](../../debugger/debug-interface-access/idiasymbol-get-pure.md)|순수 함수 인지 여부를 나타내는 플래그를 검색 합니다. 가상입니다.|  
|[IDiaSymbol::get_rank](../../debugger/debug-interface-access/idiasymbol-get-rank.md)|FORTRAN 다차원 배열의 순위를 검색합니다.|  
|[IDiaSymbol::get_reference](../../debugger/debug-interface-access/idiasymbol-get-reference.md)|포인터 형식에 대 한 참조 인지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_registerId](../../debugger/debug-interface-access/idiasymbol-get-registerid.md)|위치의 등록 지정자를 검색합니다.|  
|[IDiaSymbol::get_registerType](../../debugger/debug-interface-access/idiasymbol-get-registertype.md)|등록 형식을 검색합니다.|  
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|위치의 상대 가상 주소 RVA ()를 검색합니다.|  
|[IDiaSymbol::get_restrictedType](../../debugger/debug-interface-access/idiasymbol-get-restrictedtype.md)|지정 여부는 `this` 포인터 플래그가 지정 되어 제한으로.|  
|[IDiaSymbol::get_samplerSlot](../../debugger/debug-interface-access/idiasymbol-get-samplerslot.md)|샘플러 슬롯을 검색합니다.|  
|[IDiaSymbol::get_scoped](../../debugger/debug-interface-access/idiasymbol-get-scoped.md)|비전역 어휘 범위에서 사용자 정의 데이터 형식에 표시 되는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_signature](../../debugger/debug-interface-access/idiasymbol-get-signature.md)|기호 서명 값을 검색합니다.|  
|[IDiaSymbol::get_sizeInUdt](../../debugger/debug-interface-access/idiasymbol-get-sizeinudt.md)|사용자 정의 형식 멤버의 크기를 검색합니다.|  
|[IDiaSymbol::get_slot](../../debugger/debug-interface-access/idiasymbol-get-slot.md)|위치의 슬롯 번호를 검색합니다.|  
|[IDiaSymbol::get_sourceFileName](../../debugger/debug-interface-access/idiasymbol-get-sourcefilename.md)|소스 파일의 파일 이름을 검색합니다.|  
|[IDiaSymbol::getSrcLineOnTypeDefn](../../debugger/debug-interface-access/idiasymbol-getsrclineontypedefn.md)|지정 된 사용자 정의 형식이 정의 되어 있는 나타내는 소스 파일과 줄 번호를 검색 합니다.|  
|[IDiaSymbol::get_stride](../../debugger/debug-interface-access/idiasymbol-get-stride.md)|행렬 또는 strided 배열의 stride를 검색합니다.|  
|[IDiaSymbol::get_subType](../../debugger/debug-interface-access/idiasymbol-get-subtype.md)|하위 유형을 검색합니다.|  
|[IDiaSymbol::get_subTypeId](../../debugger/debug-interface-access/idiasymbol-get-subtypeid.md)|하위 형식 ID를 검색합니다.|  
|[IDiaSymbol::get_symbolsFileName](../../debugger/debug-interface-access/idiasymbol-get-symbolsfilename.md)|로드 된 기호는 파일의 이름을 검색 합니다.|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|고유한 기호 식별자를 검색합니다.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|기호 형식 분류자를 검색합니다.|  
|[IDiaSymbol::get_targetOffset](../../debugger/debug-interface-access/idiasymbol-get-targetoffset.md)|썽크 대상 오프셋된 부분을 검색합니다.|  
|[IDiaSymbol::get_targetRelativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-targetrelativevirtualaddress.md)|썽크 대상의 상대 가상 주소 RVA ()를 검색합니다.|  
|[IDiaSymbol::get_targetSection](../../debugger/debug-interface-access/idiasymbol-get-targetsection.md)|썽크 대상의 주소 섹션을 검색 합니다.|  
|[IDiaSymbol::get_targetVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-targetvirtualaddress.md)|썽크 대상의 가상 주소 (VA)를 검색합니다.|  
|[IDiaSymbol::get_textureSlot](../../debugger/debug-interface-access/idiasymbol-get-textureslot.md)|질감 슬롯을 검색합니다.|  
|[IDiaSymbol::get_thisAdjust](../../debugger/debug-interface-access/idiasymbol-get-thisadjust.md)|논리 검색 `this` 조정기 메서드에 대 한 합니다.|  
|[IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)|함수의 썽크 형식을 검색합니다.|  
|[IDiaSymbol::get_timeStamp](../../debugger/debug-interface-access/idiasymbol-get-timestamp.md)|내부 실행 파일의 타임 스탬프를 검색합니다.|  
|[IDiaSymbol::get_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)|관리 되는 함수 또는 변수의 메타 데이터 토큰을 검색합니다.|  
|[IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|함수 시그니처에 대 한 참조를 검색합니다.|  
|[IDiaSymbol::get_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|기호의 형식 식별자를 검색합니다.|  
|[IDiaSymbol::get_types](../../debugger/debug-interface-access/idiasymbol-get-types.md)|이 기호에 대 한 컴파일러 별 형식 값의 배열을 검색합니다.|  
|[IDiaSymbol::get_typeIds](../../debugger/debug-interface-access/idiasymbol-get-typeids.md)|이 기호에 대 한 컴파일러 별 형식 식별자 값의 배열을 검색합니다.|  
|[IDiaSymbol::get_uavSlot](../../debugger/debug-interface-access/idiasymbol-get-uavslot.md)|Uav 슬롯을 검색합니다.|  
|[IDiaSymbol::get_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)|다양 한 사용자 정의 형식 (UDT)을 검색합니다.|  
|[IDiaSymbol::get_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|사용자 정의 데이터 형식에 맞춤 인지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_undecoratedName](../../debugger/debug-interface-access/idiasymbol-get-undecoratedname.md)|데코레이팅되지 않은 이름을 검색 한 C++ 를 데코 레이트 된 링크, 이름 또는 합니다.|  
|[IDiaSymbol::get_undecoratedNameEx](../../debugger/debug-interface-access/idiasymbol-get-undecoratednameex.md)|확장 된 `get_undecoratedName` 확장 필드의 값을 기반으로 데코레이팅되지 않은 이름을 검색 하는 메서드.|  
|[IDiaSymbol::get_unmodifiedTypeId](../../debugger/debug-interface-access/idiasymbol-get-unmodifiedtypeid.md)|원래 (수정 되지 않은) 형식의 ID를 검색합니다.|  
|[IDiaSymbol::get_upperBound](../../debugger/debug-interface-access/idiasymbol-get-upperbound.md)|FORTRAN 배열 차원의 상한 값을 검색합니다.|  
|[IDiaSymbol::get_upperBoundId](../../debugger/debug-interface-access/idiasymbol-get-upperboundid.md)|FORTRAN 배열 차원의 상한을의 기호 식별자를 검색합니다.|  
|[IDiaSymbol::get_value](../../debugger/debug-interface-access/idiasymbol-get-value.md)|상수 값을 검색합니다.|  
|[IDiaSymbol::get_virtual](../../debugger/debug-interface-access/idiasymbol-get-virtual.md)|가상 함수 인지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|가상 주소 (VA) 위치를 검색 합니다.|  
|[IDiaSymbol::get_virtualBaseClass](../../debugger/debug-interface-access/idiasymbol-get-virtualbaseclass.md)|사용자 정의 데이터 형식에 가상 기본 클래스 인지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSymbol::get_virtualBaseDispIndex](../../debugger/debug-interface-access/idiasymbol-get-virtualbasedispindex.md)|가상 기본 위치 변경 테이블에 인덱스를 검색 합니다.|  
|[IDiaSymbol::get_virtualBaseOffset](../../debugger/debug-interface-access/idiasymbol-get-virtualbaseoffset.md)|가상 함수는 가상 함수 테이블의 오프셋을 검색합니다.|  
|[IDiaSymbol::get_virtualBasePointerOffset](../../debugger/debug-interface-access/idiasymbol-get-virtualbasepointeroffset.md)|가상 기본 포인터의 오프셋을 검색합니다.|  
|[IDiaSymbol::get_virtualBaseTableType](../../debugger/debug-interface-access/idiasymbol-get-virtualbasetabletype.md)|가상 기본 테이블 포인터의 형식을 검색합니다.|  
|[IDiaSymbol::get_virtualTableShape](../../debugger/debug-interface-access/idiasymbol-get-virtualtableshape.md)|사용자 정의 형식에 대 한 가상 테이블 형식의 기호 인터페이스를 검색합니다.|  
|[IDiaSymbol::get_virtualTableShapeId](../../debugger/debug-interface-access/idiasymbol-get-virtualtableshapeid.md)|기호의 가상 테이블 모양 식별자를 검색합니다.|  
|[IDiaSymbol::get_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|사용자 정의 데이터 형식이 휘발성 인지 여부를 나타내는 플래그를 검색 합니다.|  
  
## <a name="remarks"></a>설명  
  
## <a name="notes-for-callers"></a>호출자에 대 한 정보  
 다음 방법 중 하나를 호출 하 여이 인터페이스를 가져옵니다.  
  
- [IDiaEnumSymbols::Item](../../debugger/debug-interface-access/idiaenumsymbols-item.md)  
  
- [IDiaEnumSymbols::Next](../../debugger/debug-interface-access/idiaenumsymbols-next.md)  
  
- [IDiaEnumSymbolsByAddr::Next](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-next.md)  
  
- [IDiaEnumSymbolsByAddr::Prev](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-prev.md)  
  
- [IDiaEnumSymbolsByAddr::symbolByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyaddr.md)  
  
- [IDiaEnumSymbolsByAddr::symbolByRVA](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyrva.md)  
  
- [IDiaEnumSymbolsByAddr::symbolByVA](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyva.md)  
  
- [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)  
  
- [IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)  
  
- [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)  
  
- [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)  
  
- [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)  
  
- [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)  
  
- [IDiaSession::symbolById](../../debugger/debug-interface-access/idiasession-symbolbyid.md)  
  
- [IDiaStackWalkHelper::symbolForVA](../../debugger/debug-interface-access/idiastackwalkhelper-symbolforva.md)  
  
- [IDiaSymbol::get_types](../../debugger/debug-interface-access/idiasymbol-get-types.md)  
  
## <a name="example"></a>예제  
 이 예제에서는 지정된 된 상대 가상 주소에는 함수에 대 한 지역 변수를 표시 하는 방법을 보여 줍니다. 또한 다양 한 종류의 기호 서로 어떻게 관련 되어 있는지 보여 줍니다.  
  
> [!NOTE]
> `CDiaBSTR` 래핑하는 클래스를 `BSTR` 인스턴스화 범위를 벗어나면 문자열이 해제를 자동으로 처리 하 고 있습니다.  
  
```cpp#  
void DumpLocalVars( DWORD rva, IDiaSession *pSession )  
{  
    CComPtr< IDiaSymbol > pBlock;  
    if ( FAILED( psession->findSymbolByRVA( rva, SymTagBlock, &pBlock ) ) )  
    {  
        Fatal( "Failed to find symbols by RVA" );  
    }  
    CComPtr< IDiaSymbol > pscope;  
    for ( ; pBlock != NULL; )  
    {  
        CComPtr< IDiaEnumSymbols > pEnum;  
        // local data search  
        if ( FAILED( pBlock->findChildren( SymTagNull, NULL, nsNone, &pEnum ) ) )  
        {  
            Fatal( "Local scope findChildren failed" );  
        }  
        CComPtr< IDiaSymbol > pSymbol;  
        DWORD tag;  
        DWORD celt;  
        while ( pEnum != NULL &&  
                SUCCEEDED( pEnum->Next( 1, &pSymbol, &celt ) ) &&  
                celt == 1)  
        {  
            pSymbol->get_symTag( &tag );  
            if ( tag == SymTagData )  
            {  
                CDiaBSTR name;  
                DWORD    kind;  
                pSymbol->get_name( &name );  
                pSymbol->get_dataKind( &kind );  
                if ( name != NULL )  
                    wprintf_s( L"\t%s (%s)\n", name, szDataKinds[ kind ] );  
            }  
            else if ( tag == SymTagAnnotation )  
            {  
                CComPtr< IDiaEnumSymbols > pValues;  
                // local data search  
                wprintf_s( L"\tAnnotation:\n" );  
                if ( FAILED( pSymbol->findChildren( SymTagNull, NULL, nsNone, &pValues ) ) )  
                    Fatal( "Annotation findChildren failed" );  
                pSymbol = NULL;  
                while ( pValues != NULL &&  
                        SUCCEEDED( pValues->Next( 1, &pSymbol, &celt ) ) &&  
                        celt == 1 )  
                {  
                    CComVariant value;  
                    if ( pSymbol->get_value( &value ) != S_OK )  
                        Fatal( "No value for annotation data." );  
                    wprintf_s( L"\t\t%ws\n", value.bstrVal );  
                    pSymbol = NULL;  
                }  
            }  
            pSymbol = NULL;  
        }  
        pBlock->get_symTag( &tag );   
        if ( tag == SymTagFunction )    // stop when at function scope  
            break;  
        // move to lexical parent  
        CComPtr< IDiaSymbol > pParent;  
        if ( SUCCEEDED( pBlock->get_lexicalParent( &pParent ) )  
            && pParent != NULL ) {  
            pBlock = pParent;  
        }  
        else  
        {  
            Fatal( "Finding lexical parent failed." );  
        }  
    };  
}  
```  
  
## <a name="requirements"></a>요구 사항  
 `Header:` Dia2.h  
  
 라이브러리: diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>관련 항목  
 [인터페이스(디버그 인터페이스 액세스 SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [기호 형식의 클래스 계층 구조](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)   
 [기호 및 기호 태그](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)   
 [컴파일 대상](../../debugger/debug-interface-access/compiland.md)
