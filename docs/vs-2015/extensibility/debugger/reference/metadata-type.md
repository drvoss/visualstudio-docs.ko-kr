---
title: METADATA_TYPE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- METADATA_TYPE
helpviewer_keywords:
- METADATA_TYPE structure
ms.assetid: 2d8b78f6-0aef-4d79-809a-cff9b2c24659
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1be7cb6071a0307a56285b8929e52e038c263fdc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62546826"
---
# <a name="metadatatype"></a>METADATA_TYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 구조체는 메타 데이터에서 가져온 필드 형식에 대 한 정보를 지정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
typedef struct _tagTYPE_METADATA {  
   ULONG32  ulAppDomainID;  
   GUID     guidModule;  
   _mdToken tokClass;  
} METADATA_TYPE;  
```  
  
```csharp  
public struct METADATA_TYPE {  
   public uint ulAppDomainID;  
   public Guid guidModule;  
   public int  tokClass;  
};  
```  
  
#### <a name="parameters"></a>매개 변수  
 ulAppDomainID  
 기호 가져온 응용 프로그램의 ID입니다. 이 응용 프로그램의 인스턴스를 고유 하 게 식별에 사용 됩니다.  
  
 guidModule  
 이 필드를 포함 하는 모듈의 GUID입니다.  
  
 tokClass  
 이 형식의 메타 데이터 토큰 ID입니다.  
  
 [C++] `_mdToken` 되는 `typedef` 32 비트 `int`합니다.  
  
## <a name="remarks"></a>설명  
 이 구조체의 공용 구조체의 일부분으로 표시를 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) 경우 구조체를 `dwKind` 필드를 `TYPE_INFO` 구조로 설정 되어 `TYPE_KIND_METADATA` (의 값을 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) 열거형)입니다.  
  
 `tokClass` 값은 형식이 고유 하 게 식별 하는 메타 데이터 토큰입니다. 메타 데이터 토큰 ID의 상위 비트를 해석 하는 방법에 대 한 내용은 참조는 `CorTokenType` corhdr.h 파일에서 열거형은 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK.  
  
## <a name="requirements"></a>요구 사항  
 헤더: sh.h  
  
 네임스페이스: Microsoft.VisualStudio.Debugger.Interop  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>참고 항목  
 [구조체 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
