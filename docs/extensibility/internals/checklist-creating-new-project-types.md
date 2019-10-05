---
title: '검사 목록: 새 프로젝트 형식 만들기 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], creating new types
- project types, checklist for creating
ms.assetid: 29eb9c3b-1933-4741-aa85-65a33f0825ba
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 64e00c452f01c95046b4dc669dbd3bdd1517d287
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66309209"
---
# <a name="checklist-create-new-project-types"></a>검사 목록: 새 프로젝트 형식 만들기
새 프로젝트 형식을 만들려면 몇 가지 작업을 완료 해야 합니다. 이러한 작업에 대 한 지침을 제공 하는 다음 검사 목록:

1. 새 프로젝트 형식에 대 한 기능을 디자인 합니다. 자세한 내용은 [프로젝트 형식 디자인 결정](../../extensibility/internals/project-type-design-decisions.md)합니다.

2. 코드 및 기타 프로젝트 요소는 편집기가 사용을 확인 합니다. 핵심 또는 표준 편집기를 사용 하거나 만들고 프로젝트별 편집기를 사용할 수 있습니다. 자세한 내용은 [사용자 지정 편집기와 디자이너를 만들](../../extensibility/creating-custom-editors-and-designers.md) 및 [방법: 프로젝트별 편집기 열기](../../extensibility/how-to-open-project-specific-editors.md)합니다.

3. 프로젝트 항목에는 참여 수준을 확인 합니다 **클래스 뷰** 하며 **개체 브라우저**합니다. 자세한 내용은 [기호 검색 도구 지원](../../extensibility/internals/supporting-symbol-browsing-tools.md)합니다.

4. 프로젝트 및 프로젝트 항목에 대해 이전에 변경한 디자인 결정에 따라 새 클래스를 파생 합니다.

5. 다음 프로젝트 형식 구성 요소에 대 한 코드를 작성 합니다.

    - 새 프로젝트를 만들고 기존 프로젝트를 열고 관리 하려면 프로젝트 팩터리입니다. 자세한 내용은 [프로젝트 팩터리를 사용 하 여 프로젝트 인스턴스를 만들](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)합니다.

    - 프로젝트 계층 구조 및 명령 처리 합니다. 자세한 내용은 [프로젝트 유형을 구현 하도록 사용 하 여 HierUtil7 프로젝트 클래스 (C++)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346)를 [프로젝트 모델의 요소](../../extensibility/internals/elements-of-a-project-model.md)를 [프로젝트 모델 핵심 구성 요소](../../extensibility/internals/project-model-core-components.md), 및 [Menucommand 합니다. OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md)합니다.

    - 프로젝트 항목 관리, 프로젝트에 추가 하는 등의 **새 프로젝트** 대화 상자. 자세한 내용은 [프로젝트 및 프로젝트 항목 템플릿 추가](../../extensibility/internals/adding-project-and-project-item-templates.md) 하 고 [프로젝트 및 항목 템플릿을 등록](../../extensibility/internals/registering-project-and-item-templates.md)합니다.

    - 프로젝트 상태 및 개별 항목의 지 속성 자세한 내용은 [열린 프로젝트 항목을 저장 하 고](../../extensibility/internals/opening-and-saving-project-items.md)입니다. 솔루션 정보의 지 속성을 참조 하세요 [솔루션](../../extensibility/internals/solutions-overview.md)합니다.

    - 구성에 관계 없이 속성을 속성 창에서 표시 합니다. 자세한 내용은 [속성을 확장](../../extensibility/internals/extending-properties.md)합니다.

    - 프로젝트 구성에 종속 된 속성을 표시 하려면 속성 페이지에서 구현 될 때 구성 속성입니다. 자세한 내용은 [구성 옵션 관리](../../extensibility/internals/managing-configuration-options.md)합니다.

    - 배포에 대 한 출력을 열거 합니다. 자세한 내용은 [출력에 대 한 프로젝트 구성을](../../extensibility/internals/project-configuration-for-output.md)합니다.

    - 프로젝트 시작 서비스입니다. 자세한 내용은 [프로젝트 모델의 요소](../../extensibility/internals/elements-of-a-project-model.md) 하 고 [프로젝트 모델 핵심 구성 요소](../../extensibility/internals/project-model-core-components.md)합니다.

    - 개체 또는 클래스에서 파생 된 `IDispatch`, 자동화에 사용할 수 있습니다.

    - XML 명령 테이블 ( *.vsct*) 파일입니다. 자세한 내용은 [Visual Studio 명령 테이블 (.vsct) 파일](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)합니다.

6. 테스트, 디버깅 및 프로젝트 형식 시작 합니다.

7. 프로젝트를 표시 합니다 **프로젝트** 탭을 **참조 추가** 설정 하 여 대화 상자 `VARIANT_TRUE` 값으로 `VSHPROPID_ShowProjInSolutionPage`합니다. 자세한 내용은 <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> 및 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>를 참조하세요.

8. Microsoft 설치 관리자를 만듭니다 ( *.msi*) 파일에 Vspackage를 설치 합니다. 자세한 내용은 [Windows Installer를 사용 하 여 Vspackage 설치](../../extensibility/internals/installing-vspackages-with-windows-installer.md)를 [프로젝트 유형을 등록할](../../extensibility/internals/registering-a-project-type.md), 및 [Vspackage](../../extensibility/internals/vspackages.md)합니다.

## <a name="see-also"></a>참고자료
- [Visual Studio의 계층 구조](../../extensibility/internals/hierarchies-in-visual-studio.md)
- [프로젝트 형식을 만들어야 하는 경우](../../extensibility/internals/when-to-create-project-types.md)
- [프로젝트 형식 만들기](../../extensibility/internals/creating-project-types.md)