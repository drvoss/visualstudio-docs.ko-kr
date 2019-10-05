---
title: 솔루션 (합니다. Sln) 파일
ms.date: 03/15/2019
ms.topic: conceptual
helpviewer_keywords:
- sln files, VSPackages
- solutions, .sln files
- .sln files, VSPackages
ms.assetid: 7d7ef539-2e4b-4637-b853-8ec7626609df
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 30b0e0b09b12dca964958d5d7b35c6b0d83906fa
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322607"
---
# <a name="solution-sln-file"></a>솔루션 (.sln) 파일

솔루션에는 Visual Studio에서 프로젝트를 구성 하는 것에 대 한 구조입니다. 솔루션에 두 개의 파일에는 프로젝트에 대 한 상태 정보를 유지 관리합니다.

- .sln 파일 (텍스트 기반, 공유)

- .suo 파일 (이진, 사용자 고유의 솔루션 옵션)

.Suo 파일에 대 한 자세한 내용은 참조 하세요. [솔루션 사용자 옵션 (합니다. Suo) 파일](../../extensibility/internals/solution-user-options-dot-suo-file.md)합니다.

환경을 호출 하는 VSPackage는.sln 파일에서 참조 하 고 결과로 로드 되 면 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> .sln 파일에서 읽을 수 있습니다.

.Sln 파일을 찾고 지속된 된 데이터 및 참조 하는 Vspackage 프로젝트에 대 한 이름-값 매개 변수를 로드 하는 환경에서 사용 하는 텍스트 기반 정보를 포함 합니다. 사용자가 솔루션을 열면 환경 돌아가면서 선택 합니다는 `preSolution`, `Project`, 및 `postSolution` 솔루션 내 프로젝트는 솔루션을 로드 하려면.sln 파일의 정보 및 솔루션에 연결 된 모든 보관 된 정보입니다.

각 프로젝트의 파일을 해당 프로젝트의 항목을 사용 하 여 계층 구조를 채우는 환경에서 읽은 추가 정보를 포함 합니다. 계층 데이터 지 속성은 프로젝트에 의해 제어 됩니다. 데이터는 일반적으로에 저장 되지.sln 파일을 의도적으로 작성할 수 있지만 프로젝트 정보.sln 파일에 작업을 수행 하려는 경우. 지 속성에 대 한 자세한 내용은 참조 하세요. [프로젝트 지 속성](../../extensibility/internals/project-persistence.md) 하 고 [열기 및 프로젝트 항목 저장](../../extensibility/internals/opening-and-saving-project-items.md)합니다.

## <a name="file-header"></a>파일 헤더

.Sln 파일의 헤더는 다음과 같습니다.

::: moniker range="vs-2017"

```
Microsoft Visual Studio Solution File, Format Version 12.00
# Visual Studio 15
VisualStudioVersion = 15.0.26730.15
MinimumVisualStudioVersion = 10.0.40219.1
```

### <a name="definitions"></a>정의

`Microsoft Visual Studio Solution File, Format Version 12.00`\
파일 형식 버전을 정의 하는 표준 헤더입니다.

`# Visual Studio 15`\
(가장 최근에)이 솔루션 파일을 저장 하는 Visual Studio의 주 버전입니다. 이 정보는 위의 솔루션 아이콘의 버전 번호를 제어합니다.

`VisualStudioVersion = 15.0.26730.15`\
전체 버전 (가장 최근에) 솔루션 파일을 저장 하는 Visual Studio입니다. 주 버전이 같은 Visual Studio의 최신 버전으로 솔루션 파일에 저장 하면이 값 솔루션 파일의 변동을 줄이려면 하도록 업데이트 되지 않습니다.

`MinimumVisualStudioVersion = 10.0.40219.1`\
이 솔루션 파일을 열 수 있는 Visual Studio의 최소 (가장 오래 된) 버전입니다.

::: moniker-end

::: moniker range=">=vs-2019"

```
Microsoft Visual Studio Solution File, Format Version 12.00
# Visual Studio Version 16
VisualStudioVersion = 16.0.28701.123
MinimumVisualStudioVersion = 10.0.40219.1
```

### <a name="definitions"></a>정의

`Microsoft Visual Studio Solution File, Format Version 12.00`\
파일 형식 버전을 정의 하는 표준 헤더입니다.

`# Visual Studio Version 16`\
(가장 최근에)이 솔루션 파일을 저장 하는 Visual Studio의 주 버전입니다. 이 정보는 위의 솔루션 아이콘의 버전 번호를 제어합니다.

`VisualStudioVersion = 16.0.28701.123`\
전체 버전 (가장 최근에) 솔루션 파일을 저장 하는 Visual Studio입니다. 주 버전이 같은 Visual Studio의 최신 버전으로 솔루션 파일에 저장 하면이 값 파일에서 이탈을 줄이기 위해 하도록 업데이트 되지 않습니다.

`MinimumVisualStudioVersion = 10.0.40219.1`\
이 솔루션 파일을 열 수 있는 Visual Studio의 최소 (가장 오래 된) 버전입니다.

::: moniker-end

## <a name="file-body"></a>파일 본문

.Sln 파일의 본문 레이블이 지정 된 여러 섹션으로 구성 됩니다 `GlobalSection`, 다음과 같이 합니다.

```
Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1", "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"
EndProject
Global
  GlobalSection(SolutionNotes) = postSolution
  EndGlobalSection
  GlobalSection(SolutionConfiguration) = preSolution
       ConfigName.0 = Debug
       ConfigName.1 = Release
  EndGlobalSection
  GlobalSection(ProjectDependencies) = postSolution
  EndGlobalSection
  GlobalSection(ProjectConfiguration) = postSolution
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Debug.ActiveCfg = Debug|x86
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Debug.Build.0 = Debug|x86
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Release.ActiveCfg = Release|x86
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Release.Build.0 = Release|x86
  EndGlobalSection
  GlobalSection(ExtensibilityGlobals) = postSolution
  EndGlobalSection
  GlobalSection(ExtensibilityAddIns) = postSolution
  EndGlobalSection
EndGlobal
```

환경은 솔루션을 로드 하려면 다음 작업 시퀀스를 수행 합니다.

1. 환경.sln 파일의 글로벌 섹션을 읽고 표시 된 섹션을 모두 처리 `preSolution`합니다. 이 예제에서는 파일을 이러한 설명 중 하나는 있습니다.

   ```
   GlobalSection(SolutionConfiguration) = preSolution
        ConfigName.0 = Debug
        ConfigName.1 = Release
   ```

   환경에서 읽는 경우를 `GlobalSection('name')` 태그 이름에 매핑됩니다 레지스트리를 사용 하 여 VSPackage입니다. 키 이름 레지스트리의 아래에 있어야 합니다. [HKLM\\< 응용 프로그램 ID 레지스트리 루트\>\SolutionPersistence\AggregateGUIDs]. 키의 기본값은 항목을 작성 하는 VSPackage의 패키지 GUID (REG_SZ)입니다.

2. 환경 호출 VSPackage를 로드 `QueryInterface` 에서 VSPackage에 대 한는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> 인터페이스를 호출은 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> VSPackage는 데이터를 저장할 수 있도록 섹션에서 데이터를 사용 하 여 메서드. 각각에 대해이 프로세스를 반복 하는 환경 `preSolution` 섹션입니다.

3. 환경을은 프로젝트 지 속성 블록을 반복합니다. 이 경우 하나의 프로젝트가 있습니다.

   ```
   Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1",
   "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"
   EndProject
   ```

   이 문은 고유한 프로젝트 GUID 및 프로젝트 형식 GUID 포함합니다. 프로젝트 파일 또는 솔루션에 속하는 파일을 찾으려면 환경에서이 정보를 사용 하 고 VSPackage 각 프로젝트에 필요한 키를 누릅니다. GUID에 전달 되는 프로젝트 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> 프로젝트와 관련 된 특정 VSPackage를 로드 하려면 다음 프로젝트가 로드 되는 VSPackage에서. 이 경우이 프로젝트에 대 한 로드 되는 VSPackage는 Visual Basic입니다.

   각 프로젝트는 솔루션의 다른 프로젝트에서 필요에 따라 액세스할 수 있도록 고유한 프로젝트 인스턴스 ID를 유지할 수 있습니다. 이상적으로 소스 코드 제어에서 솔루션 및 프로젝트를 솔루션에 대 한 경로 기준으로 프로젝트에 경로가 있어야 합니다. 솔루션을 처음 로드 하는 경우 프로젝트 파일 사용자의 컴퓨터 일 수 없습니다. 솔루션 파일을 기준으로 서버에 저장 하는 프로젝트 파일을가지고 있으므로, 발견 하 고 사용자의 컴퓨터에 복사 될 프로젝트 파일에 대 한 비교적 간단 합니다. 그런 다음 복사 하 고 프로젝트에 필요한 파일의 나머지 부분을 로드 합니다.

4. 환경을은 프로젝트에 대 한 부분이.sln 파일에 포함 된 정보를 기반으로 각 프로젝트 파일을 로드 합니다. 프로젝트 자체는 다음 프로젝트 계층 구조를 채우기 및 모든 중첩 된 프로젝트를 로드 합니다.

5. .Sln 파일의 모든 섹션이 처리 되 면 솔루션이 솔루션 탐색기에서 표시 되 고 사용자가 수정에 대 한 준비가 되었습니다.

솔루션에서 프로젝트를 구현 하는 모든 VSPackage를 로드 하지 못하는 경우를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.OnProjectLoadFailure%2A> 메서드가 호출 되 고 솔루션의 다른 모든 프로젝트를 로드 하는 동안 만들어 둔 해당 변경 내용을 무시 기회가 주어 집니다. 구문 분석 오류가 발생 한 경우에 솔루션 파일을 사용 하 여 최대한 많은 정보 유지 되 고 환경 솔루션 손상 된 사용자 경고 대화 상자를 표시 합니다.

솔루션을 저장 하거나 닫을 때를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.QuerySaveSolutionProps%2A> 메서드는 호출 하 고.sln 파일에 입력 해야 하는 솔루션에 변경 사항이 생겼는지 확인 하려면 계층에 전달 합니다. Null 값 전달 `QuerySaveSolutionProps` 에서 <xref:Microsoft.VisualStudio.Shell.Interop.VSQUERYSAVESLNPROPS>, 솔루션에 대 한 정보를 유지 되는 것을 나타냅니다. 보관 된 정보를 특정 프로젝트의 경우에 대 한 포인터에 의해 결정은 값이 null 이면는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 인터페이스입니다.

없으면 다음 정보를 저장 해야 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> 인터페이스에 대 한 포인터를 사용 하 여 호출 되는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.SaveSolutionProps%2A> 메서드. 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> 메서드는 이름-값 쌍을 검색 하려면 환경에서 호출 됩니다 `IPropertyBag` 인터페이스 및.sln 파일에 정보를 씁니다.

`SaveSolutionProps` 및 `WriteSolutionProps` 개체에서 저장할 정보를 검색 하는 환경에서 재귀적으로 호출 하는 `IPropertyBag` .sln 파일에 입력 된 모든 변경 될 때까지 인터페이스입니다. 이러한 방식으로 솔루션 및 사용 가능한 다음 솔루션 열릴 때 사용 하 여 정보를 유지할지 확인 수 있습니다.

로드 된 모든 VSPackage.sln 파일을 저장 하려면 아무 것도 있을 경우 참조를 열거 됩니다. 레지스트리 키를 쿼리 되는 로드 시만 것입니다. 솔루션은 저장 시 메모리에 있기 때문에 모든 로드 된 패키지에 대 한 환경에 알고 있습니다.

.Sln 파일에서 항목을 포함 하는 전용 합니다 `preSolution` 고 `postSolution` 섹션입니다. 솔루션에는이 정보를 제대로 로드 해야 하므로.suo 파일에 없는 유사한 섹션은. .Suo 파일 공유 또는 소스 코드 제어에 포함 되지 않는 개인 정보, 같은 사용자 관련 옵션을 포함 합니다.

## <a name="see-also"></a>참고자료

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>
- [솔루션 사용자 옵션(.Suo) 파일](../../extensibility/internals/solution-user-options-dot-suo-file.md)
- [솔루션](../../extensibility/internals/solutions-overview.md)