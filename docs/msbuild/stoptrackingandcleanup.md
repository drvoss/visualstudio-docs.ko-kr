---
title: StopTrackingAndCleanup | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
apiname:
- StopTrackingAndCleanup
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- StopTrackingAndCleanup
ms.assetid: 9f8c5994-2dfc-43c3-a5fb-89b2f8990429
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1ffbebd651087d9aa877d0e257947352a0d0275e
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/19/2018
ms.locfileid: "39154826"
---
# <a name="stoptrackingandcleanup"></a>StopTrackingAndCleanup
모든 추적을 중지하고 추적 세션에 사용된 메모리를 해제합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp 
HRESULT WINAPI StopTrackingAndCleanup(void);  
```  
  
## <a name="return-value"></a>반환 값  
 추적이 중지된 경우 **SUCCEEDED** 비트가 설정된 **HRESULT**를 반환합니다.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** *FileTracker.h*  
  
## <a name="see-also"></a>참고 항목  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)