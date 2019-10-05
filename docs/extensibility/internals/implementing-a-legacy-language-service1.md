---
title: 레거시 언어 Service1 구현 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, managed
ms.assetid: df638f24-166d-4b80-be82-c9c39ca7a556
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 626838b0e82846f66b817465fca2df353af42dd5
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66315640"
---
# <a name="implementing-a-legacy-language-service"></a>레거시 언어 서비스 구현
구문 강조, 중괄호 일치 및 IntelliSense 완성 등 다양 한 기능을 지 원하는 레거시 언어 서비스를 구현 하려면 클래스 (MPF) 관리 되는 패키지 프레임 워크에서를 사용할 수 있습니다.

 레거시 언어 서비스는 VSPackage의 일부로 구현 됩니다 있지만 MEF 확장을 사용 하는 언어 서비스 기능을 구현 하는 최신 방법입니다. 언어 서비스를 구현 하는 새로운 방법에 대 한 자세한 내용을 참조 하세요 [편집기 및 언어 서비스 확장](../../extensibility/editor-and-language-service-extensions.md)합니다.

> [!NOTE]
> 편집기를 사용 하 여 새 API 최대한 빨리 시작 하는 것이 좋습니다. 언어 서비스의 성능이 향상 되 고 새 편집기 기능을 활용할 수 있습니다.

## <a name="in-this-section"></a>섹션 내용
- [레거시 언어 서비스 개요](../../extensibility/internals/legacy-language-service-overview.md)

 MPF에서 지원 되는 언어 서비스 기능을 간략하게 설명 합니다.

- [레거시 언어 서비스 구현](../../extensibility/internals/implementing-a-legacy-language-service2.md)

 MPF를 사용 하 여 언어 서비스를 구현 하는 데 필요한 사항에 대해 설명 합니다.

- [레거시 언어 서비스 등록](../../extensibility/internals/registering-a-legacy-language-service1.md)

 사용 하 여 MPF 기반 언어 서비스를 등록 하는 데 필요한 단계를 설명 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]합니다.

- [레거시 언어 서비스 파서 및 검사기](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)

 MPF를 사용 하 여 언어 서비스의 모든 기능을 구현 하는 데 필요한 두 개의 파서를 설명 합니다.

- [연습: 레거시 언어 서비스 만들기](../../extensibility/internals/walkthrough-creating-a-legacy-language-service.md)

 Vspackage에서는 MPF 언어 서비스를 구현 하는 데 필요한 기본 단계를 제공 합니다.

- [연습: 설치된 코드 조각 목록 가져오기(레거시 구현)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)

 설치 된 코드 조각의 목록을 검색 하는 기술을 보여 줍니다.

- [레거시 언어 서비스 기능](../../extensibility/internals/legacy-language-service-features1.md)

 MPF를 사용 하 여 언어 서비스의 모든 기능을 구현 하려면 수행 해야 하는 정보 항목에 대 한 링크를 제공 합니다.