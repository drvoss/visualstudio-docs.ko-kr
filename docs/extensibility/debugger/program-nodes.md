---
title: 노드 프로그램 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- program nodes, debugging context
- debugging [Debugging SDK], program nodes
- program nodes, adding
- program nodes, superceding
ms.assetid: 1c5a5c13-c14d-42c3-af11-4c63f1032c8d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ecc87a24b35993f200c709ee033fffe6a4ecb120
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49903623"
---
# <a name="program-nodes"></a>프로그램 노드
디버거 아키텍처에는 *프로그램 노드*:  
  
- 프로그램의 간단한 설명이입니다.  
  
- 자체 및에서 실행 중인 프로세스를 식별할 수 있습니다. 분리 되 고 있는 경우, 생성 된 디버그 엔진 (DE)에 대해 설명 하는 프로그램 노드를 연결할 수 있습니다.  
  
- 로 표시 됩니다는 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) 인터페이스를 일반적으로 DE 또는 포트에 의해 만들어집니다. 프로그램 노드는 호출 하 여 포트를 추가할 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)합니다. 프로그램 노드 포트에 추가 되 면이 프로그램 노드가 나타내는 프로그램을 포함 하는 프로세스에 추가 됩니다.  
  
  디버그 패키지의 구현에 따라 디버그 세션 시작 된 후에 잠시 프로그램 노드는 해당 프로그램을 만드는 사용 됩니다. 해당 프로그램에 대 한 프로세스를 쿼리하면 프로그램 열거 되지만 프로그램 노드마다 하나입니다.  
  
  프로그램에 연결 된 전에 IDE는 프로그램의 간단한 설명만을 요구 합니다. 프로그램 노드에서이 정보를 얻을 수 있습니다. 프로그램에 연결 된 후 IDE는 프로그램에서 실행 중인 모든 스레드 목록과 같은 자세한 정보를 표시 합니다. 이 정보는 프로그램 자체에서 가져옵니다.  
  
## <a name="see-also"></a>참고자료  
 [프로그램](../../extensibility/debugger/programs.md)   
 [프로세스](../../extensibility/debugger/processes.md)   
 [디버그 엔진](../../extensibility/debugger/debug-engine.md)   
 [디버거 개념](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)