---
title: 디렉터리 상태 코드 열거자 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- directory status code enumerator
- source control plug-ins, directory status enumeration
ms.assetid: 616026b5-f529-40ef-90c1-1836e116d797
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e082a691a389d5cb9a8fa307a627b11911e0db78
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68185246"
---
# <a name="directory-status-code-enumerator"></a>디렉터리 상태 코드 열거자
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`SccDirStatus` 소스 제어 시스템에서 디렉터리의 상태를 지정 하는 명명 된 상수 값을 포함 하는 열거자입니다. 이 열거형은에서 사용 된 [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)합니다. 이 원본 제어 플러그 인 API 버전 1.2에에서 도입 되었습니다.  
  
## <a name="syntax"></a>구문  
  
```  
enum SccDirStatus {  
   SCC_DIRSTATUS_INVALID       = -1L,  
   SCC_DIRSTATUS_NOTCONTROLLED = 0x0000L,  
   SCC_DIRSTATUS_CONTROLLED    = 0x0001L,  
   SCC_DIRSTATUS_EMPTYPROJ     = 0x0002L  
};  
```  
  
## <a name="members"></a>멤버  
 SCC_DIRSTATUS_INVALID  
 상태를 가져올 수 없습니다. 이에 의존 하지 않습니다.  
  
 SCC_DIRSTATUS_NOTCONTROLLED  
 디렉터리를 소스 제어에 없습니다.  
  
 SCC_DIRSTATUS_CONTROLLED  
 소스 제어 디렉터리가 있습니다.  
  
 SCC_DIRSTATUS_EMPTYPROJ  
 이 디렉터리에 해당 하는 프로젝트가 비어 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [원본 제어 플러그 인](../extensibility/source-control-plug-ins.md)   
 [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)
