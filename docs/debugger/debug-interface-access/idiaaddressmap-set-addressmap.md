---
title: 'Idiaaddressmap:: Set_addressmap | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::set_addressMap method
ms.assetid: 81e82073-089b-43d5-af39-49d7a4907c7a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1d097ccbe5c893c603aaa2a018f8fcd422f15ac2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49834528"
---
# <a name="idiaaddressmapsetaddressmap"></a>IDiaAddressMap::set_addressMap
이미지 레이아웃 번역을 지원 하기 위해 주소 맵을 제공 합니다.  
  
## <a name="syntax"></a>구문  
  
```C++  
HRESULT set_addressMap (   
   DWORD                     cbData,  
   struct DiaAddressMapEntry data[],  
   BOOL                      imagetoSymbols  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `cbData`  
 [in] 요소 수를 `data` 매개 변수입니다.  
  
 `data[]`  
 [in] 배열을 [DiaAddressMapEntry 구조체](../../debugger/debug-interface-access/diaaddressmapentry.md) 변환 맵을 정의 하는 구조입니다.  
  
 `imagetoSymbols`  
 [in] `TRUE` 경우는 `data` 매개 변수 정의에서 새 이미지 레이아웃을 원래 레이아웃으로 지도 (디버그 기호에서 설명). `FALSE` 경우 `data` 은 원래 레이아웃에서 가져온 새 이미지 레이아웃을 맵입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.  
  
## <a name="remarks"></a>설명  
 일반적으로 DIA 프로그램 데이터베이스 (.pdb) 파일에서 주소 변환 지도 검색합니다. 이러한 값을 사용할 수 없는 경우는 [idiaaddressmap:: Set_imageheaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) 메서드는 두 번 사용 하 여 한 번를 `imagetoSymbols` 매개 변수 설정 `TRUE` 및 한 번를 `imagetoSymbols` 매개 변수 설정 `FALSE`. 사용 하 여 주소 맵 번역을 사용할 수 없습니다는 [idiaaddressmap:: Put_addressmapenabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) 메서드 모두 번역 maps는 제공 되지 않는 경우.  
  
## <a name="see-also"></a>참고 항목  
 [DiaAddressMapEntry 구조체](../../debugger/debug-interface-access/diaaddressmapentry.md)   
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [Idiaaddressmap:: Put_addressmapenabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)   
 [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)