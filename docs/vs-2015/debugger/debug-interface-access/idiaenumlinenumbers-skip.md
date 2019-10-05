---
title: 'Idiaenumlinenumbers:: Skip | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumLineNumbers::Skip method
ms.assetid: d182c269-8c76-4d8b-8275-c6807c5ae4e1
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0f4fe7ae4fb18fbf72387675d52703daab708efc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68190041"
---
# <a name="idiaenumlinenumbersskip"></a>IDiaEnumLineNumbers::Skip
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

열거형 시퀀스에서 줄 번호의 지정된 된 수를 건너뜁니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 celt  
 [in] 열거형 시퀀스에서 줄 번호를 표시 하지 않으려면 횟수입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 반환 `S_OK`이 고, 그렇지 않으면 반환 `S_FALSE` 건너뛸 줄 번호 없음 더 많은 경우.  
  
## <a name="see-also"></a>관련 항목  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
