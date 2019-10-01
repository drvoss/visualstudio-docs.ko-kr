---
title: 컨테이너화된 앱 단위 테스트
author: ghogen
description: Visual Studio에서 Docker 프로젝트의 모든 빌드에 대해 단위 테스트 실행
ms.author: ghogen
ms.date: 06/17/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: ec5aea44362cf82f6745671cc0706f80e01a60ad
ms.sourcegitcommit: 0cd282a7584b9bfd4df7882f8fdf3ad8a270e219
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/28/2019
ms.locfileid: "71125970"
---
# <a name="how-to-run-unit-tests-for-a-containerized-app"></a>방법: 컨테이너화된 앱에 대해 단위 테스트 실행

Dockerfile을 수정하여 컨테이너화된 프로젝트의 모든 빌드에 대해 단위 테스트를 실행할 수 있습니다.

## <a name="prerequisites"></a>전제 조건

- [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) 설치
- [dotnet test](/dotnet/core/tools/dotnet-test)를 사용하여 실행되도록 설정된 단위 테스트
- [컨테이너 창 확장](https://aka.ms/vscontainerspreview) 설치

## <a name="add-unit-tests-to-the-dockerfile"></a>Dockerfile에 단위 테스트 추가

Visual Studio는 Dockerfile을 수정하기 전에 몇 가지 특별한 성능 최적화를 수행합니다. **디버그** 구성을 빌드하는 경우, Visual Studio는 로컬 컴퓨터에서 프로젝트를 빌드하고 그 결과를 컨테이너에 복사합니다. 따라서 다단계 Dockerfile의 첫 번째 스테이지만 Dockerfile에 지정된 대로 실행됩니다. 자세한 내용은 [Visual Studio 컨테이너 도구 빌드 프로세스](container-build.md)를 참조하세요.

다단계 Dockerfile에 단위 테스트를 추가하려면 Dockerfile의 `build` 스테이지와 `publish` 스테이지 사이에 `unit-test` 스테이지를 추가합니다.

```
FROM build AS unit-test
RUN dotnet unit-test --logger:trx
```

Visual Studio는 **디버그** 구성에서 첫 번째 스테이지만 실행하므로, `unit-test` 스테이지는 **릴리스** 구성에서만 실행됩니다. 그러나 **릴리스** 구성에서도 최종 이미지가 `unit-test` 스테이지가 아닌 `base` 스테이지에서 빌드되기 때문에 로그 결과가 최종 이미지에 포함되지 않습니다. 테스트를 실행하고 로그를 볼 수 있는 이미지를 생성하려면 다음 명령을 사용합니다.

```cmd
docker build --target:unit-test
```

## <a name="next-steps"></a>다음 단계

확장이 설치된 경우 [컨테이너 창](view-and-diagnose-containers.md)을 사용하여 테스트 로그를 볼 수 있습니다.  

테스트 로그를 보려면 **Ctrl**+**Q**를 사용하고 **컨테이너**를 검색하여 **컨테이너** 창을 엽니다. **컨테이너** 창에서 컨테이너를 찾아 **파일** 탭을 열고 컨테이너 파일 시스템에서 테스트 결과(.trx) 파일을 찾은 다음, Visual Studio에서 파일을 열어 결과를 확인합니다.

