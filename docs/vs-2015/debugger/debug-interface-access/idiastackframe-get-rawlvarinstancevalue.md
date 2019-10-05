---
title: 'Idiastackframe:: Get_rawlvarinstancevalue | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_rawLVarInstanceValue method
ms.assetid: ce526259-85a6-475b-9274-0b3a21d95db2
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c8ff78c38ad077084b3dea9c96e3251ffddb2206
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62573016"
---
# <a name="idiastackframegetrawlvarinstancevalue"></a>IDiaStackFrame::get_rawLVarInstanceValue
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

이 메서드는 원시 바이트로 지정 된 지역 변수 값을 검색합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT get_rawLVarInstanceValue(  
   IDiaLVarInstance* pInstance,  
   DWORD             cbDataMax,  
   DWORD*            pcbData,  
   BYTE*             pbData  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pInstance`  
 [in] `IDiaLVarInstance` 에 대 한 값을 가져올 로컬 변수의 인스턴스를 나타내는 개체입니다.  
  
 `cbDataMax`  
 [in] 최대 버퍼의 바이트 수로 가리키는 `pbData`합니다. 8 바이트의 최대 수 (`sizeof(ULONGLONG)`).  
  
 `pcbData`  
 [out] 실제 버퍼에 저장 된 바이트 수를 반환 합니다.  
  
 `pbData`  
 [out] 데이터를 입력할 버퍼입니다. 이는 `NULL`이 될 수 없습니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
