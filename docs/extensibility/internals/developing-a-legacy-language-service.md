---
title: 레거시 언어 서비스 개발 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.vsip.LangServWiz.langtoks
- vs.vsip.LangServWiz.welcome
- vs.vsip.LangServWiz.langSpec
- vs.vsip.LangServWiz.langInfo
- vs.vsip.LangServWiz.langServOpts
helpviewer_keywords:
- language services, developing
ms.assetid: 6151ba88-c1c3-41de-a1cc-668f494d48d1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6aa21b2f2e8b0321e829fd27fde1d833a63e7ecb
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351569"
---
# <a name="develop-a-legacy-language-service"></a>레거시 언어 서비스 개발
이 섹션 항목의 링크를 도움이 되는 레거시 언어 서비스를 만듭니다.

 레거시 언어 서비스는 VSPackage의 일부로 구현 됩니다 있지만 MEF 확장을 사용 하는 언어 서비스 기능을 구현 하는 최신 방법입니다. 언어 서비스를 구현 하는 새로운 방법에 대 한 자세한 내용을 참조 하세요 [편집기 및 언어 서비스 확장](../../extensibility/editor-and-language-service-extensions.md)합니다.

> [!NOTE]
> 편집기를 사용 하 여 새 API 최대한 빨리 시작 하는 것이 좋습니다. 언어 서비스의 성능이 향상 되 고 새 편집기 기능을 활용할 수 있습니다.

## <a name="in-this-section"></a>단원 내용
- [레거시 언어 서비스의 모델](../../extensibility/internals/model-of-a-legacy-language-service.md)

 에 대 한 최소 언어 서비스의 모델을 제공 합니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 핵심 편집기입니다. 사용자 고유의 언어 서비스 만들기에 대 한 지침으로이 모델을 사용할 수 있습니다.

- [레거시 언어 서비스 인터페이스](../../extensibility/internals/legacy-language-service-interfaces.md)

 구문 강조 표시, 메서드 데이터 및 기타 기능을 제공 하는 데 사용할 수 있는 추가 개체의 목록을 제공 하 고 언어 서비스를 구현 하는 데 필요한 개체를 설명 합니다.

- [레거시 언어 서비스 명령 가로채기](../../extensibility/internals/intercepting-legacy-language-service-commands.md)

 명령 필터 절편 명령 텍스트 보기 처리할 수 있는 언어 서비스에 삽입 하는 방법에 설명 합니다.

- [레거시 언어 서비스 등록](../../extensibility/internals/registering-a-legacy-language-service2.md)

 사용 하 여 언어 서비스를 등록 하는 방법에 대 한 정보를 제공 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]합니다.

- [디버깅에 대 한 언어 서비스 지원](../../extensibility/internals/language-service-support-for-debugging.md)

 언어 서비스 디버거 지원 기능을 제공할 수 있습니다 하는 방법을 설명 합니다.

- [검사 목록: 레거시 언어 서비스 만들기](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)

 만들기 및 핵심 편집기에 대 한 언어 서비스를 통합 하기 위한 단계별 지침을 제공 합니다.

## <a name="related-sections"></a>관련 단원
- [레거시 언어 서비스의 구문 색 지정](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

 언어 서비스에서 구문 강조를 구현 하는 방법에 설명 합니다.

- [레거시 언어 서비스의 문 완성](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)

 문 완성는 언어 서비스를 사용 하면 언어 키워드 또는 입력 시작 하는 요소를 완료 하는 프로세스를 설명 합니다.

- [레거시 언어 서비스의 매개 변수 정보](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)

 오버 로드 된 함수 및 메서드에 대 한 메서드 팁을 제공 하는 방법에 설명 합니다.

- [방법: 레거시 언어 서비스의 숨겨진된 텍스트 지원 제공](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)

 숨겨진된 텍스트 영역의 용도 설명 하 고 숨겨진된 텍스트 영역을 구현 하는 방법에 대 한 지침을 제공 합니다.

- [방법: 레거시 언어 서비스의 확장된 개요 표시 지원 제공](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)

 초과 지 원하는 언어에 대 한 개요 표시 지원 확장 하는 두 가지 옵션에 설명 합니다 *정의 부분만 보이기* 명령입니다.