---
title: 디버거 구성 요소 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], components
- components [Visual Studio SDK], debugging
- debugging [Debugging SDK], components
ms.assetid: 8b8ab77f-a134-495c-be42-3bc51aa62dfb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d3f79b9f22c2eb26b456e5e45c049a8f8bc04fae
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49818980"
---
# <a name="debugger-components"></a>디버거 구성 요소
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 디버거는 VSPackage로 구현 되었으며 전체 디버그 세션을 관리 합니다. 디버그 세션에는 다음 요소가 구성 됩니다.  
  
- **디버그 패키지:** 는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 디버거는 디버깅 중인 항목에 관계 없이 동일한 사용자 인터페이스를 제공 합니다.  
  
- **세션 디버그 관리자 (SDM):** 일관 된 프로그래밍 인터페이스를 제공 합니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 다양 한 디버그 엔진의 관리에 대 한 디버거. 에 의해 구현 됩니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]합니다.  
  
- **프로세스 디버그 관리자 (PDM):** 의 모든 실행 중인 인스턴스에 대 한 관리 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]을 수 있는 디버깅 중인 모든 프로그램의 목록입니다. 에 의해 구현 됩니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]합니다.  
  
- **디버그 엔진 (DE):** 디버깅 중인 프로그램을 모니터링 하는 SDM을 PDM, 실행 중인 프로그램의 상태를 통신 하 고 실시간으로 분석할 수 있도록 식 계산기 및 기호 공급자와 상호 작용 합니다 프로그램의 메모리 및 변수의 상태입니다. 에 의해 구현 됩니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (에 지 원하는 언어) 및 자체 실행된 시간을 지원 하려는 타사 공급 업체입니다. 
  
- **식 계산기 (EE):** 변수와 프로그램 특정 지점에서 중지 되었을 때 사용자가 제공한 식을 동적으로 평가 하는 것에 대 한 지원을 제공 합니다. 에 의해 구현 됩니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (에 지 원하는 언어) 및 자신의 언어를 지원 하려는 타사 공급 업체입니다.  
  
- **기호 공급자 (SP):** 라고도 기호 처리기를 프로그램의 디버깅 기호는 사용자를 매핑하여 프로그램의 실행 인스턴스 (예: 소스 코드 수준 디버깅 및 식 평가)는 의미 있는 정보를 제공할 수 있습니다. 에 의해 구현 됩니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (공용 언어 런타임 [CLR]에 대 한 기호 및 프로그램 데이터베이스 [PDB] 기호 파일 형식) 및 디버깅 정보를 저장 하는 방법이 자신의 소유 하는 타사 공급 업체입니다.  
  
  다음 다이어그램은 Visual Studio 디버거에서의 이러한 구성 요소 간의 관계를 보여줍니다.  
  
  ![디버깅 구성 요소 개요](../../extensibility/debugger/media/dbugcompovrview.gif "DBugCompOvrview")  
  
## <a name="in-this-section"></a>단원 내용  
 [패키지를 디버그 합니다.](../../extensibility/debugger/debug-package.md)  
 실행 되는 디버그 패키지에 설명 합니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 셸 및 전체 UI를 처리 합니다.  
  
 [프로세스 디버그 관리자](../../extensibility/debugger/process-debug-manager.md)  
 디버깅할 수 있는 프로세스의 관리자는 PDM의 기능에 간략하게 설명 합니다.  
  
 [세션 디버그 관리자](../../extensibility/debugger/session-debug-manager.md)  
 IDE에 디버그 세션의 통합된 보기를 제공 하는 SDM을 정의 합니다. SDM는 DE를 관리합니다.  
  
 [디버그 엔진](../../extensibility/debugger/debug-engine.md)  
 DE 제공 되는 디버깅 서비스를 설명 합니다.  
  
 [운영 모드](../../extensibility/debugger/operational-modes.md)  
 IDE 작동할 수 있는 세 가지 모드의 개요를 제공 합니다: 디자인 모드에서 실행된 모드 및 중단 모드입니다. 전환 메커니즘에 대해서도 설명 합니다.  
  
 [식 계산기](../../extensibility/debugger/expression-evaluator.md)  
 런타임에 EE의 용도 설명 합니다.  
  
 [기호 공급자](../../extensibility/debugger/symbol-provider.md)  
 평가 하는 방법을, 구현, 기호 공급자 변수 및 식에 설명 합니다.  
  
 [형식 시각화 도우미 및 사용자 지정 뷰어](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)  
 에 형식 시각화 도우미 및 사용자 지정 뷰어를 되며 어떤 식 계산기 수행 하는 역할에서 모두 지원 합니다.  
  
## <a name="related-sections"></a>관련 단원  
 [디버거 개념](../../extensibility/debugger/debugger-concepts.md)  
 기본 디버깅 아키텍처 개념을 설명합니다.  
  
 [디버거 컨텍스트](../../extensibility/debugger/debugger-contexts.md)  
 DE 동시에 코드, 설명서 및 식 평가 컨텍스트 내에서 작동 하는 방법을 설명 합니다. 세 개의 컨텍스트, 위치, 위치 또는 평가를 관련 각각에 대해 설명합니다.  
  
 [작업 디버그](../../extensibility/debugger/debugging-tasks.md)  
 프로그램을 시작 하 고 식을 계산 하는 등의 다양 한 디버깅 작업에 대 한 링크를 포함 합니다.  
  
## <a name="see-also"></a>참고자료  
 [시작](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)