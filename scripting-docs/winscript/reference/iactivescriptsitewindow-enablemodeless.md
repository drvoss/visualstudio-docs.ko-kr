---
title: IActiveScriptSiteWindow::EnableModeless | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteWindow.EnableModeless
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteWindow_EnableModeless
ms.assetid: 83fe4f62-8e97-4f03-bc6f-d90aa888657d
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4f15135273b98a65903a5d03de87c541fc032cce
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992928"
---
# <a name="iactivescriptsitewindowenablemodeless"></a>IActiveScriptSiteWindow::EnableModeless
호스트를 사용 하도록 설정 하거나 주 창 뿐만 아니라 모든 모덜리스 대화 상자를 사용 하지 않도록 하면 됩니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT EnableModeless(  
    BOOL fEnable  // enable flag  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `fEnable`  
 [in] 경우는 플래그 `TRUE`, 주 창 및 모덜리스 대화 상자를 사용 하도록 설정 또는 `FALSE`, 하를 사용 하지 않도록 설정 합니다.  
  
## <a name="return-value"></a>반환 값  
 반환 `S_OK` 성공 하면 또는 `E_FAIL` 오류가 발생 합니다.  
  
## <a name="remarks"></a>설명  
 이 메서드는 동일 합니다 `IOleInPlaceFrame::EnableModeless` 메서드.  
  
 이 메서드를 호출을 중첩할 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [IActiveScriptSiteWindow](../../winscript/reference/iactivescriptsitewindow.md)