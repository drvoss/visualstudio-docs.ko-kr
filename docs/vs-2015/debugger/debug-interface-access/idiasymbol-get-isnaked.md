---
title: 'Idiasymbol:: Get_isnaked | Microsoft Docs'
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
- IDiaSymbol::get_isNaked method
ms.assetid: b16629dc-8e17-476b-9c7b-58e7277c61ed
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8a0fea18234180bf2da2c2f82648d0e7155c49bb
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51791412"
---
# <a name="idiasymbolgetisnaked"></a>IDiaSymbol::get_isNaked
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

함수에 있는지 여부를 지정 하는 플래그를 검색 합니다 [naked](http://msdn.microsoft.com/library/69723241-05e1-439b-868e-20a83a16ab6d) 특성 (즉, 함수에 프롤로그 또는 에필로그 코드 컴파일러에 의해 추가).  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT get_isNaked(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pFlag`  
 [out] 반환 `TRUE` 함수에 있으면 합니다 `naked` 반환이 고, 그렇지 않으면 특성 `FALSE`합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 반환 `S_OK`이 고, 그렇지 않으면 반환 `S_FALSE` 또는 오류 코드입니다.  
  
> [!NOTE]
>  반환 값이 `S_FALSE` 속성 기호를 사용할 수 없는 것을 의미 합니다.  
  
## <a name="requirements"></a>요구 사항  
  
|요구 사항|설명|  
|-----------------|-----------------|  
|헤더:|dia2.h|  
|버전:|DIA SDK v8.0|  
  
## <a name="see-also"></a>참고 항목  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Naked 함수 호출](http://msdn.microsoft.com/library/2a66847a-a43f-4541-a7be-c9f5f29b5fdb)



