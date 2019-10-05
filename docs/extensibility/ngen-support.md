---
title: VSIX v3의 Ngen 지원 | Microsoft Docs
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 1472e884-c74e-4c23-9d4a-6d8bdcac043b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 24f1b0a26875bbbf8dfc4ac7db1049f7309d9aa2
ms.sourcegitcommit: 748d9cd7328a30f8c80ce42198a94a4b5e869f26
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67891113"
---
# <a name="ngen-support-in-vsix-v3"></a>VSIX v3의 Ngen 지원

새 VSIX v3 및 Visual Studio 2017 (버전 3) 확장 매니페스트 형식, 확장 개발자 수 이제 "ngen" 설치 시 해당 어셈블리입니다.

다음은 어떤 "ngen"에 대해 설명 하는 MSDN에서 발췌 한 내용이입니다.

>네이티브 이미지 생성기 (*Ngen.exe*)는 관리 되는 응용 프로그램의 성능을 향상 시키는 도구입니다. *Ngen.exe* 컴파일된 프로세서별 컴퓨터 코드가 포함 된 파일이 로컬 컴퓨터의 네이티브 이미지 캐시에 설치 되며 네이티브 이미지를 만듭니다. 런타임은 JIT(Just-In-Time) 컴파일러를 사용하지 않고 캐시의 네이티브 이미지를 사용하여 원본 어셈블리를 컴파일할 수 있습니다.
>
>[Ngen.exe (네이티브 이미지 생성기)](/dotnet/framework/tools/ngen-exe-native-image-generator)

어셈블리 "ngen" 순서로 VSIX "인스턴스별 컴퓨터별" 설치 되어야 합니다. "모든 사용자" 확인란을 선택 하 여 사용 하도록 설정할 수 있습니다이 `extension.vsixmanifest` 디자이너:

![모든 사용자를 확인 합니다.](media/check-all-users.png)

## <a name="how-to-enable-ngen"></a>Ngen을 사용 하는 방법

에 어셈블리를 ngen을 사용 하려면 사용할 수 있습니다 합니다 **속성** Visual Studio의 창.

설정할 수 있는 속성 4 가지가 있습니다.

1. **Ngen** (부울)-Visual Studio 설치 관리자를 true 인 경우 "ngen" 어셈블리를 됩니다.
2. **Ngen 응용 프로그램** Ngen는 응용 프로그램을 사용 하는 기회를 제공 (string)- *app.config* 어셈블리 종속성을 해결 하기 위해 파일입니다. 이 값에 설정할 응용 프로그램입니다 *app.config* (기준으로 Visual Studio 설치 디렉터리)를 사용 하려고 합니다.
3. **Ngen 아키텍처** (enum)-아키텍처를 기본적으로 어셈블리를 컴파일합니다. 옵션은:를 합니다. NotSpecified b입니다. X86 c입니다. X64 d입니다. 모두
4. **Ngen 우선 순위** (1과 3 사이의 정수)-The Ngen 우선 순위 수준에 설명 되어 있습니다 [Ngen.exe 우선 순위 수준을](/dotnet/framework/tools/ngen-exe-native-image-generator#priority-levels)합니다.

살펴보겠습니다 합니다 **속성** 작업에서 창:

![ngen 속성](media/ngen-in-properties.png)

이 VSIX 프로젝트 내에서 프로젝트 참조 메타 데이터를 추가 합니다 *.csproj* 파일:

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
    <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
    <Name>ClassLibrary1</Name>
    <Ngen>True</Ngen>
    <NgenApplication>vsn.exe</NgenApplication>
    <NgenArchitecture>X86</NgenArchitecture>
    <NgenPriority>2</NgenPriority>
</ProjectReference>
```

> [!NOTE]
> 원하는 경우.csproj 파일을 직접 편집할 수 있습니다.

## <a name="extra-information"></a>추가 정보

디자이너 속성 변경 내용을 이상의 프로젝트 참조에 적용 프로젝트에도 내부 항목에 대 한 Ngen 메타 데이터를 설정할 수 있습니다 (사용 하 여 위에서 설명한 동일한 메서드) 만큼 항목은.NET 어셈블리.