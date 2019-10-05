---
title: ISetNextStatement 인터페이스 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: b570c2e0-a173-4f14-97d8-f39465753115
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de300a7af8492e6431f6b8513cde84a15895ad96
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62786310"
---
# <a name="isetnextstatement-interface"></a>ISetNextStatement 인터페이스
이 인터페이스는 현재 문을 업데이트 하려면 프로세스 디버그 관리자를 허용 하는 인터프리터에 의해 구현 됩니다. 스택 프레임 개체에서 구현 하 고 PDM QueryInterface 통해이 인터페이스를 가져옵니다.  
  
 인터페이스는 실행한 다음 문으로 결정 하는 실행 위치를 설정 하는 데 도움이 되는 메서드를 제공 합니다.  
  
 상속 된 메서드 외에도 `IUnknown`, `ISetNextStatement` 인터페이스는 다음 메서드를 노출 합니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[ISetNextStatement::CanSetNextStatement](../../winscript/reference/isetnextstatement-cansetnextstatement.md)|실행 위치를 지정된 된 위치에 설정할 수 있는지 여부를 결정 합니다.|  
|[ISetNextStatement::SetNextStatement](../../winscript/reference/isetnextstatement-setnextstatement.md)|지정된 된 위치에 실행 위치를 설정합니다.|