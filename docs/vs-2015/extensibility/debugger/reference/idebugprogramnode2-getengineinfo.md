---
title: IDebugProgramNode2::GetEngineInfo | Microsoft Docs
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
- IDebugProgramNode2::GetEngineInfo
helpviewer_keywords:
- IDebugProgramNode2::GetEngineInfo
ms.assetid: 664e7fe5-9100-4b7d-9dc5-e5a4dd0d0451
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f7f4a885d1c2f119c6c0e978614502102adc5c4d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51741515"
---
# <a name="idebugprogramnode2getengineinfo"></a>IDebugProgramNode2::GetEngineInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이름 및 프로그램을 실행 하는 디버그 엔진 (DE)의 식별자를 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT GetEngineInfo (   
   BSTR* pbstrEngine,  
   GUID* pguidEngine  
);  
```  
  
```csharp  
int GetEngineInfo(  
   out string pbstrEngine,   
   out Guid pguidEngine  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pbstrEngine`  
 [out] 프로그램을 실행 하는 DE의 이름을 반환 합니다 (c + + 관련: 호출자 엔진의 이름을 원하는 임을 나타내는 null 포인터 수)입니다.  
  
 `pguidEngine`  
 [out] 프로그램을 실행 하는 DE의 전역 고유 식별자를 반환 (c + + 관련: 호출자가 엔진의 GUID에 관심이 없는 나타내는 null 포인터 수)입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)

