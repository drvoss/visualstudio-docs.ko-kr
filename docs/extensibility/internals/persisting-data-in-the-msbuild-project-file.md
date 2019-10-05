---
title: MSBuild 프로젝트 파일에 데이터를 유지 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project files, persisting data in
ms.assetid: 6a920cb7-453d-4ffd-af1c-6f3084bd03f7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c2f09d84d61464b22b9bbe01478f35410bdd0904
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66328505"
---
# <a name="persisting-data-in-the-msbuild-project-file"></a>MSBuild 프로젝트 파일의 데이터 유지
프로젝트 하위 형식이 면 나중에 사용할 프로젝트 파일에 하위 형식의 특정 데이터를 유지 해야 합니다. 프로젝트 하위 형식이 면 다음 요구 사항을 충족 하기 위해 프로젝트 파일 지 속성을 사용 합니다.

1. 프로젝트 빌드의 일부로 사용 되는 데이터를 유지 합니다. (Microsoft Build Engine에 대 한 자세한 내용은 참조 하세요. [MSBuild](../../msbuild/msbuild.md).) 빌드 관련 정보를 수행할 수 있습니다.

    1. 구성에 관계 없이 데이터입니다. 즉, 비어 있거나 누락 된 조건 사용 하 여 MSBuild 요소에 저장 된 데이터입니다.

    2. 구성에 종속 된 데이터입니다. 즉, 특정 프로젝트 구성에 대 한 조건는 MSBuild 요소에 저장 된 데이터입니다. 예를 들어:

        ```
        <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">
        ```

2. 빌드 관련 되지 않은 데이터를 유지 합니다. XML 스키마에 대해 유효성이 검사 되지 않은 자유 형식 XML에서이 데이터를 표현할 수 있습니다.

    1. 구성에 관계 없이 데이터입니다.

    2. 구성에 종속 된 데이터입니다.

## <a name="persisting-build-related-information"></a>빌드 관련 정보를 유지합니다.
 프로젝트를 빌드하기 위한 유용한 데이터의 지 속성은 MSBuild를 통해 처리 됩니다. MSBuild 시스템은 빌드 관련 정보의 마스터 테이블을 유지 합니다. 프로젝트 하위 형식 가져오기 및 설정 속성 값이이 데이터에 액세스 하는 것에 대 한 책임이 있습니다. 프로젝트 하위 형식 유지 되지 않습니다 있도록 속성을 제거 하 고 유지 하는 추가 속성을 추가 하 여 빌드 관련 데이터 테이블을 향상할 수도 있습니다.

 MSBuild 데이터를 수정 하려면 프로젝트 하위 형식에 대 한 책임이 통해 기본 프로젝트 시스템에서 MSBuild 속성 개체를 검색할 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>합니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> 실행 하 여에 대 한 핵심 프로젝트 시스템에 집계 프로젝트 하위 쿼리를 구현 하는 인터페이스는 `QueryInterface`합니다.

 다음 절차를 사용 하 여 속성을 제거 하기 위한 단계를 간략하게 설명 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>합니다.

#### <a name="to-remove-a-property-from-an-msbuild-project-file"></a>MSBuild 프로젝트 파일에서 속성을 제거 하려면

1. 호출 `QueryInterface` 에서 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> 프로젝트 하위 형식입니다.

2. 호출 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.RemoveProperty%2A> 사용 하 여 `pszPropName` 제거 하려는 속성으로 설정 합니다.

### <a name="persisting-non-build-related-information"></a>비 빌드 관련된 정보 유지
 프로젝트 파일의 빌드에 상관 없이 데이터의 지 속성을 통해 처리 됩니다 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>합니다.

 구현할 수 있습니다 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> 주 `project subtype aggregator` 개체는 `project subtype project configuration` 개체 중 하나 또는 둘 다.

 다음 사항을 아닌 빌드 관련 정보의 지 속성에 대 한 주요 개념을 간략하게 설명합니다.

- 기본 프로젝트 개체를 호출 합니다 주 프로젝트 하위 형식 (즉, 가장 바깥쪽 프로젝트 하위 형식) 집계를 로드 하 고 구성 독립적인 데이터를 저장 및 로드 또는 구성에 종속적인 저장 하려면 프로젝트 하위 형식 프로젝트 구성 개체에서 호출 데이터입니다.

- 메서드를 호출 하는 기본 프로젝트 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> 여러 프로젝트 하위 형식, 집계의 각 수준에 대 한 시간 및 각 수준에 대 한 GUID를 전달 합니다.

- 기본 프로젝트를 전달할지 받을지 전용 특정 프로젝트 하위 형식으로 사용 되는 집계 수준 간의 상태를 유지 하는 방법으로이 메커니즘을 사용 하 여 XML 조각입니다.

- 가장 바깥쪽 프로젝트 하위 형식을 호출 하는 기본 프로젝트 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>구현 GUID를 전달 합니다. 호출 자체; 처리 GUID 가장 바깥쪽 프로젝트 하위 형식에 속하는 경우 그렇지 않으면 프로젝트 하위 형식에 해당 하는 GUID는 발견 될 때까지 호출을 내부 프로젝트 하위 형식 및 등을 위임 합니다.

- 프로젝트 하위 형식 전이나 후에 내부 프로젝트 하위 형식에 대 한 호출을 위임 하는 XML 조각을 수정할 수도 있습니다. 다음 예제에서는 프로젝트 하위 형식에 관련 된 속성을 포함 하는 파일의 이름을 해당 프로젝트 하위 형식에 전달 되는 프로젝트 파일에서 발췌를 보여 줍니다.

    ```
    <ProjectExtensions>
        <VisualStudio>
          <FlavorProperties GUID="{<FlavorGUID>}">
            <FlavorProject TestFileFolder="TestFile" />
          </FlavorProperties>
        </VisualStudio>
      </ProjectExtensions>
    ```

## <a name="see-also"></a>참고 항목
- [프로젝트 하위 형식](../../extensibility/internals/project-subtypes.md)