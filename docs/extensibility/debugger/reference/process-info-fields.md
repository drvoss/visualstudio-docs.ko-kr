---
title: PROCESS_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROCESS_INFO_FIELDS
helpviewer_keywords:
- PROCESS_INFO_FIELDS enumeration
ms.assetid: 0d9cc345-3d3a-44d8-ae15-a67acb97a828
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fe9a1854fe5583d001e1dc156bfad5833fd1c08f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66309452"
---
# <a name="processinfofields"></a>PROCESS_INFO_FIELDS
프로세스에 대 한 검색할 정보의 종류를 지정 합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_PROCESS_INFO_FIELDS { 
   PIF_FILE_NAME             = 0x00000001,
   PIF_BASE_NAME             = 0x00000002,
   PIF_TITLE                 = 0x00000004,
   PIF_PROCESS_ID            = 0x00000008,
   PIF_SESSION_ID            = 0x00000010,
   PIF_ATTACHED_SESSION_NAME = 0x00000020,
   PIF_CREATION_TIME         = 0x00000040,
   PIF_FLAGS                 = 0x00000080,
   PIF_ALL                   = 0x000000ff
};
typedef DWORD PROCESS_INFO_FIELDS;
```

```csharp
public enum enum_PROCESS_INFO_FIELDS { 
   PIF_FILE_NAME             = 0x00000001,
   PIF_BASE_NAME             = 0x00000002,
   PIF_TITLE                 = 0x00000004,
   PIF_PROCESS_ID            = 0x00000008,
   PIF_SESSION_ID            = 0x00000010,
   PIF_ATTACHED_SESSION_NAME = 0x00000020,
   PIF_CREATION_TIME         = 0x00000040,
   PIF_FLAGS                 = 0x00000080,
   PIF_ALL                   = 0x000000ff
};
```

## <a name="fields"></a>필드
 `PIF_FILE_NAME`\
 초기화/사용 된 `bstrFileName` 필드를 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) 구조입니다.

 `PIF_BASE_NAME`\
 초기화/사용 된 `bstrBaseName` 필드는 `PROCESS_INFO` 구조입니다.

 `PIF_TITLE`\
 초기화/사용 된 `bstrTitle` 필드는 `PROCESS_INFO` 구조입니다.

 `PIF_PROCESS_ID`\
 초기화/사용 된 `ProcessId` 필드는 `PROCESS_INFO` 구조입니다.

 `PIF_SESSION_ID`\
 초기화/사용 된 `dwSessionId` 필드는 `PROCESS_INFO` 구조입니다.

 `PIF_ATTACHED_SESSION_NAME`\
 초기화/사용 된 `bstrAttachedSessionName` 필드는 `PROCESS_INFO` 구조입니다.

 `PIF_CREATION_TIME`\
 초기화/사용 된 `CreationTime` 필드는 `PROCESS_INFO` 구조입니다.

 `PIF_FLAGS`\
 초기화/사용 된 `Flags` 필드는 `PROCESS_INFO` 구조입니다.

 `PIF_ALL`\
 모든 필드를 채웁니다.

## <a name="remarks"></a>설명
 에 전달 합니다 [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) 의 필드를 표시 하는 방법을 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) 구조는 초기화할 합니다.

 에서도 사용 됩니다 `Fields` 필드는 `PROCESS_INFO` 에 유효 하 고 사용 되는 필드는 구조체.

 이러한 플래그는 비트과 결합 될 수 `OR`입니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: Microsoft.VisualStudio.Debugger.Interop

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)