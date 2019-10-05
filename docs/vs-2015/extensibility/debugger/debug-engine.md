---
title: 디버그 엔진 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines
ms.assetid: 148b1efc-ca07-4d8e-bdfc-c723a760c620
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6e81a95cffebc9e26821b9cc6157627100343452
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63383375"
---
# <a name="debug-engine"></a>디버그 엔진
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

디버그 엔진 (DE) 작동 인터프리터 또는 운영 시스템 실행 제어, 중단점 및 식 평가 같은 디버깅 서비스를 제공 합니다. DE는 디버그 중인 프로그램의 상태를 모니터링 하는 일을 담당 합니다. 이 위해 수행 하는 DE 어떤 방법이 지원 되는 런타임에서 사용 가능한 런타임에서 CPU 또는 Api에서 제공 하는지 여부를 사용 합니다.  
  
 예를 들어, 공용 언어 런타임 (CLR) ICorDebugXXX 인터페이스를 통해 실행 중인 프로그램을 모니터링 하는 메커니즘을 제공 합니다. CLR을 지 원하는 DE 디버깅 중인 관리 코드 프로그램을 추적 하기 위해 적절 한 ICorDebugXXX 인터페이스를 사용 합니다. 이러한 정보를 전달 하는 세션 디버그 관리자 (SDM) 상태 변경 후 통신을 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE.  
  
> [!NOTE]
> 디버그 엔진에는 특정 런타임 실행 되 고 있는 프로그램 디버그는 시스템 즉, 대상으로 합니다. CLR은 관리 코드에 대해 런타임 및 Win32 런타임은 네이티브 Windows 응용 프로그램입니다. 이 두 런타임은 중 만든 언어 대상 수 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 이미 필요한 디버그 엔진을 제공 합니다. 모든 구현 해야 하는 식 계산기입니다.  
  
## <a name="debug-engine-operation"></a>엔진 작업 디버그  
 모니터링 서비스 DE 인터페이스를 통해 구현 되 고 다른 운영 모드 사이 전환 디버그 패키지 발생할 수 있습니다. 자세한 내용은 [운영 모드](../../extensibility/debugger/operational-modes.md)합니다. 일반적으로 런타임 환경 별로 하나의 DE 구현이입니다.  
  
> [!NOTE]
> TRANSACT-SQL에 대 한 별도 DE 구현을 있기는 및 [!INCLUDE[jsprjscript](../../includes/jsprjscript-md.md)], VBScript 및 [!INCLUDE[jsprjscript](../../includes/jsprjscript-md.md)] 단일 DE를 공유 합니다.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 디버깅 하면 두 가지 방법 중 하나를 실행 하는 엔진 디버그: 동일한 프로세스에서는 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 셸 또는 대상 프로그램과 동일한 프로세스에서 디버깅 중인 합니다. 두 번째 폼에는 일반적으로 디버깅 중인 프로세스는 인터프리터에서 실행 되는 스크립트에 실제로 디버그 엔진 스크립트를 모니터링 하려면 인터프리터에 대 한 깊은 지식이 있어야 때 발생 합니다. 이 경우 인터프리터는 런타임 실제로; 디버그 엔진은 특정 런타임 구현에 대 한 합니다. 또한 단일 DE 구현 (예: 원격 디버깅) 프로세스 및 컴퓨터 경계에 걸쳐 분할할 수 있습니다.  
  
 DE 노출 된 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 디버깅 인터페이스입니다. COM. 통해 모든 통신은 In process, 프로세스 아웃 또는 다른 컴퓨터에서 로드 되는 DE 여부를 구성 요소 통신에는 영향을 주지 않습니다.  
  
 DE 해당 특정 실행된 시간에 대 한 식의 구문을 이해 하는 DE를 사용 하도록 설정 하는 식 계산기 구성 요소를 사용 하 여 작동 합니다. 언어 컴파일러에서 생성 된 기호화 된 디버그 정보에 액세스 하는 기호 처리기 구성 요소는 DE 에서도 작동 합니다. 자세한 내용은 [식 계산기](../../extensibility/debugger/expression-evaluator.md) 하 고 [기호 공급자](../../extensibility/debugger/symbol-provider.md)합니다.  
  
## <a name="see-also"></a>참고 항목  
 [디버거 구성 요소](../../extensibility/debugger/debugger-components.md)   
 [식 계산기](../../extensibility/debugger/expression-evaluator.md)   
 [기호 공급자](../../extensibility/debugger/symbol-provider.md)
