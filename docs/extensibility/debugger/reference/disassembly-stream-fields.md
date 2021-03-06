---
title: DISASSEMBLY_STREAM_FIELDS | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- DISASSEMBLY_STREAM_FIELDS
helpviewer_keywords:
- DISASSEMBLY_STREAM_FIELDS enumeration
ms.assetid: cfc9b4de-c756-4844-bea7-d9f186a51d1b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9489b8c4399ae72bf7f6a70011eec347d870ca80
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49928336"
---
# <a name="disassemblystreamfields"></a>DISASSEMBLY_STREAM_FIELDS
디스어셈블리 필드에 대 한 검색 정보를 지정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
enum enum_DISASSEMBLY_STREAM_FIELDS {   
   DSF_ADDRESS          = 0x00000001,  
   DSF_ADDRESSOFFSET    = 0x00000002,  
   DSF_CODEBYTES        = 0x00000004,  
   DSF_OPCODE           = 0x00000008,  
   DSF_OPERANDS         = 0x00000010,  
   DSF_SYMBOL           = 0x00000020,  
   DSF_CODELOCATIONID   = 0x00000040,  
   DSF_POSITION         = 0x00000080,  
   DSF_DOCUMENTURL      = 0x00000100,  
   DSF_BYTEOFFSET       = 0x00000200,  
   DSF_FLAGS            = 0x00000400,  
   DSF_OPERANDS_SYMBOLS = 0x00010000,  
   DSF_ALL              = 0x000107ff  
};  
typedef DWORD DISASSEMBLY_STREAM_FIELDS;  
```  
  
```csharp  
public enum enum_DISASSEMBLY_STREAM_FIELDS {   
   DSF_ADDRESS          = 0x00000001,  
   DSF_ADDRESSOFFSET    = 0x00000002,  
   DSF_CODEBYTES        = 0x00000004,  
   DSF_OPCODE           = 0x00000008,  
   DSF_OPERANDS         = 0x00000010,  
   DSF_SYMBOL           = 0x00000020,  
   DSF_CODELOCATIONID   = 0x00000040,  
   DSF_POSITION         = 0x00000080,  
   DSF_DOCUMENTURL      = 0x00000100,  
   DSF_BYTEOFFSET       = 0x00000200,  
   DSF_FLAGS            = 0x00000400,  
   DSF_OPERANDS_SYMBOLS = 0x00010000,  
   DSF_ALL              = 0x000107ff  
};  
```  
  
## <a name="members"></a>멤버  
 DSF_ADDRESS  
 초기화/사용 된 `bstrAddress` 필드입니다.  
  
 DSF_ADDRESSOFFSET  
 초기화/사용 된 `bstrAddressOffset` 필드입니다.  
  
 DSF_CODEBYTES  
 초기화/사용 된 `bstrCodeBytes` 필드입니다.  
  
 DSF_OPCODE  
 초기화/사용 된 `bstrOpCode` 필드입니다.  
  
 DSF_OPERANDS  
 초기화/사용 된 `bstrOperands` 필드입니다.  
  
 DSF_SYMBOL  
 초기화/사용 된 `bstrSymbol` 필드입니다.  
  
 DSF_CODELOCATIONID  
 초기화/사용 된 `uCodeLocationId` 필드입니다.  
  
 DSF_POSITION  
 초기화/사용 된 `posBeg` 고 `posEnd` 필드입니다.  
  
 DSF_DOCUMENTURL  
 초기화/사용 된 `bstrDocumentUrl` 필드입니다.  
  
 DSF_BYTEOFFSET  
 초기화/사용 된 `dwByteOffset` 필드입니다.  
  
 DSF_FLAGS  
 초기화/사용 된 `dwFlags` ([DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)) 필드입니다.  
  
 DSF_OPERANDS_SYMBOLS  
 기호 이름에 포함 된 `bstrOperands` 필드입니다.  
  
 DSF_ALL  
 디스어셈블리 스트림에 대 한 모든 필드를 지정합니다.  
  
## <a name="remarks"></a>설명  
 매개 변수로 전달 합니다 [읽기](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) 의 필드를 표시 하는 방법 합니다 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) 구조는 초기화할.  
  
 에 사용 되는 합니다 `dwFields` 의 멤버는 `DisassemblyData` 구조 반환 되 면 유효 하 고 사용 되는 필드는 구조체.  
  
 이러한 값을 비트 결합할 수 있습니다 `OR`합니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>참고 항목  
 [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)   
 [읽기](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)   
 [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)