---
title: 사용자 지정 도구 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, custom tools
- tools [Visual Studio], custom
- custom tools
ms.assetid: d669f154-9b23-48b6-b9f6-7419c8dd61a6
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 594d564cf4a18eb0b673abd9b45b7d70e20381b1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68196911"
---
# <a name="custom-tools"></a>사용자 지정 도구
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

*사용자 지정 도구* 프로젝트에서 항목을 사용 하 여 도구에 연결 하 고 파일을 저장할 때마다 해당 도구를 실행할 수 있습니다. 특정 사용자 지정 도구 라고도 *단일 파일 생성기*는 그 반대로 데이터에서 코드를 생성 하는 변환기를 구현 하는 데 자주 사용 됩니다. 예를 들어, 단일 파일 생성기 만들기 [!INCLUDE[csprcs](../../includes/csprcs-md.md)] 고 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] .settings 및.resx 파일에서 코드를 원본입니다. 생성된 된 소스 코드.settings 및.resx 파일의 데이터에 대 한 강력한 형식의 액세스를 제공합니다. 합니다 [!INCLUDE[csprcs](../../includes/csprcs-md.md)] 고 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 프로젝트 형식 사용자 지정 도구를 지원 합니다. [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] 프로젝트 형식 하지 않습니다. 사용자 고유의 프로젝트 형식을 사용자 지정 도구 기능도 사용할 수 있습니다.  
  
 사용자 지정 도구를 구현 하는 등록 된 구성 요소는 `IVsSingleFileGenerator` 인터페이스입니다.  
  
 와 연결 된 사용자 지정 도구를 `ProjectItem` 인터페이스 개체 및 디자이너와 편집기 같습니다. 사용자 지정 도구는 변수로 나타낸 파일을 `ProjectItem` 으로 입력 및 파일 이름이 제공한 새 파일을 쓰는 `DefaultExtension` 메서드.  
  
## <a name="in-this-section"></a>섹션 내용  
 [단일 파일 생성기 구현](../../extensibility/internals/implementing-single-file-generators.md)  
 사용 하는 방법에 설명 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> 사용자 지정 도구를 구현 하는 인터페이스입니다.  
  
 [프로젝트의 기본 네임스페이스 확인](../../misc/determining-the-default-namespace-of-a-project.md)  
 사용 중인 언어에 따라 올바른 네임 스페이스를 확인 하는 방법에 설명 합니다.  
  
 [단일 파일 생성기 등록](../../extensibility/internals/registering-single-file-generators.md)  
 사용자 지정 도구에 대 한 모든 레지스트리 항목에 대 한 설명을 제공합니다.  
  
 [비주얼 디자이너에 형식 노출](../../extensibility/internals/exposing-types-to-visual-designers.md)  
 어떻게 프로젝트 시스템 지원을 제공 액세스 생성 클래스 및 형식에 비주얼 디자이너에 대 한 임시 pe (이식 가능) 파일을 통해 설명 합니다.  
  
 [프로젝트 항목의 속성 유지](../../extensibility/persisting-the-property-of-a-project-item.md)  
 프로젝트 파일에서 소스 파일의 작성자와 같은 프로젝트 항목 속성을 유지 하는 방법을 보여 줍니다.  
  
## <a name="reference"></a>참조  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>  
 에 대 한 세부 정보를 제공 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>, 컴파일 또는 프로젝트에 추가 될 수 있는 단일 출력 파일에 단일 입력된 파일을 변환 하는 합니다.  
  
 <xref:EnvDTE.ProjectItem>  
 에 대해 설명 합니다 `ProjectItem` 프로젝트에서 항목을 나타내는 인터페이스입니다.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>  
 에 대 한 세부 정보를 제공 합니다 `DefaultExtension` 출력 파일 이름에 지정 된 파일 이름 확장명을 검색 하는 메서드.  
  
## <a name="related-sections"></a>관련 단원  
 [프로젝트 확장](../../extensibility/extending-projects.md)  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 프로젝트 및 솔루션을 사용하여 코드 파일 및 리소스 파일을 구성하는 방법 및 소스 제어를 구현하는 방법을 설명합니다.
