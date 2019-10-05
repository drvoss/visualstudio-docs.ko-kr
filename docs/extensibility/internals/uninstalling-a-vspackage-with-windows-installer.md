---
title: Windows Installer 사용 하 여 VSPackage 제거 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- packages, uninstalling
- VSPackages, uninstalling
- uninstalling VSPackages
ms.assetid: c4575ac7-82da-4af8-a375-ea756a101fbf
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4ddb09668d3114c055ddac1e4fb677a46754f388
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66344755"
---
# <a name="uninstalling-a-vspackage-with-windows-installer"></a>Windows Installer를 사용하여 VSPackage 제거
대부분의 경우 Windows 설치 관리자를 제거할 수 VSPackage에서 방금 수행한 VSPackage를 설치 하려면 "취소"입니다. 사용자 지정 작업에서 설명한 [명령은 해야 수 실행 한 후 설치](../../extensibility/internals/commands-that-must-be-run-after-installation.md) 도 제거 후 실행 해야 합니다. Devenv.exe 호출 하 여 설치 및 제거에 모두에 대 한 InstallFinalize 표준 작업 바로 전에 발생 하므로 두 경우 모두 CustomAction 및 InstallExecuteSequence 테이블 항목에 제공 합니다.

> [!NOTE]
> 실행 `devenv /setup` MSI 패키지를 제거 합니다.

 일반적으로 Windows Installer 패키지에 사용자 지정 작업을 추가 하는 경우를 처리 해야 해당 작업을 제거 하 고 롤백 중. 예를 들어 자체 VSPackage를 등록 하려면 사용자 지정 작업을 추가 하면 너무 등록을 취소 하려면 사용자 지정 작업을 추가 해야 합니다.

> [!NOTE]
> VSPackage를 설치 하 고 다음의 버전을 제거 하는 사용자 수 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 와 통합 됩니다. VSPackage의 제거에 종속성을 사용 하 여 코드를 실행 하는 사용자 지정 작업을 제거 하 여이 시나리오에서 작동 하는지 확인 하는 것이 도움이 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]합니다.

## <a name="handling-launch-conditions-at-uninstall-time"></a>처리 시작 상태 제거
 LaunchConditions 표준 작업 오류를 표시할 시작 조건 테이블의 행을 읽습니다 조건이 충족 되지 않으면 메시지입니다. 시작 조건을 일반적으로 사용 되었는지 확인 하려면 시스템 요구 사항이 충족 되는 조건을 추가 하 여 시작 조건을 제거 하는 동안 일반적으로 건너뛸 수 있습니다 `NOT Installed`, 시작 조건 표의 LaunchConditions 행입니다.

 대안은 추가할 `OR Installed` 를 제거 하는 동안 중요 하지 않은 상태를 시작 합니다. 그렇게 하면는 조건이 항상 true 제거 하는 동안 되며 시작 조건 오류 메시지가 표시 되지 것입니다.

> [!NOTE]
> `Installed` VSPackage는 시스템에 이미 설치 되어 있는지 검색 하는 경우 설정 하는 Windows Installer 속성이입니다.

## <a name="see-also"></a>참고 항목
- [Windows Installer](https://msdn.microsoft.com/library/187d8965-c79d-4ecb-8689-10930fa8b3b5)
- [시스템 요구 사항 검색](../../extensibility/internals/detecting-system-requirements.md)