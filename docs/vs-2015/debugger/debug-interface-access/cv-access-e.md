---
title: CV_access_e | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CV_access_e enumeration
ms.assetid: 33c05d65-abb4-4800-a382-54a3805ea7b0
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1ce5997555b37cf5ab30f091e7124b5025284c0e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68164380"
---
# <a name="cvaccesse"></a>CV_access_e
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

표시 유형 (액세스 수준) 멤버 함수 및 변수의 범위를 지정합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
typedef enum CV_access_e {   
   CV_private   = 1,  
   CV_protected = 2,  
   CV_public    = 3  
} CV_access_e;  
```  
  
## <a name="elements"></a>요소  
 CV_private  
 멤버 액세스 가능성은 private입니다.  
  
 CV_protected  
 멤버 액세스를 보호 했습니다.  
  
 CV_public  
 멤버에 대 한 공용 액세스 합니다.  
  
## <a name="remarks"></a>설명  
 `friend` 액세스 지정 자가 포함 되지 않습니다 여기서 클래스의 전용 및 보호 된 요소에 액세스할 수 있는 비 멤버 함수에 의해 일반적으로 사용 됩니다. 사용 된 [idiasymbol:: Get_symtag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) 메서드를 사용 하 여 기호 찾기 `SymTagFriend` 액세스 합니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: cvconst.h  
  
## <a name="see-also"></a>참고 항목  
 [열거형 및 구조체](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)   
 [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)
