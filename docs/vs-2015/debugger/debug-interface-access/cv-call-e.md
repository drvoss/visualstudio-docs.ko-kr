---
title: CV_call_e | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CV_call_e enumeration
ms.assetid: f230560b-4243-432d-8f19-46df112043b9
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cd1ee4c024894e5752277a5000d37745c88c4ac6
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442102"
---
# <a name="cvcalle"></a>CV_call_e
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

함수의 호출 규칙을 지정 합니다.  
  
> [!NOTE]
> 가장 일반적인 열거형 값만 여기에 설명 되어 있습니다. 전체 열거형 cvconst.h 헤더 파일에서 제공 됩니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
typedef enum CV_call_e {   
   CV_CALL_NEAR_C    = 0x00,  
   CV_CALL_NEAR_FAST = 0x04,  
   CV_CALL_NEAR_STD  = 0x07,  
   CV_CALL_NEAR_SYS  = 0x09,  
   CV_CALL_THISCALL  = 0x0b,  
   CV_CALL_CLRCALL   = 0x16  
} CV_call_e;  
```  
  
## <a name="elements"></a>요소  
 CV_CALL_NEAR_C  
 거의 오른쪽에서 왼쪽 푸시를 사용 하 여 함수 호출 규칙을 지정 합니다. 함수 호출 스택을 지웁니다.  
  
 CV_CALL_NEAR_FAST  
 레지스터를 사용 하 여 거의 왼쪽-오른쪽 푸시를 사용 하 여 함수 호출 규칙을 지정 합니다. 호출된 된 함수 매개 변수 바이트의 합계를 사용 하 여 스택을 지웁니다.  
  
 CV_CALL_NEAR_STD  
 거의 표준 호출 (오른쪽에서 왼쪽 밀어넣기)를 사용 하 여 함수 호출 규칙을 지정 합니다.  
  
 CV_CALL_NEAR_SYS  
 거의 시스템 호출을 사용 하 여 함수 호출 규칙을 지정 합니다.  
  
 CV_CALL_THISCALL  
 사용 하 여 함수 호출 규칙 지정 `this` 호출 (`this` 레지스터에 전달 된 포인터).  
  
 CV_CALL_CLRCALL  
 함수 호출 규칙을 사용 하 여 언어 런타임 (CLR (공용) (라고도 하며 관리 되는 코드를 호출 규칙)을 지정 합니다.  
  
## <a name="remarks"></a>설명  
 이 열거형의 값에는 호출에서 반환 되는 [idiasymbol:: Get_callingconvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md) 메서드.  
  
## <a name="requirements"></a>요구 사항  
 헤더: cvconst.h  
  
## <a name="see-also"></a>참고 항목  
 [열거형 및 구조체](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)
