---
title: Exe | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- .dll files
- Exe symbol
- .exe files
- executable files, Exe symbol
ms.assetid: a781d2cf-55fe-4373-9cf1-b732864244e0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 348edea779d22b6a7330712657740056e1bb766c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745203"
---
# <a name="exe"></a>Exe
Exe는 .exe 또는 .dll 파일의 전역 범위를 나타내므로 어휘 또는 클래스 부모가 없는 유일한 기호입니다. 파일 마다 `SymTagExe` 태그를 포함 하는 기호가 하나 뿐입니다. [IDiaSession:: get_globalScope](../../debugger/debug-interface-access/idiasession-get-globalscope.md) 메서드는 기호를 반환 합니다.

## <a name="properties"></a>데이터 액세스
 다음 표에서는이 기호 형식에 유효한 속성을 보여 줍니다.

|속성|데이터 형식|설명|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_age](../../debugger/debug-interface-access/idiasymbol-get-age.md)|`DWORD`|이 실행 파일의 보존 기간입니다.|
|[IDiaSymbol::get_guid](../../debugger/debug-interface-access/idiasymbol-get-guid.md)|`GUID`|이 실행 파일의 `GUID`입니다.|
|[IDiaSymbol::get_isCTypes](../../debugger/debug-interface-access/idiasymbol-get-isctypes.md)|`BOOL`|이 실행 파일에 연결 된 기호 파일에 C 형식이 포함 된 경우 `TRUE` 합니다 (DIA SDK v 8.0 이상에만 해당).|
|[IDiaSymbol::get_isStripped](../../debugger/debug-interface-access/idiasymbol-get-isstripped.md)|`BOOL`|이 실행 파일에 연결 된 기호 파일에서 전용 기호를 제거 했는지 여부를 `TRUE` 합니다 (DIA SDK v 8.0 이상 에서만).|
|[IDiaSymbol::get_machineType](../../debugger/debug-interface-access/idiasymbol-get-machinetype.md)|`DWORD`|대상 CPU ( [CV_CPU_TYPE_e 열거형](../../debugger/debug-interface-access/cv-cpu-type-e.md) 값 중 하나)를 나타내는 값입니다.|
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|.Exe 파일의 이름입니다.|
|[IDiaSymbol::get_signature](../../debugger/debug-interface-access/idiasymbol-get-signature.md)|`DWORD`|실행 파일의 서명입니다.|
|[IDiaSymbol::get_symbolsFileName](../../debugger/debug-interface-access/idiasymbol-get-symbolsfilename.md)|`BSTR`|.Exe 파일 .pdb 또는 dbg 파일의 전체 경로입니다.|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|기호의 인덱스 ID입니다.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|[SymTagEnum 열거형](../../debugger/debug-interface-access/symtagenum.md) 값 중 하나인 `SymTagExe` 반환 합니다.|

## <a name="see-also"></a>참조
- [IDiaSession::get_globalScope](../../debugger/debug-interface-access/idiasession-get-globalscope.md)
- [기호 형식의 어휘 계층 구조](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)