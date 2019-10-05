---
title: 'Iactivescriptsiteuicontrol:: Getuibehavior 메서드 | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 9a944335-856a-4c6b-b2bc-8872542941b7
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1e3f6247afc70ef1197ea759ffdf475c2d6c0a0c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992228"
---
# <a name="iactivescriptsiteuicontrolgetuibehavior-method"></a>IActiveScriptSiteUIControl::GetUIBehavior 메서드
가져옵니다를 [SCRIPTUICHANDLING 열거형](../../winscript/reference/scriptuichandling-enumeration.md) 나타내는 UI 컨트롤을 처리 해야 하는 방식입니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetUIBehavior(     [in] SCRIPTUICITEM UicItem,     [out] SCRIPTUICHANDLING * pUicHandling );   
```  
  
#### <a name="parameters"></a>매개 변수  
 `UicItem`  
 컨트롤의 형식입니다.  
  
 `pUicHandling`  
 컨트롤을 처리 해야 하는 방법입니다.