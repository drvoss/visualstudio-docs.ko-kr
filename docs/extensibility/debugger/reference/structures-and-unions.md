---
title: 구조체 및 공용 구조체 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- structures [Visual Studio SDK]
ms.assetid: 9ff0a8f8-1ee6-4fdd-8b80-206436ff589b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2da39e0327f9a0be2cf0f61227de5ea51af03285
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66329125"
---
# <a name="structures-and-unions"></a>구조체 및 공용 구조체
구조체 및 공용 구조체는 Visual Studio 디버깅 SDK에는 다음과 같습니다.

- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) 시스템 ID 또는 GUID 일 수 있는 프로세스 ID를 지정 합니다.

- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) 중단점은 발생 조건을 설명 합니다.

- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) 위치, 프로그램 및 스레드를 포함 하 여 오류 중단점을 해상도 설명 합니다.

- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) 중단점의 위치를 설명 하는 데 사용 하는 구조체의 형식을 지정 합니다.

- [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md) 코드 주소 중단점의 위치를 설명 하는 구성 요소를 정의 합니다.

- [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md) 디버깅 중인 프로그램의 주소에 직접 바인딩된 중단점의 위치를 설명 합니다.

- [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) 코드 소스 파일의 줄에 중단점의 위치를 설명 합니다.

- [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) 코드의 함수 중단점의 오프셋된 위치를 설명 합니다.

- [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md) IDE에서 입력할 수 있는 문자열을 기반으로 코드 중단점을 설정 하는 것에 대 한 사용 합니다.

- [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md) IDE에서 입력할 수 있는 문자열을 기반으로 하는 데이터 중단점을 설정 하는 것에 대 한 사용 합니다.

- [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md) 특정 위치에 있는 중단점의 해상도 설명 합니다.

- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) 기반이 중단점 있으면 이전에 전달 된 후 발생은 개수 및 조건에 설명 합니다.

- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) 중단점을 구현 하는 데 필요한 정보를 포함 합니다.

- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) 중단점을 구현 하는 데 필요한 정보를 포함 (동일 합니다 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) 구조에는 있지만 공급 업체 GUID, 제약 조건 및 추적점 정보가 포함 됩니다).

- [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md) 코드 중단점의 위치를 설명 합니다.

- [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md) 바인딩 데이터 중단점의 결과 설명 합니다.

- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) 코드 중단점 또는 데이터 중단점에 대 한 바인딩된 중단점 정보를 설명 합니다.

- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) 중단점 해결 위치의 구조를 지정 합니다.

- [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md) 문자열의 배열에 설명 합니다.

- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) 메타 데이터에서 가져온 필드 형식에 대 한 정보를 지정 합니다.

- [CODE_PATH](../../../extensibility/debugger/reference/code-path.md) 함수 또는 메서드 호출에 설명 합니다.

- [COMPUTER_INFO](../../../extensibility/debugger/reference/computer-info.md) 디버거를 실행 중인 컴퓨터에 설명 합니다.

- [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md) Guid 목록에 설명 합니다.

- [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) 메모리 컨텍스트 또는 코드 컨텍스트를 설명 합니다.

- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) 디버깅 중인 프로그램의 주소에 설명 합니다.

- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) 주소의 다양 한 종류의 숫자 중 하나를 나타냅니다.

- [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) 형식 시각화 도우미 또는 사용자 지정 뷰어를 나타냅니다.

- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) 에 이름, 형식 및 값이 있는 계층적 특성의 개체를 설명 하는 디버그 속성을 설명 합니다.

- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) 참조를 설명 합니다.

- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) 디스어셈블리 표시 하기 위해 IDE에 설명 합니다.

- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) 디버깅 중인 프로그램에서 throw 된 예외 또는 런타임 오류를 설명 합니다.

- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) 지역 변수, 매개 변수 또는 다른 필드에 설명 합니다.

- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) 스택 프레임에 설명 합니다.

- [GUID_ARRAY](../../../extensibility/debugger/reference/guid-array.md) 사용할 디버그 엔진에 대 한 고유 식별자의 배열에 설명 합니다.

- [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) JustMyCode 모듈에 대 한 정보를 설정 하는 데 사용 합니다.

- [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md) 특정 컴퓨터에 설명 합니다.

- [METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) 배열 내에서 배열 요소에 설명 합니다.

- [METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) 클래스 또는 구조체의 필드의 주소에 설명 합니다.

- [METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) (일반적으로 함수 또는 메서드) 범위 내에서 로컬 변수의 주소에 설명 합니다.

- [METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) 클래스 메서드의 주소에 설명 합니다.

- [METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) 메서드 또는 함수의 매개 변수를 설명 합니다.

- [METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) 메서드 또는 함수에서 반환 값에 설명 합니다.

- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) 메타 데이터에서 가져온 필드 형식에 설명 합니다.

- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) 특정 모듈 (DLL, EXE 또는 어셈블리)에 대해 설명 합니다.

- [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md) 에 대 한 검색이 있는 기호 검색 경로 대 한 상태 정보에 설명 합니다.

- [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) 기본 주소에 설명 합니다.

- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) PDB 기호에서 가져온 필드 형식에 설명 합니다.

- [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md) 코드 위치에 바인딩할 수 있는 중단점의 상태를 설명 합니다.

- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) 과정을 설명 합니다.

- [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md) 설명의 목록을 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) 프로그램 노드를 나타내는 개체입니다.

- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) 컴퓨터에서 실행 중인 프로세스에 설명 합니다.

- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) 지정된 된 텍스트의 줄 및 열 위치를 설명 합니다.

- [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) 스레드의 속성을 설명 합니다.

- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) 필드의 형식에 설명 합니다.

- [UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) 실제 주소에 설명 합니다.

- [UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) 기준으로 하는 주소에 설명 합니다는 `this` 포인터 (`Me` Visual basic에서).

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h, sh.h, 또는 ee.h

 네임스페이스: Microsoft.VisualStudio.Debugger.Interop

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [API 참조](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)