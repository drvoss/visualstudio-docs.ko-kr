---
title: DataKind | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- DataKind enumeration
ms.assetid: b64be708-22d6-4360-99e7-8f4e6b196de7
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a6a72d1093bc8acd9aae788ff357aee2efeb9e52
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68197629"
---
# <a name="datakind"></a>DataKind
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

데이터 값의 특정 범위를 나타냅니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
enum DataKind {   
   DataIsUnknown,  
   DataIsLocal,  
   DataIsStaticLocal,  
   DataIsParam,  
   DataIsObjectPtr,  
   DataIsFileStatic,  
   DataIsGlobal,  
   DataIsMember,  
   DataIsStaticMember,  
   DataIsConstant  
};  
```  
  
## <a name="elements"></a>요소  
 DataIsUnknown  
 데이터 기호를 확인할 수 없습니다.  
  
 DataIsLocal  
 데이터 항목에는 지역 변수입니다.  
  
 DataIsStaticLocal  
 데이터 항목에는 정적 지역 변수입니다.  
  
 DataIsParam  
 데이터 항목에는 정식 매개 변수입니다.  
  
 DataIsObjectPtr  
 데이터 항목 개체 포인터는 (`this`).  
  
 DataIsFileStatic  
 데이터 항목에는 파일 범위 변수입니다.  
  
 DataIsGlobal  
 데이터 항목에는 전역 변수입니다.  
  
 DataIsMember  
 데이터 항목 개체 멤버 변수입니다.  
  
 DataIsStaticMember  
 데이터 항목에는 정적 클래스 변수입니다.  
  
 DataIsConstant  
 데이터 항목에는 상수 값입니다.  
  
## <a name="remarks"></a>설명  
 이 열거형의 값에서 반환 되는 [idiasymbol:: Get_datakind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md) 메서드.  
  
## <a name="requirements"></a>요구 사항  
 헤더: cvconst.h  
  
## <a name="see-also"></a>참고 항목  
 [열거형 및 구조체](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)
