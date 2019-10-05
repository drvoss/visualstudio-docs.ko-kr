---
title: IProvideExpressionContexts 인터페이스 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IProvideExpressionContexts interface
ms.assetid: e4c70f2c-7d86-4fdc-a1cb-f5a0bb8ed037
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b6ec0d5e17b0d3527252352c2e789adfac4fa859
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63410060"
---
# <a name="iprovideexpressioncontexts-interface"></a>IProvideExpressionContexts 인터페이스
특정 구성 요소에서 인식하고 있는 식 컨텍스트를 열거하는 방법을 제공합니다. 스크립트 엔진은 일반적으로이 인터페이스를 구현 합니다.  
  
 프로세스 디버그 관리자는 지정 된 스레드와 연결 된 모든 전역 식 컨텍스트를 찾으려면이 인터페이스를 사용 합니다.  
  
> [!NOTE]
> 이 인터페이스는 관심 스레드 내에서 호출 됩니다. 구현 자가 현재 스레드를 식별 하 고 적절 한 열거자를 반환 하는 것입니다.  
  
## <a name="methods"></a>메서드  
 상속 된 메서드 외에도 `IUnknown`, `IProvideExpressionContexts` 인터페이스는 다음 메서드를 노출 합니다.  
  
|메서드|설명|  
|------------|-----------------|  
|[IProvideExpressionContexts::EnumExpressionContexts](../../winscript/reference/iprovideexpressioncontexts-enumexpressioncontexts.md)|이 구성 요소에서 식 컨텍스트의 열거자를 반환 합니다.|