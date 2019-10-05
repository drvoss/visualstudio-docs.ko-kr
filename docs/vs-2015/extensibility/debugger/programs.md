---
title: 프로그램 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], programs
- programs, debugging
ms.assetid: e1f955d8-95da-493b-837e-e97741a26d7e
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9070b33c7522cdc13fd6217956fcab72cd83f8d1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68153639"
---
# <a name="programs"></a>Programs
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

디버거 아키텍처 측면을 **프로그램**:  
  
- 일련의 모듈 및 스레드 집합이 모두에 대 한 컨테이너입니다. 프로그램을 Windows 운영 체제에 없는 단일 비유  
  
     프로그램이 하위 프로세스의 종류에 설명 합니다. 예를 들어, 웹 사이트를 디버깅 하는 경우에 스크립트를 프로그램으로 볼 수 있습니다. 스크립팅 엔진 프로세스의 스크립트를 실행 하는 동안 다른 스크립트의 독립적인 있습니다 스레드 자체 집합입니다. 디버그 엔진 (DE) 프로세스 또는 스레드는 프로그램을 연결합니다.  
  
- 자체 및 프로세스에서 실행 되 고, 분리 하 고 있는 경우 생성 된 DE 설명에 첨부할 수를 식별할 수 있습니다. 프로그램 수 실행, 중지, 계속 해 서를 종료 합니다.  
  
- 모든 스레드가 열거할 수 있습니다. 프로그램을 자체 디스어셈블리 스트림에 제공할 수도 있습니다 및 지정 된 문서 위치의 모든 코드 컨텍스트를 열거할 수 있습니다.  
  
- 로 표시 됩니다는 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) 프로그램은 연결 전이나 구현에 따라 연결 프로세스의 일부로 만든 인터페이스입니다. 프로세스의 프로그램을 열거 하는 포트, 해당에 따라 각 프로그램 생성 됩니다 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) 인터페이스에 대 한 인수로 전달 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)합니다. 디버그 엔진을 만들 수도 있지만 `IDebugProgram2` 프로그램 노드에 따라 프로그램에서 이러한 프로그램이 나타내는 인터페이스 생성 되지 않습니다. `IDebugProgramNode2` 는 DE 만든 인터페이스는 실제 디버깅을 위해 사용 되 고 프로세스에서는 프로그램이 실행 중인 검색만 사용 되는 포트에서 생성 된 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [프로세스](../../extensibility/debugger/processes.md)   
 [프로그램 노드](../../extensibility/debugger/program-nodes.md)   
 [모듈](../../extensibility/debugger/modules.md)   
 [디버거 개념](../../extensibility/debugger/debugger-concepts.md)   
 [디버그 엔진](../../extensibility/debugger/debug-engine.md)   
 [문서 위치](../../extensibility/debugger/document-position.md)   
 [코드 컨텍스트](../../extensibility/debugger/code-context.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
