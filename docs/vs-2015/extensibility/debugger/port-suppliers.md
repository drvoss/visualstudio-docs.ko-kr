---
title: 공급 업체 포트 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- port suppliers
- debugging [Debugging SDK], port suppliers
ms.assetid: a8f3db96-1a13-4e93-9ef6-0861880369e0
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e90871927c30399dea4691381baa749db2b3e8bf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68153710"
---
# <a name="port-suppliers"></a>포트 공급자
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

디버거 아키텍처 측면을 **포트 공급자**:  
  
- 서버에 포함 하 고 해당 서버에 요청에서 포트를 제공 합니다.  
  
- 추가 하 고 포함 하는 서버에서 포트를 제거할 수 있습니다.  
  
- 서버에 제공 된 모든 포트를 열거할 수 있습니다.  
  
- 로 표시 됩니다는 [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) 레지스트리를 통해 Visual Studio를 사용 하 여 등록 되는 인터페이스입니다. 이 인터페이스를 호출 하 여 얻을 수 있습니다 [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)합니다.  
  
  [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 기본 포트 공급자와 기본 포트를 제공합니다. 사용자 지정 포트를 구현 해야 하는 경우 사용자 지정 포트 공급자도 해야 해당 사용자 지정 포트를 제공 하도록 구현 해야 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [서버](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [포트](../../extensibility/debugger/ports.md)   
 [디버거 개념](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)
