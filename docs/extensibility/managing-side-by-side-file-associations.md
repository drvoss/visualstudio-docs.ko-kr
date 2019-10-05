---
title: Side-by-side-파일 연결 관리 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- verbs, setting default
ms.assetid: 9b6df3bc-d15c-4a5d-9015-948a806193b7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b5d389ea97c9a77fe859a4029e4447adf76624e3
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66340664"
---
# <a name="manage-side-by-side-file-associations"></a>Side-by-side-파일 연결 관리

VSPackage 파일 연결을 제공 하는 경우는 side-by-side-설치를 처리 하는 방법을 결정 해야 특정 버전의 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 파일을 호출 해야 합니다. 호환 되지 않는 파일 형식 문제를 복합 합니다.

사용자는 데이터 손실 없이 새 버전이 기존 파일을 로드할 수 있습니다 있도록 이전 버전과 호환 되도록 제품의 새 버전을 기대 합니다. 이상적으로 VSPackage 수 모두 로드 및 저장 이전 버전의 파일 형식. true가 아닐 경우에 파일 형식을 VSPackage의 새 버전으로 업그레이드를 제공 해야 합니다. 이 방식의 단점은 이전 버전에서 업그레이드 된 파일을 열 수 없습니다.

이 문제를 방지 하려면 호환 되지 않는 파일 형식 될 때 확장을 변경할 수 있습니다. 예를 들어, VSPackage의 버전 1 확장을 사용 *.mypkg10*, 및 버전 2 확장을 사용할 수 있습니다 *.mypkg20*합니다. 이러한 차이 특정 파일을 엽니다는 VSPackage를 식별 합니다. 이전 확장을 사용 하 여 관련 된 프로그램 목록에 새 Vspackage를 추가 하는 경우 사용자는 파일을 마우스 오른쪽 단추로 클릭 하 고 최신 VSPackage에서 열도록 선택할 수 있습니다. 이 시점에서 VSPackage는 새 형식으로 파일을 업그레이드 또는 파일을 열고, VSPackage의 이전 버전과 호환성을 유지 관리를 제공할 수 있습니다.

> [!NOTE]
> 이러한 접근 방식은 결합할 수 있습니다. 예를 들어 이전 파일을 로드 하 여 이전 버전과 호환성을 제공할 수 있으며 사용자 저장 하는 경우 파일 형식으로 업그레이드 하려면 제공 수 있습니다.

## <a name="face-the-problem"></a>얼굴 문제

동일한 확장을 사용 하려면 여러 side-by-side-Vspackage를 하려는 경우 버전을 선택 해야 합니다 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 확장을 사용 하 여 연결 합니다. 두 가지 방법을 다음과 같습니다.

- 최신 버전의 파일을 엽니다 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 사용자의 컴퓨터에 설치 합니다.

   이 방법에서 설치 관리자 판단할 책임은 최신 버전의 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 및 기록 파일 연결에 대 한 레지스트리 항목에는 포함 합니다. Windows Installer 패키지에서의 최신 버전을 나타내는 속성을 설정 하려면 사용자 지정 작업을 포함할 수 있습니다 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]합니다.

  > [!NOTE]
  > 이 컨텍스트에서 "latest" 의미 "최신 지원 되는 버전입니다." 이러한 설치 관리자 항목의 이후 릴리스를 자동으로 검색 하지는 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]합니다. 항목에서 [시스템 요구 사항 검색](../extensibility/internals/detecting-system-requirements.md) 고 [명령을 해야 수 실행 한 후 설치](../extensibility/internals/commands-that-must-be-run-after-installation.md) 여기에 제시 된 것과 비슷한 및의 추가 버전을 지원 하는 데 필요한 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]합니다.

   CustomAction 표의 다음 행을 AppSearch 설정한 속성 DEVENV_EXE_LATEST 속성을 설정 하 고 RegLocator 테이블에서 설명한 [설치 후 실행 해야 하는 명령을](../extensibility/internals/commands-that-must-be-run-after-installation.md)합니다. InstallExecuteSequence 테이블의 행에는 초기 실행 순서에에서 사용자 지정 동작을 예약합니다. 조건 열 make 논리 작업에에서 대 한 값:

  - Visual Studio.NET 2002는만 있는 버전인 경우 최신 버전입니다.

  - 있는 경우에 visual Studio.NET 2003은 최신 버전 및 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 가 없습니다.

  - [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 만 있는 버전인 경우 최신 버전이입니다.

    결과 DEVENV_EXE_LATEST devenv.exe의 최신 버전의 경로 포함 하는 경우

  **Visual Studio의 최신 버전을 결정 하는 CustomAction 테이블 행**

  |작업|형식|Source|대상|
  |------------|----------|------------|------------|
  |CA_SetDevenvLatest_2002|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2002]|
  |CA_SetDevenvLatest_2003|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2003]|
  |CA_SetDevenvLatest_2005|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2005]|

  **Visual Studio의 최신 버전을 결정 하는 InstallExecuteSequence 테이블 행**

  |작업|조건|Sequence|
  |------------|---------------|--------------|
  |CA_SetDevenvLatest_2002|DEVENV_EXE_2002 아니라 (DEVENV_EXE_2003 또는 DEVENV_EXE_2005)|410|
  |CA_SetDevenvLatest_2003|DEVENV_EXE_2003 및 DEVENV_EXE_2005 없습니다|420|
  |CA_SetDevenvLatest_2005|DEVENV_EXE_2005|430|

   쓸 Windows Installer 패키지의 레지스트리 표에 DEVENV_EXE_LATEST 속성을 사용할 수 있습니다 합니다 **HKEY_CLASSES_ROOT*ProgId*ShellOpenCommand** 키의 기본값을 [DEVENV_EXE_LATEST] "%1"

- 사용 가능한 VSPackage 버전에서 최상의 만들 수 있는 공유 시작 관리자 프로그램을 실행 합니다.

   개발자 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 여러 형식의 솔루션 및 프로젝트의 여러 버전에서 발생 하는 복잡 한 요구 사항을 처리 하려면이 방법을 선택한 이유 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]합니다. 이 방법에서는 확장 처리기로 시작 관리자 프로그램을 등록합니다. 파일을 검사 하 고 버전을 결정 하는 시작 관리자 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSPackage는 해당 특정 파일을 처리할 수 있습니다. 예를 들어 사용자가 VSPackage의 특정 버전에서 마지막으로 저장 된 파일을 열면, 시작 관리자에서에서 시작할 수는 VSPackage의 일치 하는 버전 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]합니다. 또한 사용자는 항상 최신 버전을 시작 하려면 시작 관리자를 구성할 수 있습니다. 또한 시작 관리자는 사용자에 게 파일의 형식으로 업그레이드를 요구할 수 있습니다. 파일 형식의 버전 번호를 포함 하는 경우에 시작 관리자 파일 형식을 하나 이상의 설치 Vspackage 보다 최신 버전의 경우 사용자에 알릴 수 있습니다.

   시작 관리자는 모든 버전의 VSPackage 사용 하 여 공유 되는 Windows Installer 구성 요소에 있어야 합니다. 이 과정은 최신 버전 항상 설치 되 고 VSPackage의 모든 버전에는 제거 될 때까지 제거 되지 않습니다. 이러한 방식으로 파일 연결 및 시작 관리자 구성 요소의 다른 레지스트리 항목 VSPackage의 버전을 제거 하는 경우에 유지 됩니다.

## <a name="uninstall-and-file-associations"></a>제거 하 고 파일 연결

파일 연결을 제거 파일 연결에 대 한 레지스트리 항목을 작성 하는 VSPackage를 제거 합니다. 따라서 확장에 연결 된 프로그램이 없습니다. Windows Installer 복구 되지 않습니다 "" VSPackage를 설치할 때 추가 된 레지스트리 항목. 사용자의 파일 연결을 수정 하는 몇 가지는 다음과 같습니다.

- 앞에서 설명한 대로 공유 시작 관리자 구성 요소를 사용 합니다.

- 파일 연결을 소유 하는 사용자가 VSPackage의 버전의 복구를 실행 하도록 지시 합니다.

- 적절 한 레지스트리 항목을 다시 작성 하는 별도 실행 프로그램을 제공 합니다.

- 구성 옵션 페이지 또는 대화 상자를 사용자가 파일 연결을 선택 하 고 손실 된 연결을 회수할 수 있도록 제공 합니다. 제거 후에 실행 하는 사용자에 게 지시 합니다.

## <a name="see-also"></a>참고자료

- [Side-by-side-배포에 대 한 파일 이름 확장명 등록](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)
- [파일 이름 확장명에 대 한 동사 등록](../extensibility/registering-verbs-for-file-name-extensions.md)