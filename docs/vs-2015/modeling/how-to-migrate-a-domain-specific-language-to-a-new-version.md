---
title: '방법: 도메인 특정 언어를 새 버전으로 마이그레이션 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 6a1ae073-443e-45ca-8bc9-9b944362b449
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7f3cefc7c6e2a78d757bb931a430f09c6da103c1
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65681033"
---
# <a name="how-to-migrate-a-domain-specific-language-to-a-new-version"></a>방법: 도메인 특정 언어를 새 버전으로 마이그레이션
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

정의 및 도메인 특정 언어를 사용 하는 프로젝트를 마이그레이션할 수 있습니다 [!INCLUDE[vs2010](../includes/vs2010-md.md)] 버전의 [!INCLUDE[dsl](../includes/dsl-md.md)] 와 함께 배포 된는 [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)]합니다.  
  
 마이그레이션 도구가의 일부로 제공 됩니다 [!INCLUDE[vssdk_current_long](../includes/vssdk-current-long-md.md)]합니다. 도구 변환 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 프로젝트 및 솔루션을 사용 하거나 DSL 도구를 정의 합니다.  
  
 마이그레이션 도구를 명시적으로 실행 해야 합니다:이 시작 되지 자동으로 솔루션을 열면 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]합니다. 이 경로에 도구 및 자세한 지침 문서를 찾을 수 있습니다.  
  
 **%Program Files%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**  
  
## <a name="before-you-migrate-your-dsl-projects"></a>DSL 프로젝트를 마이그레이션 전에  
 마이그레이션 도구를 수정 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 프로젝트 파일 (**.csproj**) 및 솔루션 파일 (**.sln**).  
  
#### <a name="to-prepare-projects-for-migration"></a>마이그레이션에 대 한 프로젝트를 준비 합니다.  
  
- 있는지 확인 합니다 **.csproj** 하 고 **.sln** 파일에 쓸 수 있습니다. 소스 제어에서 사용 중인 경우 선택 되어 있는지 확인 합니다.  
  
- 마이그레이션 하려는 폴더의 복사본을 만듭니다.  
  
## <a name="migrating-a-collection-of-projects"></a>프로젝트의 컬렉션 마이그레이션  
  
#### <a name="to-migrate-dsl-projects-and-solutions-to-visual-studio-2010"></a>Visual Studio 2010 DSL 프로젝트 및 솔루션 마이그레이션  
  
1. DSL 마이그레이션 도구를 시작 합니다.  
  
   - Windows 탐색기 (또는 파일 탐색기)에서 도구를 두 번 클릭 하거나 명령 프롬프트에서 도구를 시작할 수 있습니다. 이 도구는이 위치에서:  
  
        **%ProgramFiles%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**  
  
2. 솔루션 및 프로젝트를 변환 하려면 포함 된 폴더를 선택 합니다.  
  
   - 도구의 맨 위에 있는 상자에 경로 입력 하거나 클릭 **찾아보기**합니다.  
  
     마이그레이션 도구 또는 Dsl을 사용 하 여 정의 하는 프로젝트 트리를 표시 합니다. 트리를 사용 하는 모든 프로젝트를 포함 합니다 **Microsoft.VisualStudio.Modeling.Sdk** 하거나 **TextTemplating** 어셈블리입니다.  
  
3. 프로젝트의 트리를 검토 하 고 변환 하지 않을 프로젝트를 선택 취소 합니다.  
  
   - 프로젝트 또는 솔루션 도구 되도록 변경 내용 목록을 보려면를 선택 합니다.  
  
       > [!NOTE]
       > 폴더 이름 옆에 나타나는 확인란 아무런 효과가 없습니다. 프로젝트 및 솔루션을 검사 하는 폴더를 확장 해야 합니다.  
  
4. 프로젝트를 변환 합니다.  
  
   1. 클릭 **변환**합니다.  
  
        복사본을 각 프로젝트 파일 변환 전에 _프로젝트_**.csproj** 로 저장 됩니다 _프로젝트_**. vs2008.csproj**  
  
        각 복사본 _솔루션_**.sln** 로 저장 됩니다 _솔루션_**. vs2008.sln**  
  
   2. 보고 된 모든 실패 한 변환을 조사 합니다.  
  
        오류는 텍스트 창에 보고 됩니다. 또한 트리 보기는 변환 하지 못했습니다가 있는 각 노드에서 빨간색 플래그를 표시 합니다. 해당 오류에 대 한 자세한 정보를 보려면 노드를 클릭할 수 있습니다.  
  
5. **모든 템플릿 변환** 성공적으로 포함 된 솔루션에서 프로젝트 변환 합니다.  
  
   1. 솔루션을 엽니다.  
  
   2. 클릭 합니다 **모든 템플릿 변환** 솔루션 탐색기의 헤더에는 단추입니다.  
  
       > [!NOTE]
       > 이 단계는 불필요 한으로 만들 수 있습니다. 자세한 내용은 [모든 템플릿 변환 자동화 방법](https://msdn.microsoft.com/b63cfe20-fe5e-47cc-9506-59b29bca768a)합니다.  
  
6. 변환 된 프로젝트에서 사용자 지정 코드를 업데이트 합니다.  
  
   - 프로젝트를 빌드하고 모든 오류를 조사 하려고 합니다.  
  
   - 디자이너를 테스트 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [시각화 및 모델링 SDK의 새로운 기능](../misc/what-s-new-in-visualization-and-modeling-sdk.md)
