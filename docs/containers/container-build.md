---
title: Visual Studio Container Tools 빌드 개요
author: ghogen
description: 컨테이너 도구 빌드 프로세스 개요
ms.author: ghogen
ms.date: 06/06/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: edc4674e2468124ecb46b25a1411043ed4b66a2a
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71253109"
---
# <a name="building-containerized-apps-using-visual-studio-or-the-command-line"></a>Visual Studio 또는 명령줄을 사용하여 컨테이너화된 앱 빌드

Visual Studio IDE에서 빌드하거나 명령줄 빌드를 설정하는 경우, Visual Studio 빌드에서 Dockerfile을 사용하여 프로젝트를 빌드하는 방법을 알고 있어야 합니다.  성능상의 이유로, Visual Studio는 컨테이너화된 앱을 위해 특별한 프로세스를 따릅니다. Dockerfile을 수정하여 빌드 프로세스를 사용자 지정하는 경우에는 Visual Studio에서 프로젝트를 빌드하는 방법을 이해하는 것이 특히 중요합니다.

Visual Studio는 Docker 컨테이너를 사용하지 않는 프로젝트를 빌드할 때, 로컬 컴퓨터에서 MSBuild를 호출하고 로컬 솔루션 폴더 아래에 있는 폴더(일반적으로 `bin`)에 출력 파일을 생성합니다. 그러나 컨테이너화된 프로젝트의 경우 빌드 프로세스에서 컨테이너화된 앱 빌드에 대한 Dockerfile의 지침을 고려합니다. Visual Studio에서 사용하는 Dockerfile은 여러 스테이지로 나누어져 있습니다. 이 프로세스는 Docker의 ‘다단계 빌드’ 기능을 사용합니다. 

## <a name="multistage-build"></a>다단계 빌드

다단계 빌드 기능을 사용하면 컨테이너 빌드 프로세스를 보다 효율적으로 수행할 수 있으며, 앱이 런타임에 필요로 하는 비트만 포함하여 컨테이너를 더 작게 만들 수 있습니다. 다단계 빌드는 .NET Framework 프로젝트가 아닌 .NET Core 프로젝트에 사용됩니다.

다단계 빌드를 사용하면 중간 이미지를 생성하는 스테이지에서 컨테이너 이미지를 만들 수 있습니다. 예를 들어 Visual Studio에서 생성되는 일반적인 Dockerfile을 생각해 봅시다. 첫 번째 스테이지는 `base`입니다.

```
FROM mcr.microsoft.com/dotnet/core/aspnet:2.2-stretch-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443
```

Dockerfile의 줄은 Microsoft Container Registry(mcr.microsoft.com)의 Nanoserver 이미지로 시작하며 포트 80과 443을 공개하는 중간 이미지 `base`를 만든 다음, 작업 디렉터리를 `/app`으로 설정합니다.

다음 스테이지는 `build`이며 다음과 같이 표시됩니다.

```
FROM mcr.microsoft.com/dotnet/core/sdk:2.2-stretch AS build
WORKDIR /src
COPY ["WebApplication43/WebApplication43.csproj", "WebApplication43/"]
RUN dotnet restore "WebApplication43/WebApplication43.csproj"
COPY . .
WORKDIR "/src/WebApplication43"
RUN dotnet build "WebApplication43.csproj" -c Release -o /app
```

`build` 스테이지는 base에서 계속되는 것이 아니라 레지스트리의 다른 원본 이미지(`aspnet` 대신 `sdk`)에서 시작되는 것을 확인할 수 있습니다.  `sdk` 이미지에는 모든 빌드 도구가 포함되어 있으므로, 런타임 구성 요소만 포함하는 aspnet 이미지보다 훨씬 더 큽니다. Dockerfile의 나머지 부분을 살펴보면 개별 이미지를 사용해야 하는 이유가 명확해집니다.

```
FROM build AS publish
RUN dotnet publish "WebApplication43.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "WebApplication43.dll"]
```

최종 스테이지는 다시 `base`에서 시작되며, 게시된 출력을 최종 이미지에 복사하는 `COPY --from=publish`를 포함합니다. 이 프로세스를 사용하면 `sdk` 이미지에 있던 모든 빌드 도구를 포함할 필요가 없으므로 최종 이미지가 훨씬 더 작아질 수 있습니다.

## <a name="faster-builds-for-the-debug-configuration"></a>디버그 구성의 빌드 속도 향상

Visual Studio에서 컨테이너화된 프로젝트에 대한 빌드 프로세스의 성능 향상을 지원하는 여러 가지 최적화 기능이 있습니다. F5 키를 눌러 디버깅을 시작하면 이전에 빌드한 이미지가 재사용됩니다(가능한 경우). 이전 컨테이너를 재사용하지 않으려는 경우, Visual Studio의 **다시 빌드** 또는 **정리** 명령을 사용하여 Visual Studio에서 새 컨테이너를 사용하도록 강제로 적용할 수 있습니다.

또한 성능 향상을 위해 컨테이너화된 앱의 빌드 프로세스는 Dockerfile에 설명된 단계만큼 간단하게 진행되지 않습니다. 컨테이너에서 빌드하는 경우 로컬 컴퓨터에서 빌드하는 것보다 훨씬 더 느립니다.  따라서 **디버그** 구성으로 빌드하는 경우, Visual Studio는 실제로 로컬 컴퓨터에서 프로젝트를 빌드한 다음, 볼륨 탑재를 사용하여 출력 폴더를 컨테이너에 공유합니다. 이 최적화 기능을 사용하는 빌드를 ‘고속’ 모드 빌드라고 합니다. 

**고속** 모드에서 Visual Studio는 `base` 스테이지만 빌드하도록 Docker에 지시하는 인수를 사용하여 `docker build`를 호출합니다.  Visual Studio는 Dockerfile의 내용에 관계없이 프로세스의 나머지 부분을 처리합니다. 따라서 컨테이너 환경을 사용자 지정하거나 추가 종속성을 설치하기 위해 Dockerfile을 수정하는 경우, 수정 내용을 첫 번째 스테이지에 배치해야 합니다.  Dockerfile의 `build`, `publish` 또는 `final` 스테이지에 배치된 사용자 지정 단계는 모두 실행되지 않습니다.

이 성능 최적화 기능은 **디버그** 구성으로 빌드하는 경우에만 수행됩니다. **릴리스** 구성에서는 Dockerfile에 지정된 대로 컨테이너에서 빌드가 수행됩니다.

성능 최적화 기능을 사용하지 않고 Dockerfile에 지정된 대로 빌드하려면, 프로젝트 파일에서 다음과 같이 **ContainerDevelopmentMode** 속성을 **Regular**로 설정합니다.

```xml
<PropertyGroup>
   <ContainerDevelopmentMode>Regular</ContainerDevelopmentMode>
</PropertyGroup>
```

성능 최적화 기능을 복원하려면 프로젝트 파일에서 해당 속성을 제거합니다.

## <a name="building-from-the-command-line"></a>명령줄에서 빌드

`docker build` 또는 `MSBuild`를 사용하여 명령줄에서 빌드할 수 있습니다.

### <a name="docker-build"></a>docker build

명령줄에서 컨테이너화된 솔루션을 빌드하려는 경우, 일반적으로 솔루션의 각 프로젝트에 대해 `docker build <context>` 명령을 사용할 수 있습니다. ‘빌드컨텍스트’ 인수를 제공합니다.  Dockerfile의 ‘빌드 컨텍스트’는 이미지를 생성하기 위한 작업 폴더로 사용되는 로컬 컴퓨터의 폴더입니다.  예를 들어 컨테이너에 복사할 때, 복사할 파일이 들어 있는 폴더입니다.  .NET Core 프로젝트에서는 솔루션 파일(.sln)이 포함된 폴더를 사용합니다.  이 인수는 상대 경로로 표시되며, 일반적으로 프로젝트 폴더의 Dockerfile과 부모 폴더의 솔루션 파일은 “..”으로 지정됩니다.  .NET Framework 프로젝트의 빌드 컨텍스트는 솔루션 폴더가 아닌 프로젝트 폴더입니다.

```cmd
docker build -f Dockerfile ..
```

### <a name="msbuild"></a>MSBuild

Visual Studio에서 만든 .NET Framework 프로젝트용(및 Visual Studio 2017 업데이트 4 이전의 Visual Studio 버전에서 만든 .NET Core 프로젝트용) Dockerfile은 다단계 Dockerfile이 아닙니다.  해당 Dockerfile의 단계에서는 코드를 컴파일하지 않습니다.  대신, Visual Studio에서 .NET Framework Dockerfile을 빌드할 때 먼저 MSBuild를 사용하여 프로젝트를 컴파일합니다.  작업이 성공하면 Visual Studio에서 Dockerfile을 빌드합니다. 이 프로세스에서는 MSBuild의 빌드 출력을 결과 Docker 이미지에 복사하기만 합니다.  코드를 컴파일하는 단계가 Dockerfile에 포함되지 않기 때문에, 명령줄에서 `docker build`를 사용하여 .NET Framework Dockerfile을 빌드할 수 없습니다. 이러한 프로젝트를 빌드하려면 MSBuild를 사용해야 합니다.

단일 Docker 컨테이너 프로젝트용 이미지를 빌드하려는 경우, `/t:ContainerBuild` 명령 옵션과 함께 MSBuild를 사용할 수 있습니다. 예:

```cmd
MSBuild MyProject.csproj /t:ContainerBuild /p:Configuration=Release
```

Visual Studio IDE에서 솔루션을 빌드할 때 **출력** 창에 표시되는 것과 유사한 출력이 표시됩니다. Visual Studio에서 다단계 빌드 최적화 기능을 사용하는 경우 **디버그** 구성을 빌드할 때 결과가 예상과 다를 수 있으므로 항상 `/p:Configuration=Release`를 사용합니다.

Docker Compose 프로젝트를 사용하는 경우에는 다음 명령을 사용하여 이미지를 빌드합니다.

```cmd
msbuild /p:SolutionPath=<solution-name>.sln /p:Configuration=Release docker-compose.dcproj
```

## <a name="next-steps"></a>다음 단계

프로젝트 파일에서 추가 MSBuild 속성을 설정하여 빌드를 추가로 사용자 지정하는 방법을 알아봅니다. [컨테이너 프로젝트에 대한 MSBuild 속성](container-msbuild-properties.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSBuild](../msbuild/msbuild.md)
[Windows의 Dockerfile](/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
[Windows의 Linux 컨테이너](/virtualization/windowscontainers/deploy-containers/linux-containers)
