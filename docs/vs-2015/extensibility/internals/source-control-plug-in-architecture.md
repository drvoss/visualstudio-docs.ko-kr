---
title: 원본 제어 플러그 인 아키텍처 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, architecture
ms.assetid: 35351d4c-9414-409b-98fc-f2023e2426b7
caps.latest.revision: 25
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 370f88ce4d8fc372ce31e1e85e88d5379f4e1ba5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68183397"
---
# <a name="source-control-plug-in-architecture"></a>소스 제어 플러그 인 아키텍처
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

소스 제어 지원에 추가할 수 있습니다는 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 구현 하 고 소스 제어 플러그 인을 연결 하 여 통합된 개발 환경 (IDE)입니다. IDE는 잘 정의 된 원본 제어 플러그 인 API를 통해 플러그 인 소스 제어에 연결합니다. IDE 도구 모음 및 메뉴 명령으로 구성 된 사용자 인터페이스 (UI)를 제공 하 여 원본 제어 시스템의 버전 제어 기능을 노출 합니다. 소스 제어 플러그 인 소스 제어 기능을 구현합니다.  
  
## <a name="source-control-plug-in-resources"></a>소스 제어 플러그 인 리소스  
 원본 제어 플러그 인 만들기 및 버전 관리 응용 프로그램을 연결 하는 데 리소스를 제공 합니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE. 원본 제어 플러그 인에 통합 될 수 있도록 소스 제어 플러그 인에서 구현 해야 하는 API 사양을 포함 된 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE. 코드 샘플도 포함 (작성 된 C++)를 기본 원본 제어 플러그 인 설명 함수의 구현 형태가 필수 원본 제어 플러그 인 API를 사용 하 여 준수를 구현 하는 합니다.  
  
 원본 제어 플러그 인 API 사양을 사용 하면 필요한 원본 제어 플러그 인 API에 따라 구현 된 함수 집합을 사용 하 여 소스 제어 DLL을 만드는 경우 선택한 모든 소스 제어 시스템을 활용할 수 있습니다.  
  
## <a name="components"></a>구성 요소  
 다이어그램에서 소스 제어 어댑터 패키지는 소스 제어 플러그 인에서 지원 되는 함수 호출에 소스 제어 작업에 대 한 사용자의 요청을 변환 하는 IDE의 구성 요소입니다. 그러려면, IDE 및 소스 제어 플러그 인 IDE와 플러그 인 간에 앞뒤로 정보를 전달 하는 효과적인 대화 상자를 있어야 합니다. 수행이 대화 상자에 대 한 동일한 언어를 말해야 둘 다. 이 설명서에 설명 된 원본 제어 플러그 인 API는이 교환에 대 한 일반적인 어휘입니다.  
  
 ![원본 코드 제어 아키텍처 다이어그램](../../extensibility/internals/media/vs-sccsdk-plug-in-arch.gif "vs_sccsdk_plug_in_arch")  
간의 상호 작용 VS 및 소스 제어 플러그 인을 보여 주는 아키텍처 다이어그램  
  
 아키텍처 다이어그램에 표시 된 대로 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] shell, VS shell 다이어그램에서으로 레이블이 지정 된 사용자의 작업 프로젝트 및 편집기 및 솔루션 탐색기와 같은 관련된 구성 요소를 호스팅합니다. 소스 제어 어댑터 패키지 IDE 및 소스 제어 플러그 인 간의 상호 작용을 처리합니다. 소스 제어 어댑터 패키지는 고유한 소스 제어 UI를 제공합니다. 최상위 UI를 시작 하 고 소스 제어 작업의 범위를 정의 하기 위해 상호 작용 하는 것입니다.  
  
 소스 제어 플러그 인은 그림에 나와 있는 것 처럼 두 부분으로 구성 되는 자체 UI를 가질 수 있습니다. "공급 업체 UI" 이라는 상자를 원본 제어 플러그 인 작성자를 제공 하는 사용자 지정 사용자 인터페이스 요소를 나타냅니다. 이러한 사용자는 고급 소스 제어 작업을 호출 하는 경우 소스 제어 플러그 인에서 직접 표시 됩니다. 소스 제어 플러그 인 UI 기능 IDE를 통해 직접 호출 되는 집합이 "도우미 UI" 레이블이 지정 된 상자가 표시 됩니다. 소스 제어 플러그 인 IDE에서 제공 하는 특수 콜백 함수를 통해 IDE에 UI 관련 메시지를 전달 합니다. 도우미 UI에 IDE 사용 하 여 보다 원활한 통합을 용이 하 게 (자주 이용을 **고급** 단추)는 더 통합 된 최종 사용자 환경을 제공 하는 합니다.  
  
 소스 제어 플러그 인을 변경할 수 없습니다는 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 셸 및 결과적으로 소스 제어 어댑터 패키지 또는 원본 IDE에서 제공 하는 UI를 제어 합니다. 최종 사용자에 대 한 통합된 된 환경을에 영향을 주는 다양 한 원본 제어 플러그 인 API 함수의 구현을 통해 제공 하는 유연성을 최대한으로 사용을 해야 합니다. 원본 제어 플러그 인 API 설명서의 참조 섹션에는 몇 가지 고급 소스 제어 플러그 인 기능에 대 한 정보가 포함 됩니다. 이러한 기능을 악용 하기 소스 제어 플러그 인 선언 해야 ide 고급 기능 초기화 하는 동안 하며, 각 기능에 대 한 특정 고급 함수를 구현 해야 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [원본 제어 플러그 인](../../extensibility/source-control-plug-ins.md)   
 [용어집](../../extensibility/source-control-plug-in-glossary.md)   
 [소스 제어 플러그 인 만들기](../../extensibility/internals/creating-a-source-control-plug-in.md)
