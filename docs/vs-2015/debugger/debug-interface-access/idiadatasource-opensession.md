---
title: 'Idiadatasource:: Opensession | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::openSession method
ms.assetid: a3319ed0-3979-483b-9852-c0af96852c48
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4bec5507d15374e6e88afd4567d4b0fec9ca6cb7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68198596"
---
# <a name="idiadatasourceopensession"></a>IDiaDataSource::openSession
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

기호를 쿼리 하는 것에 대 한 세션을 엽니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT openSession (   
   IDiaSession** ppSession  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 ppSession  
 [out] 반환 된 [IDiaSession](../../debugger/debug-interface-access/idiasession.md) 세션 열기를 나타내는 개체입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다. 다음 표에서이 메서드에 대 한 가능한 반환 값을 보여 줍니다.  
  
|값|Description|  
|-----------|-----------------|  
|E_UNEXPECTED|합니다 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md) 개체 기호는 소스를 사용 하 여 이전에 초기화 되지 않았습니다.|  
|E_INVALIDARG|잘못된 `ppSession` 매개 변수입니다.|  
|E_OUTOFMEMORY|메모리가 부족 하 여 세션을 열에 없습니다.|  
  
## <a name="remarks"></a>설명  
 이 메서드를 엽니다는 [IDiaSession](../../debugger/debug-interface-access/idiasession.md) 데이터 원본에 대 한 개체입니다.  
  
 `IDiaSession` 데이터 원본에 쿼리를 구현 하는 개체입니다. 세션은 디버그 기호의 각 집합에 대 한 이상의 주소 공간을 관리합니다. 데이터 원본 기호에서 설명 하는.exe 또는.dll 파일은 활성 여러 주소에서 범위 (예를 들어 여러 프로세스가 있으므로 로드) 한 다음 각 주소 범위에 대 한 세션을 사용 해야 합니다.  
  
## <a name="example"></a>예제  
  
```cpp#  
IDiaSession* pSession;  
HRESULT hr = pSource->openSession( &pSession );  
if (FAILED(hr))  
{  
   // report error  
}  
```  
  
## <a name="see-also"></a>참고 항목  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [개요](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [.Pdb 파일 쿼리](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)
