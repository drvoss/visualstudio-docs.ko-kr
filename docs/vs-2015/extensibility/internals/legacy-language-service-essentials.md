---
title: 레거시 언어 서비스 필수 항목 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- languages, integrating into Visual Studio
- language services, integrating programming languages
- Visual Studio, integrating programming languages
- programming languages, integrating into Visual Studio
ms.assetid: c15e0ccb-e7c5-4dbb-affb-fe3d3244debe
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a3926ff84f3b2e6415df1ca7333409c05d839685
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436259"
---
# <a name="legacy-language-service-essentials"></a>레거시 언어 서비스 필수 항목
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio 프로그래밍 언어를 통합 하도록 언어 서비스를 제공 해야 합니다. 이 항목에서는 레거시 언어 서비스에서 제공 되는 기능을 설명 합니다.  
  
 레거시 언어 서비스는 VSPackage의 일부로 구현 됩니다 있지만 MEF 확장을 사용 하는 언어 서비스 기능을 구현 하는 최신 방법입니다. 언어 서비스를 구현 하는 새로운 방법에 대 한 자세한 내용을 참조 하세요 [편집기 및 언어 서비스 확장](../../extensibility/editor-and-language-service-extensions.md)합니다.  
  
> [!NOTE]
> 편집기를 사용 하 여 새 API 최대한 빨리 시작 하는 것이 좋습니다. 언어 서비스의 성능이 향상 되 고 새 편집기 기능을 활용할 수 있습니다.  
  
 레거시 언어 서비스는 다음과 같은 기능을 제공합니다.  
  
|기능|설명|  
|-------------|-----------------|  
|구문 색 지정|편집기 뷰를 서로 다른 색 및 언어의 다양 한 요소에 대 한 글꼴 스타일을 표시 하면 됩니다. 이 차별화를 읽고 파일을 편집할 쉽게 수 있습니다.<br /><br /> 일반적인 정보를 참조 하세요 [레거시 언어 서비스의 구문 색 지정](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)합니다.<br /><br /> MPF ()에서 관리 되는 패키지 프레임 워크에서이 기능에 대 한 정보를 참조 하세요 [레거시 언어 서비스의 구문 색 지정](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)합니다.|  
|문 완성 |문 또는 사용자 입력을 시작 되었음을 나타내는 키워드를 완료 합니다. 문 완성에는 사용자가 입력 하 고 더 적은 오류 가능성을 사용 하 여 어려운 문을 더 쉽게 입력할 수 있습니다.<br /><br /> 일반적인 정보를 참조 하세요 [레거시 언어 서비스에서 문 완성](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)합니다.<br /><br /> MPF에서이 기능에 대 한 정보를 참조 하세요 [레거시 언어 서비스의 단어 완성](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)합니다.|  
|중괄호 일치|중괄호 등 쌍을 이루는 문자를 강조 표시 합니다. 때 사용자가 닫는 문자 같은 "}", 중괄호 일치 강조 표시와 같은 문자를 열고 해당 "{0}". 문자를 포함 하는 여러 수준의 경우이 기능은 사용자는 바깥쪽 문자 쌍이 올바른지 확인 합니다.<br /><br /> MPF에서이 기능에 대 한 정보를 참조 하세요 [레거시 언어 서비스의 중괄호 일치](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)합니다.|  
|매개 변수 정보 도구 설명|사용자가 현재 입력 하는 오버 로드 된 메서드에 대 한 가능한 서명의 목록을 표시 합니다.<br /><br /> 일반적인 정보를 참조 하세요 [레거시 언어 서비스의 매개 변수 정보](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)합니다.<br /><br /> MPF에서이 기능에 대 한 정보를 참조 하세요 [레거시 언어 서비스의 매개 변수 정보](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)합니다.|  
|오류 표식|빨강 물결선 밑줄, 라고도 물결 구문이 잘못 된 텍스트 아래에 표시 됩니다. 일반적으로 오류 표식 사용자 맞춤법 오류가 있는 키워드 "," 닫히지 않은 괄호가 "," 잘못 된 문자를 "및"와 유사한 오류를 인식 하도록 하는 데 사용 됩니다.<br /><br /> MPF 클래스, 오류 표식에서 자동으로 처리 됩니다 합니다 <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> 메서드는 <xref:Microsoft.VisualStudio.Package.AuthoringSink> 클래스입니다.|  
  
 소스 코드를 구문 분석할 수 있도록 언어 서비스를 해야 하는 기능이 많습니다. 자주 다시 사용할 수 있습니다는 토큰화 및 코드 컴파일러 또는 인터프리터를 구문 분석 합니다.  
  
 다음 기능은 프로그래밍 언어에 대 한 지원 관련 되어 있지만 언어 서비스의 일부가 아닌:  
  
|기능|설명|  
|-------------|-----------------|  
|식 계산기|지원 합니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 에 표시할 중단점 유효성을 검사 하 고 식의 목록을 제공 하 여 디버거를 **자동** 디버그 창입니다.<br /><br /> 자세한 내용은 [디버깅에 대 한 언어 서비스 지원](../../extensibility/internals/language-service-support-for-debugging.md)합니다.|  
|기호 검색 도구|지원 **개체 브라우저**를 **클래스 뷰**합니다 **호출 브라우저**, 및 **기호 찾기 결과**합니다.|
