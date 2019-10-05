---
title: VSPackage 개발을 위한 Devenv 명령줄 스위치 | Microsoft Docs
ms.date: 12/10/2018
ms.topic: conceptual
helpviewer_keywords:
- /Setup command line switch
- /ResetSkipPkgs command line switch
- /RootSuffix command line switch
- /SafeMode command line switch
- /Splash command line switch
- command-line switches
- registry, Visual Studio SDK
- command line, switches
- Visual Studio SDK, command-line switches
ms.assetid: d65d2c04-dd84-42b0-b956-555b11f5a645
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 289f31c503143dc2b992717483f4d8701414e09d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66348045"
---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>VSPackage 개발을 위한 Devenv 명령줄 스위치

Visual Studio에서는 실행 하는 경우 명령줄에서 작업을 자동화 하는 개발자 `devenv.exe`, Visual Studio IDE를 시작 하는 파일입니다.

 작업은 다음과 같습니다.

- IDE 외부에서 미리 정의 된 구성에서 응용 프로그램을 배포 합니다.

- 자동으로 사전 설정을 사용 하 여 프로젝트 빌드는 빌드 설정 또는 디버그 구성 합니다.

- IDE 외부 모두에서 특정 한 구성에서 IDE를 로드 합니다. 시작할 때 IDE를 사용자 지정할 수도 있습니다.

## <a name="guidelines-for-switches"></a>스위치에 대 한 지침

Visual Studio 설명서 사용자 수준 설명 `devenv` 명령줄 스위치입니다. 자세한 내용은 [Devenv 명령줄 스위치](../ide/reference/devenv-command-line-switches.md)합니다. `devenv` 도구에서는 VSPackage 개발, 배포 및 디버깅을 사용 하 여 유용한 명령줄 스위치를 추가 합니다.

| 명령줄 스위치 | 설명 |
|---------------------| - |
| `/ResetSkipPkgs` | 문제 Vspackage, 로드 되지 않도록 하 고 Visual Studio를 시작 하는 사용자가 추가 된 모든 건너뛰기 로드 옵션을 지웁니다. SkipLoading 태그가 존재 VSPackage 로드 하는 사용 하지 않도록 설정 합니다. 태그를 지우면 VSPackage 로드 하는 다시 사용 하도록 설정 합니다.<br /><br /> 이 스위치는 인수가 필요 없습니다. |
| `/RootSuffix` | 대체 위치를 사용 하 여 Visual Studio를 시작 합니다. Visual Studio SDK 설치 관리자가 만든 바로 가기를에서 다음 명령을 실행 됩니다.<br /><br /> `devenv /RootSuffix exp`<br /><br /> 이 예에서 `exp` 특정 접미사를 사용 하 여 위치를 식별 (예를 들어 `10.0Exp` 대신 `10.0`). 실험적 인스턴스를 사용 하면 코드를 작성 하는 데 사용할 Visual Studio 인스턴스에서 개별적으로 VSPackage를 디버깅할 수 있습니다.<br /><br /> 이 스위치는 VSRegEx.exe를 사용 하 여 만든 위치를 식별 하는 모든 문자열을 사용할 수 있습니다. 자세한 내용은 [의 실험적 인스턴스에서](../extensibility/the-experimental-instance.md)합니다. |
| `/SafeMode` | 기본 IDE 및 서비스를 로드 하는 안전 모드에서 Visual Studio를 시작 합니다. `/SafeMode` 스위치에서 안정적으로 실행 되도록 하는 Visual Studio가 시작 될 때 로드 모든 타사 VSPackages를 방지 합니다.<br /><br /> 이 스위치는 인수가 필요 없습니다. |
| `/Setup` | Visual Studio의 메뉴, 도구 모음 및 모든 사용 가능한 VSPackages에서 명령 그룹을 설명 하는 리소스 메타 데이터 병합을 강제로 수행 합니다. 관리자 권한으로이 명령은 실행할 수 있습니다. <br /><br /> 이 스위치는 인수가 필요 없습니다. `devenv /Setup` 명령은 일반적으로 설치 프로세스의 마지막 단계로 표시됩니다. 사용 된 `/Setup` 스위치는 IDE를 시작 하지 않습니다.|
| `/Splash` | 일반적으로 화면 및 주요 IDE를 표시 하기 전에 메시지를 표시 한 다음 상자 Visual Studio 시작을 표시 합니다. 메시지 상자를 사용 하면 시작 화면 (예: VSPackage 제품 아이콘에 대 한 확인)를 연구 합니다.<br /><br /> 이 스위치는 인수가 필요 없습니다. |

## <a name="see-also"></a>참고자료

- [명령줄 스위치를 추가 합니다.](../extensibility/adding-command-line-switches.md)
- [Devenv 명령줄 스위치](../ide/reference/devenv-command-line-switches.md)