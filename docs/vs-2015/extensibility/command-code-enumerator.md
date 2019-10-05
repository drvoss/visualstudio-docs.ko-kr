---
title: 명령 코드 열거자 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- command code enumerator
- source control plug-ins, command code enumeration
ms.assetid: 5d2c360c-59e4-4da8-bcb4-dd07c7441e40
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 06f1a3f7146125e59d02efc72a4d4fc9ab33be39
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68184382"
---
# <a name="command-code-enumerator"></a>명령 코드 열거자
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 열거자에 대 한 옵션에 사용 되는 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) 하며 [SccPopulateList](../extensibility/sccpopulatelist-function.md)옵션 지정 되는 명령을 나타냅니다.  
  
## <a name="syntax"></a>구문  
  
```  
enum SCCCOMMAND {  
   SCC_COMMAND_GET,  
   SCC_COMMAND_CHECKOUT,  
   SCC_COMMAND_CHECKIN,  
   SCC_COMMAND_UNCHECKOUT,  
   SCC_COMMAND_ADD,  
   SCC_COMMAND_REMOVE,  
   SCC_COMMAND_DIFF,  
   SCC_COMMAND_HISTORY,  
   SCC_COMMAND_RENAME,  
   SCC_COMMAND_PROPERTIES,  
   SCC_COMMAND_OPTIONS  
};  
```  
  
## <a name="members"></a>멤버  
 SCC_COMMAND_GET  
 에 해당 하는 [SccGet](../extensibility/sccget-function.md)합니다.  
  
 SCC_COMMAND_CHECKOUT  
 에 해당 하는 [SccCheckout](../extensibility/scccheckout-function.md)합니다.  
  
 SCC_COMMAND_CHECKIN  
 에 해당 하는 [SccCheckin](../extensibility/scccheckin-function.md)합니다.  
  
 SCC_COMMAND_UNCHECKOUT  
 에 해당 하는 [SccUncheckout](../extensibility/sccuncheckout-function.md)합니다.  
  
 SCC_COMMAND_ADD  
 에 해당 하는 [SccAdd](../extensibility/sccadd-function.md)합니다.  
  
 SCC_COMMAND_REMOVE  
 에 해당 하는 [SccRemove](../extensibility/sccremove-function.md)합니다.  
  
 SCC_COMMAND_DIFF  
 에 해당 하는 [SccDiff](../extensibility/sccdiff-function.md)합니다.  
  
 SCC_COMMAND_HISTORY  
 에 해당 하는 [SccHistory](../extensibility/scchistory-function.md)합니다.  
  
 SCC_COMMAND_RENAME  
 에 해당 하는 [SccRename](../extensibility/sccrename-function.md)합니다.  
  
 SCC_COMMAND_PROPERTIES  
 에 해당 하는 [SccProperties](../extensibility/sccproperties-function.md)합니다.  
  
 SCC_COMMAND_OPTIONS  
 에 해당 하는 [SccSetOption](../extensibility/sccsetoption-function.md)합니다.  
  
## <a name="see-also"></a>참고 항목  
 [원본 제어 플러그 인](../extensibility/source-control-plug-ins.md)   
 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)   
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)
