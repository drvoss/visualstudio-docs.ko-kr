---
title: 프로젝트 형식 필수 항목 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types [Visual Studio SDK]
ms.assetid: 09991589-2300-430e-b6a4-7f2b95fe676f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bc60ae68f008cefd468af8a688e9aae9241ca3be
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66318965"
---
# <a name="project-type-essentials"></a>프로젝트 형식 필수 항목
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 같은 언어에 대 한 여러 프로젝트 유형이 포함 되어 있습니다 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 또는 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]합니다. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 또한 사용자 고유의 프로젝트 형식을 만들 수 있습니다.

 사용자 지정 명령, 편집기, 또는 도구 창을 추가 하려는 경우 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], 새 프로젝트 형식을 만들지 않고이 수행할 수 있습니다. 자세한 내용은 다음 항목을 참조하세요.

- [명령, 메뉴 및 도구 모음](../../extensibility/internals/commands-menus-and-toolbars.md)

- [편집기 및 언어 서비스 확장](../../extensibility/editor-and-language-service-extensions.md)

- [도구 창 확장 및 사용자 지정](../../extensibility/extending-and-customizing-tool-windows.md)

  마찬가지로, 제공된 된 동작을 사용자 지정 하려는 경우 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 및 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 하면 프로젝트 형식에 사용 하 여 프로젝트 하위 형식입니다. 자세한 내용은 [프로젝트 하위 형식](../../extensibility/internals/project-subtypes.md)합니다.

  새 프로젝트 형식을 기반으로 하는 언어 이외의 다른 프로젝트를 만들어야 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 고 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 다음 중 하나 이상을 지원 하려는 경우:

- 빌드

- 배포

- 여러 구성

- 소스 제어

- 디버깅

- 솔루션 탐색기에서 프로젝트 항목

- 합니다 **프로젝트 열기** 하거나 **새 프로젝트** 대화 상자

- 프로젝트 중첩

- 프로젝트 형식의 기능에 대 한 자세한 내용은 다음을 참조 하세요.

- 프로젝트 형식은 인터페이스 집합을 구현 하는 VSPackage에서 개체 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 필요 합니다. 사용 중인 경우 C# 프로젝트 형식을 개발, 관리 패키지 프레임 워크 프로젝트 클래스를 필요한 인터페이스를 구현 되며 해당 구현을 상속할 수 있습니다. 자세한 내용은 [프로젝트 형식 (C#)를 구현 하는 관리 패키지 프레임 워크를 사용 하 여](../../extensibility/internals/using-the-managed-package-framework-to-implement-a-project-type-csharp.md)입니다.

- 에 대 한 C++ 개발자 HierUtil 라이브러리의 클래스는 비슷한 방식으로 작동 합니다. 자세한 내용은 참조 하세요. [빌드에 없음: 프로젝트 유형을 구현 하도록 HierUtil7 프로젝트 클래스를 사용 하 여 (C++)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346)합니다.

- 프로젝트 형식에는.exe 또는.dll 어셈블리로 작성 하는 일반적인 소스 코드 파일 이외의 데이터 지원할 수 있습니다. 예를 들어 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 데이터베이스 프로젝트 디스크에 저장 하는 스크립트 및 쿼리 파일에 대 한 참조를 포함 하 고 하는 명령을 추가 **솔루션 탐색기** 실행 하는 스크립트 및 데이터베이스에 있지만 프로젝트에 대 한 쿼리 지원 하지 않습니다 동작을 빌드하십시오. 자세한 내용은 [열기 및 프로젝트 항목 저장](../../extensibility/internals/opening-and-saving-project-items.md)합니다.

- 프로젝트 형식 파일을 전혀 사용할 필요가 없습니다. 예를 들어, 프로젝트 형식을 데이터베이스에서 모든 데이터를 저장 수 있습니다. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 프로젝트 형식 프로젝트 및 프로젝트 항목에 대 한 데이터는 유지 하는 방법을 완전히 제어를 제공 합니다. 자세한 내용은 [프로젝트 형식 디자인 결정](../../extensibility/internals/project-type-design-decisions.md)합니다.

- 프로젝트 형식을 제공 해야 합니다는 *프로젝트 팩터리*, 프로젝트의 인스턴스를 만드는 개체는 때마다 입력 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 해당 프로젝트 형식을 기반으로 하는 프로젝트를 만들거나 열에 지시 합니다. 자세한 내용은 [만들 프로젝트 인스턴스에서 사용 하 여 프로젝트 팩터리](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)합니다.

- 프로젝트 형식에는 프로젝트 및 프로젝트 항목에 대 한 템플릿을 제공 해야 합니다. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 사용자가 새 프로젝트를 만들고 기존 프로젝트에 새 항목을 추가 하는 경우 서식 파일을 사용 합니다. 자세한 내용은 [추가 프로젝트 및 프로젝트 항목 템플릿](../../extensibility/internals/adding-project-and-project-item-templates.md)합니다.

- 프로젝트 형식에는 디버그 및 릴리스 등 여러 구성을 지원할 수 있습니다. 사용자는 프로젝트의 다양 한 구성을 제공 하는 속성 페이지를 사용 하 여 변경할 수 있습니다. 자세한 내용은 [구성 옵션 관리](../../extensibility/internals/managing-configuration-options.md)합니다.

## <a name="see-also"></a>참고 항목
- [프로젝트 형식 배포](../../extensibility/internals/deploying-project-types.md)