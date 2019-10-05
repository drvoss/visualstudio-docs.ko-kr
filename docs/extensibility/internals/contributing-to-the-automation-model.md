---
title: 자동화 모델에 영향을 주는 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK]
ms.assetid: 44de482d-93c8-41a4-843c-cefda995a03e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 47e6686c82dcb0272fa9b3b3c4d3b7c73afe4475
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66335439"
---
# <a name="contribute-to-the-automation-model"></a>자동화 모델에 참여
Visual Studio 환경 사용자 지정에 대 한 일련의 자동화 인터페이스를 제공 합니다. 자동화 모델에는 최종 사용자가 Visual Studio 추가 기능 및 확장을 만들 수 있는 개체 모델이입니다.

 또한 적합 하면 VSPackage 개발자는 자동화 모델에 영향을 주는 이 작업을 수행 하면 최종 사용자가 추가 기능 만들기에서 VSPackage를 사용할 때 일반적으로 일관 된 사용자 모델 경험을 제공 하 여 VSPackage의 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]합니다.

 최종 사용자 경험을 일관 되 게 따르면 지침 집합이 VSPackage에 대 한 자동화 모델의 아이디어를 뒤에 오도록 VSPackage를 디자인할 때 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]합니다.

## <a name="in-this-section"></a>단원 내용
- [자동화 모델 개요](../../extensibility/internals/automation-model-overview.md)

 공용 환경의 주요 측면을 제어 하는 개체의 관련된 그룹으로 자동화 모델을 정의 합니다. 이 개체 집합이 자동화 모델의 다이어그램에 나와 있습니다.

- [Vspackage에 대 한 자동화 제공](../../extensibility/internals/providing-automation-for-vspackages.md)

 VSPackage에 대 한 자동화를 제공 하는 두 가지 주요 방법에 설명 합니다.

- [프로젝트 개체 노출](../../extensibility/internals/exposing-project-objects.md)

 VSPackage 관련 개체를 만들기 위한 단계별 지침을 제공 합니다.

- [프로젝트 모델링](../../extensibility/internals/project-modeling.md)

 새 프로젝트 형식에 대 한 자동화를 만드는 데 필요한 표준 프로젝트 개체를 설명 하 고 프로젝트 자동화 뒤에 오는 경로 보여 줍니다. 이 항목에는 또한 선언 및 구현 클래스의 목록을 제공합니다.

- [이벤트를 노출 합니다.](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)

 자동화 모델에 대 한 이벤트를 만들기 위한 단계별 지침을 제공 합니다.

- [Automation 옵션 페이지에 대 한 지원](../../extensibility/internals/automation-support-for-options-pages.md)

 VSPackage의 속성을 지 원하는 사용자 지정에 대 한 자동화 개체를 반환 하는 방법에 설명 **옵션** 대화 상자에는 **도구** 확장 하 여 메뉴를 `DTE.Properties` 개체입니다.

- [코드에 대 한 자동화 제공](../../extensibility/internals/providing-automation-for-code.md)

 코드에 대 한 자동화 모델을 만드는 필요 하지 않음을 설명 합니다. 그러나 코드 모델에 대 한 통찰력 있는 정보를 제공 하는이 항목의 링크가 제공 됩니다.

- [방법: Windows에 대 한 자동화 제공](../../extensibility/internals/how-to-provide-automation-for-windows.md)

 창에서 자동화 개체를 사용할 수 있도록 하 고 환경에서 바로 사용할 수 있는 자동화 개체를 이미 제공 하지 않습니다 때마다 자동화를 제공 하는 것이 좋습니다는 있는지 설명 합니다. 도구 창과 문서 창에 대 한 자동화를 설명합니다.

- [자동화 모델을 사용](../../extensibility/internals/using-the-automation-model.md)

 Automation 소비자를 얻는 방법을 초기 프로젝트 자동화 개체를 보여 주는 두 가지 코드 예제를 제공 합니다.

- [구성 및 SelectedItem 개체 자동화](../../extensibility/internals/automation-for-configuration-and-selecteditem-objects.md)

 구성 및 SelectedItems 개체에 대 한 자동화에 대 한 정보를 제공합니다.

## <a name="reference"></a>참조
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> VSPackage에서 DTE 자동화 개체 모델 참여 하는 방법을 보여 주는 코드 샘플을 제공 합니다. 매개 변수, 반환 값 및 선택한 설명을 나열합니다.
