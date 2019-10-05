---
title: '방법: 도메인별 언어 솔루션 만들기 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.dsltools.designerwizard
helpviewer_keywords:
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools], creating domain-specific language
- Domain-Specific Language Tools, creating solutions
ms.assetid: e585b63b-34d2-405a-8d81-39ea22317975
caps.latest.revision: 43
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: eae08b771f3bd5748485f9029f7f12725df6f28f
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65698128"
---
# <a name="how-to-create-a-domain-specific-language-solution"></a>방법: 도메인 특정 언어 솔루션 만들기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

도메인 특정 언어 (DSL) 이라는 특수을 사용 하 여 만들어지는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 솔루션입니다.  
  
## <a name="prerequisites"></a>전제 조건  
 이 절차를 시작 하기 전에 이러한 구성 요소를 먼저 설치 해야 합니다.  
  
|||  
|-|-|  
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185579](http://go.microsoft.com/fwlink/?LinkID=185579)|  
|[!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185580](http://go.microsoft.com/fwlink/?LinkID=185580)|  
|Visual Studio Visualization and Modeling SDK|[http://go.microsoft.com/fwlink/?LinkID=185581](http://go.microsoft.com/fwlink/?LinkID=185581)|  
  
## <a name="creating-a-domain-specific-language-solution"></a>도메인별 언어 솔루션 만들기  
  
#### <a name="to-create-a-domain-specific-language-solution"></a>도메인별 언어 솔루션을 만들려면  
  
1. DSL 마법사를 시작 합니다.  
  
   1. **파일** 메뉴에서 **새로 만들기**를 가리킨 다음 **프로젝트**를 클릭합니다.  
  
   2. **새 프로젝트** 대화 상자가 나타납니다.  
  
   3. 아래 **프로젝트 형식**를 확장 합니다 **기타 프로젝트 형식** 노드를 마우스 클릭 **확장성**.  
  
   4. 클릭 **도메인별 언어 디자이너**합니다.  
  
   5. 에 **이름을** 상자는 솔루션에 대 한 이름을 입력 합니다. **확인**을 클릭합니다.  
  
       합니다 **도메인별 언어 디자이너 마법사** 나타납니다.  
  
      > [!NOTE]
      > 가급적 코드 생성에 사용할 수 있으므로 이름을 입력 하는 유효한 Visual C# 식별자를 해야 합니다.  
  
      ![DSL 만들기 대화 상자](../modeling/media/create-dsldialog.png "Create_DSLDialog")  
  
2. DSL 템플릿을 선택 합니다.  
  
    에 **도메인별 언어 옵션 선택** 페이지와 같은 솔루션 템플릿 중 하나를 선택 합니다 **최소 언어**합니다. 만들려는 DSL 비슷한 템플릿을 선택 합니다.  
  
    솔루션 템플릿에 대 한 자세한 내용은 참조 하십시오 [도메인별 언어 솔루션 템플릿 선택](../modeling/choosing-a-domain-specific-language-solution-template.md)합니다.  
  
3. 파일 이름 확장명을 입력 합니다 **파일 확장명** 페이지입니다. 컴퓨터에서 고유 해야 하 고 DSL을 설치 하려는 모든 컴퓨터에서. 메시지가 나타납니다 **응용 프로그램이 나 Visual Studio 편집기는이 확장을 사용할**합니다.  
  
   - 완전히 설치 되지 않은 이전 실험적 Dsl의 파일 이름 확장명을 사용한 경우 지울 수는 있습니다 축소를 사용 하 여 합니다 **실험적 인스턴스 다시 설정** 에서 찾을 수 있는 도구는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] SDK 메뉴.  
  
   - 다른 경우 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 확장이 파일 확장명을 사용 하는 컴퓨터에 완전히 설치 되 면 제거 하는 것이 좋습니다. 에 **도구** 메뉴에서 클릭 **확장 관리자**합니다.  
  
4. 를 검사 하 고 필요한 경우 필드를 조정, 마법사의 나머지 페이지의 키를 누릅니다. 설정에 만족 했으면 클릭 **완료**합니다. 설정에 대 한 자세한 내용은 참조 하세요. [DSL 디자이너 마법사 페이지](#settings)합니다.  
  
    마법사 라는 두 개의 프로젝트가 포함 된 솔루션을 만듭니다 **Dsl** 하 고 **DslPackage**합니다.  
  
   > [!NOTE]
   > 신뢰할 수 없는 소스에서 텍스트 템플릿을 실행 하려면 클릭 하지 경고를 생성 하는 메시지가 표시 되 면 **확인**합니다. 이 메시지가 다시 표시 하지를 설정할 수 있습니다.  
  
## <a name="settings"></a> DSL 디자이너 마법사 페이지  
 다양 한 해당 기본값에서 변경 되지 않은 필드를 둘 수 있습니다. 그러나 파일 확장명 필드를 설정 하는 해야 합니다.  
  
### <a name="solution-settings-page"></a>솔루션 설정 페이지  
 **도메인 특정 언어에서 기본 템플릿을 사용 하 시겠습니까?**  
 만들려는 DSL 비슷한 템플릿을 선택 합니다. 다양 한 템플릿을 편리한 시작점을 제공합니다. 솔루션 템플릿으로 선택 하면 마법사는 설명을 표시 합니다. 솔루션 템플릿에 대 한 자세한 내용은 참조 하십시오 [도메인별 언어 솔루션 템플릿 선택](../modeling/choosing-a-domain-specific-language-solution-template.md)합니다.  
  
 **도메인 특정 언어 이름을 지정 하 시겠습니까?**  
 기본값은 솔루션 이름입니다. 이 값에서 코드가 생성 됩니다. C# 클래스 이름으로 유효 해야 합니다.  
  
### <a name="file-extension-page"></a>파일 확장명 페이지  
 **어떤 확장 해야 모델 파일에서 사용**  
 새 파일 확장명을 입력 합니다.  
  
 이 파일 확장명에 아직 등록 되지이 컴퓨터에서 사용 하기 위해 다음과 같이 확인 합니다.  
  
 아래를 봅니다 **이 확장 처리를 위해 등록 하는 다른 도구 및 응용 프로그램**합니다. 메시지가 표시 되 면 **응용 프로그램이 나 Visual Studio 편집기는이 확장을 사용할**,이 파일 확장명을 사용할 수 있습니다.  
  
 도구 또는 패키지의 목록에 표시 되 면 다음 중 하나를 수행 해야 합니다.  
  
- 다른 파일 확장명을 입력 합니다.  
  
     \- 또는 -  
  
- 다시 설정 된 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 실험적 인스턴스. 이전에 만든 Dsl의 모든 등록을 취소 합니다. 에 **시작** 메뉴에서 클릭 **모든 프로그램**, **Microsoft Visual Studio 2010 SDK**, **도구**를 차례로 **다시 설정 합니다 Microsoft Visual Studio 2010 실험적 인스턴스**합니다. 다시 사용 하려는 다른 모든 Dsl을 다시 작성할 수 있습니다.  
  
     \- 또는 -  
  
- 경우는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 확장이 파일 확장명을 사용 하는 컴퓨터에 완전히 설치 되 면 제거 합니다. 에 **도구** 메뉴에서 클릭 **확장 관리자**합니다.  
  
### <a name="product-settings-page"></a>제품 설정 페이지  
 **새 도메인 특정 언어에 속하는 제품의 이름은 무엇입니까?**  
 기본값은 DSL 이름입니다.  
  
 이 값은이 파일 확장명을 가진 파일을 설명 하기 위해 Windows 탐색기 (또는 파일 탐색기)에서 사용 됩니다.  
  
 **제품에 속하는 회사의 이름은 무엇입니까?**  
 회사 이름입니다.  
  
 이 값은 DSL 패키지의 AssemblyInfo 속성에 통합 됩니다.  
  
 **이 솔루션의 프로젝트에 대 한 루트 네임 스페이스란?**  
 회사에서 구성 된 이름 및 제품 이름을이 기본값은입니다.  
  
### <a name="signing-page"></a>서명 페이지  
 **강력한 이름 키 파일 만들기**  
 기본 옵션을 DSL 어셈블리에 서명할 새 키를 만드는 것입니다.  
  
 **기존 강력한 이름 키 사용**  
 다른 어셈블리를 사용 하 여 DSL을 통합 하려는 경우이 옵션을 사용 합니다.  
  
 강력한 이름 지정에 대 한 자세한 내용은 참조 하세요. [강력한 어셈블리 만들기 및 사용](http://go.microsoft.com/fwlink/?LinkId=186073)합니다.  
  
## <a name="see-also"></a>참고 항목  
 [도메인 특정 언어를 정의 하는 방법](../modeling/how-to-define-a-domain-specific-language.md)   
 [도메인 특정 언어 도구 용어집](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
