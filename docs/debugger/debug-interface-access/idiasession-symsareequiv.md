---
title: 'Idiasession:: Symsareequiv | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::symsAreEquiv method
ms.assetid: 9941d520-e203-46c0-83c3-b3a967f4fc59
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bdaa1ab070b6d95af0f28f5bdaa005b9ac808766
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49850986"
---
# <a name="idiasessionsymsareequiv"></a>IDiaSession::symsAreEquiv
두 기호에 해당 하는 경우를 확인 합니다.  
  
## <a name="syntax"></a>구문  
  
```C++  
HRESULT symsAreEquiv (   
   IDiaSymbol* symbolA,  
   IDiaSymbol* symbolB  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `symbolA`  
 [in] 첫 번째 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 비교에 사용 되는 개체입니다.  
  
 `symbolB`  
 [in] 두 번째 `IDiaSymbol` 비교에 사용 되는 개체입니다.  
  
## <a name="return-value"></a>반환 값  
 기호에 해당 하는 경우 반환 `S_OK`이 고, 그렇지 않으면 반환 `S_FALSE`, 기호 같지 않습니다. 그렇지 않으면 오류 코드를 반환 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)