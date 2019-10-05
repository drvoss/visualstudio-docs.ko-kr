---
title: IActiveScriptStats 인터페이스 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptStats interface
ms.assetid: dbe84d6f-1b77-4877-aced-cd4e01ead5b5
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e7a0e1e616fdee2dac58c8a5a1d24ed120b28bc2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62991968"
---
# <a name="iactivescriptstats-interface"></a>IActiveScriptStats 인터페이스
호스트를를 실행 중인 스크립트의 통계를 쿼리할 수 있습니다. 호스트는이 정보를 사용 하 여 경우 스크립트에서 너무 오래 걸렸습니다. 결정할 수 있습니다.  
  
 상속 된 메서드 외에도 `IUnknown`, `IActiveScriptStats` 인터페이스는 다음 메서드를 노출 합니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[IActiveScriptStats::GetStat](../../winscript/reference/iactivescriptstats-getstat.md)|표준 스크립트 통계 중 하나를 반환 합니다.|  
|[IActiveScriptStats::GetStatEx](../../winscript/reference/iactivescriptstats-getstatex.md)|사용자 지정 스크립트 통계를 반환 합니다.|  
|[IActiveScriptStats::ResetStats](../../winscript/reference/iactivescriptstats-resetstats.md)|이 스크립트에 대 한 통계를 다시 설정합니다.|