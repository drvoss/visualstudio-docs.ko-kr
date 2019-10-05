---
title: IDebugApplicationNode100 인터페이스 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationNode100 Interface
ms.assetid: 43966d4e-5f89-4a04-a08d-782347d00c2d
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d8de6f57cabe808df1506870fe65da31ef74e644
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436025"
---
# <a name="idebugapplicationnode100-interface"></a>IDebugApplicationNode100 인터페이스
합니다 `IDebugApplicationNode100` 인터페이스의 기능을 확장 합니다 [IDebugApplicationNode 인터페이스](../../winscript/reference/idebugapplicationnode-interface.md)합니다. 구현에서 QueryInterface를 호출 하 여이 인터페이스의 인스턴스를 가져올 수 있습니다 [IDebugApplicationNode 인터페이스](../../winscript/reference/idebugapplicationnode-interface.md)합니다.  
  
> [!IMPORTANT]
> 이 인터페이스는 PDM v10.0에서 큰 구현 됩니다. activdbg100.h에서 찾을 수 있습니다.  
  
## <a name="methods"></a>메서드  
 `IDebugApplicationNode100` 인터페이스는 다음 메서드를 노출합니다.  
  
|메서드|설명|  
|------------|-----------------|  
|[IDebugApplicationNode100::GetExcludedDocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md)|지정한 필터에 의해 숨겨진 텍스트 문서를 가져옵니다.|  
|[IDebugApplicationNode100::QueryIsChildNode](../../winscript/reference/idebugapplicationnode100-queryischildnode.md)|지정된 된 문서가 노드의 자식 노드 중 하나에 속하는지 여부를 결정 합니다.|  
|[IDebugApplicationNode100::SetFilterForEventSink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md)|특정 필터를 설정 합니다 [IDebugApplicationNodeEvents 인터페이스](../../winscript/reference/idebugapplicationnodeevents-interface.md) 구현 합니다. 스크립트 디버거를 PDM는 더 이상 노드 생성 되거나 제거 될 때 이벤트를 보낼 수 있도록 컴파일러에서 생성 된 자식 응용 프로그램 노드를 필터링 할 수 없습니다. 기본적으로 모든 노드에 전송 됩니다.|