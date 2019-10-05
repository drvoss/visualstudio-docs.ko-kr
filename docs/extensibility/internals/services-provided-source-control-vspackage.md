---
title: 서비스 제공 (소스 제어 VSPackage) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, source control packages
- source control packages, services
ms.assetid: 9db07d70-87d2-4401-bc88-e3a49d81e9a2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 72c95b0cf5b89588f5436663046829dc589bc9f2
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322664"
---
# <a name="services-provided-source-control-vspackage"></a>제공된 서비스(소스 제어 VSPackage)
서비스는 있는 기능 및 Visual Studio 통합된 개발 환경 (IDE)와 해당 설치 Vspackage Vspackage 간에 공유 되는 기본 메커니즘입니다. 서비스 및 Visual Studio IDE에서 중요도의 자세한 설명을 참조 하세요[사용 및 제공 서비스](../../extensibility/using-and-providing-services.md)합니다.

## <a name="the-source-control-service"></a>소스 제어 서비스
 Visual Studio 서비스, IDE 수준 서비스 및 패키지 수준 서비스의 두 계층을 제공합니다. Visual Studio IDE는 고유 하 게 IDE 수준 서비스를 제공합니다. 소스 제어 패키지 이러한 서비스 중 일부를 사용 합니다. 소스 제어 VSPackage로 패키지 자체의 개인 원본 제어 서비스를 제공 하 여 해당 원본 제어 기능을 공유 합니다. 소스 제어 패키지는 Visual Studio IDE에서 사용할 수 있는 계약의 형식에 의해 구현 된 원본 제어와 관련 된 인터페이스 집합을 캡슐화 합니다.

## <a name="see-also"></a>참고 항목
- [디자인 요소](../../extensibility/internals/source-control-vspackage-design-elements.md)