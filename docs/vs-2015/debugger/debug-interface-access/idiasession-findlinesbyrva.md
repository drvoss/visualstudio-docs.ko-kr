---
title: IDiaSession::findLinesByRVA | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findLinesByRVA method
ms.assetid: 06f53b0b-b5b4-42cf-9252-dcee0dbe2d71
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8c066e183d60a1f7d967cafa1114d6241b28caa4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68165502"
---
# <a name="idiasessionfindlinesbyrva"></a>IDiaSession::findLinesByRVA
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

지정 된 상대 가상 주소 RVA ()를 포함 하는 지정 된 compiland에서 줄을 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT findLinesByRVA (   
   DWORD                 rva,  
   DWORD                 length,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `rva`  
 [in] RVA로 주소를 지정합니다.  
  
 `length`  
 [in] 이 쿼리를 처리 하기 위해 주소 범위의 바이트 수를 지정 합니다.  
  
 `ppResult`  
 [out] 반환 된 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) 모든 줄의 목록을 포함 하는 개체 번호 규정 하는 지정된 된 주소 범위입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.  
  
## <a name="example"></a>예제  
 이 예제에서는 함수의 상대 가상 주소 및 길이 사용 하 여 지정된 된 함수에 포함 된 모든 줄 번호를 가져오는 함수를 보여 줍니다.  
  
```cpp#  
IDiaEnumLineNumbers* GetLineNumbersByRVA(IDiaSymbol *pFunc, IDiaSession *pSession)  
{  
    IDiaEnumLineNumbers* pEnum = NULL;  
    DWORD                rva;  
    ULONGLONG            length;  
  
    if (pFunc->get_relativeVirtualAddress ( &rva ) == S_OK)  
    {  
        pFunc->get_length ( &length );  
        pSession->findLinesByRVA( rva, static_cast<DWORD>( length ), &pEnum );  
    }  
    return(pEnum);  
}  
```  
  
## <a name="see-also"></a>참고 항목  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
