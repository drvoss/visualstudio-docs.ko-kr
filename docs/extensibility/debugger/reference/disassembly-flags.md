---
title: DISASSEMBLY_FLAGS | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- DISASSEMBLY_FLAGS
helpviewer_keywords:
- DISASSEMBLY_FLAGS enumeration
ms.assetid: c1ec5a4d-5d42-4660-932c-7348550140cb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f6d42a7c5e9247359abfcdb4d65db5a4e0de247e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49916402"
---
# <a name="disassemblyflags"></a>DISASSEMBLY_FLAGS
디스어셈블리에 대 한 플래그를 지정합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
enum enum_DISASSEMBLY_FLAGS {   
   DF_DOCUMENTCHANGE     = 0x00000001,  
   DF_DISABLED           = 0x00000002,  
   DF_INSTRUCTION_ACTIVE = 0x00000004,  
   DF_DATA               = 0x00000008,  
   DF_HASSOURCE          = 0x00000010,  
   DF_DOCUMENT_CHECKSUM  = 0x00000020  
};  
typedef DWORD DISASSEMBLY_FLAGS;  
```  
  
```csharp  
public enum enum_DISASSEMBLY_FLAGS {   
   DF_DOCUMENTCHANGE     = 0x00000001,  
   DF_DISABLED           = 0x00000002,  
   DF_INSTRUCTION_ACTIVE = 0x00000004,  
   DF_DATA               = 0x00000008,  
   DF_HASSOURCE          = 0x00000010,  
   DF_DOCUMENT_CHECKSUM  = 0x00000020  
};  
```  
  
## <a name="members"></a>멤버  
 DF_DOCUMENTCHANGE  
 이 명령은 이전 보다 다른 문서의 임을 나타냅니다.  
  
 DF_DISABLED  
 이 명령이 실행 되지 않도록 나타냅니다.  
  
 DF_INSTRUCTION_ACTIVE  
 이 명령을 실행 하려면 다음 지침 중 하나 임을 나타냅니다 (있을 둘 이상).  
  
 DF_DATA  
 실제로이 명령이 데이터 (코드 아님) 임을 나타냅니다.  
  
 DF_HASSOURCE  
 이 명령은 소스에 있음을 나타냅니다. 프로 파일링 또는 가비지 컬렉션 코드와 같은 몇 가지 지침을 해당 하는 소스가 없는 경우  
  
 DF_DOCUMENT_CHECKSUM  
 나타내는 `bstrDocumentUrl` 필드 문서 URL 후 체크섬 데이터를 포함 합니다. 에 대 한 설명 섹션을 참조 합니다 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) 체크섬 데이터가 저장 되는 방법에 대 한 구조입니다.  
  
## <a name="remarks"></a>설명  
 로 사용 합니다 `dwFlags` 의 멤버는 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) 구조입니다.  
  
 이러한 플래그는 비트과 결합 될 수 `OR`입니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>참고 항목  
 [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)