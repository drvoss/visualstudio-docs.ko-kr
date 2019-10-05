---
title: IDebugAlias2::GetAppDomainId | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- GetAppDomainId
- IDebugAlias2::GetAppDomainId
ms.assetid: 23581aaa-5a53-4859-b264-eca49fc44bcd
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 79f6a71376d410f6eb0b524a309f5f6dffcdf614
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68197925"
---
# <a name="idebugalias2getappdomainid"></a>IDebugAlias2::GetAppDomainId
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

응용 프로그램 도메인에 대 한 식별자를 검색합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT GetAppDomainId (  
   ULONG32* pappDomainId  
);  
```  
  
```csharp  
int GetAppDomainId (  
   out uint pappDomainId  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pappDomainId`  
 [out] 응용 프로그램 도메인 식별자를 반환합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.  
  
## <a name="remarks"></a>설명  
 응용 프로그램 다시 시작 될 때마다 응용 프로그램 도메인 식별자 변경 및 새 응용 프로그램 도메인 생성 됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)
