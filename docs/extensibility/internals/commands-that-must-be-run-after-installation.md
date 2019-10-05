---
title: 설치 후 실행 해야 하는 명령을 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- post-install commands
ms.assetid: c9601f2e-2c6e-4da9-9a6e-e707319b39e2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d8a59e1a6613936c586c5529dcfc6a56a957112c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66341985"
---
# <a name="commands-that-must-be-run-after-installation"></a>설치 후 실행 해야 하는 명령
통해 확장 프로그램을 배포 하는 경우는 *.msi* 를 실행 해야 파일 **devenv /setup** for Visual Studio 확장을 검색 하는 순서 대로 설치의 일부로.

> [!NOTE]
> 이 항목의 정보를 찾기 위한 적용 *devenv.exe* Visual Studio 2008 및 이전 버전입니다. 검색 하는 방법에 대 한 자세한 *devenv.exe* 이상 버전의 Visual Studio를 사용 하 여 참조 [시스템 요구 사항 검색](../../extensibility/internals/detecting-system-requirements.md)합니다.

## <a name="find-devenvexe"></a>Devenv.exe 찾기
 각 버전을 찾을 수 있습니다 *devenv.exe* 값을 레지스트리에서 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] RegLocator 테이블과 AppSearch 테이블을 사용 하 여 레지스트리 값을 속성으로 저장 하는 설치 관리자가 작성 합니다. 자세한 내용은 [시스템 요구 사항 검색](../../extensibility/internals/detecting-system-requirements.md)합니다.

### <a name="reglocator-table-rows-to-locate-devenvexe-from-different-versions-of-visual-studio"></a>Visual Studio의 서로 다른 버전의 devenv.exe를 찾으려고 RegLocator 테이블 행

|서명|루트|Key|이름|형식|
|-----------------|----------|---------|----------|----------|
|RL_DevenvExe_2002|2|SOFTWARE\Microsoft\VisualStudio\7.0\Setup\VS|EnvironmentPath|2|
|RL_DevenvExe_2003|2|SOFTWARE\Microsoft\VisualStudio\7.1\Setup\VS|EnvironmentPath|2|
|RL_DevenvExe_2005|2|SOFTWARE\Microsoft\VisualStudio\8.0\Setup\VS|EnvironmentPath|2|
|RL_DevenvExe_2008|2|SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS|EnvironmentPath|2|

### <a name="appsearch-table-rows-for-corresponding-reglocator-table-rows"></a>해당 RegLocator 테이블 행에 대 한 AppSearch 테이블 행

|속성|서명|
|--------------|-----------------|
|DEVENV_EXE_2002|RL_DevenvExe_2002|
|DEVENV_EXE_2003|RL_DevenvExe_2003|
|DEVENV_EXE_2005|RL_DevenvExe_2005|
|DEVENV_EXE_2008|RL_DevenvExe_2008|

 Visual Studio 설치 관리자에서 레지스트리 값을 작성 하는 예를 들어 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS\EnvironmentPath** 으로 *C:\VS2008\Common7\IDE\devenv.exe*, 설치 관리자를 실행 해야 하는 실행 파일 경로 완료 합니다.

> [!NOTE]
> RegLocator 테이블의 유형 열이 2 이면 되므로 서명 테이블에 추가적인 버전 정보를 지정할 필요가 없습니다.

## <a name="run-devenvexe"></a>Devenv.exe를 실행 합니다.
 설치 관리자에서 실행 되는 표준 작업 AppSearch, 후 각 AppSearch 표에 속성이 가리키는 값을 *devenv.exe* 해당 버전의 Visual Studio에 대 한 파일입니다. 있는 경우 지정 된 레지스트리 값-해당 버전의 Visual Studio에 설치 되어 있지 않으므로-지정 된 속성은 null로 합니다.

 사용자 지정 작업을 통해 속성을 가리키는 실행 파일을 실행 하는 Windows Installer 지원 50을 입력 합니다. 사용자 지정 작업 스크립트의 실행 옵션을 포함 해야 `msidbCustomActionTypeInScript` (1024) 및 `msidbCustomActionTypeCommit` VSPackage에 통합 하기 전에 성공적으로 설치 되었는지 확인 하려면 (512), [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]합니다. 자세한 내용은 [CustomAction 테이블](https://docs.microsoft.com/windows/desktop/msi/customaction-table) 하 고 [사용자 지정 작업 스크립트의 실행 옵션](https://docs.microsoft.com/windows/desktop/msi/custom-action-in-script-execution-options)합니다.

 50 형식의 사용자 지정 동작 실행 파일의 원본 열 및 대상 열에 명령줄 인수를 값으로 포함 된 속성을 지정 합니다.

### <a name="customaction-table-rows-to-run-devenvexe"></a>Devenv.exe를 실행 하려면 CustomAction 테이블 행

|작업|형식|Source|대상|
|------------|----------|------------|------------|
|CA_RunDevenv2002|1586|DEVENV_EXE_2002|/setup|
|CA_RunDevenv2003|1586|DEVENV_EXE_2003|/setup|
|CA_RunDevenv2005|1586|DEVENV_EXE_2005|/setup|
|CA_RunDevenv2008|1586|DEVENV_EXE_2008|/setup|

 사용자 지정 동작 설치 하는 동안 실행 하도록 일정을 잡는 InstallExecuteSequence 테이블에 작성 해야 합니다. 조건 열의 각 행의 해당 속성을 사용 하 여는 경우 실행 되지 않도록 사용자 지정 작업을 방지 하기 위해 버전 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 시스템에 설치 되지 않은 합니다.

> [!NOTE]
> Null 값 속성으로 계산 `False` 조건에 사용 되는 경우.

 각 사용자 지정 작업에 대 한 시퀀스 열의 값에 Windows Installer 패키지의 다른 시퀀스 값에 따라 달라 집니다. 시퀀스 값 이어야 합니다 되도록 합니다 *devenv.exe* 와 InstallFinalize 표준 작업 직전 최대한 가깝게 사용자 지정 작업으로 실행 합니다.

### <a name="installexecutesequence-table-to-schedule-the-devenvexe-custom-actions"></a>Devenv.exe 사용자 지정 동작을 예약 하려면 InstallExecuteSequence 테이블

|작업|조건|Sequence|
|------------|---------------|--------------|
|CA_RunDevenv2002|DEVENV_EXE_2002|6602|
|CA_RunDevenv2003|DEVENV_EXE_2003|6603|
|CA_RunDevenv2005|DEVENV_EXE_2005|6605|
|CA_RunDevenv2008|DEVENV_EXE_2008|6608|

## <a name="see-also"></a>참고자료
- [Windows Installer를 사용 하 여 Vspackage 설치](../../extensibility/internals/installing-vspackages-with-windows-installer.md)