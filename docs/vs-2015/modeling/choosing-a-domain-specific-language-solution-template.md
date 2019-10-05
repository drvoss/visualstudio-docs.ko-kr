---
title: 도메인별 언어 솔루션 템플릿 선택 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, solution templates
ms.assetid: 9c05955f-1548-4df6-b09b-4b348823c237
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 36b821219b02fa77171d89214d8cf4813ce92303
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63433397"
---
# <a name="choosing-a-domain-specific-language-solution-template"></a>도메인별 언어 솔루션 템플릿 선택
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

도메인별 언어 솔루션을 만들려면 도메인 특정 언어 디자이너 마법사에서 사용할 수 있는 솔루션 템플릿 중 하나를 선택 합니다. 서식 파일을 만들려고 할 수 있는 언어와 가장 유사한를 선택 하 여 시작 솔루션을 확인 해야 할 수정 작업을 최소화할 수 있습니다.  
  
 다음 솔루션 템플릿은 도메인별 언어 디자이너 마법사에서 사용할 수 있습니다.  
  
> [!NOTE]
> 템플릿의 용도 시작 DSL을 제공 하는 것입니다. 클래스 및 구성 요소 다이어그램의 명명 된 템플릿 전체 UML 다이어그램 않습니다. UML 모델을 만들려는 경우 UML을 모델링 도구는 단일 모델을 중심으로 통합 된 다이어그램 집합을 제공 하는 것이 좋습니다. ModelBus를 사용하면 이러한 다이어그램을 확장할 수 있으며 DSL과 통합할 수 있습니다. 자세한 내용은 [앱에 대 한 모델을 만들](../modeling/create-models-for-your-app.md)합니다.  
  
|템플릿|기능|설명|  
|--------------|--------------|-----------------|  
|클래스 다이어그램|-구획 도형<br />클래스 상속<br />관계 상속<br />-모양 상속<br />관계 속성|이 솔루션 템플릿에 사용 하 여 엔터티 및 관계 속성이 있는 도메인 특정 언어에 포함 된 경우. 이 템플릿은 UML 클래스 다이어그램을 유사한 도메인 특정 언어를 만듭니다. 주 엔터티는 클래스 및 인터페이스를 연결, 일반화 및 구현 관계와 함께 합니다. 클래스 또는 인터페이스 특성의 목록을 포함 하는 상자로 나타납니다.|  
|구성 요소 다이어그램|-포트|도메인 특정 언어 구성 요소, 즉, 소프트웨어 시스템의 부분을 포함 하는 경우이 솔루션 템플릿에 사용 합니다. 이 템플릿은 UML 구성 요소 다이어그램을 유사한 도메인 특정 언어를 만듭니다. 주 엔터티는 구성 요소 및 구성 요소의 외부에 있는 작은 모양으로 표시 되는 포트입니다.|  
|작업 흐름 다이어그램|-이미지 및 기 하 도형 모양<br />-   *스윔 레인*|도메인 특정 언어에는 워크플로, 상태 또는 시퀀스에 포함 된 경우이 솔루션 템플릿에 사용 합니다. 이 템플릿은 UML 동작 다이어그램을 유사한 도메인 특정 언어를 만듭니다. 주 엔터티와 활동 이며 기본 관계 활동 간에 전환 합니다. 템플릿을 시작 상태, 마지막 상태 및 동기화 막대와 같은 다른 여러 요소를 포함합니다.|  
|최소 언어|-하나 클래스 및 도형<br />-하나 관계 및 연결선|도메인 특정 언어의 다른 템플릿을 비슷하지 않을 경우이 솔루션 템플릿에 사용 합니다. 이 템플릿은 두 개의 클래스 및 관계의 경우에 표시 되는 포함 하는 도메인 특정 언어를 만듭니다.는 **도구 상자** 으로 **상자** 하 고 **줄**합니다. 클래스 및 관계는 각 문자열 속성의 예로 경우|  
|최소 WinForm Designer|-작은 모델입니다.<br />모델을 표시 하는-Windows 폼입니다.|DSL 그래픽 디자이너를 사용 하지 않고 Windows 폼에 바인딩된 응용 프로그램을 빌드 하려는 경우이 템플릿을 사용 합니다.<br /><br /> 언어에 대 한 사용자 인터페이스 역할을 하는 폼이 Dsl\UI 폴더에 있습니다.<br /><br /> 폼 디자이너를 열기 전에 프로젝트를 빌드해야 합니다.<br /><br /> 자세한 내용은 [Windows Forms-Based 도메인별 언어 만들기](../modeling/creating-a-windows-forms-based-domain-specific-language.md)합니다.|  
|최소 WPF 디자이너|-작은 모델<br />모델을 표시 하는 Windows Presentation Foundation 사용자 인터페이스-|DSL 그래픽 디자이너 보다는 WPF 사용자 인터페이스에 바인딩된 응용 프로그램을 빌드 하려는 경우이 템플릿을 사용 합니다.<br /><br /> 사용자 인터페이스 디자이너 Dsl\UI 폴더에는 합니다.<br /><br /> UI 디자이너를 열기 전에 프로젝트를 빌드해야 합니다.<br /><br /> 자세한 내용은 [WPF-Based 도메인별 언어 만들기](../modeling/creating-a-wpf-based-domain-specific-language.md)합니다.|  
|DSL 라이브러리|-최소 라이브러리|다른 DSL 정의를 가져올 수 있는 부분 DSL 정의 빌드 하려는 경우이 템플릿을 사용 합니다.|  
  
## <a name="see-also"></a>참고 항목  
 [도메인별 언어 도구 개요](../modeling/overview-of-domain-specific-language-tools.md)
