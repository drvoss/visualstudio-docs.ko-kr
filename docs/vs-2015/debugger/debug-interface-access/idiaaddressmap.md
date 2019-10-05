---
title: IDiaAddressMap | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap interface
ms.assetid: e6467529-508c-4328-85d7-89444ae4d1c1
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 012d6b1ca06b06f56239048fee712d898a79efa9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62547509"
---
# <a name="idiaaddressmap"></a>IDiaAddressMap
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

DIA SDK 디버그 개체에 대 한 가상 및 상대 가상 주소를 계산 하는 방법에 대 한 제어를 제공 합니다.  
  
## <a name="syntax"></a>구문  
  
```  
IDiaAddressMap : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 다음 표에서의 메서드를 보여 줍니다. `IDiaAddressMap`합니다.  
  
|메서드|설명|  
|------------|-----------------|  
|[IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)|주소 지도 특정 세션에 대해 설정 되었는지 여부를 나타냅니다.|  
|[IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)|기호 주소 변환할 매핑된 주소를 사용할지 여부를 지정 합니다.|  
|[IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)|계산 및 상대 가상 주소 사용 하 여 사용 되는지 여부를 나타냅니다.|  
|[IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)|클라이언트를 상대 가상 주소에 대 한 계산을 사용할지 여부 있습니다.|  
|[IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)|현재 이미지 맞춤을 검색합니다.|  
|[IDiaAddressMap::put_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md)|이미지 맞춤을 설정합니다.|  
|[IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)|집합 이미지 헤더의 경우 상대 가상 주소를 사용 하도록 설정 합니다.|  
|[IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)|이미지 레이아웃 번역을 지원 하기 위해 주소 맵을 제공 합니다.|  
  
## <a name="remarks"></a>설명  
 이 인터페이스에서 제공 되는 컨트롤이 두 제공한 데이터 집합에 캡슐화 됩니다: 헤더 이미지 및 지도 해결 합니다. 대부분의 클라이언트를 사용 합니다 [idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) 이미지 및 메서드를 검색할 수 있습니다 일반적으로 모든 필요한 헤더 및 지도 데이터 자체에 대 한 적절 한 디버그 정보를 찾는 방법입니다. 그러나 일부 클라이언트는 특수 한 처리 및 데이터에 대 한 검색을 구현 합니다. 메서드를 사용 하는 이러한 클라이언트는 `IDiaAddressMap` 검색 결과 사용 하 여 DIA SDK를 제공 하는 인터페이스입니다.  
  
## <a name="notes-for-callers"></a>호출자에 대 한 정보  
 이 인터페이스는 DIA 세션 개체에서 사용할 수 있습니다. 클라이언트 호출을 `QueryInterface` DIA 세션 개체 인터페이스에서 일반적으로 메서드 [IDiaSession](../../debugger/debug-interface-access/idiasession.md), 검색할는 `IDiaAddressMap` 인터페이스입니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: Dia2.h  
  
 라이브러리: diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>참고 항목  
 [인터페이스(디버그 인터페이스 액세스 SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
