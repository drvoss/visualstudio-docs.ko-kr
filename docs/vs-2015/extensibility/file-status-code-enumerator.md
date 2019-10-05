---
title: 파일 상태 코드 열거자 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- named constants, SccStatus enumerator
- source control plug-ins, file status enumeration
- SccStatus enumerator
- file status code enumerator
ms.assetid: 5c37876b-c83c-4ca1-837b-57cd465a879a
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1b6e74caa9eedd42e25339d62f5837ccfe82d001
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68204369"
---
# <a name="file-status-code-enumerator"></a>파일 상태 코드 열거자
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
 SCC_STATUS_INVALID  
 상태를 가져올 수 없습니다. 이에 의존 하지 않습니다.  
  
 SCC_STATUS_NOTCONTROLLED  
 파일이 소스 제어 아닙니다.  
  
 SCC_STATUS_CONTROLLED  
 파일이 소스 제어 합니다.  
  
 SCC_STATUS_CHECKEDOUT  
 로컬 디스크에 현재 사용자가 체크 아웃 합니다.  
  
 SCC_STATUS_OUTOTHER  
 파일은 다른 사용자가 체크 아웃 됩니다.  
  
 SCC_STATUS_OUTEXCLUSIVE  
 파일이는 배타적으로 체크 아웃 됩니다.  
  
 SCC_STATUS_OUTMULTIPLE  
 파일은 둘 이상의 사용자가 체크 아웃 됩니다.  
  
 SCC_STATUS_OUTOFDATE  
 파일이 최신 아닙니다.  
  
 SCC_STATUS_DELETED  
 프로젝트에서 파일 삭제 되었습니다.  
  
 SCC_STATUS_LOCKED  
 파일이 잠겨 있습니다. 더 많은 버전을 사용할 수 없습니다.  
  
 SCC_STATUS_MERGED  
 파일 병합 되었지만 아직 고정/확인할 수 있습니다.  
  
 SCC_STATUS_SHARED  
 파일은 프로젝트 간에 공유 됩니다.  
  
 SCC_STATUS_PINNED  
 파일은 특정 버전에 공유 됩니다.  
  
 SCC_STATUS_MODIFIED  
 파일을 수정/손상/위반 되었습니다.  
  
 SCC_STATUS_OUTBYUSER  
 파일은 현재 사용자가 체크 아웃 됩니다.  
  
 SCC_STATUS_NOMERGE  
 사용 하 여 병합할 수 없습니다 파일과 가져오기 전 저장할 수 있어야 합니다.  
  
 SCC_STATUS_RESERVED_1  
 내부용으로 예약됩니다.  
  
 SCC_STATUS_RESERVED_2  
 내부용으로 예약됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [원본 제어 플러그 인](../extensibility/source-control-plug-ins.md)   
 [SccQueryInfo](../extensibility/sccqueryinfo-function.md)   
 [POPLISTFUNC](../extensibility/poplistfunc.md)
