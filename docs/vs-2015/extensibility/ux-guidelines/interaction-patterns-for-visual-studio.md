---
title: 상호 작용 패턴
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: a3643792-b0df-481c-bc35-576f948e04cf
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f570d665ddbc97ccddf058e1bb424c62e23912cb
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67825276"
---
# <a name="interaction-patterns-for-visual-studio"></a>Visual Studio의 상호 작용 패턴
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="overview"></a>개요
 디자인 패턴에는 일반적으로 비슷한 제약 조건 집합을 사용 하 여 문제를 해결 하는 특정 상황에서 적용할 수 있는 디자인의 핵심 이며 기능 및 시스템 디자이너는 시작 점으로 특정 상황에 적용할 수 있는 이러한 디자인 패턴을 사용 합니다.

 Visual Studio의 새 기능을 빌드할 때 고려해 야 하는 일반적인 상호 작용 패턴을 라이브러리를 있습니다. 이 디자인 패턴에 대 한 두 가지 핵심 컨텍스트 가지가 있습니다. Visual Studio 클라이언트 (devenv) 및 Visual Studio Online입니다. 일부 디자인 문제에 대해서는 모든 상황에서 잘 작동 유비쿼터스 패턴입니다. 그러나 대부분의 경우에서 솔루션 다를 수 있습니다 하 고 클라이언트 응용 프로그램에서 호스트 되는 브라우저 내에서 제공 되는 UI에 대 한 합니다.

### <a name="visual-studio-client-pattern-types"></a>Visual Studio 클라이언트 패턴 유형

|패턴 유형|Description|예|
|------------------|-----------------|--------------|
|**응용 프로그램 수준 패턴**|개략적인 패턴 또는 확인 하 고, 응용 프로그램 컨텍스트를 표시 하 고, 복합 및 컨트롤 패턴 내에 포함 된 응용 프로그램에 공통적으로 적용|-도구 창<br />-문서 창|
|**복합 패턴**|응용 프로그램 패턴에 걸쳐 존재할 수 있는 일반적인 패턴 또는 고유한 구성에서 여러 컨트롤 이루어져 인식할 수 있는 패턴|뷰 전환<br />목록 작성기<br />-데이터를 표시합니다.<br />-알림<br />유효성 검사<br />모델 선택|
|**컨트롤 패턴**|동작 해야 하는 방법을 하위 수준 컨트롤에 대 한 세부 정보|-트리 뷰<br />-표 형태 컨트롤에서 편집합니다.|

## <a name="application-patterns"></a>응용 프로그램 패턴
 높은 수준에서 Visual Studio 인터페이스에는 여러 windows, 대화 상자, 명령 및 도구 모음을 하나의 IDE 내에서 구성 됩니다. Visual Studio 계층 드라이브 및 상황에 맞는 메뉴를 결정합니다. IDE 사용자 인터페이스에 주요 통합 요소는 문서 windows, 도구 창, 프로젝트, 명령 구조, 텍스트 편집기, 도구 상자, 속성 창 및 도구 > 옵션.

 각각의 사용자 인터페이스에서 IDE의 주요 통합 지점에 대 한 기본 사용 패턴 가지가 있습니다.

- [Visual Studio의 메뉴 및 명령](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)

- [Visual Studio의 애플리케이션 패턴](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)

  - [창의 상호 작용](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_WindowInteractions)

  - [도구 창](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_ToolWindows)

  - [편집기 도움말 표기법](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_DocumentEditorConventions)

  - [대화 상자](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)

  - [프로젝트](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Projects)

## <a name="common-control-patterns"></a>일반적인 컨트롤 패턴
 컨트롤 패턴은 주로 개별 컨트롤에 대 한 것으로 예상 됩니다 동작입니다. 일관성의 가장 중요 한 영역입니다.

 Visual Studio에서 가장 일반적인 컨트롤 데스크톱 Windows 지침을 따라야 합니다. 지침에는 Visual Studio 관련 상호 작용 또는 위치는에서는 대체 지침 완전히 Visual Studio의 복잡 한 사용자 요구에 맞게 조정 하기 위해 사용 하 여 공통 규칙을 확장 해야 하는 영역만 포함 됩니다.

- [Visual Studio의 일반 컨트롤 패턴](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md)

  - [공용 컨트롤](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CommonControls)

  - [텍스트 컨트롤](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

  - [단추, 하이퍼링크](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

## <a name="composite-patterns"></a>복합 패턴
 사용자가 작업을 수행 해야 하는 방법의 여러 가지가 있습니다. 가능 하면 기능을 모두 상호 작용 및 시각적 디자인에 대 한 이러한 패턴을 사용 하도록 설계 되어야 합니다.

 가장 중요 한 일부 Visual Studio 내에서 여러 복합 패턴 있기는 일관성와 관련 하 여 됩니다.

- [Visual Studio의 복합 패턴](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md)

  - [개체에 UI 및 보기](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)

  - [모델 선택](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)

  - [지 속성 및 설정 저장 중](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)

  - [터치식 입력](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)
