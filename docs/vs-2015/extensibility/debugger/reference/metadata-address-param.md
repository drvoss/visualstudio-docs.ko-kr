---
title: METADATA_ADDRESS_PARAM | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- METADATA_ADDRESS_PARAM
helpviewer_keywords:
- METADATA_ADDRESS_PARAM structure
ms.assetid: 90904f19-0e71-4cb3-a56e-6a2e92f66dfc
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6ca2be0201da46081765d6f216e10acd8edec380
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51756115"
---
# <a name="metadataaddressparam"></a>METADATA_ADDRESS_PARAM
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 구조는 메서드 또는 함수 매개 변수를 나타냅니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
typedef struct _tagMETADATA_ADDRESS_PARAM {  
   _mdToken tokMethod;  
   _mdToken tokParam;  
   DWORD    dwIndex;  
} METADATA_ADDRESS_PARAM;  
```  
  
```csharp  
public struct METADATA_ADDRESS_PARAM {  
   public int  tokMethod;  
   public int  tokParam;  
   public uint dwIndex;  
}  
```  
  
## <a name="terms"></a>용어  
 tokMethod  
 메서드의 ID의 일부입니다.  
  
 tokParam  
 ID 매개 변수입니다.  
  
 dwIndex  
 매개 변수 목록의 매개 변수의 인덱스입니다.  
  
## <a name="remarks"></a>설명  
 이 구조체의 공용 구조체의 일부인를 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) 경우 구조체를 `dwKind` 필드를 `DEBUG_ADDRESS_UNION` 구조로 설정 되어 `ADDRESS_KIND_PARAM` (의 값을 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) 열거형)입니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>참고 항목  
 [구조체 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)

