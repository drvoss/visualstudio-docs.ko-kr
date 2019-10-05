---
title: 원본 제어 통합 개요 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], about source control
ms.assetid: 3a46e4eb-e677-49c3-8647-d927d035a19a
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4e2761958cd60721ccf05a14ec54d3e365572ea1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68148356"
---
# <a name="source-control-integration-overview"></a>소스 제어 통합 개요
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

이 섹션에서는 Visual Studio 소스 제어;에 통합 하는 두 가지 방법 비교 소스 제어 플러그 인 및 원본 제어 솔루션을 제공 하 고 새 소스 제어 기능을 강조 표시 하는 VSPackage는 합니다. Visual Studio 자동 솔루션 기반 전환 뿐 아니라 소스 제어 Vspackage와 원본 제어 플러그 인 간에 수동 전환할 수 있습니다.  
  
## <a name="source-control-integration"></a>소스 제어 통합  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 두 가지 유형의 원본 제어 통합 옵션을 지원합니다. 모든 버전의 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]를 통합할 수도 있습니다 API에 따라 소스 제어 플러그 인 (이전에 라고도 MSSCCI API), 소스 제어 사용자 인터페이스 (Visual Studio를 사용 하는 동안 기본 원본 제어 기능을 제공 하는 플러그 인 UI)입니다. 소스 제어 VSPackage는 반면에 심층 통합을 새로운 제공 [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] 경로 높은 수준의 숙련도 및 원본 제어 모델이 자율성을 요구 하는 소스 제어 통합에 적합 합니다.  
  
 ![소스 제어 개요](../../extensibility/internals/media/sourcectnrloverview.gif "SourceCtnrlOverview")  
  
## <a name="source-control-plug-in"></a>소스 제어 플러그 인  
 모든 버전의 Visual Studio 통합 경로로 원본 제어 플러그 인 API 사양 버전 1.2 지원 합니다. 원본 제어 플러그 인 구현자에 설명 된 대로 원본 제어 통합 및 등록에 대 한 원본 제어 플러그 인 API 함수를 구현 하는 DLL를 씁니다 [는 원본 제어 플러그 인 만들기](../../extensibility/internals/creating-a-source-control-plug-in.md)합니다. 이 방법에서는 통합 개발 환경 (IDE) 사용 하는 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 체크 인, 체크 아웃, 도구/옵션 속성 페이지, 도구 모음 및 원본 제어 문자 모양을 같은 대화 상자에 대 한 UI입니다. 원본 제어 플러그 인 API 엄격한 준수 하면 Visual Studio에 사용자는 문제 없이 환경을 쉽게 통합 합니다. 즉, 소스 제어 플러그 인에 대부분의 함수 및 API에 자세히 설명 하는 콜백을 구현 해야 합니다.  
  
 원본 제어 플러그 인 API를 사용 하 여 플러그 인 소스 제어를 구현 하려면 다음이 단계를 수행 합니다.  
  
1. 에 지정 된 함수를 구현 하는 DLL을 만드는 [소스 제어 플러그 인](../../extensibility/source-control-plug-ins.md)합니다.  
  
2. 적절 한 레지스트리 항목을 만들어 DLL을 등록 (에 설명 된 [방법: 소스 제어 플러그 인 설치](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)).  
  
3. UI 및 표시 (Visual Studio 구성 요소 소스 제어 플러그 인을 통해 소스 제어 기능을 처리 하는) 소스 제어 어댑터 패키지에서 메시지가 표시 되 면 도우미 만들기  
  
   원본 제어 명령에 대 한 응답으로 Visual Studio IDE 기본 작업에 대 한 표준 UI가 표시 한 다음 정보를 전달 소스 제어 플러그 인 원본 제어 플러그 인 API에 정의 된 함수를 통해. 고급 옵션을 소스 제어 플러그 인에 호출할 수는 자체 UI를 표시 하도록 예를 들어, 소스 제어 프로젝트에 대 한 검색 합니다. 즉, 사용자 소스 제어를 사용 하 여 처리할 때 두 가지 다를 수 있는 스타일의 UI 사용 하 여 표시 될 수 있습니다: Visual Studio에서 제공 하는 UI 및 소스 제어 플러그 인을 제공 하는 UI입니다. 고급 소스 제어 작업을 사용 하 여 가장 눈에 띄는입니다.  
  
### <a name="drawbacks-to-implementing-a-source-control-plug-in"></a>소스 제어 플러그 인을 구현 하는 데 단점  
  
- 고급 기능에 대 한 사용자 나타날 인터페이스의 두 가지 다른 스타일을 혼동할 수 있습니다.  
  
- 소스 제어 플러그 인이 원본 제어 플러그 인 API 사용 권한에 포함 된 소스 제어 모델에만 적용 됩니다.  
  
- 원본 제어 플러그 인 API는 일부 소스 제어 시나리오에 대 한 너무 제한적일 수 있습니다.  
  
### <a name="advantages-to-implementing-a-source-control-plug-in"></a>소스 제어 플러그 인을 구현 하는 장점  
  
- Visual Studio 소스 제어 플러그 인 잠재적으로 복잡 한 UI를 구현 하지 않아도 되도록 모든 기본 소스 제어 작업에 대 한 모든 UI를 제공 합니다.  
  
- 엄격한 API 때문에 소스 제어 플러그 인 쉽게 상호 작용할 수 외부 소스 컨트롤 프로그램이 보다 광범위 한 기능을 제공 하기 Visual Studio 영향을 받지 않으며 훨씬 어떻게 너무 소스 제어 기능을 달성는 원본 제어 플러그 인 API에 따라 수행 됩니다.  
  
- 소스 제어 VSPackage 보다 플러그 인 소스 제어를 구현 하는 것이 쉽습니다.  
  
## <a name="source-control-vspackage"></a>소스 제어 VSPackage  
 [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] 원본 제어 기능의 완전 한 제어 및 Visual Studio가 제공한 원본 제어 사용자 인터페이스의 완전 한 대체를 사용 하 여 Visual Studio에 심층 통합이 가능 합니다. 소스 제어 VSPackage Visual Studio를 사용 하 여 등록 되 고 소스 제어 기능을 제공 합니다. Visual Studio를 사용 하 여 여러 소스 제어 Vspackage를 등록할 수 있습니다, 있지만 그 중 하나에 활성화할 수 한 번에 합니다. 소스 제어 VSPackage 활성 상태인 동안 Visual Studio에서 소스 제어 기능 및 모양을 완전히 제어할을에 있습니다. 기타 모든 소스 제어 시스템에 등록 될 수 있는 Vspackage 활성화 되며 UI를 전혀 표시 되지 않습니다.  
  
 소스 제어 VSPackage를 구현 하는 "양자 택일" 전략에 필요 합니다. 소스 제어 VSPackage의 작성자는 상당한 노력을 구현 하는 다양 한 원본 제어 인터페이스 및 새 UI 요소 (대화 상자, 메뉴 및 도구 모음) 전체 소스 제어 기능을 포괄 하도록 투자 해야 합니다. 참조 [소스 제어 VSPackage를 만드는](../../extensibility/internals/creating-a-source-control-vspackage.md) 대 한 자세한 내용은 합니다.  
  
### <a name="drawbacks-to-implementing-a-source-control-vspackage"></a>소스 제어 VSPackage를 구현 하는 데 단점  
  
- VSPackage는 다양 한 Visual Studio를 사용 하 여 성공적으로 통합 하는 복잡 한 인터페이스를 구현 해야 합니다.  
  
- VSPackage는 원본 제어;에 필요한 모든 UI를 제공 해야 합니다. Visual Studio는이 영역에서 도움을 제공 됩니다.  
  
- 소스 제어 VSPackage Visual Studio에 깊숙히 연결 되 고 원본 제어 프로그램의 외부 버전을 사용 하 여 기능을 쉽게 공유할 수 없습니다 있도록 독립 실행형 프로그램을 사용 하 여 수행할 수 없습니다.  
  
### <a name="advantages-to-implementing-a-source-control-vspackage"></a>소스 제어 VSPackage를 구현 하는 이점  
  
- VSPackage에 소스 제어 UI 통해 완전 한 제어 및 기능 때문에 소스 제어에 대 한 효율적인 인터페이스를 사용 하 여 사용자가 표시 됩니다.  
  
- VSPackage는 특정 원본 제어 모델이에 한정 되지 않습니다.  
  
## <a name="see-also"></a>참고 항목  
 [소스 제어](../../extensibility/internals/source-control.md)   
 [소스 제어 플러그 인 만들기](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [소스 제어 VSPackage 만들기](../../extensibility/internals/creating-a-source-control-vspackage.md)   
 [소스 제어의 새로운 기능](../../extensibility/internals/what-s-new-in-source-control.md)
