---
title: 소스 제어 VSPackage 아키텍처 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, architecture
ms.assetid: 453125fc-23dc-49b1-8476-94581f05e6c7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c05ae692a364d4e7a81a017d376dd820ade56b73
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322498"
---
# <a name="source-control-vspackage-architecture"></a>소스 제어 VSPackage 아키텍처
소스 제어 패키지를 사용 하는 VSPackage는 서비스는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE를 제공 합니다. 소스 제어 패키지를 원본 제어 서비스와 해당 기능을 제공합니다. 또한 소스 제어 패키지는 소스 제어 플러그 인에 소스 제어 통합을 보다 융통성이 뛰어납니다. 또한 대안 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]합니다.

 소스 제어 플러그 인 소스 제어 플러그 인 API를 구현 하는 엄격한 계약을 적용 합니다. 예를 들어, 플러그 인 바꿀 수 없습니다 기본 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 사용자 인터페이스 (UI). 또한 소스 제어 플러그 인 API는 고유한 소스 제어 모델을 구현 하는 플러그 인을 사용 하지 않습니다. 그러나 원본 제어 패키지를는 모두 이러한 제한 사항을 극복합니다. 소스 제어 패키지에 원본 제어 환경 완전히 제어는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 사용자입니다. 또한 소스 제어 패키지 자체의 소스 제어 모델 및 논리를 사용할 수 있고 모든 소스 제어와 관련 된 사용자 인터페이스를 정의할 수 있습니다.

## <a name="source-control-package-components"></a>소스 제어 패키지 구성 요소
 아키텍처 다이어그램에 표시 된 대로 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 소스 제어 스텁 이라는 구성 요소는 사용 하 여 소스 제어 패키지를 통합 하는 VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]합니다.

 원본 제어 스텁 다음 작업을 처리합니다.

- 소스 제어 패키지 등록에 필요한 일반적인 UI를 제공 합니다.

- 소스 제어 패키지를 로드합니다.

- 활성/비활성으로 소스 제어 패키지를 설정합니다.

  원본 제어 스텁 소스 제어 패키지에 대 한 활성 서비스를 찾아 해당 패키지에 IDE에서 들어오는 모든 서비스 호출을 라우팅합니다.

  소스 제어 어댑터 패키지는 특수 한 소스 제어 패키지를 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 제공 합니다. 이 패키지는 원본 제어 플러그 인 API를 기반으로 원본 제어 플러그 인을 지원 하기 위한 핵심 구성 요소입니다. 소스 제어 플러그 인 활성 플러그 인 경우 원본 제어 스텁 소스 컨트롤 어댑터 패키지에 해당 이벤트를 보냅니다. 차례로 소스 제어 어댑터 패키지는 원본 제어 플러그 인 API를 사용 하 여 소스 제어 플러그 인을 사용 하 여 통신 하 고도 기본값 모든 원본 제어 플러그 인에 대 한 공통 되는 UI를 제공 합니다.

  소스 제어 패키지에는 활성 패키지 되 면 다른 한편으로 원본 제어 스텁와 직접 통신 패키지를 사용 하 여는 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 소스 제어 패키지 인터페이스입니다. 소스 제어 패키지는 소스 제어 UI 자체 호스트 하는 일을 담당 합니다.

  ![소스 제어 아키텍처 그래픽](../../extensibility/internals/media/vsipsccarch.gif "VSIPSCCArch")

  소스 제어 패키지의 경우 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 소스 제어 또는 통합에 대 한 API를 제공 하지 않습니다. 에 설명 된 접근 방식을 사용 하 여이 대조해 보세요 [는 원본 제어 플러그 인 만들기](../../extensibility/internals/creating-a-source-control-plug-in.md) 고정 함수 집합과 콜백을 구현 하려면 소스 제어 플러그 인에 있습니다.

  모든 VSPackage를 같은 소스 제어 패키지는 COM 개체를 사용 하 여 만들 수 있는 `CoCreateInstance`합니다. VSPackage에서 사용할 수 있게 하는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 를 구현 하 여 IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>합니다. VSPackage는 사이트 포인터를 받는 인스턴스를 만들면 및 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> VSPackage 액세스의 사용 가능한 서비스 및 IDE에서 인터페이스를 제공 하는 인터페이스입니다.

  소스 제어 VSPackage 기반 패키지를 작성 원본 제어 플러그 인 API 기반 작성 보다 더 많은 고급 프로그래밍 전문 필요한 플러그 인입니다.

## <a name="see-also"></a>참고 항목
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>
- [시작](../../extensibility/internals/getting-started-with-source-control-vspackages.md)