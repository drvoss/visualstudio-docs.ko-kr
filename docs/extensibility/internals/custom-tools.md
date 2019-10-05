---
title: 사용자 지정 도구 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, custom tools
- tools [Visual Studio], custom
- custom tools
ms.assetid: d669f154-9b23-48b6-b9f6-7419c8dd61a6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f9bad62d071fd7c2ef6e0a7c1f5500a5fccb18e0
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66312258"
---
# <a name="custom-tools"></a>사용자 지정 도구
*사용자 지정 도구* 프로젝트에서 항목을 사용 하 여 도구에 연결 하 고 파일을 저장할 때마다 해당 도구를 실행할 수 있습니다. 특정 사용자 지정 도구 라고도 *단일 파일 생성기*는 그 반대로 데이터에서 코드를 생성 하는 변환기를 구현 하는 데 자주 사용 됩니다. 예를 들어, 단일 파일 생성기 만들기 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 하 고 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 소스 코드의는 *.settings* 하 고 *.resx* 파일입니다. 생성된 된 소스 코드의 데이터에 대 한 강력한 형식의 액세스를 제공 합니다 *.settings* 하 고 *.resx* 파일입니다. 합니다 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 고 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 프로젝트 형식 사용자 지정 도구를 지원 합니다. [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 프로젝트 형식 하지 않습니다. 사용자 고유의 프로젝트 형식을 사용자 지정 도구 기능도 사용할 수 있습니다.

 사용자 지정 도구를 구현 하는 등록 된 구성 요소는 `IVsSingleFileGenerator` 인터페이스입니다.

 와 연결 된 사용자 지정 도구를 `ProjectItem` 인터페이스 개체 및 디자이너와 편집기 같습니다. 사용자 지정 도구는 변수로 나타낸 파일을 `ProjectItem` 으로 입력 및 파일 이름이 제공한 새 파일을 쓰는 `DefaultExtension` 메서드.

## <a name="in-this-section"></a>단원 내용
- [단일 파일 생성기 구현](../../extensibility/internals/implementing-single-file-generators.md)

 사용 하는 방법에 설명 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> 사용자 지정 도구를 구현 하는 인터페이스입니다.

- [등록 단일 파일 생성기](../../extensibility/internals/registering-single-file-generators.md)

 사용자 지정 도구에 대 한 모든 레지스트리 항목에 대 한 설명을 제공합니다.

- [비주얼 디자이너에 형식 노출](../../extensibility/internals/exposing-types-to-visual-designers.md)

 어떻게 프로젝트 시스템 지원을 제공 액세스 생성 클래스 및 형식에 비주얼 디자이너에 대 한 임시 pe (이식 가능) 파일을 통해 설명 합니다.

- [프로젝트 항목의 속성 유지](../../extensibility/persisting-the-property-of-a-project-item.md)

 프로젝트 파일에서 소스 파일의 작성자와 같은 프로젝트 항목 속성을 유지 하는 방법을 보여 줍니다.

## <a name="reference"></a>참조
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> 에 대 한 세부 정보를 제공 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>, 컴파일 또는 프로젝트에 추가 될 수 있는 단일 출력 파일에 단일 입력된 파일을 변환 하는 합니다.

 <xref:EnvDTE.ProjectItem> 에 대해 설명 합니다 `ProjectItem` 프로젝트에서 항목을 나타내는 인터페이스입니다.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> 에 대 한 세부 정보를 제공 합니다 `DefaultExtension` 출력 파일 이름에 지정 된 파일 이름 확장명을 검색 하는 메서드.

## <a name="related-sections"></a>관련 단원
- [프로젝트를 확장 합니다.](../../extensibility/extending-projects.md)

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 프로젝트 및 솔루션을 사용하여 코드 파일 및 리소스 파일을 구성하는 방법 및 소스 제어를 구현하는 방법을 설명합니다.