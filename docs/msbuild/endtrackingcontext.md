---
title: EndTrackingContext | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- EndTrackingContext
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- EndTrackingContext
ms.assetid: c2c5d794-8dc8-4594-8717-70dc79a0e75d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b7f837e7a983d0f2c2520d7e379ffb49f332c75c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62821119"
---
# <a name="endtrackingcontext"></a>EndTrackingContext
현재 추적 컨텍스트를 종료합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT WINAPI EndTrackingContext();
```

## <a name="return-value"></a>반환 값
추적 컨텍스트가 종료된 경우 **SUCCEEDED** 비트가 설정된 **HRESULT**를 반환합니다.

## <a name="requirements"></a>요구 사항
**헤더:** *FileTracker.h*

## <a name="see-also"></a>참고 항목
- [StartTrackingContext](../msbuild/starttrackingcontext.md)
