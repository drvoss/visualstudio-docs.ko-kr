---
title: SuspendTracking | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- SuspendTracking
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- SuspendTracking
ms.assetid: f5e06e5a-8083-444c-99c1-07ba834226b5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cc2a8b3dc2f5940c64be870df452b088dce7bc0e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62939008"
---
# <a name="suspendtracking"></a>SuspendTracking
현재 컨텍스트에서 추적을 일시 중단합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT WINAPI SuspendTracking(void);
```

## <a name="return-value"></a>반환 값
 추적이 일시 중단된 경우 **SUCCEEDED** 비트가 설정된 **HRESULT**를 반환합니다.

## <a name="requirements"></a>요구 사항
 **헤더:** *FileTracker.h*

## <a name="see-also"></a>참고 항목
- [ResumeTracking](../msbuild/resumetracking.md)