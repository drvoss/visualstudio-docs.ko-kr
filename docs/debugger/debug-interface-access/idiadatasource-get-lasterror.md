---
title: 'Idiadatasource:: Get_lasterror | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::get_lastError method
ms.assetid: cf08850b-8b75-4e8c-90bd-bd0214756f99
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e197262b84fcf964afb74f85e86ff384daa26c9e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49819839"
---
# <a name="idiadatasourcegetlasterror"></a>IDiaDataSource::get_lastError
마지막 로드 오류에 대 한 파일 이름을 검색합니다.  
  
## <a name="syntax"></a>구문  
  
```C++  
HRESULT get_lastError (  
   BSTR* pRetVal  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 pRetVal  
 [out] 마지막 로드 오류와 관련 된.pdb 파일 이름을 포함 하는 문자열을 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 로드 작업으로 인 한 마지막 오류 코드를 반환 합니다. 반환 `E_INVALIDARG` 경우는 `pRetVal` 매개 변수는 `NULL`합니다.  
  
## <a name="example"></a>예제  
  
```C++  
BSTR    fileName;  
HRESULT errorCode = pSource->get_lastError( &fileName );  
```  
  
## <a name="see-also"></a>참고 항목  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)