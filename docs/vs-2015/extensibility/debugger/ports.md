---
title: 포트 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- ports
- debugging [Debugging SDK], ports
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 73003e00fef5c37db4a702e7a4a1121600673844
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68153694"
---
# <a name="ports"></a>포트
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

디버거 아키텍처 측면을 **포트**:  
  
- 서버에서 실행 중 프로세스 집합에 대 한 컨테이너입니다. 예를 들어, 포트를 연결 된 직렬 케이블을 통해 Windows CE 기반 장치 또는 DCOM이 아닌 네트워크에 연결 된 컴퓨터에 나타낼 수 있습니다. 로컬 포트를 호출 하는 하나의 특수 포트는 로컬 컴퓨터에서 실행 중인 모든 프로세스를 포함 합니다.  
  
- 이름 또는 식별자로 자신을 식별할 수 있습니다.  
  
- 열거 포트에서 실행 중인 모든 프로세스 및 시작 하 고 이러한 프로세스를 종료 합니다.  
  
- 로 표시 됩니다는 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) 전달 하 여 생성 된 인터페이스는 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) 인수를 [포트 추가](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)합니다.  
  
  [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 모든 Windows 기반 프로세스, 네이티브 및 관리를 처리 하는 기본 포트를 제공 합니다. Windows 기반 하지 않는 외부 장치를 사용 하 여 사용자 지정 포트 연결에 대 한 구현 되어야 합니다. 이러한 사용자 지정 포트를 제공 하려면 사용자 지정 포트 공급자도 구현 해야 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [서버](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [프로세스](../../extensibility/debugger/processes.md)   
 [디버거 개념](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)   
 [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
