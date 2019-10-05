---
title: Visual Studio 폴더 열기 확장성 개요 | Microsoft Docs
ms.date: 02/21/2018
ms.topic: conceptual
ms.assetid: 94c3f8bf-1de3-40ea-aded-7f40c4b314c7
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 2bb74703f639848d643f536edf620e30b1836310
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62806475"
---
# <a name="open-folder-extensibility"></a>열린 폴더 확장성

합니다 [폴더 열기](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) 기능을 사용 하면 사용자가 열 수 프로젝트 또는 솔루션 파일에 대 한 필요 없이 Visual Studio에서 코드 베이스입니다. 폴더 열기 기능 사용자와 같은 Visual Studio에서 기대를 제공 합니다.

* 솔루션 탐색기 통합 및 검색
* 편집기 색 지정
* 이동 탐색
* 검색 하면 파일에서 찾기

함께 사용 하면 워크 로드 등.NET의 경우 및 C++ 개발, 사용자도 가져오기:

* 다양 한 Intellisense
* 언어별 기능

폴더 열기를 사용 하 여 확장 작성자는 모든 언어에 대 한 다양 한 기능을 만들 수 있습니다. 가지 Api는 사용자의 모든 파일의 코드 베이스에 대 한 빌드, 디버깅 및 기호 검색을 지원 합니다. 현재 extender 백업 프로젝트 또는 솔루션 없이 코드를 이해 하는 기존 Visual Studio 기능을 업데이트할 수 있습니다.

## <a name="an-api-without-project-systems"></a>프로젝트 시스템 없이 API

지금까지 Visual Studio 솔루션 및 프로젝트 시스템을 사용 하 여 해당 프로젝트의 파일만 인식 합니다. 프로젝트 시스템 로드 된 프로젝트의 기능 및 사용자 상호 작용을 담당 합니다. 해당 프로젝트 파일에 프로젝트 콘텐츠를 다른 프로젝트에 대 한 종속성의 시각적 표시 및 수정 기본 프로젝트 파일 이해 합니다. 이러한 계층 및 다른 구성 요소는 사용자를 대신 하 여 작업 수행 하는 기능을 통해 것입니다. 코드 베이스의 모든 프로젝트 및 솔루션 구조에도 표시 됩니다. 스크립팅 언어 및 오픈 소스 코드 작성 된 C++ Linux 용은 좋은 예입니다. 폴더 열기를 사용 하 여 Visual Studio는 사용자가 소스 코드와 상호 작용 하는 새로운 방법을 제공 합니다.

열린 폴더 Api는 아래를 `Microsoft.VisualStudio.Workspace.*` 네임 스페이스 extender 생성 하 고 데이터 또는 열려 있는 폴더 내의 파일 관련 작업을 사용할 수 있게 됩니다. 확장 이러한 Api를 사용 하 여 같은 많은 영역에 대 한 기능을 제공할 수 있습니다.

- [작업 영역](workspaces.md) -작업 영역 및 해당 Api는 폴더 열기의 지점 확장성을 시작 합니다.
- [컨텍스트 및 작업 파일](workspace-file-contexts.md) -파일 컨텍스트를 통해 제공 되는 특정 코드 인텔리전스 파일입니다.
- [인덱싱](workspace-indexing.md) -수집 하 고 폴더 열기 작업 영역에 대 한 데이터를 유지 합니다.
- [언어 서비스](workspace-language-services.md) -폴더 열기 작업 영역에 언어 서비스를 통합 합니다.
- [빌드](workspace-build.md) -빌드 폴더 열기 작업 영역에 대 한 지원.

다음 형식을 사용 하는 기능을 폴더 열기를 지원 하기 위해 새 Api를 도입 해야 합니다.

- `IVsHierarchy`
- `IVsProject`
- `DTE`

## <a name="feedback-comments-issues"></a>피드백, 의견, 문제

폴더 열기 및 `Microsoft.VisualStudio.Workspace.*` Api는 현재 개발 합니다. 예기치 않은 동작이 관심 릴리스의 알려진된 문제를 참조 하십시오. [개발자 커뮤니티](https://developercommunity.visualstudio.com) 투표 하 고 문제를 만들 수 있는 권장 되는 곳입니다. 각 피드백 좋습니다 문제의 자세한 설명을입니다. Visual Studio 버전에 대 한 개발 하는, (구현 했습니다와 상호 작용 하는)를 사용 하는 Api, 예상된 결과 실제 결과 포함 됩니다. 가능 하다 면 devenv.exe 프로세스의 덤프를 포함 합니다. GitHub의 문제에 피드백을 제공 하는 것에 대 한 추적을 사용 하 고 관련 설명서.

## <a name="next-steps"></a>다음 단계

* [작업 영역](workspaces.md) -폴더 열기 작업 영역 API에 알아봅니다.