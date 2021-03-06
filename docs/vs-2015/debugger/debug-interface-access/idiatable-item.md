---
title: 'Idiatable:: Item | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable::Item method
ms.assetid: eae11b26-4807-400c-be25-e85bbc0c6b20
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2d1ebea7d657683d4174784a92ca2213851dcae9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51816738"
---
# <a name="idiatableitem"></a>IDiaTable::Item
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

테이블의 지정된 된 항목에 대 한 참조를 검색합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT Item (   
   DWORD      index,  
   IUnknown** element  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `index`  
 [in] 범위의 0 테이블 항목의 인덱스 `count`-1로, 여기서 `count` 반환한를 [idiatable:: Get_count](../../debugger/debug-interface-access/idiatable-get-count.md)메서드.  
  
 `element`  
 [out] 반환 된 `IUnknown` 지정 된 테이블 항목을 나타내는 개체입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.  
  
## <a name="remarks"></a>설명  
 테이블 개체의 컬렉션을 나타냅니다. 이러한 개체에 따라 요소 매개 변수를 적절 한 인터페이스에 캐스팅할 수 있습니다. 예를 들어 테이블에 대 한 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) element 매개 변수를 캐스팅할 수 다음 개체는 `IDiaSegment` 인터페이스입니다.  
  
 호출 하는 보다 일반적인이 방식은 합니다 `QueryInterface` 에서 메서드를 [IDiaTable](../../debugger/debug-interface-access/idiatable.md) 적절 한 열거자 인터페이스에 대 한 인터페이스 및 열거자의 특정 메서드를 사용 하 여 테이블 내용을 액세스. 참조 된 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) 예제에 대 한 인터페이스입니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)   
 [Idiatable:: Get_count](../../debugger/debug-interface-access/idiatable-get-count.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)   
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)



