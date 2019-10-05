---
title: SymTagEnum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- SymTagEnum enumeration
ms.assetid: 528a50cf-e13d-46ec-a98c-323d5d047de9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dbc86bb43048b06bc1f7080bc6cb579771138c49
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62854726"
---
# <a name="symtagenum"></a>SymTagEnum
기호 유형을 지정합니다.

## <a name="syntax"></a>구문

```C++
enum SymTagEnum {
    SymTagNull,
    SymTagExe,
    SymTagCompiland,
    SymTagCompilandDetails,
    SymTagCompilandEnv,
    SymTagFunction,
    SymTagBlock,
    SymTagData,
    SymTagAnnotation,
    SymTagLabel,
    SymTagPublicSymbol,
    SymTagUDT,
    SymTagEnum,
    SymTagFunctionType,
    SymTagPointerType,
    SymTagArrayType,
    SymTagBaseType,
    SymTagTypedef,
    SymTagBaseClass,
    SymTagFriend,
    SymTagFunctionArgType,
    SymTagFuncDebugStart,
    SymTagFuncDebugEnd,
    SymTagUsingNamespace,
    SymTagVTableShape,
    SymTagVTable,
    SymTagCustom,
    SymTagThunk,
    SymTagCustomType,
    SymTagManagedType,
    SymTagDimension,
    SymTagCallSite,
    SymTagInlineSite,
    SymTagBaseInterface,
    SymTagVectorType,
    SymTagMatrixType,
    SymTagHLSLType
};
```

## <a name="elements"></a>요소
`SymTagNull` 기호 형식에 있음을 나타냅니다.

`SymTagExe` 기호는.exe 파일을 나타냅니다. 하나만 `SymTagExe` 기호 저장소 당 기호입니다. 전역 범위 역할도 하 고 어휘 부모가 없습니다.

`SymTagCompiland` 기호 저장소의 각 컴파일 대상 구성 요소에 대 한 컴파일 대상 기호를 나타냅니다. 네이티브 응용 프로그램에 대 한 `SymTagCompiland` 기호 이미지에 연결 된 개체 파일에 해당 합니다. 일부 종류의 언어 MSIL (Microsoft Intermediate) 이미지에 대 한 클래스당 하나의 compiland가 있습니다.

`SymTagCompilandDetails` 기호는 compiland의 확장된 특성에 있음을 나타냅니다. 이러한 속성을 검색 컴파일 대상 기호를 로드 해야 할 수 있습니다.

`SymTagCompilandEnv` 기호는 컴파일 대상에 대해 정의 된 환경 문자열 임을 나타냅니다.

`SymTagFunction` 기호는 함수 임을 나타냅니다.

`SymTagBlock` 기호는 중첩된 된 블록을 나타냅니다.

`SymTagData` 기호 데이터 임을 나타냅니다.

`SymTagAnnotation` 코드 주석에 대 한 기호를 나타냅니다. 이 기호의 자식은 상수 데이터 문자열 (`SymTagData`하십시오 `LocIsConstant`, `DataIsConstant`). 대부분의 클라이언트는이 기호를 무시합니다.

`SymTagLabel` 기호는 레이블을 나타냅니다.

`SymTagPublicSymbol` 기호는 공용 기호를 나타냅니다. 네이티브 응용 프로그램의 경우이 기호는 이미지를 연결 하는 동안 발생 하는 COFF 외부 기호입니다.

`SymTagUDT` 기호는 사용자 정의 형식 (구조체, 클래스 또는 공용 구조체) 임을 나타냅니다.

`SymTagEnum` 기호는 열거형을 나타냅니다.

`SymTagFunctionType` 함수 서명 형식 기호 인지를 나타냅니다.

`SymTagPointerType` 기호는 포인터 형식을 나타냅니다.

`SymTagArrayType` 기호는 배열 형식을 나타냅니다.

`SymTagBaseType` 기호는 기본 형식을 나타냅니다.

`SymTagTypedef` 기호는 나타냅니다는 `typedef`, 즉, 다른 형식에 대 한 별칭입니다.

`SymTagBaseClass` 기호는 사용자 정의 형식의 기본 클래스를 나타냅니다.

`SymTagFriend` 기호는 사용자 정의 형식의 friend 임을 나타냅니다.

`SymTagFunctionArgType` 기호는 함수 인수 임을 나타냅니다.

`SymTagFuncDebugStart` 기호는 함수 프롤로그 코드의 끝 위치를 나타냅니다.

`SymTagFuncDebugEnd` 기호는 함수 에필로그 코드의 시작 위치를 나타냅니다.

`SymTagUsingNamespace` 기호는 현재 범위에서 활성 네임 스페이스 이름을 나타냅니다.

`SymTagVTableShape` 기호는 가상 테이블 설명을 나타냅니다.

`SymTagVTable` 기호에 대 한 가상 테이블 포인터 임을 나타냅니다.

`SymTagCustom` 기호는 사용자 지정 기호 이며 동안에서 해석 되지 않습니다 나타냅니다.

`SymTagThunk` 기호 썽크 16 및 32 비트 코드 간에 데이터를 공유 하는 데 임을 나타냅니다.

`SymTagCustomType` 기호는 사용자 지정 컴파일러 기호를 나타냅니다.

`SymTagManagedType` 메타 데이터에서 기호를 나타냅니다.

`SymTagDimension` 기호는 FORTRAN 다차원 배열 임을 나타냅니다.

`SymTagCallSite` 기호 호출 사이트를 나타냅니다.

`SymTagInlineSite` 기호는 인라인 사이트를 나타냅니다.

`SymTagBaseInterface` 기호는 기본 인터페이스를 나타냅니다.

`SymTagVectorType` 기호 벡터 형식 인지를 나타냅니다.

`SymTagMatrixType` 기호는 매트릭스 형식을 나타냅니다.

`SymTagHLSLType` 기호 High Level Shader Language 형식임을 나타냅니다.

## <a name="remarks"></a>설명
디버그 파일 내에서 모든 기호 식별 태그 기호 형식을 지정 하는 경우

이 열거형의 값에는 호출에서 반환 되는 [idiasymbol:: Get_symtag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) 메서드.

이 열거형의 값은 특정 기호 형식에 대 한 검색 범위를 제한 하려면 다음 방법에 전달 됩니다.

- [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)

- [IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)

- [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)

- [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)

- [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)

- [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)

- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)

- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)

## <a name="requirements"></a>요구 사항
헤더: cvconst.h

## <a name="see-also"></a>참고 항목
- [열거형 및 구조체](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [기호 형식의 어휘 계층 구조](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
- [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)
- [IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)
- [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)
- [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)
- [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)
- [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
