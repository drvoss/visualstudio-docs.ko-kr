---
title: IDiaSymbol::findChildrenExByVA | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::findChildrenExByVA
ms.assetid: 29080009-36e4-4697-acd7-50f2e3e1bf1b
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6798f3a1dfd8979db926960a6155c5b07e255f21
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/12/2019
ms.locfileid: "68149965"
---
# <a name="idiasymbolfindchildrenexbyva"></a>IDiaSymbol::findChildrenExByVA
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

지정된 된 가상 주소에서 사용할 수 있는 기호 자식을 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT findChildrenExByVA (   
   enum SymTagEnum   symtag,  
   LPCOLESTR         name,  
   DWORD             compareFlags,  
   DWORD             address,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `symtag`  
 [in] 에 정의 된 대로 검색 되는 자식의 기호 태그를 지정 합니다 [SymTagEnum 열거형](../../debugger/debug-interface-access/symtagenum.md)합니다. 로 `SymTagNull` 검색할 모든 자식에 대 한 합니다.  
  
 `name`  
 [in] 검색할 자식 컨트롤의 이름을 지정 합니다. 로 `NULL` 검색할 모든 자식에 대 한 합니다.  
  
 `compareFlags`  
 [in] 이름 일치에 적용할 비교 옵션을 지정 합니다. 값을 [NameSearchOptions 열거형](../../debugger/debug-interface-access/namesearchoptions.md) 열거형 따로 또는 함께 사용할 수 있습니다.  
  
 `address`  
 [in] 가상 주소를 지정 합니다.  
  
 `ppResult`  
 [out] 반환 된 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) 자식 기호 목록을 포함 하는 개체 검색 합니다.  
  
## <a name="return-value"></a>반환 값  
 반환 `S_OK` 기호의 자식이 하나 이상 찾을 하거나 반환 하는 경우 `S_FALSE` 자식이 없는 경우; 그렇지 않으면 오류 코드를 반환 합니다.  
  
## <a name="remarks"></a>설명  
 반환 되는 로컬 기호 라이브 범위 정보를 포함 합니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: Dia2.h  
  
 라이브러리: diaguids.lib  
  
 DLL: msdia100.dll  
  
## <a name="see-also"></a>참고 항목  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum 열거형](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [NameSearchOptions 열거형](../../debugger/debug-interface-access/namesearchoptions.md)
