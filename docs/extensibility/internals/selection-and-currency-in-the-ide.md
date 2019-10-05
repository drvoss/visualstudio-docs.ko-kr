---
title: IDE의 선택 및 통화 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- currency, Visual Studio IDE
- IDE, selection
- selection, Visual Studio IDE
- IDE, currency
ms.assetid: 2f6f18d1-acd8-454d-a856-9a4d81155052
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 23ce55a85fd6f1408c623a49fc16b8766c535dfc
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66318705"
---
# <a name="selection-and-currency-in-the-ide"></a>IDE의 선택 및 통화
합니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 통합된 개발 환경 (IDE) 선택을 사용 하 여 현재 선택한 개체 사용자에 대 한 정보를 유지 관리 *상황에 맞는*합니다. 선택 항목 컨텍스트를 사용 하 여 Vspackage 두 가지 방법으로 추적 하는 통화로 포함이 될 수 있습니다.

- IDE에 Vspackage에 대 한 통화 정보를 전파 합니다.

- IDE 내에서 사용자의 현재 선택을 모니터링 합니다.

## <a name="selection-context"></a>선택 항목 컨텍스트
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 전역으로 추적 IDE 통화의 고유한 전역 선택 컨텍스트 개체입니다. 다음 표에서 선택 항목 컨텍스트를 구성 하는 요소를 보여 줍니다.

|요소|설명|
|-------------|-----------------|
|현재 계층|일반적으로 현재 프로젝트 NULL 현재 계층 솔루션 전체를 대상으로 현재 임을 나타냅니다.|
|현재 ItemID|현재 계층; 내에서 선택한 항목 프로젝트 창에서 여러 항목을 선택할 경우 현재 항목이 여러 개 있을 수 있습니다.|
|현재 `SelectionContainer`|속성 창의 속성을 표시 하는 하나 이상의 개체를 보유 합니다.|

 또한 환경에는 두 가지 전역 목록을 유지 관리합니다.

- 활성 UI 명령 식별자의 목록

- 현재 요소 형식의 목록입니다.

### <a name="window-types-and-selection"></a>창 유형 및 선택
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE는 두 가지 일반 유형으로 windows를 구성 합니다.

- 계층 유형을 windows

- 도구 및 문서 창 등의 프레임 창

  IDE는 다른 방식으로 이러한 각 유형의 창에 대 한 통화를 추적합니다.

  가장 일반적인 프로젝트 형식 IDE 제어 하는 솔루션 탐색기입니다. 현재 계층 구조를 확인 하려면 사용자의 선택 창 사용 및 프로젝트 형식 창 글로벌 계층 및 ItemID 전역 선택 컨텍스트를 추적 합니다. 환경을 프로젝트 형식 창에 대 한 글로벌 서비스를 제공 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>을 통해 어떤 Vspackage 열기 요소에 대 한 현재 값을 모니터링할 수 있습니다. 환경에서 검색 속성은이 글로벌 서비스에 의해 좌우 됩니다.

  반면, 프레임 창 선택 영역 컨텍스트 값 (계층/ItemID/SelectionContainer 다음과)에 적용할 DocObject 프레임 창 내에서 사용 합니다. . 서비스를 사용 하는 프레임 창 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> 이 목적입니다. ItemID 변경, MDI 자식 문서에 대 한 일반적인 그대로 및 DocObject 푸시할 수 선택 컨테이너에 대 한 값만 계층 구조에 대 한 로컬 값을 유지 합니다.

### <a name="events-and-currency"></a>이벤트 및 통화
 두 가지 유형의 이벤트는 통화의 환경의 개념에 영향을 주는 발생할 수 있습니다.

- 전역 수준에 전파 되 고 창 프레임 선택 컨텍스트를 변경 하는 이벤트입니다. 이 유형의 이벤트의 예로 열려 있는 전역 도구 창 또는 열려 있는 프로젝트 형식 도구 창이 열려 있는 MDI 자식 창이 있습니다.

- 창 프레임 선택 컨텍스트 내에서 추적 요소를 변경 하는 이벤트입니다. DocObject 내에서 선택을 변경 하거나 프로젝트 형식 창에서 선택을 변경을 예로 들 수 있습니다.

## <a name="see-also"></a>참고 항목
- [선택 컨텍스트 개체](../../extensibility/internals/selection-context-objects.md)
- [사용자에 대한 피드백](../../extensibility/internals/feedback-to-the-user.md)