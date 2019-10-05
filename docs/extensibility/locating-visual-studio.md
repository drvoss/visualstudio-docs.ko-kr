---
title: Visual Studio 찾기 | Microsoft Docs
ms.date: 08/21/2017
ms.topic: conceptual
helpviewer_keywords:
- deployment, VSIX
ms.assetid: 680c3b25-7901-4768-8363-6d1fcd1ea636
ms.author: heaths
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a7187fbcc3e3aca990846176676a47f5d17aaf00
ms.sourcegitcommit: 62f42113ae4dae1ddfff1c4e02445acc09913445
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/29/2019
ms.locfileid: "64878152"
---
# <a name="locate-visual-studio"></a>Visual Studio를 찾습니다

Visual Studio 2017부터 동일한 버전 또는 심지어 버전의 여러 인스턴스를 설치할 수 있습니다. 이전 설치를 유지 하면서 기본 개발 컴퓨터에 새 기능을 미리 볼 때 유용 합니다. 이러한 변경으로 인해 단일 환경 변수 또는 레지스트리 값 인스턴스를 찾는 데 사용할 수 있습니다. 대신 사용할 수 있습니다는 [COM 쿼리 API](https://msdn.microsoft.com/library/microsoft.visualstudio.setup.configuration.aspx) 확장 프로그램 관련 조건에 따라 인스턴스를 찾으려고 합니다.

이 네이티브 및 관리 코드에 사용할 수 있는 NuGet 패키지를 사용 하 여 신속 하 고 읽기 전용 API입니다.

| 코드 | Package |
| ---- | --- |
| 네이티브 | https://nuget.org/packages/Microsoft.VisualStudio.Setup.Configuration.Native |
| 관리 | https://nuget.org/packages/Microsoft.VisualStudio.Setup.Configuration.Interop |

지정 된 경로 또는 현재 프로세스를 단일 인스턴스를 찾을 수도 있고 모든 인스턴스를 열거할 수 있습니다. 참조 [샘플](https://github.com/Microsoft/vs-setup-samples) Visual Studio를 찾는 방법의 전체 예제입니다.

## <a name="tools"></a>도구

빌드 환경, PowerShell 스크립트, 설치 관리자 및 더 많은 시나리오에서 Visual Studio 및 기타 도구를 찾으려면, 다양 한 오픈 소스 도구를 직접 사용 하거나 사용자 고유의 스크립트와 함께 재배포할 수 있습니다.

| 프로젝트 | 설명 |
| ------- | ----------- |
| [vswhere](https://github.com/Microsoft/vswhere) | 단일 파일 릴리스 또는 시험판, 등 어떤 제품이 설치 되어 있는 작업을 설치 하는 조건을 충족 하는 인스턴스를 찾을 수 네이티브 실행 파일입니다. 적은 정보를 반환 하는 Visual Studio 2017에 대 한 이상 하지만 2010 이상 Visual Studio를 찾기도 지원 합니다. 참조 된 [wiki](https://github.com/Microsoft/vswhere/wiki) 예입니다. |
| [VSSetup cmdlet](https://github.com/Microsoft/vssetup.powershell) | 지원 되는 PowerShell cmdlet 동일한 조건에 따라 인스턴스를 찾는 데 사용할 수 있는 개체로 풍부한 정보를 반환 하는 2.0 이상 _vswhere_ 및 인스턴스에 대 한 더 많은 속성을 검색 합니다. 참조 된 [wiki](https://github.com/Microsoft/vssetup.powershell/wiki) 예입니다. |
| [VSIXBootstrapper](https://github.com/Microsoft/vsixbootstrapper) | 자동으로 찾습니다 _VSIXInstaller_ 하 고 설치 하려면 명령줄을 통해 전달 된 **.vsix* 파일입니다. 이 기능은 쿼리 Api에 대 한 직접 지원 되지 않은 설치 관리자에서 유용할 수 있습니다. 참조 된 [wiki](https://github.com/Microsoft/vsixbootstrapper/wiki) 예입니다. |

## <a name="see-also"></a>참고자료

* [Visual Studio 2017 설치 프로그램 변경 내용](https://devblogs.microsoft.com/setup/changes-to-visual-studio-15-setup/)
* [DTE를 사용 하 여 Visual Studio를 시작 합니다.](launch-visual-studio-dte.md)