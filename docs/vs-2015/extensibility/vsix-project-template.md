---
title: VSIX 프로젝트 템플릿 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- deploy packages
- publish extension
ms.assetid: b6c82167-e2a5-4cff-8c8b-2d72e2a9092c
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2386f1be805f6347fc32fba4ee8bfe57c8602329
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436899"
---
# <a name="vsix-project-template"></a>VSIX 프로젝트 템플릿
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSIX 프로젝트에서 하나 이상의 Visual Studio 확장을 래핑할 VSIX 프로젝트 템플릿을 사용 하 고 다음에서 패키지를 게시할 수 있습니다 합니다 [Visual Studio Marketplace](https://marketplace.visualstudio.com/) 웹 사이트입니다.  
  
 VSIX 배포에는 Vspackage, 어셈블리, MEF 구성 요소, 프로젝트 템플릿, 항목 템플릿, 도구 상자 컨트롤 및 사용자 지정 확장 형식을 지원합니다.  
  
> [!NOTE]
> VSIX 프로젝트를 사용 하려면 Visual Studio SDK를 설치 해야 합니다. Visual Studio SDK에 대 한 자세한 내용은 참조 하세요. [Visual Studio SDK](../extensibility/visual-studio-sdk.md)합니다.  
  
## <a name="where-to-find-the-vsix-project-template"></a>VSIX 프로젝트 템플릿 검색 위치  
 VSIX 프로젝트 템플릿에 사용할 수 있습니다 합니다 **새 프로젝트** 대화 상자. 확장 된 **Visual Basic** 노드 또는 **Visual C#** 노드를 선택한 후 **확장성**합니다.  
  
> [!TIP]
> 확인 해야 해당.NET Framework 4.5 또는 더 높은 맨 위에 있는 드롭다운 목록에 지정 된 된 **새 프로젝트** 대화 상자.  
  
## <a name="uses-of-the-vsix-project-template"></a>VSIX 프로젝트 템플릿 사용  
 주요 용도 VSIX 프로젝트 템플릿:  
  
- 프로젝트 템플릿과 항목 템플릿 VSIX 지원 되지 않은 다른 확장을 배포 합니다.  
  
- 에 하나의 배포 패키지에 여러 확장의 출력을 래핑합니다.  
  
  VSIX 프로젝트 템플릿을 사용 하 여 Vspackage 또는 다른 종류의 지원 되는 VSIX에 이미 있는 확장을 배포할 필요가 없습니다.  
  
## <a name="packaging-an-extension-in-an-empty-vsix-project"></a>빈 VSIX 프로젝트에서 확장 패키지  
 기존 확장 또는 이미 사용 하 여 빈 VSIX 프로젝트에서 지원 되는 VSIX가 없는 확장을 패키징할 수 있습니다. 래핑될 확장에서 지원 되는 형식 이어야 합니다 [VSIX 스키마](../extensibility/vsix-extension-schema-2-0-reference.md)합니다.  
  
#### <a name="to-package-an-extension-by-using-a-vsix-project"></a>VSIX 프로젝트를 사용 하 여 확장 패키지  
  
1. 확장 프로그램을 구성 하는 프로젝트를 빌드하십시오.  
  
2. VSIX 프로젝트를 사용 하 여 만듭니다는 **VSIX 프로젝트** 템플릿.  
  
     Source.extension.vsixmanifest 열립니다 **매니페스트 디자이너**합니다.  
  
3. 에 **자산** 탭을 선택 합니다 **새로 만들기** 단추입니다.  
  
     합니다 **새 자산 추가** 대화 상자가 나타납니다.  
  
4. 에 **형식** 목록에서 추가할 확장의 유형을 선택 합니다.  
  
5. 현재 솔루션 (예: 항목 템플릿 또는 컴파일된 어셈블리)에 포함 된 확장 프로그램이 나 콘텐츠 요소를 추가 하려면 다음 단계를 수행 합니다.  
  
    1. 에 **소스** 목록에서 선택 **현재 솔루션의 프로젝트**합니다.  
  
    2. 에 **프로젝트** 목록, 확장의 이름을 선택 합니다.  
  
    3. 에 **이 폴더에 포함** 자산을 포함 하 고 선택한 폴더의 이름을 입력 합니다 **확인** 단추입니다.  
  
6. 확장명이 나 현재 솔루션에 포함 되지 않은 콘텐츠 요소를 추가 하려면 다음 단계를 수행 합니다.  
  
    1. 에 **소스** 목록 상자에서 선택 **파일 시스템의 파일**합니다.  
  
    2. 에 **경로** 필드, 컴파일된 또는 압축 된 확장 파일에 전체 경로 입력 하거나 사용 합니다 **찾아보기** 파일 찾아보기 단추입니다.  
  
    3. 에 **이 폴더에 포함** 자산을 포함 하 고 선택한 폴더의 이름을 입력 합니다 **확인** 단추입니다.  
  
7. 추가 확장을 포함 하도록 패키지를 원한다 면 동일한 방식으로 추가 합니다.  
  
8. 솔루션을 빌드합니다.  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] VSIX 매니페스트 파일, [Content_Types].xml 파일 및 프로젝트에 추가한 확장 자산을 모두 포함 된.vsix 파일을 빌드합니다.  
  
## <a name="see-also"></a>참고 항목  
 [VSIX 확장 스키마 2.0 참조](../extensibility/vsix-extension-schema-2-0-reference.md)   
 [Visual Studio 확장 찾기 및 사용](../ide/finding-and-using-visual-studio-extensions.md)
