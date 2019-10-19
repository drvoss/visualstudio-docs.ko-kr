---
title: IActiveScriptParseProcedureOld 인터페이스 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParseProcedureOld
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptParseProcedureOld interface
ms.assetid: d94b391e-4c24-46da-a01f-2c134ca4f041
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4558a0cab2aea9b56db2759bb80b1287cd33ce87
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571430"
---
# <a name="iactivescriptparseprocedureold-interface"></a>IActiveScriptParseProcedureOld 인터페이스
프로시저에 대 한 소스 코드 텍스트를 스크립트에 추가할 수 있습니다. VBScript와 같이 독립적인 제작 환경이 없는 해석 된 스크립트 언어의 경우에는 이름 공간에 스크립트 프로시저를 추가할 수 있는 대체 메커니즘 (`IActiveScriptParse` 또는 `IPersist*` 제외)이 제공 됩니다.  
  
> [!NOTE]
> 이 인터페이스는 `IActiveScriptParseProcedure` 인터페이스를 위해 더 이상 사용 되지 않습니다.  
  
## <a name="methods"></a>메서드  
 @No__t_0에서 상속 된 메서드 외에도 `IActiveScriptParseProcedureOld` 인터페이스는 다음 메서드를 노출 합니다.  
  
|메서드|설명|  
|------------|-----------------|  
|[IActiveScriptParseProcedureOld::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedureold-parseproceduretext.md)|지정 된 코드 프로시저를 구문 분석 하 고 프로시저를 이름 공간에 추가 합니다.|  
  
## <a name="see-also"></a>참조  
 [IActiveScriptParseProcedure](../../winscript/reference/iactivescriptparseprocedure.md)