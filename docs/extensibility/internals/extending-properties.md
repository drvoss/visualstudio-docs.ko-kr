---
title: 속성 확장 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, providing support
ms.assetid: 68e2cbd4-861c-453f-8c9f-4ab6afc80e67
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ee70a4d88dfc6eb1dae5c0d8fba0fb1deb7a7621
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66332187"
---
# <a name="extend-properties"></a>확장 속성
합니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **속성** 창은 COM 및 COM + 구성 요소에 대 한 유니버설 속성 브라우저를 모두 지원 하며 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 제품입니다. 합니다 **속성** 창을 사용 하 여 작동 `ITypeInfo` 정보 및 COM + 통합된 개발 환경 (IDE)에서 다른 창에서 현재 선택한 개체에 대 한 디자인 타임 속성을 나열 하려면 메타 데이터를 입력 합니다.

 합니다 **속성** 키를 눌러 열 수 있는 창 **F4** 키보드에서 선택 하거나 **속성 창** 에 **보기** 메뉴 보기 및 편집 구성에 관계 없이, 디자인 타임 속성 및 선택한 개체의 이벤트에 사용 됩니다. 솔루션 및 프로젝트와 관련 된 구성에 종속 된 속성에 표시 됩니다 [속성 페이지](../../extensibility/internals/property-pages.md)합니다. 자세한 내용은 [구성 옵션 관리](../../extensibility/internals/managing-configuration-options.md)합니다.

 ![속성 창 개요](../../extensibility/internals/media/vspropertieswindow.png "vsPropertiesWindow") 속성 창

 이 섹션의 개별 영역에 관련 된 자세한 정보를 제공 합니다 **속성** 창 및 구현 해야 하는 인터페이스 창을 채울를 호출 합니다.

## <a name="in-this-section"></a>단원 내용
- [속성 창 개요](../../extensibility/internals/properties-window-overview.md)

 용도 설명 합니다 **속성** 창 문서 창과 도구 창을 기준으로 합니다.

- [템플릿 정책 및 속성 창](../../extensibility/internals/template-policy-and-the-properties-window.md)

 엔터프라이즈 템플릿 프로젝트를에 프로젝트를 포함 하는 방법 및 엔터프라이즈 템플릿 프로젝트에 해당 정책을 적용할 수 있습니다 하는 방법을 설명 합니다.

- [속성 창 필드 및 인터페이스](../../extensibility/internals/properties-window-fields-and-interfaces.md)

 선택 영역에 표시 되는 정보를 결정 하는 기준에 설명 합니다 **속성** 창입니다.

- [속성 창 개요 목록](../../extensibility/internals/properties-window-object-list.md)

 용도 설명 합니다 **속성** 창 개체 목록, 방법,이 목록에서 다른 개체에 대 한 호출 트리거되면 환경 합리적인는 new-object가 선택 되어 있는지를 설명 하는 합니다.

- [속성 창 단추](../../extensibility/internals/properties-window-buttons.md)

 에 표시 된 네 가지 기본 단추의 용도 설명 하는 **속성** 창 도구 모음입니다.

- [속성 눈금 표시](../../extensibility/internals/properties-display-grid.md)

 표에서 속성 이름 및 속성 값 필드 발견에 대해 설명 합니다.

## <a name="related-sections"></a>관련 단원
- [프로젝트 형식](../../extensibility/internals/project-types.md)

 빌딩 블록으로 프로젝트에 설명 합니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.

- [컴파일 및 빌드](../../ide/compiling-and-building-in-visual-studio.md)

 사용 하는 방법에 대해 설명 합니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 지속적으로 테스트 및 빌드하 응용 프로그램을 디버깅 하기 위한 플랫폼입니다.

- [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)

 에 대해 설명 합니다 `IDispatch` 먼저 automation에 액세스 하 고 메서드 및 개체의 속성에 대 한 정보를 검색 하는 런타임에 바인딩된 메커니즘을 제공을 지원 하도록 설계 된 인터페이스.

- [애플리케이션 설정 관리(.NET)](../../ide/managing-application-settings-dotnet.md)

 속성 값은 응용 프로그램의 컴파일된 코드는 대신 외부 구성 파일에 저장 되므로 응용 프로그램을 구성할 수 있는 응용 프로그램 설정에 간략하게 설명 합니다.

- [솔루션 및 프로젝트](../../ide/solutions-and-projects-in-visual-studio.md)

 에 대해 설명 하는 방법을 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 참조, 데이터 연결, 폴더 및 솔루션 및 프로젝트를 통해 개발 작업에 필요한 파일을 같은 항목을 효율적으로 관리 합니다.

- [Visual Studio의 다른 부분 확장](../../extensibility/extending-other-parts-of-visual-studio.md)

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 서비스를 사용하여 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]의 나머지와 일치하는 UI 요소를 만드는 방법을 설명합니다.