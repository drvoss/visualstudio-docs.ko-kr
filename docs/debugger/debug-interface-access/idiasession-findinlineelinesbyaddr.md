---
title: IDiaSession::findInlineeLinesByAddr | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: bb70e408-eed1-4c9c-b5b1-44323125f48b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dbbf31de5c3a20ecf21a8e293657d4ed3a7eff1e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49925801"
---
# <a name="idiasessionfindinlineelinesbyaddr"></a>IDiaSession::findInlineeLinesByAddr
클라이언트가 모든 없는 함수를 인라인을 직접 또는 간접적으로 지정 된 부모 기호는 줄 번호 정보를 반복 하는 데 사용 하는 지정 된 주소 범위 내에 포함 된 열거자를 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```C++  
HRESULT findInlineeLinesByAddr (   
   IDiaSymbol*           parent,   DWORD                 isect,   DWORD                 offset,   DWORD                 length,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `parent`  
 [in] `IDiaSymbol` 부모를 나타내는 개체입니다.  
  
 `isect`  
 [in] 주소 섹션 구성 요소를 지정합니다.  
  
 `offset`  
 [in] 주소의 오프셋된 구성 요소를 지정합니다.  
  
 `length`  
 [in] 이 쿼리를 처리 하기 위해 바이트 수의 주소 범위를 지정 합니다.  
  
 `ppResult`  
 [out] 보유 한 `IDiaEnumLineNumbers` 검색 되는 줄 번호의 목록을 포함 하는 개체입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum 열거형](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)