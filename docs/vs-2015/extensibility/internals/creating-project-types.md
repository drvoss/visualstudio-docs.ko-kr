---
title: 프로젝트 형식 만들기 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, new
- projects [Visual Studio SDK], new project types
ms.assetid: bdb2d22e-d622-450c-bb2d-98152a745fcf
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bbe65d1615603e4dc7546dbfe3530093c62528e5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68155034"
---
# <a name="creating-project-types"></a>프로젝트 형식 만들기
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

확장할 수 있습니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 새 프로젝트 형식을 만들어 합니다. 새 프로젝트 형식을 만들려면 몇 가지 개념을 이해 하 고 다양 한 단계를 완료 해야 합니다. 다음 항목에서는 프로젝트 유형을 만드는 방법의 개요를 제공 합니다.  
  
## <a name="in-this-section"></a>섹션 내용  
 [프로젝트 형식 디자인 결정](../../extensibility/internals/project-type-design-decisions.md)  
 항목, 프로젝트 파일 지 속성 및 새 프로젝트 형식을 만들기 전에 확인 해야 하는 약정 정비공 디자인 결정에 설명 합니다.  
  
 [검사 목록: 새 프로젝트 형식 만들기](../../extensibility/internals/checklist-creating-new-project-types.md)  
 코드 편집 및 컴파일, 빌드, 디버깅 및 배포 프로젝트에서 응용 프로그램으로 프로그래밍 작업을 지 원하는 새 프로젝트 형식 만들기 위해 따라야 하는 단계에 간략하게 설명 합니다.  
  
 [프로젝트 팩터리를 사용하여 프로젝트 인스턴스 만들기](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)  
 제공 하 고 새 프로젝트의 인스턴스를 만드는 프로젝트 팩터리를 사용 하는 방법에 대 한 정보를 제공 합니다.  
  
 [프로젝트 형식 등록](../../extensibility/internals/registering-a-project-type.md)  
 문의 레지스트리에서 기본 경로 및 데이터 테이블을 제공 하는 각 문에 대 한 레지스트리 스크립트에서 항목을 포함 하는 코드 샘플을 제공 합니다.  
  
 [프로젝트 지속성](../../extensibility/internals/project-persistence.md)  
 사용 하는 방법을 설명 `IPersistFileFormat` 파일 및 파일 기반이 아닌 프로젝트 개체를 유지 합니다.  
  
 [MSBuild 사용](../../extensibility/internals/using-msbuild.md)  
 프로젝트 형식을 사용 하 여는 방법을 설명 합니다 [!INCLUDE[vstecmsbuild](../../includes/vstecmsbuild-md.md)] 빌드 엔진에서 작성 하는 사용자가 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 및 명령줄에서.  
  
## <a name="related-sections"></a>관련 단원  
 [기호 검색 도구 지원](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 보기 도구와 같은 코드의 아키텍처를 설명 합니다 **개체 브라우저** 하 고 **클래스 뷰** 창입니다. 인터페이스 및 VSPackage에서 개체 검색을 구현 하는 데 사용 되는 메서드를 설명 합니다.  
  
 [프로젝트 및 프로젝트 항목 템플릿 추가](../../extensibility/internals/adding-project-and-project-item-templates.md)  
 프로젝트 프로젝트 항목을 열 때 편집기는 결정을 수행 하는 중요 한 이유를 설명 및 방법 project 리소스를 조작할 수 있습니다.  
  
 [Windows Installer를 사용하여 VSPackage 설치](../../extensibility/internals/installing-vspackages-with-windows-installer.md)  
 VSPackage는 자체 고유 id를 지정 하는 방법 및 Windows Installer 패키지에서 VSPackage Dll 및 기타 정보를 래핑하는 방법을 보여 줍니다 (합니다. MSI 파일)를 고객에 게 배포 합니다.  
  
 [Visual Studio의 계층 구조](../../extensibility/internals/hierarchies-in-visual-studio.md)  
 에 대해 설명 하는 방법을 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 뷰와 주소 계층입니다.  
  
 [VSPackage](../../extensibility/internals/vspackages.md)  
 VSPackage로 확장 하는 설치할 수 있는 COM 개체에 간략하게는 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 환경 및 사용자 고유의 VSPackage를 구현 하는 방법에 설명 합니다.  
  
 [프로젝트 형식](../../extensibility/internals/project-types.md)  
 코드를 수정, 컴파일 및 코드를 작성 및 실행 코드를 디버깅 프로젝트를 사용 하는 방법에 설명 하 고 프로젝트 유형을 만드는 방법에 대 한 자세한 항목에 대 한 링크를 제공 합니다.
