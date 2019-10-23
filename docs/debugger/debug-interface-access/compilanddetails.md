---
title: CompilandDetails | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CompilandDetails symbol
ms.assetid: ddc7d794-c622-4c63-b2a6-72f8b2d0022a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b72a5ae53c336877c68cc9b164cf787017dacbe2
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745412"
---
# <a name="compilanddetails"></a>CompilandDetails
Compiland 정보는 `SymTagCompiland` 태그 (낮은 정보)와 `SymTagCompilandDetails` 태그 (높은 세부 정보)를 사용 하 여 기호 간에 분할 됩니다. `SymTagCompilandDetails` 추가 기호를 로드 해야 합니다. 그러나 `SymTagCompiland` 기호와 함께 사용할 수 없는 compiland에 대 한 다양 한 정보를 제공 합니다.

## <a name="properties"></a>데이터 액세스
 다음 표에서는이 기호 형식에 유효한 속성을 보여 줍니다.

|속성|데이터 형식|설명|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_backEndBuild](../../debugger/debug-interface-access/idiasymbol-get-backendbuild.md)|`DWORD`|컴파일러의 백 엔드 빌드 번호입니다.|
|[IDiaSymbol::get_backEndMajor](../../debugger/debug-interface-access/idiasymbol-get-backendmajor.md)|`DWORD`|컴파일러의 백 엔드 주 버전 번호입니다.|
|[IDiaSymbol::get_backEndMinor](../../debugger/debug-interface-access/idiasymbol-get-backendminor.md)|`DWORD`|컴파일러의 백 엔드 부 버전 번호입니다.|
|[IDiaSymbol::get_compilerName](../../debugger/debug-interface-access/idiasymbol-get-compilername.md)|`BSTR`|이 compiland을 생성 한 컴파일러의 이름입니다 (DIA SDK V 8.0 이상 에서만).|
|[IDiaSymbol::get_editAndContinueEnabled](../../debugger/debug-interface-access/idiasymbol-get-editandcontinueenabled.md)|`BOOL`|컴파일하는 동안 편집 하며 계속 하기를 사용 하도록 설정 된 경우 `TRUE` 합니다.|
|[IDiaSymbol::get_frontEndBuild](../../debugger/debug-interface-access/idiasymbol-get-frontendbuild.md)|`DWORD`|컴파일러의 프런트 엔드 빌드 번호입니다.|
|[IDiaSymbol::get_frontEndMajor](../../debugger/debug-interface-access/idiasymbol-get-frontendmajor.md)|`DWORD`|컴파일러의 프런트 엔드 주 버전 번호입니다.|
|[IDiaSymbol::get_frontEndMinor](../../debugger/debug-interface-access/idiasymbol-get-frontendminor.md)|`DWORD`|컴파일러의 프런트 엔드 부 버전 번호입니다.|
|[IDiaSymbol::get_hasDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-hasdebuginfo.md)|`BOOL`|이 compiland에 디버그 정보가 있는 경우 `TRUE` (DIA SDK V 8.0 이상에만 해당).|
|[IDiaSymbol::get_hasManagedCode](../../debugger/debug-interface-access/idiasymbol-get-hasmanagedcode.md)|`BOOL`|이 compiland 관리 코드를 포함 하는 경우 `TRUE` (DIA SDK v 8.0 이상에만 해당).|
|[IDiaSymbol::get_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|`BOOL`|compiland가 [/gs (Buffer Security Check)](/cpp/build/reference/gs-buffer-security-check) 컴파일러 스위치를 사용 하 여 컴파일 되었는지 여부를 `TRUE` 합니다 (DIA SDK v 8.0 이상에만 해당).|
|[IDiaSymbol::get_isCVTCIL](../../debugger/debug-interface-access/idiasymbol-get-iscvtcil.md)|`BOOL`|compiland가 CIL (공용 중간 언어) 코드에서 네이티브 코드로 변환 되었는지 여부를 `TRUE` 합니다.|
|[IDiaSymbol::get_isDataAligned](../../debugger/debug-interface-access/idiasymbol-get-isdataaligned.md)|`BOOL`|UDT (사용자 정의 형식)가 지정 된 일부 메모리 경계 (DIA SDK V 8.0 이상 에서만)에 정렬 되었는지 여부를 `TRUE` 합니다.|
|[IDiaSymbol::get_isHotpatchable](../../debugger/debug-interface-access/idiasymbol-get-ishotpatchable.md)|`BOOL`|compiland가 [/hotpatch (Create 핫 패치 가능 Image)](/cpp/build/reference/hotpatch-create-hotpatchable-image) 컴파일러 스위치 (DIA SDK v 8.0 이상 에서만)로 컴파일 되었는지 여부를 `TRUE` 합니다.|
|[IDiaSymbol::get_isLTCG](../../debugger/debug-interface-access/idiasymbol-get-isltcg.md)|`BOOL`|compiland가 [/ltcg (링크 타임 코드 생성)](/cpp/build/reference/ltcg-link-time-code-generation) 컴파일러 스위치 (DIA SDK v 8.0 이상 에서만)로 컴파일 되었는지 여부를 `TRUE` 합니다.|
|[IDiaSymbol::get_isMSILNetmodule](../../debugger/debug-interface-access/idiasymbol-get-ismsilnetmodule.md)|`BOOL`|Compiland이 MSIL (Microsoft 중간 언어) 모듈인 경우 TRUE이 고 DIA SDK v 8.0 이상 에서만 해당 됩니다.|
|[IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)|`DWORD`|소스 코드 언어입니다.|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Compiland 기호입니다.|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|어휘 부모 기호의 ID입니다.|
|[IDiaSymbol::get_platform](../../debugger/debug-interface-access/idiasymbol-get-platform.md)|`DWORD`|Compiland 컴파일되는 플랫폼 ( [CV_CPU_TYPE_e 열거형](../../debugger/debug-interface-access/cv-cpu-type-e.md) 값 중 하나)입니다.|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|기호의 인덱스 ID입니다.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|[SymTagEnum 열거형](../../debugger/debug-interface-access/symtagenum.md) 값 중 하나인 `SymTagCompilandDetails` 반환 합니다.|

## <a name="remarks"></a>주의
 컴파일러는 일반적으로 두 개의 pass 컴파일러 라는 형태로 제공 됩니다. 일부 컴파일러 버전에서 각 패스는 개별 프로그램에 의해 처리 됩니다. 이러한 기능을 프런트 엔드 및 백 엔드 컴파일러 라고 하며, 따라서 백 엔드 및 프런트 엔드 버전 번호에 대 한 기호 속성을 각각 사용할 수 있습니다.

## <a name="see-also"></a>참조
- [컴파일 대상](../../debugger/debug-interface-access/compiland.md)
- [기호 형식의 어휘 계층 구조](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)