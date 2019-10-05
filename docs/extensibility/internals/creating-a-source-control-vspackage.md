---
title: 소스 제어 VSPackage 만들기 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], creating source control packages
- source control packages
ms.assetid: cca0a9ed-48ff-409f-8036-ed8db0f7533e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 259273eee51c74eb7cb5ca4534db9bc575fd1758
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66345484"
---
# <a name="create-a-source-control-vspackage"></a>소스 제어 VSPackage 만들기
이 설명서와 통합 소스 제어 패키지의 아키텍처 개요에 대 한 링크가 포함 되어 있습니다. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], 인터페이스를 구현 하 고 사용할 수 있도록 서비스에서 정의한 API 및 간단한 소스를 보여 주는 샘플 패키지 구현을 제어 합니다.

 소스 제어 VSPackage 통해 통합 소스 제어에 대 한 긴밀 한 통합 경로 만들 수 있습니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]합니다. 패키지를 기본 원본 제어에서 호스트 되는 UI를 무시할 수 있도록 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]프로젝트 시스템에서 원본 제어 요청에 응답 하 고 상호 작용 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 와 같은 구성 요소 **솔루션 탐색기**합니다. [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 극대화할 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 통합할 수 있는 VSPackage를 만들려면 메커니즘을 사용 하 여 파트너 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 서비스 모델을 사용 하 여 합니다.

## <a name="in-this-section"></a>단원 내용
- [시작](../../extensibility/internals/getting-started-with-source-control-vspackages.md)

 고급 대안을 소스 제어에서 소스 제어 기능을 구현 하는 것에 대 한 플러그 인 소스 제어 패키지 설명 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]합니다.

- [아키텍처](../../extensibility/internals/source-control-vspackage-architecture.md)

 다이어그램을 표시 하 고 원본 제어 패키지의 구성 요소를 설명 합니다.

- [기능](../../extensibility/internals/source-control-vspackage-features.md)

 소스 제어 패키지의 다양 한 기능을 설명 합니다.

- [디자인 요소](../../extensibility/internals/source-control-vspackage-design-elements.md)

 긴밀 한 통합에 대 한 소스 제어 패키지를 구현 해야 하는 VSPackage의 구조를 설명 합니다.

## <a name="related-sections"></a>관련 단원
- [소스 제어 플러그 인 만들기](../../extensibility/internals/creating-a-source-control-plug-in.md)

 소스 제어 기능을 제공 하는 소스 제어 플러그 인을 만드는 방법에 설명 합니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 소스 제어 사용자 인터페이스 (UI).

- [소스 제어](../../extensibility/internals/source-control.md)

 소스 제어의 통합된 기능으로 구현 하기 위한 옵션에 설명 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]합니다.
