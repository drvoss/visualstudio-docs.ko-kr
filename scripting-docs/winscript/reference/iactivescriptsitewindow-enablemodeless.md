---
title: 'IActiveScriptSiteWindow:: EnableModeless | Microsoft Docs'
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
ms.openlocfilehash: 756bda6209b6209ff14f6d67fef18faaed0b5618
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574133"
---
# <a name="iactivescriptsitewindowenablemodeless"></a>IActiveScriptSiteWindow::EnableModeless
호스트에서 주 창 및 모덜리스 대화 상자를 사용 하거나 사용 하지 않도록 설정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT EnableModeless(  
    BOOL fEnable  // enable flag  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `fEnable`  
 진행 @No__t_0 경우 주 창 및 모덜리스 대화 상자를 사용 하도록 설정 하거나 `FALSE` 경우 사용 하지 않도록 설정 하는 플래그입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 `S_OK`을 반환 하 고, 오류가 발생 한 경우 `E_FAIL` 합니다.  
  
## <a name="remarks"></a>주의  
 이 메서드는 `IOleInPlaceFrame::EnableModeless` 메서드와 동일 합니다.  
  
 이 메서드에 대 한 호출은 중첩 될 수 있습니다.  
  
## <a name="see-also"></a>참조  
 [IActiveScriptSiteWindow](../../winscript/reference/iactivescriptsitewindow.md)