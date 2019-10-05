---
title: 'Idiasession:: Put_loadaddress | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::put_loadAddress method
ms.assetid: b157b245-1ea0-4b80-8962-d8b278dbc742
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f697384874726904960fc5ba04733c3acfe1cd06
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438462"
---
# <a name="idiasessionputloadaddress"></a>IDiaSession::put_loadAddress
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

이 기호 저장소에 기호에 해당 하는 실행 파일의 로드 주소를 설정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT put_loadAddress (   
   ULONGLONG NewVal  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `NewVal`  
 [in] 실행 파일에 대 한 주소를 로드 합니다.  
  
## <a name="remarks"></a>설명  
 기호 가상 주소 (VA) 속성 값이 메서드를 사용 하 여 계산 됩니다. 가상 주소에는이 속성이 설정 되지 않았으면 0이 아닌 계산 되지 않습니다.  
  
> [!NOTE]
> 가져올 때이 메서드를 호출 해야 합니다 [IDiaSession](../../debugger/debug-interface-access/idiasession.md) 개체 및 기호에서 모든 가상 속성을 사용 하는 경우 개체를 사용 하 여을 시작 하기 전에 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
