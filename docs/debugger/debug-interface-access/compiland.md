---
title: 컴파일 대상 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- compiland symbol
- compilands, compiland symbol
ms.assetid: c798eb2b-664a-41ec-ae90-5e9d292507ca
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6236a585c635ed62f8316191940899dc60a89c03
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31457841"
---
# <a name="compiland"></a>컴파일 대상
하나의 `SymTagCompiland` .exe 파일에 연결 된 각 컴파일 대상에 대 한 기호입니다. 컴파일 대상 정보도 기호 분할는 `SymTagCompiland` 추가 컴파일 대상 기호를 로드 하지 않고 검색할 수 있는 태그와 기호만 `SymTagCompilandDetails` 태그 추가 기호를 로드 해야 할 수도 있습니다.  
  
## <a name="properties"></a>속성  
 다음 표에서이 기호 형식에 대해 사용할 수 있는 속성을 보여 줍니다.  
  
|속성|데이터 형식|설명|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_editAndContinueEnabled](../../debugger/debug-interface-access/idiasymbol-get-editandcontinueenabled.md)|`BOOL`|`TRUE` 편집 하며 계속 하기 컴파일에서 설정 된 경우.|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|.Exe 파일에 대 한 기호입니다.|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|어휘 부모 기호의 ID입니다.|  
|[IDiaSymbol::get_libraryName](../../debugger/debug-interface-access/idiasymbol-get-libraryname.md)|`BSTR`|개체를 로드 하는 라이브러리 또는 개체 파일의 이름입니다.|  
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|컴파일 대상의 개체 파일의 파일 이름입니다.|  
|[IDiaSymbol::get_sourceFileName](../../debugger/debug-interface-access/idiasymbol-get-sourcefilename.md)|`BSTR`|소스 파일의 이름입니다.|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|기호 인덱스 ID입니다.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|반환 `SymTagCompiland` (중 하나는 [SymTagEnum 열거형](../../debugger/debug-interface-access/symtagenum.md) 값).|  
  
## <a name="see-also"></a>참고 항목  
 [CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)   
 [CompilandEnv](../../debugger/debug-interface-access/compilandenv.md)   
 [기호 형식의 어휘 계층 구조](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)