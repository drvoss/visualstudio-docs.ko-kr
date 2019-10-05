---
title: 파일 상태 코드 열거자 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- named constants, SccStatus enumerator
- source control plug-ins, file status enumeration
- SccStatus enumerator
- file status code enumerator
ms.assetid: 5c37876b-c83c-4ca1-837b-57cd465a879a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 94bd9ff93872139fc056c4c8bb7a59191616919e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66342696"
---
# <a name="file-status-code-enumerator"></a>파일 상태 코드 열거자
`SccStatus` 소스 제어 시스템에서 파일의 상태를 지정 하는 명명 된 상수 값을 포함 하는 열거자입니다. 이 열거형은에서 사용 합니다 [SccQueryInfo](../extensibility/sccqueryinfo-function.md) 하며 `POPLISTFUNC` 콜백 함수 (참조 [POPLISTFUNC](../extensibility/poplistfunc.md) 세부 정보에 대 한).

## <a name="syntax"></a>구문

```
enum SccStatus {
   SCC_STATUS_INVALID          = -1L,
   SCC_STATUS_NOTCONTROLLED    = 0x0000L,
   SCC_STATUS_CONTROLLED       = 0x0001L,
   SCC_STATUS_CHECKEDOUT       = 0x0002L,
   SCC_STATUS_OUTOTHER         = 0x0004L,
   SCC_STATUS_OUTEXCLUSIVE     = 0x0008L,
   SCC_STATUS_OUTMULTIPLE      = 0x0010L,
   SCC_STATUS_OUTOFDATE        = 0x0020L,
   SCC_STATUS_DELETED          = 0x0040L,
   SCC_STATUS_LOCKED           = 0x0080L,
   SCC_STATUS_MERGED           = 0x0100L,
   SCC_STATUS_SHARED           = 0x0200L,
   SCC_STATUS_PINNED           = 0x0400L,
   SCC_STATUS_MODIFIED         = 0x0800L,
   SCC_STATUS_OUTBYUSER        = 0x1000L
   SCC_STATUS_NOMERGE          = 0x2000L
   SCC_STATUS_RESERVED_1       = 0x4000L
   SCC_STATUS_RESERVED_2       = 0x8000L
};
```

## <a name="members"></a>멤버
 SCC_STATUS_INVALID 상태를 가져올 수 없습니다. 이에 의존 하지 않습니다.

 SCC_STATUS_NOTCONTROLLED 파일이 소스 제어 아닙니다.

 SCC_STATUS_CONTROLLED 파일이 소스 제어 합니다.

 로컬 디스크에서 현재 사용자가 로그 아웃 SCC_STATUS_CHECKEDOUT 확인 합니다.

 SCC_STATUS_OUTOTHER 파일이 다른 사용자가 체크 아웃 됩니다.

 SCC_STATUS_OUTEXCLUSIVE 파일 단독으로 체크 아웃 됩니다.

 SCC_STATUS_OUTMULTIPLE 파일 둘 이상의 사용자가 체크 아웃 됩니다.

 SCC_STATUS_OUTOFDATE 파일 최신 아닙니다.

 SCC_STATUS_DELETED 파일 프로젝트에서 삭제 되었습니다.

 SCC_STATUS_LOCKED 파일이 잠겨 있습니다. 더 많은 버전을 사용할 수 없습니다.

 SCC_STATUS_MERGED 파일 병합 되었지만 아직 고정/확인할 수 있습니다.

 SCC_STATUS_SHARED 파일은 프로젝트 간에 공유 됩니다.

 SCC_STATUS_PINNED 파일 특정 버전에 공유 됩니다.

 SCC_STATUS_MODIFIED 파일 수정/손상/위반 되었습니다.

 현재 사용자가 SCC_STATUS_OUTBYUSER 파일 체크 아웃 됩니다.

 SCC_STATUS_NOMERGE 파일 되지 병합 될 수 있습니다 및 GET 하기 전에 저장 되지 해야 합니다.

 SCC_STATUS_RESERVED_1 내부 용도로 예약 되어 있습니다.

 SCC_STATUS_RESERVED_2 내부 용도로 예약 되어 있습니다.

## <a name="see-also"></a>참고자료
- [원본 제어 플러그 인](../extensibility/source-control-plug-ins.md)
- [SccQueryInfo](../extensibility/sccqueryinfo-function.md)
- [POPLISTFUNC](../extensibility/poplistfunc.md)