---
title: Visual Studio 제거
titleSuffix: ''
description: 컴퓨터에서 Visual Studio를 완전히 제거하는 방법을 단계별로 알아봅니다.
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- uninstall
- uninstall Visual Studio
- remove
- remove Visual Studio
- cleanup
- cleanup Visual Studio
- clean up
- clean up Visual Studio
ms.assetid: 9c81a777-9c95-4934-b517-c60c6dc78799
author: heaths
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: e363065d96169660817a548fb97d39f09cf679c9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62810392"
---
# <a name="remove-visual-studio"></a>Visual Studio 제거

치명적인 오류가 발생하여 Visual Studio를 복구 또는 제거할 수 없는 경우 `InstallCleanup.exe` 도구를 실행하여 설치된 모든 Visual Studio 2017 또는 Visual Studio 2019 인스턴스에 대한 설치 파일 및 제품 정보를 제거할 수 있습니다. 이 도구는 복구 또는 제거가 실패할 경우에만 마지막 수단으로 실행해야 하며 복구해야 할 수도 있는 다른 Visual Studio 설치 또는 기타 제품에서 기능을 제거할 수 있습니다.

다음 지침에서는 다음과 같은 동작을 통해 다른 명령줄 스위치로 도구를 실행할 수 있습니다.

| 스위치 | 동작 |
| ------ | -------- |
| `-i`   | 이 스위치는 전달된 다른 스위치가 없을 경우 기본값이며 기본 설치 디렉터리 및 제품 정보만 제거합니다. 이 동작은 `InstallCleanup.exe` 도구를 실행한 후 동일한 버전을 다시 설치하려는 경우 사용하는 것이 좋습니다. |
| `-f`   | 이 스위치를 지정하면 기본 설치 디렉터리, 제품 정보는 물론, 다른 Visual Studio 설치 또는 기타 제품과 공유할 수 있는 설치 디렉터리 외부에 설치된 대부분 기타 기능이 제거됩니다. 이 동작은 나중에 다시 설치하지 않고 Visual Studio를 제거하려는 경우에 사용하는 것이 좋습니다. |

1. Visual Studio 설치 관리자를 닫습니다.
2. 관리자 명령 프롬프트를 엽니다. 관리자 명령 프롬프트를 열려면 다음 단계를 따릅니다.
   * "검색하려면 여기에 입력" 상자에 **cmd**를 입력합니다.
   * **명령 프롬프트**를 마우스 오른쪽 단추로 클릭하고 **관리자 권한으로 실행**을 클릭합니다.
3. `InstallCleanup.exe` 유틸리티의 전체 경로를 입력하고 원하는 명령줄 스위치를 전달합니다. 기본적으로 유틸리티 경로는 다음과 같습니다.

   ```
   C:\Program Files (x86)\Microsoft Visual Studio\Installer\resources\app\layout\InstallCleanup.exe
   ```

Visual Studio 설치 관리자 디렉터리에서 항상 `%ProgramFiles(x86)%\Microsoft Visual Studio`에 있는 `InstallCleanup.exe`을 찾지 못한 경우 지침에 따라 [Visual Studio를 설치](install-visual-studio.md)하고 워크로드 선택 화면이 표시되면 창을 닫고 이전 단계를 다시 따릅니다.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>참고 항목

* [Visual Studio 설치](install-visual-studio.md)
* [Visual Studio 업데이트](update-visual-studio.md)
* [Visual Studio 수정](modify-visual-studio.md)
* [Visual Studio 제거](uninstall-visual-studio.md)
