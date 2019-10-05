---
title: IDebugProcessSecurity::GetUserName | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 17a6ef52d7df1c60b0cb6581a7e15eeaf67e7875
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68202777"
---
# <a name="idebugprocesssecuritygetusername"></a>IDebugProcessSecurity::GetUserName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

포트 공급자에서 사용자 이름을 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT GetUserName(  
    BSTR *pbstrUserName  
);  
```  
  
```csharp  
int GetUserName (  
    string pbstrUserName  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pbstrUserName`  
 [out] 사용자 이름을 포함 하는 문자열입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드가 성공 하는 경우 반환 `S_OK`합니다. 그렇지 않으면 오류 코드를 반환합니다.  
  
## <a name="remarks"></a>설명  
 `GetUserName` 에 표시 되는 사용자 이름을 반환 합니다 **사용자 이름** 열의 합니다 **프로세스에 연결** 대화 상자. 보려는 합니다 **프로세스에 연결** 대화 상자에서 클릭 **프로세스에 연결** 에 **도구** 메뉴에서를 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 통합된 개발 환경 (IDE).  
  
## <a name="see-also"></a>관련 항목  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
