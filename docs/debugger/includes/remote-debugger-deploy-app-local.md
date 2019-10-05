---
title: 로컬 폴더에 배포
description: 로컬 폴더에 앱 배포
services: ''
author: mikejo5000
ms.service: ''
ms.topic: include
ms.date: 05/23/2018
ms.author: mikejo
ms.custom: include file
ms.openlocfilehash: 3fa0569739ee81ec4b2aa0eec8157068ffc949cd
ms.sourcegitcommit: 748d9cd7328a30f8c80ce42198a94a4b5e869f26
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68149215"
---
1. 에 **솔루션 탐색기**, 프로젝트 노드를 마우스 오른쪽 단추로 **게시** (Web Forms에 대 한 **웹 앱 게시**).

    게시 프로필을 이전에 구성한 경우 **게시** 창이 나타납니다. 클릭 **새 프로필**합니다.

1. 에 **게시** 대화 상자에서 **폴더**, 클릭 **찾아보기**, 새 폴더를 만들고 **C:\Publish**합니다.

    ![RemoteDBG_Publish_Local](../media/remotedbg_publish_local.png "RemoteDBG_Publish_Local")

    Web Forms 앱의 경우 선택 **사용자 지정** 게시 대화 상자에서 프로필 이름을 입력 하 고 선택 **확인**합니다.

1. 클릭 **프로필 만들기** 드롭 다운 목록에서 (**게시** 기본값).

1. 에 **게시** 대화 상자에서 클릭을 **설정** 링크를 선택한 후는 **설정** 탭.

1. 구성을 설정 **디버그**를 선택 **게시 하기 전에 모든 기존 파일 삭제**를 클릭 하 고 **저장**합니다.

    > [!NOTE]
    > 릴리스 빌드를 사용 하면 게시할 때 web.config 파일에서 디버깅 비활성화할 수 있습니다.

1. **게시**를 클릭합니다.

    ![RemoteDBG_Publish_Debug_Config](../media/remotedbg_publish_debug_config.png "RemoteDBG_Publish_Debug_Config")

    응용 프로그램 게시를 **디버그** 로컬 폴더에 프로젝트의 구성 합니다. 출력 창에 진행률 보여 줍니다.

1. ASP.NET 앱에 대해 구성 된 로컬 디렉터리에 Visual Studio 컴퓨터에서 ASP.NET 프로젝트 디렉터리를 복사 (이 예제의 **C:\Publish**) Windows Server 컴퓨터. 이 자습서에서는 수동으로 복사 하는 PowerShell, Xcopy 또는 Robocopy와 같은 다른 도구를 사용할 수 있지만 가정 합니다.

    > [!CAUTION]
    > 코드를 다시 빌드를 변경 하는 경우에 다시 게시 하 고이 단계를 반복 해야 합니다. 원격 컴퓨터에 복사한 실행 파일은 로컬 소스 및 기호와 정확히 일치해야 합니다.    받게이 수행 되지 않으면를 `cannot find or open the PDB file` 프로세스를 디버깅 하려고 할 때 Visual Studio에서 경고 합니다.

1. Windows Server에서 실행할 수 있는지 앱 올바르게 브라우저에서 앱을 열어서를 확인 합니다.

    앱은 제대로 실행 되지 않는, 서버 및 Visual Studio 컴퓨터에 설치 하는 ASP.NET의 버전 간에 일치 하지 않을 아니면 IIS 또는 웹 사이트 구성을 사용 하 여 문제가 될 수 있습니다. 이전 단계를 다시 확인 합니다.
