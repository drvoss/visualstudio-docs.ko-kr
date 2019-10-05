---
title: IDebugProcessEx2::AddImplicitProgramNodes | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes
helpviewer_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes method
ms.assetid: 8b491b00-f9e7-45b3-9115-fe58c3464289
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: faca728144bde572d8a1d3424fbfcf908403d679
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68202827"
---
# <a name="idebugprocessex2addimplicitprogramnodes"></a>IDebugProcessEx2::AddImplicitProgramNodes
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 메서드는 지정 된 각 디버그 엔진 (DE)에 대 한 프로그램 노드를 추가 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT AddImplicitProgramNodes(  
   REFGUID guidLaunchingEngine,  
   GUID*   rgguidSpecificEngines,  
   DWORD   celtSpecificEngines  
);  
```  
  
```csharp  
int AddImplicitProgramNodes(  
   ref Guid guidLaunchingEngine,  
   Guid[]   rgguidSpecificEngines,  
   uint     celtSpecificEngines  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `guidLaunchingEngine`  
 [in] `GUID` 프로그램을 시작 하는 데는 (및 자체 프로그램 노드를 추가 하려면 가정)는 DE입니다.  
  
 `rgguidSpecificEngines`  
 [in] 배열을 `GUID`의프로그램에 대 한 노드를 추가할 수는 DEs입니다.  
  
 `celtSpecificEngines`  
 [in] 수가 `GUID`의 `rgguidSpecificEngines` 배열입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.  
  
## <a name="remarks"></a>설명  
 [노드 프로그램](../../../extensibility/debugger/program-nodes.md) 에 나열 된 각 DE 예정 `rgguidSpecificEngines`-시작 엔진 제외 하 고 (에 지정 된 대로 `guidLaunchingEngine`), 프로그램을 시작할 때 자체 프로그램 노드를 추가 하려면 가정 된 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)   
 [프로그램 노드](../../../extensibility/debugger/program-nodes.md)
