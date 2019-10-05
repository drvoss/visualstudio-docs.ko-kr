---
title: IDebugProgram2::WriteDump | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgram2::WriteDump
helpviewer_keywords:
- IDebugProgram2::WriteDump
ms.assetid: 375afb8c-882d-44db-bfa7-e2c9eb555122
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 491515d2778c6ad16287739bfc88d8134903d2bb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68205798"
---
# <a name="idebugprogram2writedump"></a>IDebugProgram2::WriteDump
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

덤프 파일에 씁니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT WriteDump(   
   DUMPTYPE  DumpType,  
   LPCOLESTR pszDumpUrl  
);  
```  
  
```csharp  
int WriteDump(   
   enum_DUMPTYPE  DumpType,  
   string         pszDumpUrl  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `DumpType`  
 [in] 값을 [DUMPTYPE](../../../extensibility/debugger/reference/dumptype.md) 예를 들어, 짧은 덤프의 형식을 지정 하는 열거형 또는 long입니다.  
  
 `pszDumpUrl`  
 [in] 덤프를 작성 하려면 URL입니다. 형태로 이것이 일반적으로 `file://c:\path\filename.ext`, 하지만 임의의 올바른 URL이 될 수 있습니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.  
  
## <a name="remarks"></a>설명  
 프로그램 덤프는 일반적으로 현재 스택 프레임, 스택 자체, 프로그램과 프로그램을 소유 하는 메모리 수에서 실행 중인 스레드의 목록에 포함 됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
