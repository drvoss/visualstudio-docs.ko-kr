---
title: Visual Studio Shell | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- shell, Visual Studio
- Visual Studio, shell
ms.assetid: cb124ef4-1a6b-4bfe-bfbf-295ef9c07f36
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8a147abd4655c923604dd9ca6696e97aac4944ec
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66332883"
---
# <a name="visual-studio-shell"></a>Visual Studio Shell
합니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] shell은 통합의 주요 에이전트인 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]합니다. 셸에 공통 서비스를 공유 하는 Vspackage를 사용 하도록 설정 하려면 필요한 기능을 제공 합니다. 때문에 아키텍처 목표 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 는 Vspackage의 기본 기능이 vest 방법은 셸에서 기본 기능을 제공 하 고 Vspackage 해당 구성 요소 간에 간 통신을 지원 하기 위한 프레임 워크입니다.

## <a name="shell-responsibilities"></a>셸 책임
 셸에 주요 책임은 다음과 같습니다.

- 사용자 인터페이스 (UI)의 기본 요소 (COM 인터페이스)를 통해 지원합니다. 이러한 기본 메뉴 및 도구 모음, 문서 창 프레임 또는 다중 문서 MDI (인터페이스) 자식 창 및 도구 창 프레임 및 도킹 지원을 포함 합니다.

- 문서의 지 속성을 조정 하기 위해 및 여러 가지 방법 또는 호환 되지 않는 방식으로 문서를 열 수 없습니다를 보장 하기 위해 실행 중인 문서 테이블 실행 (RDT)에서 모든 현재 열린 문서의 목록을 유지 관리 합니다.

- 명령 라우팅 및 명령 처리 인터페이스를 지 원하는 `IOleCommandTarget`합니다.

- 적절 한 시간에 Vspackage를 로드 합니다. 지연 로드 VSPackage 셸 성능 향상 됩니다.

- 공유 서비스와 같은 특정 관리 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>, 기본 셸 기능을 제공 하는 및 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>, 기본적인 창 관리 기능을 제공 하는 합니다.

- 솔루션 (.sln) 파일을 관리 합니다. 시각적 개체의 작업 영역 (.dsw) 파일과 유사한 관련된 프로젝트의 그룹을 포함 하는 솔루션 C++ 6.0.

- 셸 전체 선택 영역 추적, 컨텍스트 및 통화입니다. 셸은은 다음과 같은 유형의 항목을 추적합니다.

  - 현재 프로젝트

  - 현재 프로젝트 항목 또는 현재 ItemID <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>

  - 현재 선택을 합니다 **속성** 창 또는 `SelectionContainer`

  - Id 또는 CmdUIGuids 명령, 메뉴 및 도구 모음의 표시 유형을 제어 하는 UI 컨텍스트

  - 활성 창, 문서 및 실행 취소 관리자와 같은 현재 요소

  - 동적 도움말을 구동 하는 사용자 컨텍스트 특성

  셸에는 설치 된 Vspackage 및 현재 서비스 간의 통신은 중재합니다. Shell의 주요 기능을 지원 하 고 통합 하는 모든 Vspackage를 사용할 수 있게 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]합니다. 이러한 핵심 기능에 다음 항목을 포함 합니다.

- **에 대 한** 대화 상자 및 시작 화면

- **신규 및 기존 항목 추가 추가** 대화 상자

- **클래스 뷰** 창 및 **개체 브라우저**

- **참조** 대화 상자

- **문서 개요** 창

- **동적 도움말** 창

- **찾을** 고 **대체**

- **프로젝트를 엽니다** 하 고 **파일 열기** 대화 상자에 **새로 만들기** 메뉴

- **옵션** 대화 상자에는 **도구** 메뉴

- **속성** 창

- **솔루션 탐색기**

- **작업 목록** 창

- **도구 상자**

## <a name="see-also"></a>참고 항목
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>
- [VSPackage](../../extensibility/internals/vspackages.md)