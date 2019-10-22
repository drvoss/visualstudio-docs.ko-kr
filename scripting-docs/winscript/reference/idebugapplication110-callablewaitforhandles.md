---
title: 'IDebugApplication110:: CallableWaitForHandles | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplication110::CallableWaitForHandles
ms.assetid: 02e79b60-0d67-47f9-bf78-b65a02c9c014
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 22af0e9dcf548bbd2f0f8c179b4889d5294eb284
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575081"
---
# <a name="idebugapplication110callablewaitforhandles"></a>IDebugApplication110::CallableWaitForHandles
스레드 간 호출이이 스레드에 게시 되도록 허용 하는 동안 지정 된 핸들이 신호를 받을 때까지 기다립니다. 이 메서드는 디버거 스레드에서 호출 해야 합니다.  
  
> [!IMPORTANT]
> [IDebugApplication110 인터페이스](../../winscript/reference/idebugapplication110-interface.md) 는 PDM v 11.0 이상에 의해 구현 됩니다. activdbg100.h에서 찾을 수 있습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT CallableWaitForHandles([in] DWORD handleCount, [in, size_is(handleCount)] const HANDLE* pHandles, [out] DWORD* pIndex);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `handleCount`  
 대기할 핸들의 수입니다.  
  
 `pHandles`  
 대기할 핸들 집합입니다.  
  
 `pIndex`  
 HRESULT 값이 S_OK 인 경우 신호를 받은 핸들의 `pHandles`에 대 한 인덱스가 반환 됩니다.  
  
## <a name="see-also"></a>참조  
 [IDebugApplication110 인터페이스](../../winscript/reference/idebugapplication110-interface.md)