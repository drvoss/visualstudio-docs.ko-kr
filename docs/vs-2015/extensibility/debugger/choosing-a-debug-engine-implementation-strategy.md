---
title: 디버그 엔진 구현 전략 선택 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementation strategies
ms.assetid: 90458fdd-2d34-4f10-82dc-6d8f31b66d8b
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6b03e69892da217d84d56b39b7df61784907d2b0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68183464"
---
# <a name="choosing-a-debug-engine-implementation-strategy"></a>디버그 엔진 구현 전략 선택
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

런타임 아키텍처를 사용 하 여 디버그 엔진 (DE) 구현 전략을 결정 합니다. 디버그 엔진에는 in-process에 프로그램이 디버깅된, Visual Studio 세션 디버그 관리자 (SDM) 또는 둘 다에 프로세스 아웃 프로세스를 만들 수 있습니다. 다음 지침은 이러한 세 가지 전략 중에서 선택 하는 데 도움이 됩니다.  
  
## <a name="guidelines"></a>지침  
 de-out-of-process를 할 수 있지만 모두 SDM을 프로그램을 디버깅할 수 있습니다는 일반적으로 수행할 필요가 없습니다. 프로세스 경계를 넘어 호출 속도가 비교적 느립니다.  
  
 디버그 엔진은 공용 언어 런타임 환경 및 Win32 기본 런타임 환경에 대 한 이미 제공 됩니다. 이러한 환경 중 하나는 DE 바꿔야 DE in-process SDM을 사용 하 여 만들어야 합니다.  
  
 그렇지 않으면 in-process SDM로 또는 프로그램을 디버깅 하는 프로세스에는 DE 만드는 간에 선택할 수 있습니다. 식 계산기는 DE의 프로그램 기호 저장소에 자주 액세스 해야 하는 여부와 빠른 액세스를 위해 메모리에 기호 저장소를 로드할 수 있는지 여부를 고려 하는 것이 반드시 합니다. 또한 다음을 고려 합니다.  
  
- 식 계산기 및 기호 저장소 간의 호출 수 없는 경우, SDM 메모리 공간에 기호 저장소를 읽을 수 있으면 DE in-process SDM 만듭니다. 프로그램에 연결할 때 SDM을 디버그 엔진의 CLSID를 반환 해야 합니다. SDM이이 CLSID를 사용 하 여는 DE의 in process 인스턴스를 만듭니다.  
  
- DE 기호 저장소에 액세스 하는 프로그램을 호출 해야 프로그램과 DE-프로세스를 만듭니다. 이 경우 프로그램은 DE의 인스턴스를 만듭니다.  
  
## <a name="see-also"></a>참고 항목  
 [Visual Studio 디버거 확장성](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
