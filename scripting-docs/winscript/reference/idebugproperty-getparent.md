---
title: IDebugProperty::GetParent | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugProperty.GetParent
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugProperty::GetParent
ms.assetid: 673d625b-acca-45c4-88f4-b72275042f8f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f78d72bad8cb12b72f4b51e113d23dcd64ada8fd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49838363"
---
# <a name="idebugpropertygetparent"></a>IDebugProperty::GetParent
속성의 부모 속성을 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```  
HRESULT GetParent (  
   IDebugProperty** ppParent  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `ppParent`  
 [out] 반환 된 `IDebugProperty` 속성의 부모를 나타내는 인터페이스입니다.  
  
## <a name="return-value"></a>반환 값  
 유효한 반환 `HRESULT`, 일반적으로 `S_OK`.  
  
## <a name="see-also"></a>참고 항목  
 [IDebugProperty 인터페이스](../../winscript/reference/idebugproperty-interface.md)