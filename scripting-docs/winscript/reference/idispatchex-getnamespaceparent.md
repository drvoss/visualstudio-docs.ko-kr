---
title: 'IDispatchEx:: GetNameSpaceParent | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.GetNameSpaceParent
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetNameSpaceParent method
ms.assetid: 0b077d39-2fd6-4390-8cd5-128d9b8dc90c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d2f47fab9831441e72a4ef3d4332a41c08e6a108
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574078"
---
# <a name="idispatchexgetnamespaceparent"></a>IDispatchEx::GetNameSpaceParent
개체의 네임 스페이스 부모에 대 한 인터페이스를 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetNameSpaceParent(  
   IUnknown **ppunk  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `ppunk`  
 네임 스페이스 부모의 인터페이스를 수신 하는 `IUnknown` 인터페이스 포인터의 주소입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 `S_OK`을 반환 하 고, 그렇지 않으면 OLE 정의 오류 코드를 반환 합니다.  
  
## <a name="see-also"></a>참조  
 [IDispatchEx 인터페이스](../../winscript/reference/idispatchex-interface.md)