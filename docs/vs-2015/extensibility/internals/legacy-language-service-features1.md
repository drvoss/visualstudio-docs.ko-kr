---
title: 레거시 언어 서비스 기능 1 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework]
ms.assetid: a646e4f0-767d-4cd1-8e1a-9a2aa210a1b7
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9506c6756c785741c40f86ae5839101bf0079854
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68196133"
---
# <a name="legacy-language-service-features"></a>레거시 언어 서비스 기능
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

하나 이상의 관리 되는 패키지 프레임 워크 (MPF) 언어 서비스를 지원할 수 있습니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 구문 강조 표시, IntelliSense 및 중단점 유효성 검사와 같은 기능을 합니다. 각 기능 독립적으로 구현할 수 있지만 파서와 스캐너만 해야 하는 구문 강조 표시를 제외 하 고 스캐너 모두 필요 합니다.  
  
## <a name="in-this-section"></a>섹션 내용  
 [레거시 언어 서비스의 중괄호 일치](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)  
 라고도 중괄호 일치, 일치 하는 언어 쌍을 지원 하기 위해 필요한 것에 대해 설명 합니다.  
  
 [레거시 언어 서비스의 코드 주석 처리](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)  
 주석 달기 및 선택한 코드의 주석 처리 제거를 지원 하기 위해 필요한 것에 대해 설명 합니다.  
  
 [레거시 언어 서비스의 사용자 지정 문서 속성](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)  
 소스 파일에 포함 된 문서 속성을 지원 하기 위해 필요한 것에 대해 설명 합니다.  
  
 [레거시 언어 서비스의 개요 표시](../../extensibility/internals/outlining-in-a-legacy-language-service.md)  
 숨겨진된 영역의 구현을 통해 개요를 지원 하기 위해 필요한 것을 설명 합니다.  
  
 [레거시 언어 서비스의 코드 서식 다시 지정](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)  
 다시 포맷 코드 지 원하는 데 필요한 사항에 대해 설명 합니다.  
  
 [레거시 언어 서비스의 코드 조각 지원](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)  
 삽입 되 고 편집할 수 있는 코드 세그먼트인 코드 조각을 지원 하기 위해 필요한 것에 대해 설명 합니다.  
  
 [레거시 언어 서비스의 매개 변수 정보](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)  
 메서드는 입력 한 대로 메서드 시그니처를 표시 하는 것에 대 한 IntelliSense 매개 변수 정보 작업을 지원 하는 데 필요한 사항에 대해 설명 합니다.  
  
 [레거시 언어 서비스의 빠른 정보](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)  
 식별자에 대 한 정보를 표시 하는 것에 대 한 IntelliSense 요약 정보 작업을 지원 하는 데 필요한 사항에 대해 설명 합니다.  
  
 [레거시 언어 서비스의 멤버 완성](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)  
 목록에서 네임 스페이스의 멤버를 선택 하기 위한 IntelliSense 멤버 완성 작업을 지원 하는 데 필요한 내용을 설명 합니다.  
  
 [레거시 언어 서비스의 단어 완성](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)  
 부분적으로 입력된 되는 단어를 완료 하기 위한 IntelliSense 단어 자동 완성 작업을 지원 하는 데 필요한 사항에 대해 설명 합니다.  
  
 [레거시 언어 서비스의 자동 창 지원](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)  
 언어 서비스를 지원 하기 위해 수행할 수 있는 작업에 대해 설명 합니다 **자동** 디버깅 하는 동안 창입니다.  
  
 [레거시 언어 서비스의 탐색 모음 지원](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)  
 사용 하는 방법에 설명 합니다 **탐색 모음** 모든 형식 또는 멤버 보기에 표시 된 파일에 빠른 탐색을 제공 하는 편집기 뷰의 맨...  
  
 [레거시 언어 서비스의 구문 색 지정](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)  
 소스 코드 구문 강조 표시를 지원 하기 위해 필요한 것에 대해 설명 합니다.  
  
 [레거시 언어 서비스의 중단점 유효성 검사](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)  
 언어 서비스는 디버거 외부에서 유효성 검사 중단점을 지원 하기 위해 수행할 수 있는 작업에 대해 설명 합니다.  
  
## <a name="related-sections"></a>관련 단원  
 [레거시 언어 서비스 파서 및 검사기](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)  
 파서 및 관리 패키지 프레임 워크를 사용 하는 언어 서비스의 모든 기능을 구현 하는 데 필요한 스캐너를 설명 합니다.  
  
 [레거시 언어 서비스 구현](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
 MPF를 사용 하 여 언어 서비스를 구현 하는 데 필요한 사항에 대해 설명 합니다.  
  
 [레거시 언어 서비스 등록](../../extensibility/internals/registering-a-legacy-language-service1.md)  
 사용 하 여 MPF 기반 언어 서비스를 등록 하는 데 필요한 단계를 설명 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]합니다.  
  
 [IntelliSense 사용](../../ide/using-intellisense.md)  
 IntelliSense에서 방법을 언어 참조에 쉽게 액세스할 수에 대해 설명 합니다.  
  
 [레거시 언어 서비스 구현](../../extensibility/internals/implementing-a-legacy-language-service1.md)  
 관리 되는 코드에서 모든 기능을 갖춘 언어 서비스를 구현 하는 관리 패키지 프레임 워크 (MPF)를 사용 하는 방법에 대 한 정보를 제공 합니다.
