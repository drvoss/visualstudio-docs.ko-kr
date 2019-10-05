---
title: 도메인별 언어 솔루션 템플릿 선택
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, solution templates
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6b3e6d9812f06df6d4af65f624579ec5f6550515
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62424065"
---
# <a name="choosing-a-domain-specific-language-solution-template"></a>도메인별 언어 솔루션 템플릿 선택
도메인별 언어 솔루션을 만들려면 도메인 특정 언어 디자이너 마법사에서 사용할 수 있는 솔루션 템플릿 중 하나를 선택 합니다. 서식 파일을 만들려고 할 수 있는 언어와 가장 유사한를 선택 하 여 시작 솔루션을 확인 해야 할 수정 작업을 최소화할 수 있습니다.

 다음 솔루션 템플릿은 도메인별 언어 디자이너 마법사에서 사용할 수 있습니다.

|템플릿|기능|설명|
|-|-|-|
|클래스 다이어그램|-구획 도형<br />클래스 상속<br />관계 상속<br />-모양 상속<br />관계 속성|이 솔루션 템플릿에 사용 하 여 엔터티 및 관계 속성이 있는 도메인 특정 언어에 포함 된 경우. 이 템플릿은 UML 클래스 다이어그램을 유사한 도메인 특정 언어를 만듭니다. 주 엔터티는 클래스 및 인터페이스를 연결, 일반화 및 구현 관계와 함께 합니다. 클래스 또는 인터페이스 특성의 목록을 포함 하는 상자로 나타납니다.|
|구성 요소 다이어그램|-포트|도메인 특정 언어 구성 요소, 즉, 소프트웨어 시스템의 부분을 포함 하는 경우이 솔루션 템플릿에 사용 합니다. 이 템플릿은 UML 구성 요소 다이어그램을 유사한 도메인 특정 언어를 만듭니다. 주 엔터티는 구성 요소 및 구성 요소의 외부에 있는 작은 모양으로 표시 되는 포트입니다.|
|작업 흐름 다이어그램|-이미지 및 기 하 도형 모양<br />-   *스윔 레인*|도메인 특정 언어에는 워크플로, 상태 또는 시퀀스에 포함 된 경우이 솔루션 템플릿에 사용 합니다. 이 템플릿은 UML 동작 다이어그램을 유사한 도메인 특정 언어를 만듭니다. 주 엔터티와 활동 이며 기본 관계 활동 간에 전환 합니다. 템플릿을 시작 상태, 마지막 상태 및 동기화 막대와 같은 다른 여러 요소를 포함합니다.|
|최소 언어|-하나 클래스 및 도형<br />-하나 관계 및 연결선|도메인 특정 언어의 다른 템플릿을 비슷하지 않을 경우이 솔루션 템플릿에 사용 합니다. 이 템플릿은 두 개의 클래스 및 관계의 경우에 표시 되는 포함 하는 도메인 특정 언어를 만듭니다.는 **도구 상자** 으로 **상자** 하 고 **줄**합니다. 클래스 및 관계는 각 문자열 속성의 예로 경우|
|최소 WinForm Designer|-작은 모델입니다.<br />모델을 표시 하는-Windows 폼입니다.|DSL 그래픽 디자이너를 사용 하지 않고 Windows 폼에 바인딩된 응용 프로그램을 빌드 하려는 경우이 템플릿을 사용 합니다.<br /><br /> 언어에 대 한 사용자 인터페이스 역할을 하는 폼이 Dsl\UI 폴더에 있습니다.<br /><br /> 폼 디자이너를 열기 전에 프로젝트를 빌드해야 합니다.<br /><br /> 자세한 내용은 [Windows Forms-Based 도메인별 언어 만들기](../modeling/creating-a-windows-forms-based-domain-specific-language.md)합니다.|
|최소 WPF 디자이너|-작은 모델<br />모델을 표시 하는 Windows Presentation Foundation 사용자 인터페이스-|DSL 그래픽 디자이너 보다는 WPF 사용자 인터페이스에 바인딩된 응용 프로그램을 빌드 하려는 경우이 템플릿을 사용 합니다.<br /><br /> 사용자 인터페이스 디자이너 Dsl\UI 폴더에는 합니다.<br /><br /> UI 디자이너를 열기 전에 프로젝트를 빌드해야 합니다.<br /><br /> 자세한 내용은 [WPF-Based 도메인별 언어 만들기](../modeling/creating-a-wpf-based-domain-specific-language.md)합니다.|
|DSL 라이브러리|-최소 라이브러리|다른 DSL 정의를 가져올 수 있는 부분 DSL 정의 빌드 하려는 경우이 템플릿을 사용 합니다.|

## <a name="see-also"></a>참고 항목

- [도메인별 언어 도구 개요](../modeling/overview-of-domain-specific-language-tools.md)
