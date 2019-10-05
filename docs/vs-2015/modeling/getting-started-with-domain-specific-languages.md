---
title: 도메인별 언어 시작 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 024392a2-2c04-404f-a27b-7273553c3b60
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ca90a90d476acc0bdbc1df426b981d98207bbd28
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65687242"
---
# <a name="getting-started-with-domain-specific-languages"></a>도메인별 언어 시작
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 항목에서는 정의 하 고 Visual Studio 용 모델링 SDK를 사용 하 여 만든 도메인 특정 언어 (DSL)를 사용 하 여 기본적인 개념을 설명 합니다.  
  
 Dsl을 처음 접하는 경우 진행 하는 것이 좋습니다 합니다 **DSL 도구 랩**,이 사이트에서 찾을 수 있습니다. [Visualizaton 및 모델링 SDK](http://go.microsoft.com/fwlink/?LinkID=186128)  
  
## <a name="what-can-you-do-with-a-domain-specific-language"></a>도메인 특정 언어를 사용 하 여 수행할 수 있습니까?  
 도메인 특정 언어는 노테이션 일반적으로 그래픽 특정 용도로 사용 하도록 디자인 된 경우 반면, UML 같은 언어는 범용입니다. DSL의 모델 요소 및 해당 관계 및 화면에 표시 되는 방식을 유형을 정의할 수 있습니다.  
  
 DSL을 디자인할 때 Visual Studio 통합 확장 (VSIX) 패키지의 일부로 배포할 수 있습니다. 사용자 작업에서 DSL을 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]:  
  
 ![패밀리 트리 다이어그램, 도구 상자 및 탐색기](../modeling/media/familyt-instance.png "FamilyT_Instance")  
  
 표기법은 DSL의 일부일 뿐입니다. VSIX 패키지 라는 표기와 함께 사용자가 편집 하 고 해당 모델에서 자료를 생성 하는 데 적용할 수 있는 도구를 포함 합니다.  
  
 Dsl의 주 응용 프로그램 중 프로그램 코드, 구성 파일 및 기타 아티팩트를 생성 하는 것입니다. 특히 대규모 프로젝트 및 제품 라인, 제품의 여러 변형을 만들어지는, Dsl에서 생성 하는 다양 한 변수 측면을 제공할 수 있습니다 늘어날 안정성 및 요구 사항 변경에 대 한 매우 빠른 응답.  
  
 이 개요의 나머지 부분은 만들고 도메인 특정 언어를 사용 하 여 기본 작업을 소개 하는 연습은 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]합니다.  
  
## <a name="prerequisites"></a>전제 조건  
 DSL을 정의하려면 다음 구성 요소를 설치해야 합니다.  
  
|||  
|-|-|  
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185579](http://go.microsoft.com/fwlink/?LinkId=185579)|  
|[!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185580](http://go.microsoft.com/fwlink/?LinkId=185580)|  
|Visual Studio 용 모델링 SDK|[MSDK를 다운로드 합니다.](https://www.microsoft.com/download/details.aspx?id=48148)|  
  
## <a name="creating-a-dsl-solution"></a>DSL 솔루션 만들기  
 새 도메인 특정 언어를 만들려면 새로 만든 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 도메인 특정 언어 프로젝트 템플릿을 사용 하 여 솔루션입니다.  
  
#### <a name="to-create-a-dsl-solution"></a>DSL 솔루션을 만들려면  
  
1. **파일** 메뉴에서 **새로 만들기**를 가리킨 다음 **프로젝트**를 클릭합니다.  
  
2. 아래 **프로젝트 형식**를 확장 합니다 **기타 프로젝트 형식** 노드를 마우스 클릭 **확장성**.  
  
3. 클릭 **도메인별 언어 디자이너**합니다.  
  
    ![DSL 만들기 대화 상자](../modeling/media/create-dsldialog.png "Create_DSLDialog")  
  
4. 에 **이름을** 상자에 입력 **FamilyTree**합니다. **확인**을 클릭합니다.  
  
    합니다 **도메인별 언어 마법사** 열리고 템플릿 DSL 솔루션 목록이 표시 됩니다.  
  
    각 템플릿에 대 한 설명을 보려면 클릭  
  
    템플릿은 유용한 시작점입니다. 각각의 전체 작업 요구에 맞게 편집할 수 있는 DSL을 제공 합니다. 일반적으로를 만들려는 가장 가까운 템플릿을 선택 합니다.  
  
5. 이 연습에서는 선택 된 **최소 언어** 템플릿.  
  
6. 해당하는 마법사 페이지에서 DSL의 파일 이름 확장명을 입력합니다. 이 확장명은 DSL의 인스턴스가 포함된 파일에 사용됩니다.  
  
   - DSL을 설치 하려는 모든 컴퓨터 또는 컴퓨터에서 응용 프로그램과 연결 되지 않은 확장을 선택 합니다. 예를 들어 **docx** 하 고 **htm** 허용 되지 않는 파일 이름 확장명을 수 있습니다.  
  
   - 입력한 확장명이 DSL로 사용되고 있으면 경고가 표시됩니다. 이 경우 다른 파일 이름 확장명을 사용해야 합니다. Visual Studio SDK 실험적 인스턴스를 다시 설정하여 오래된 실험적 디자이너를 지울 수도 있습니다. 클릭 **시작**, 클릭 **모든 프로그램**를 **Microsoft Visual Studio 2010 SDK**를 **도구**를 차례로 **Microsoft를 다시 설정 Visual Studio 2010 실험적 인스턴스**합니다.  
  
7. 다른 페이지를 검사 하 고 클릭 **완료**합니다.  
  
    솔루션에는 두 프로젝트가 포함 된 생성 됩니다. Dsl과 DslPackage 라고 합니다. 다이어그램 파일을 엽니다 명명된 DslDefinition.dsl입니다.  
  
   > [!NOTE]
   > 대부분의 두 프로젝트의 폴더에서 볼 수 있는 코드는 DslDefinition.dsl에서 생성 됩니다. 이러한 이유로 대부분 DSL 수정이이 파일에 만들어집니다.  
  
   이제 사용자 인터페이스는 다음 그림과 같이 표시됩니다.  
  
   ![dsl 디자이너](../modeling/media/dsl-designer.png "dsl_designer")  
  
   이 솔루션은 DSL을 정의합니다. 자세한 내용은 [도메인별 언어 도구 사용자 인터페이스 개요](../modeling/overview-of-the-domain-specific-language-tools-user-interface.md)합니다.  
  
## <a name="the-important-parts-of-the-dsl-solution"></a>DSL 솔루션의 중요 한 부분  
 새 솔루션의 다음 측면을 확인할 수 있습니다.  
  
- **Dsl\DslDefinition.dsl** DSL 솔루션을 만들 때 참조 하는 파일입니다. 대부분의 DSL 정의에 대해 수행한 변경 내용이 여기 및 솔루션의 거의 모든 코드를이 파일에서 생성 됩니다. 자세한 내용은 참조를 사용 합니다 [DSL 정의 다이어그램 작업](../modeling/working-with-the-dsl-definition-diagram.md).  
  
- **Dsl 프로젝트** 이 프로젝트에 도메인 특정 언어를 정의 하는 코드가 포함 되어 있습니다.  
  
- **DslPackage 프로젝트** 이 프로젝트를 열고 편집할 수는 DSL의 인스턴스를 허용 하는 코드가 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]합니다.  
  
## <a name="Debugging"></a> DSL을 실행합니다.  
 만든 즉시 DSL 솔루션을 실행할 수 있습니다. 나중에 수정할 수 있습니다 DSL 정의 점진적으로, 각 변경 후에 다시 솔루션을 실행 합니다.  
  
#### <a name="to-experiment-with-the-dsl"></a>DSL을 사용 하 여 실험  
  
1. 클릭 **모든 템플릿 변환** 솔루션 탐색기 도구 모음에서입니다. 이 대부분의 DslDefinition.dsl에서 소스 코드를 다시 생성합니다.  
  
   > [!NOTE]
   > DslDefinition.dsl을 변경할 때마다 눌러야 **모든 템플릿 변환** 솔루션을 다시 작성 하기 전에 합니다. 이 단계는 자동화할 수 있습니다. 자세한 내용은 [모든 템플릿 변환 자동화 방법](https://msdn.microsoft.com/b63cfe20-fe5e-47cc-9506-59b29bca768a)합니다.  
  
2. F5 키를 또는 **디버깅할** 메뉴에서 클릭 **디버깅 시작**합니다.  
  
    DSL을 빌드하고 실험적 인스턴스의 설치 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]합니다.  
  
    [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 의 실험적 인스턴스가 시작됩니다. 실험적 인스턴스에서 레지스트리를 별도 하위 트리에서 해당 설정을 여기서 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 확장 디버깅을 위해 등록 됩니다. 표준 인스턴스의 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 그곳에 등록 된 확장에 대 한 액세스 권한이 없습니다.  
  
3. 실험적 인스턴스에서 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], 명명 된 모델 파일을 엽니다 **테스트** 에서 **솔루션 탐색기**합니다.  
  
    \- 또는 -  
  
    디버깅 프로젝트를 마우스 오른쪽 **추가**를 클릭 하 고 **항목**합니다. 에 **항목 추가** 대화 상자에서 DSL의 파일을 입력 합니다.  
  
    모델 파일에 빈 다이어그램이 열립니다.  
  
    도구 상자 열리고 다이어그램 형식에 적합 한 도구를 표시 합니다.  
  
4. 다이어그램에서 모양 및 연결선을 만들려면 도구를 사용 합니다.  
  
   1. 셰이프를 만들려면 다이어그램 예제 셰이프 도구에서 끕니다.  
  
   2. 두 셰이프를 연결 하려면 예제 연결선 도구, 첫 번째 셰이프를 클릭 및 두 번째 셰이프를 클릭 합니다.  
  
5. 레이블을 변경 하려면 셰이프를 클릭 합니다.  
  
   실험적 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 다음 예와 비슷하게 표시 됩니다.  
  
   ![](../modeling/media/dsl-min.png "DSL_min")  
  
### <a name="the-content-of-a-model"></a>모델의 콘텐츠  
 DSL의 인스턴스인 파일의 내용을 호출 되는 *모델*합니다. 모델에 포함 된 *모델 요소* 하 고 *링크* 요소 사이입니다. DSL 정의의 모델 요소 유형을 지정 하 고 링크 된 모델에 있을 수 있습니다. 예를 들어 최소 언어 템플릿에서 만든 DSL의 모델 요소 형식 및가 한 가지 유형의 링크  
  
 DSL 정의 다이어그램에 모델을 표시 하는 방법을 지정할 수 있습니다. 다양 한 모양과 연결선의 스타일에서에서 선택할 수 있습니다. 다른 셰이프 안에 일부 셰이프에 나타나는지를 지정할 수 있습니다.  
  
 에 트리 모델을 볼 수는 **탐색기** 모델을 편집 하는 동안 확인 합니다. 다이어그램에 셰이프를 추가 하면 모델 요소는 또한 탐색기에 나타납니다. 탐색기를 다이어그램이 없습니다 경우에 사용할 수 있습니다.  
  
 디버깅 인스턴스에서 탐색기를 볼 수 없습니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]에 **보기** 선택 된 위치 **다른 Windows**, 클릭 하 고  *\<Your 언어 >* **탐색기**합니다.  
  
### <a name="the-api-of-your-dsl"></a>DSL의 API  
 DSL을 읽고 인스턴스인 DSL의 모델을 업데이트할 수 있는 API를 생성 합니다. API의 응용 프로그램 모델에서 텍스트 파일을 생성 하는 것입니다. 자세한 내용은 [T4 텍스트 템플릿을 사용 하 여 디자인 타임 코드 생성](../modeling/design-time-code-generation-by-using-t4-text-templates.md)합니다.  
  
 디버깅 솔루션에서 ".tt" 확장을 사용 하 여 템플릿 파일을 엽니다. 이러한 샘플에는 모델에서 텍스트를 생성 및 DSL의 API를 테스트할 수 있습니다 하는 방법을 보여 줍니다. 작성 된 샘플 중 하나 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]는 서로 [!INCLUDE[csprcs](../includes/csprcs-md.md)]합니다.  
  
 각 템플릿 아래에 있는 파일은 생성 하는 파일입니다. 솔루션 탐색기에서 템플릿 파일을 확장 하 고 생성된 된 파일을 엽니다.  
  
 템플릿 파일을 모델의 모든 요소를 나열 하는 코드의 짧은 세그먼트를 포함 합니다.  
  
 생성된 된 파일의 결과 포함합니다.  
  
 모델 파일을 변경 하면 파일을 다시 생성 한 후 생성 된 파일에서 해당 변경 내용이 표시 됩니다.  
  
##### <a name="to-regenerate-text-files-after-you-change-the-model-file"></a>모델 파일을 변경한 후 텍스트 파일을 다시 생성 하려면  
  
1. 실험적 인스턴스에서 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], 모델 파일을 저장 합니다.  
  
2. 각.tt 파일에서 파일 이름 매개 변수로 실험에 사용할 모델 파일을 나타내는지 확인 합니다. .Tt 파일을 저장 합니다.  
  
3. 클릭 **모든 템플릿 변형** 도구 모음에서 **솔루션 탐색기**합니다.  
  
    \- 또는 -  
  
    다시 생성 하 고 클릭 하려는 템플릿을 마우스 오른쪽 단추로 클릭 **사용자 지정 도구 실행**합니다.  
  
   텍스트 템플릿 파일을 프로젝트에 추가할 수 있습니다. 각 템플릿은 하나의 결과 파일을 생성합니다.  
  
> [!NOTE]
> DSL 정의 변경한 경우 샘플 텍스트 템플릿 코드가 작동 하지 않습니다,이 업데이트 하지 않으면.  
  
 자세한 내용은 참조 하세요. [도메인별 언어에서 코드 생성](../modeling/generating-code-from-a-domain-specific-language.md) 하 고 [도메인별 도메인별 언어 사용자 지정 하려면 코드 작성](../modeling/writing-code-to-customise-a-domain-specific-language.md)합니다.  
  
## <a name="customizing-the-dsl"></a>DSL 사용자 지정  
 DSL 정의 수정 하려는 경우 실험적 인스턴스를 닫고 기본에서 정의 업데이트 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 인스턴스.  
  
> [!NOTE]
> DSL 정의 수정한 후에 이전 버전을 사용 하 여 만든 테스트 모델에서 정보를 손실 될 수 있습니다.  예를 들어, 디버깅 솔루션에는 몇 가지 모양 및 연결선을 포함 하는 샘플 라는 파일이 있습니다. DSL 정의 개발을 시작한 후에 표시 되지 않습니다 및 파일을 저장할 때 손실 됩니다.  
  
 DSL에 다양 한 확장을 만들 수 있습니다. 다음 예제에서는 새 가능성을 제공 합니다.  
  
 DSL 정의 저장할 각 변경 후 클릭 **모든 템플릿 변환** 에서 **솔루션 탐색기**를 누릅니다 **F5** 변경 된 DSL을 사용 하 여 실험 합니다.  
  
### <a name="rename-the-types-and-tools"></a>형식 및 도구 이름 바꾸기  
 기존 도메인 클래스 및 관계의 이름을 바꿉니다. 예를 들어 최소 언어 템플릿에서 만든 Dsl 정의에서 시작 하며, DSL 패밀리 트리를 나타낼 수 있도록 다음과 같은 이름 바꾸기 작업을 수행할 수 있습니다.  
  
##### <a name="to-rename-domain-classes-relationships-and-tools"></a>도메인 클래스, 관계 및 도구 이름을 바꾸려면  
  
1. DslDefinition 다이어그램 이름 바꾸기 **ExampleModel** 하 **FamilyTreeModel**, **ExampleElement** 에 **Person**,  **대상** 하 **부모**, 및 **원본** 에 **자식을**합니다. 각 레이블을 변경 하려면 클릭 수 있습니다.  
  
     ![DSL 정의 다이어그램 &#45; 패밀리 트리 모델](../modeling/media/familyt-person.png "FamilyT_Person")  
  
2. 요소 및 연결선 도구를 이름을 바꿉니다.  
  
    1. 솔루션 탐색기에서 탭을 클릭 하 여 DSL 탐색기 창을 엽니다. 볼 수 없는 경우,에 **뷰** 메뉴 가리킵니다 **다른 Windows** 클릭 하 고 **DSL 탐색기**합니다. DSL 탐색기 DSL 정의 다이어그램이 활성 창인 경우에 표시 됩니다.  
  
    2. 속성 창을 열고 동시 DSL 탐색기 및 속성을 볼 수 있도록 배치 합니다.  
  
    3. DSL 탐색기에서 확장 **편집기**, **도구 상자 탭**를  *\<DSL >* 를 차례로 **도구**합니다.  
  
    4. 클릭 **ExampleElement**합니다. 요소를 만드는 데 사용 되는 도구 상자 항목입니다.  
  
    5. 속성 창에서 변경 된 **이름** 속성을 **Person**합니다.  
  
         다음에 유의 합니다 **캡션** 속성도 변경 합니다.  
  
    6. 동일한 방식으로 이름을 변경 합니다 **ExampleConnector** 도구를 **ParentLink**합니다. Alter 합니다 **캡션** 속성 한다는 이름 속성은 복사 되지 않도록 합니다. 예를 들어 입력 **부모 링크**합니다.  
  
3. DSL을 다시 작성 합니다.  
  
    1. DSL 정의 파일을 저장 합니다.  
  
    2. 클릭 **모든 템플릿 변환** 솔루션 탐색기의 도구 모음  
  
    3. F5 키를 누릅니다. 실험적 인스턴스에서 될 때까지 기다렸다가 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 나타납니다.  
  
4. 실험적 인스턴스에서 디버깅 솔루션에 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], 테스트 모델 파일을 엽니다. 도구 상자에서 끌어 요소를 끕니다. 도구 캡션 및 DSL 탐색기에 형식 이름이 변경 되었습니다. 알 수 있습니다.  
  
5. 모델 파일을 저장 합니다.  
  
6. .Tt 파일을 열고 새 이름을 사용 하 여 이전 형식 및 속성 이름을 바꿀 합니다.  
  
7. .Tt 파일에 지정 된 파일 이름을 테스트 모델을 지정 하는지 확인 합니다.  
  
8. .Tt 파일을 저장 합니다. .Tt 파일에서 코드를 실행 하는 결과 확인 하려면 생성 된 파일을 엽니다. 이 정확한 지 확인 합니다.  
  
### <a name="add-domain-properties-to-classes"></a>클래스에 도메인 속성을 추가 합니다.  
 예를 들어 사람의 사망 및 생년월일의 연도를 나타내는 도메인 클래스 속성을 추가 합니다.  
  
 새 속성에 표시 되도록 다이어그램을 추가 해야 합니다 *데코레이터* 모양으로 모델 요소를 표시 합니다. 또한 decorator에 속성을 매핑해야 합니다.  
  
##### <a name="to-add-properties-and-display-them"></a>속성을 추가 하 고 표시 하려면  
  
1. 속성을 추가 합니다.  
  
   1. DSL 정의 다이어그램에서 마우스 오른쪽 단추로 클릭 합니다 **Person** 도메인 클래스를 가리킵니다 **추가**를 클릭 하 고 **도메인 속성**합니다.  
  
   2. 와 같은 새 속성 이름 목록을 입력 **출생** 하 고 **사망**합니다. 키를 눌러 **Enter** 각각.  
  
2. 모양에 속성을 표시 하는 데코레이터를 추가 합니다.  
  
   1. 다이어그램의 다른 쪽에 Person 도메인 클래스에서 확장 되는 회색 선을 수행 합니다. 다이어그램 요소 맵을 이것이입니다. 도메인 클래스 모양 클래스에 연결 합니다.  
  
   2. 이 모양 클래스를 마우스 오른쪽 **추가**를 클릭 하 고 **텍스트 Decorator**합니다.  
  
   3. 같은 이름의 두 decorator를 추가 **BirthDecorator** 하 고 **DeathDecorator**합니다.  
  
   4. 각 새 decorator를 선택 하 고 속성 창에서 설정 된 **위치** 필드입니다. 이 도메인 속성 값을 모양에 표시할 위치를 결정 합니다. 예를 들어 설정할 **InnerBottomLeft** 하 고 **InnerBottomRight**합니다.  
  
        ![구획 모양 정의](../modeling/media/familyt-compartment.png "FamilyT_Compartment")  
  
3. Decorator는 속성에 매핑됩니다.  
  
   1. DSL 세부 정보 창을 엽니다. 일반적으로 출력 창 옆에 있는 탭입니다. 볼 수 없는 경우,에 **보기** 메뉴에서 **다른 Windows**를 클릭 하 고 **DSL 정보**.  
  
   2. DSL 정의 다이어그램에서 연결 하는 선을 클릭 합니다 **Person** 도메인 클래스 모양 클래스를 합니다.  
  
   3. **DSL 세부 정보**에 **Decorator 맵** 탭에서 매핑되지 않은 decorator는에 있는 확인란을 클릭 합니다. **표시 속성**, 원하는 매핑되어 도메인 속성을 선택 합니다. 예를 들어 매핑할 **BirthDecorator** 하 **출생**합니다.  
  
4. DSL을 저장 하 고, 모든 템플릿 변환을 클릭 및 F5 키를 누릅니다.  
  
5. 샘플 모델 다이어그램에서 이제 선택한 위치를 클릭 하 고 수 있는 값에 입력을 확인 합니다. 또한 선택 하면를 **Person** 셰이프의 속성 창에 생일 및 사망 새 속성이 표시 됩니다.  
  
6. .Tt 파일에서 각 사용자의 속성을 가져오는 코드를 추가할 수 있습니다.  
  
   ![패밀리 트리 다이어그램, 도구 상자 및 탐색기](../modeling/media/familyt-instance.png "FamilyT_Instance")  
  
### <a name="define-new-classes"></a>새 클래스를 정의 합니다.  
 도메인 클래스 및 관계를 모델에 추가할 수 있습니다. 예를 들어 마을과를 나타내는 사용자를 town에서 활성 상태로 유지 새 관계를 나타내는 새 클래스를 만들 수 있습니다.  
  
 다양 한 유형에 고유 모델 다이어그램을 위해 다른 기 하 도형 및 색을 사용 하 여 도형 또는 다른 종류의 도형, 도메인 클래스를 매핑할 수 있습니다.  
  
##### <a name="to-add-and-display-a-new-domain-class"></a>추가 하 고 새 도메인 클래스를 표시 합니다.  
  
1. 도메인 클래스를 추가 하 고 모델 루트의 자식으로 만듭니다.  
  
    1. DSL 정의 다이어그램을 클릭 합니다 **포함 관계** 도구는 루트 클래스를 클릭 합니다 **FamilyTreeModel**, 다이어그램의 빈 부분에서를 클릭 하 고 합니다.  
  
         새 도메인 클래스가 나타납니다 포함 관계를 사용 하 여 FamilyTreeModel에 연결 됩니다.  
  
         예를 들어 이름 설정 **Town**합니다.  
  
        > [!NOTE]
        > 모델의 루트를 제외한 모든 도메인 클래스 하나 이상 포함 관계의 대상 이거나 포함의 대상이 되는 클래스에서 상속 해야 합니다. 이 따라서 자주 포함 관계 도구를 사용 하 여 도메인 클래스를 만드는 편리한 것입니다.  
  
    2. 예를 들어 새 클래스에 도메인 속성을 추가 **이름을**입니다.  
  
2. Person 및 Town 간에 참조 관계를 추가 합니다.  
  
    1. 클릭 합니다 **참조 관계** 도구, 사용자를 클릭 한 다음 Town을 클릭 합니다.  
  
         ![DSL 정의 조각: 패밀리 트리 루트](../modeling/media/familyt-root.png "FamilyT_Root")  
  
        > [!NOTE]
        > 참조 관계는 다른 모델 트리의 한 부분에서 상호 참조를 나타냅니다.  
  
3. 모델 다이어그램에서 도심지 나타내는 셰이프를 추가 합니다.  
  
    1. 끌어서를 **기 하 도형** 다이어그램 도구 상자에서 예를 들어, 이름을 **TownShape**합니다.  
  
    2. 속성 창에서 새 셰이프의 채우기 색 등 기 하 도형 모양 필드를 설정 합니다.  
  
    3. 도시별으로의 이름을 표시 하는 데코레이터를 추가 하 고 NameDecorator 바꿉니다. 해당 위치 속성을 설정 합니다.  
  
4. 마을 도메인 클래스는 TownShape 매핑됩니다.  
  
    1. 클릭 합니다 **다이어그램 요소 맵을** Town 도메인 클래스 TownShape 모양 클래스와 다음를 클릭 한 다음 도구를 합니다.  
  
    2. 에 **Decorator 맵** 탭을 **DSL 세부 정보** 선택한 맵 커넥터를 사용 하 여 창을 NameDecorator를 확인 하 고 설정 **표시 속성** 이름에.  
  
5. 도심지와 사용자 간의 관계를 표시 하려면 커넥터를 만듭니다.  
  
    1. 도구 상자에서 다이어그램에 커넥터를 끕니다. 그 이름을 바꾸고 해당 모양 속성을 설정 합니다.  
  
    2. 사용 된 **다이어그램 요소 맵을** Person 및 Town 간의 관계에 새 커넥터를 연결 하는 도구입니다.  
  
         ![추가 된 모양 맵 사용 하 여 패밀리 트리 정의](../modeling/media/familyt-shapemap.png "FamilyT_ShapeMap")  
  
6. 새로운 지역 하기 요소 도구를 만듭니다.  
  
    1. **DSL 탐색기**를 확장 하 고 **편집기** 한 다음 **도구 상자 탭**합니다.  
  
    2. 마우스 오른쪽 단추로 클릭  *\<DSL >* 을 클릭 한 다음 **새 요소 도구 추가**합니다.  
  
    3. 설정 된 **이름** 새로운 도구 집합의 속성 해당 **클래스** Town 속성입니다.  
  
    4. 설정 된 **도구 상자 아이콘** 속성입니다. 클릭 **[...]**  고 합니다 **파일 이름** 필드, 아이콘 파일을 선택 합니다.  
  
7. 도심지와 사용자 간의 링크 하기 위한 커넥터 도구를 만듭니다.  
  
    1. 마우스 오른쪽 단추로 클릭  *\<DSL >* 을 클릭 한 다음 **새 커넥터 도구 추가**합니다.  
  
    2. 새 도구의 Name 속성을 설정 합니다.  
  
    3. 에 **ConnectionBuilder** 속성인 사용자 대 지역 관계의 이름을 포함 하는 작성기를 선택 합니다.  
  
    4. 설정 된 **도구 상자 아이콘**합니다.  
  
8. DSL 정의 저장, 클릭 **모든 템플릿 변형**, 누릅니다 **F5**합니다.  
  
9. 실험적 인스턴스에서 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], 테스트 모델 파일을 엽니다. 도심지 및 도심지와 사람 간의 링크를 만드는 새로운 도구를 사용 합니다. 만 요소의 올바른 형식 간의 링크를 만들 수 있는지 확인 합니다.  
  
10. 각 사용자 거주 하는 동을 나열 하는 코드를 만듭니다. 텍스트 템플릿은 이러한 코드를 실행 하는 위치 중 하나입니다. 예를 들어, 다음 코드를 포함 하는 디버깅 솔루션에 기존 Sample.tt 파일을 수정할 수 있습니다.  
  
    ```  
    <#@ template inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" debug="true" #>  
    <#@ output extension=".txt" #>  
    <#@ FamilyTree processor="FamilyTreeDirectiveProcessor" requires="fileName='Sample.ftree'" #>  
  
    <#  
      foreach (Person person in this.FamilyTreeModel.People)  
      {  
    #>  
        <#= person.Name #><#if (person.Town != null) {#> of <#= person.Town.Name #> <#}#>  
  
    <#  
          foreach (Person child in person.Children)  
      {  
    #>  
                <#= child.Name #>  
    <#  
      }  
      }  
    #>  
  
    ```  
  
     *.Tt 파일을 저장 하는 경우 사용자 및 해당 residences 목록을 포함 하는 보조 파일이 만들어집니다. 자세한 내용은 [도메인별 언어에서 코드 생성](../modeling/generating-code-from-a-domain-specific-language.md)합니다.  
  
## <a name="validation-and-commands"></a>유효성 검사 및 명령  
 유효성 검사 제약 조건을 추가 하 여이 DSL을 추가로 개발할 수 있습니다. 이러한 제약 조건은 모델 올바른 상태에서 인지 확인 하는 메서드를 정의할 수 있습니다. 예를 들어 정의할 수 있습니다 되도록 제약 조건을 자식의 생년월일 부모 보다 이후입니다. 유효성 검사 기능 DSL 사용자 제약 조건 중 하나를 중단 하는 모델을 저장 하려고 하는 경우 경고를 표시 합니다. 자세한 내용은 [도메인별 언어에서 유효성 검사](../modeling/validation-in-a-domain-specific-language.md)합니다.  
  
 또한 사용자가 호출할 수 있는 메뉴 명령을 정의할 수 있습니다. 명령에는 모델을 수정할 수 있습니다. 다른 모델과 상호 작용할 수도 있습니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 및 외부 리소스를 사용 하 여 합니다. 자세한 내용은 [방법: 표준 메뉴 명령 수정](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)합니다.  
  
## <a name="deploying-the-dsl"></a>DSL 배포  
 다른 사용자가 도메인 특정 언어를 사용할 수 있도록 배포를 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 확장 (VSIX) 파일입니다. DSL 솔루션을 빌드할 때 만들어집니다.  
  
 솔루션의 bin 폴더에서.vsix 파일을 찾습니다. 설치 하려는 컴퓨터에 복사 합니다. 컴퓨터에서 VSIX 파일을 두 번 클릭 합니다. DSL의 모든 인스턴스에서 사용할 수 있습니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 컴퓨터에 있습니다.  
  
 동일한 절차를 사용 하 여 DSL을 설치할 컴퓨터에 자체의 실험적 인스턴스를 사용할 필요가 없도록 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]합니다.  
  
 자세한 내용은 [도메인 특정 언어 솔루션 배포](../modeling/deploying-domain-specific-language-solutions.md)를 참조하세요.  
  
## <a name="Reset"></a> 오래 된 실험적 Dsl 제거  
 실험적 Dsl을 만들지 않은 경우 원하지 않는 다시 설정 하 여 컴퓨터에서 제거할 수는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 실험적 인스턴스.  
  
 모든 실험적 Dsl 및 실험적 다른 컴퓨터에서 제거 됩니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 확장 합니다. 이 디버깅 모드에서 실행 된 확장입니다.  
  
 이 절차가 완료 된 Dsl 또는 기타 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] VSIX 파일을 실행 하 여 완전히 설치 된 확장 합니다.  
  
#### <a name="to-reset-the-visual-studio-experimental-instance"></a>Visual Studio 실험적 인스턴스 다시 설정 하려면  
  
1. 클릭 **시작**, 클릭 **모든 프로그램**를 **Microsoft Visual Studio 2010 SDK**를 **도구**를 차례로 **Microsoft를 다시 설정 Visual Studio 2010 실험적 인스턴스**합니다.  
  
2. 모든 실험적 Dsl 또는 다른 실험적 다시 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 계속 사용 하려는 확장 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [모델, 클래스 및 관계 이해](../modeling/understanding-models-classes-and-relationships.md)   
 [도메인 특정 언어를 정의 하는 방법](../modeling/how-to-define-a-domain-specific-language.md)   
 [Visualizaton 및 모델링 SDK](http://go.microsoft.com/fwlink/?LinkID=186128)
