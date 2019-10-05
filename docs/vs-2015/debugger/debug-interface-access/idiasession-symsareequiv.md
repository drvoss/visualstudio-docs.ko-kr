---
title: IDiaSession::symsAreEquiv | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::symsAreEquiv method
ms.assetid: 9941d520-e203-46c0-83c3-b3a967f4fc59
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ba8c77d7d97da75ce82fcbe732db64acf633b8af
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68150219"
---
# <a name="idiasessionsymsareequiv"></a>IDiaSession::symsAreEquiv
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

두 기호에 해당 하는 경우를 확인 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
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
  
## <a name="see-also"></a>관련 항목  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
