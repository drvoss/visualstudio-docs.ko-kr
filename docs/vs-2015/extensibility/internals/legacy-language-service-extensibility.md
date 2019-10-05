---
title: 레거시 언어 서비스 확장성 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services
- Visual Studio, language services
ms.assetid: 2700cd4d-5f68-43fc-b62f-dc80c3f3aa85
caps.latest.revision: 43
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9346311aac4bc5833005423e90c2eb92faddcb84
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68194990"
---
# <a name="legacy-language-service-extensibility"></a>레거시 언어 서비스 확장성
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

언어 서비스를 IDE에서 소스 코드 편집 언어별 지원을 제공 합니다.  
  
 레거시 언어 서비스는 VSPackage의 일부로 구현 됩니다 있지만 MEF 확장을 사용 하는 언어 서비스 기능을 구현 하는 최신 방법입니다. 언어 서비스를 구현 하는 새로운 방법에 대 한 자세한 내용을 참조 하세요 [편집기 및 언어 서비스 확장](../../extensibility/editor-and-language-service-extensions.md)합니다.  
  
 이 섹션에서는 구조와 레거시 언어 서비스의 구현을 설명 합니다.  
  
## <a name="in-this-section"></a>섹션 내용  
 [레거시 언어 서비스 마이그레이션](../../extensibility/internals/migrating-a-legacy-language-service.md)  
 최신 Visual Studio 2008에서 언어 서비스를 업데이트 하는 방법을 설명 합니다.  
  
 [레거시 언어 서비스 필수 항목](../../extensibility/internals/legacy-language-service-essentials.md)  
 Visual Studio 프로그래밍 언어를 통합 하기 위해 언어 서비스를 개발 하는 방법에 대 한 중요 한 정보를 제공 합니다.  
  
 [레거시 언어 서비스 개발](../../extensibility/internals/developing-a-legacy-language-service.md)  
 언어 서비스를 만들 수 있는 항목의 링크를 제공 합니다.  
  
 [레거시 언어 서비스의 구문 색 지정](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)  
 언어 서비스에서 구문 강조를 지 원하는 정보를 제공 합니다.  
  
 [레거시 언어 서비스 구현](../../extensibility/internals/implementing-a-legacy-language-service1.md)  
 관리 되는 코드에서 모든 기능을 갖춘 언어 서비스를 구현 하는 관리 패키지 프레임 워크 (MPF)를 사용 하는 방법에 대 한 정보를 제공 합니다.  
  
 [기호 검색 도구 지원](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 IDE에서 기호의 트리 뷰를 이동할 수 있는 라이브러리 및 도구에 설명 합니다.  
  
## <a name="related-sections"></a>관련 단원  
 [편집기 및 언어 서비스 확장](../../extensibility/editor-and-language-service-extensions.md)  
 Visual Studio 편집기에 간략하게 설명 합니다.  
  
 [디버깅에 대한 언어 서비스 지원](../../extensibility/internals/language-service-support-for-debugging.md)  
 Visual Studio 디버깅 sdk 만들기 및 프로그램을 디버그 하는 데 사용 되는 디버거 구성 요소를 사용자 지정 하는 데 필요한 정보를 포함 하는 방법에 대 한 정보 및 링크를 제공 합니다.
