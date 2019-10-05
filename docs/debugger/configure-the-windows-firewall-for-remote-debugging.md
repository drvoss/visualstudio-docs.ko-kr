---
title: 원격 디버깅용 Windows 방화벽 구성 | Microsoft Docs
ms.date: 10/31/2018
ms.topic: conceptual
ms.assetid: 66e3230a-d195-4473-bbce-8ca198516014
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ff64735e1711a18bd7c55c6e052fa8579bd12e16
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62563723"
---
# <a name="configure-windows-firewall-for-remote-debugging"></a>원격 디버깅용 Windows 방화벽을 구성 합니다.

Windows 방화벽에 의해 보호 되는 네트워크, 원격 디버깅을 허용 하도록 방화벽 구성 해야 합니다. Visual Studio 및 원격 디버깅 도구를 설치 또는 시작 하는 동안 올바른 방화벽 포트 열기를 시도 하지만 포트를 열거나 수동으로 앱을 허용 하도록 할 수도 있습니다.

이 항목에서는 Windows 10, 8/8.1 및 7의 원격 디버깅을 사용 하도록 Windows 방화벽을 구성 하는 방법 설명 및 Windows Server 2012 R2, 2012 및 2008 R2 컴퓨터. Visual Studio와 원격 컴퓨터를 동일한 운영 체제를 실행 하 고 필요가 없습니다. 예를 들어 Visual Studio 컴퓨터는 Windows 10을 실행하고 원격 컴퓨터는 Windows Server 2012 R2를 실행할 수 있습니다.

>[!NOTE]
>다른 운영 체제에 이전 버전의 Windows에 대 한 Windows 방화벽을 구성 하는 것에 대 한 지침을 약간 다릅니다. word를 사용 하 여 Windows 8/8.1, Windows 10 및 Windows Server 2012 설정을 *앱*반면 단어를 사용 하 여 Windows 7 및 Windows Server 2008 *프로그램*합니다.

## <a name="configure-ports-for-remote-debugging"></a>원격 디버깅에 대 한 포트 구성

Visual Studio와 원격 디버거 설치 또는 시작 중 올바른 포트를 열어 보십시오. 그러나 타사 방화벽 등의 일부 시나리오에서 수동으로 포트를 열려면 해야 할 수 있습니다.

**포트를 열려면:**

1. Windows에서 **시작** 메뉴, 검색 및 열기 **Windows Firewall with Advanced Security**합니다. Windows 10에서 이것이 **고급 보안이 포함 된 Windows Defender 방화벽**합니다.

1. 새 수신 포트를 선택 **인바운드 규칙** 선택한 후 **새 규칙**합니다. 나가는 규칙을 선택 **아웃 바운드 규칙** 대신 합니다.

1. 에 **새 인바운드 규칙 마법사**를 선택 **포트**를 선택한 후 **다음**합니다.

1. 선택 **TCP** 하거나 **UDP**다음 테이블에서 포트 번호에 따라 합니다.

1. 아래 **특정 로컬 포트**, 다음 테이블에서 포트 번호를 입력 하 고 선택 **다음**합니다.

1. 선택 **연결 허용**를 선택한 후 **다음**합니다.

1. 원격 연결의 경우 네트워크 유형 등을 사용 하려면 하나 이상의 네트워크 종류를 선택 하 고 선택한 **다음**합니다.

1. 규칙에 대 한 이름을 추가 (예를 들어 **msvsmon**를 **IIS**, 또는 **웹 배포**)를 선택한 후 **마침**합니다.

   새 규칙 표시 되어야 하 고 선택 합니다 **인바운드 규칙** 또는 **아웃 바운드 규칙** 목록입니다.

### <a name="ports-on-the-remote-computer-that-enable-remote-debugging"></a>원격 디버깅을 사용할 수 있도록 하는 원격 컴퓨터의 포트

원격 디버깅을 위해 다음 포트를 원격 컴퓨터에서 열어야 합니다.

::: moniker range="vs-2017"

|**포트**|**들어오는/나가는 포트**|**프로토콜**|**설명**|
|-|-|-|-|
|4022|들어오는|TCP|VS 2017에 사용됩니다. Visual Studio 버전 마다 2 씩 포트 번호가 높으면 합니다. 자세한 내용은 [Visual Studio 원격 디버거 포트 할당](../debugger/remote-debugger-port-assignments.md)을 참조하세요.|
|4023|들어오는|TCP|VS 2017에 사용됩니다. Visual Studio 버전 마다 2 씩 포트 번호가 높으면 합니다. 이 포트는 원격으로 사용 되는 디버그 원격 디버거의 64 비트 버전에서 32 비트 프로세스입니다. 자세한 내용은 [Visual Studio 원격 디버거 포트 할당](../debugger/remote-debugger-port-assignments.md)을 참조하세요.|
|3702|나가는 포트|UDP|(선택 사항) 원격 디버거 검색에 필요합니다.|

::: moniker-end

::: moniker range=">= vs-2019"

|**포트**|**들어오는/나가는 포트**|**프로토콜**|**설명**|
|-|-|-|-|
|4024|들어오는|TCP|VS 2019에 사용됩니다. Visual Studio 버전 마다 2 씩 포트 번호가 높으면 합니다. 자세한 내용은 [Visual Studio 원격 디버거 포트 할당](../debugger/remote-debugger-port-assignments.md)을 참조하세요.|
|4025|들어오는|TCP|VS 2019에 사용됩니다. Visual Studio 버전 마다 2 씩 포트 번호가 높으면 합니다. 이 포트는 원격으로 사용 되는 디버그 원격 디버거의 64 비트 버전에서 32 비트 프로세스입니다. 자세한 내용은 [Visual Studio 원격 디버거 포트 할당](../debugger/remote-debugger-port-assignments.md)을 참조하세요.|
|3702|나가는 포트|UDP|(선택 사항) 원격 디버거 검색에 필요합니다.|

::: moniker-end

선택 하는 경우 **사용 하 여 관리 되는 호환성 모드** 아래에서 **도구** > **옵션** > **디버깅**, 열기 이러한 추가 원격 디버거 포트입니다. 디버거 관리 되는 호환성 모드에는 Visual Studio 2010 버전의 디버거를 레거시 수 있습니다.

|**포트**|**들어오는/나가는 포트**|**프로토콜**|**설명**|
|-|-|-|-|
|135, 139, 445|나가는 포트|TCP|필수.|
|137, 138|나가는 포트|UDP|필수 요소.|

도메인 정책에 따라 IPSec을 통해 수행할 네트워크 통신에 필요한 경우 Visual Studio와 원격 컴퓨터에서 추가 포트를 열어야 합니다. 원격 IIS 웹 서버를 디버깅 하려면 원격 컴퓨터에서 포트 80을 엽니다.

|**포트**|**들어오는/나가는 포트**|**프로토콜**|**설명**|
|-|-|-|-|
|500, 4500|나가는 포트|UDP|도메인 정책에 따라 IPSec을 통해 네트워크 통신을 수행해야 하는 경우에 필요합니다.|
|80|나가는 포트|TCP|웹 서버 디버깅에 필요합니다.|

Windows 방화벽을 통해 특정 앱을 허용 하려면 참조 [Windows 방화벽을 통해 원격 디버깅 구성](#configure-remote-debugging-through-windows-firewall)합니다.

## <a name="configure-remote-debugging-through-windows-firewall"></a>Windows 방화벽을 통해 원격 디버깅 구성

원격 컴퓨터의 원격 디버깅 도구를 설치 하거나 공유 폴더에서 실행할 수 있습니다. 두 경우 모두 원격 컴퓨터 방화벽을 올바르게 구성 되어야 합니다.

원격 컴퓨터에 원격 디버깅 도구에서:

*\<Visual Studio 설치 디렉터리\>\\Common7\\IDE\\원격 디버거\\\<x86*하십시오 *x64*, 또는  *Appx*\>

### <a name="allow-and-configure-the-remote-debugger-through-windows-firewall"></a>허용 및 Windows 방화벽을 통해 원격 디버거 구성

1. Windows에서 **시작** 메뉴, 검색 및 열기 **Windows 방화벽**, 또는 **Windows Defender 방화벽**합니다.

1. 선택 **앱을 Windows 방화벽을 통해**합니다.

1. 하는 경우 **원격 디버거** 또는 **Visual Studio 원격 디버거** 아래에 표시 하지 않습니다 **허용 된 앱 및 기능**선택, **설정을변경할**를 선택한 후 **다른 앱 허용**합니다.

1. 여전히 원격 디버거 응용 프로그램에 나열 되지 않은 경우는 **앱 추가** 대화 상자에서 **찾아보기**, 이동할  *\<Visual Studio 설치 디렉터리\> \\Common7\\IDE\\원격 디버거\\\<x86*하십시오 *x64*, 또는 *Appx* \> 를 앱에 대 한 적절 한 아키텍처에 따라 합니다. 선택 *msvsmon.exe*를 선택한 후 **추가**합니다.

1. 에 **앱** 목록에서 합니다 **원격 디버거** 방금 추가한 합니다. 선택 **네트워크 형식과**, 한 다음 원격 연결에 대 한 네트워크 종류를 포함 하 여 하나 이상의 네트워크 형식을 선택 합니다.

1. 선택 **추가**를 선택한 후 **확인**합니다.

## <a name="troubleshooting"></a>원격 디버깅 연결 문제 해결

원격 디버거를 사용 하 여 앱에 연결할 수 없습니다, 있는지 확인 원격 디버깅 방화벽 포트, 프로토콜 및 네트워크 형식과 앱 설정을 모두 올바른지 확인 합니다.

- Windows에서 **시작** 메뉴, 검색 및 열기 **Windows 방화벽**를 선택한 **앱을 Windows 방화벽을 통해**합니다. 했는지 **원격 디버거** 또는 **Visual Studio 원격 디버거** 에 표시 되는 **허용 된 앱 및 기능** 올바른 네트워크 형식과 선택한 확인란을 사용 하 여 목록 선택 합니다. 그러지 않으면 [올바른 앱 및 설정을 추가](#configure-remote-debugging-through-windows-firewall)합니다.

- 에 Windows **시작** 메뉴, 검색 및 열기 **Windows Firewall with Advanced Security**합니다. 했는지 **원격 디버거** 하거나 **Visual Studio 원격 디버거** 아래에 나타납니다 **인바운드 규칙** (및 필요에 따라 **아웃 바운드 규칙**) 녹색 확인 표시 아이콘, 및를 사용 하 여 모든 설정이 올바릅니다.

  - 을 확인 하거나 규칙 설정을 변경 하려면 마우스 오른쪽 단추로 클릭 합니다 **원격 디버거** 앱 목록에 선택 **속성**합니다. 사용 된 **속성** 탭을 사용 하도록 설정 또는 규칙을 사용 하지 않도록 설정 하거나 변경 하려면 포트 번호, 프로토콜 또는 네트워크 형식입니다.
  - 원격 디버거 앱 규칙 목록에 나타나지 않는 경우 [추가 하 고 올바른 포트를 구성](#configure-ports-for-remote-debugging)합니다.

## <a name="see-also"></a>참고자료

- [원격 디버깅](../debugger/remote-debugging.md)
- [Visual Studio 원격 디버거 포트 할당](../debugger/remote-debugger-port-assignments.md)
