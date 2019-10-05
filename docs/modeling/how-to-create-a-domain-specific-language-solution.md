---
title: '방법: 도메인 특정 언어 솔루션 만들기'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.designerwizard
helpviewer_keywords:
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools], creating domain-specific language
- Domain-Specific Language Tools, creating solutions
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0ac8a47aeca8875dabe3fdf388e9a73d68ec514e
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63445213"
---
# <a name="how-to-create-a-domain-specific-language-solution"></a>방법: 도메인 특정 언어 솔루션 만들기
도메인 특정 언어 (DSL) 특수 한 Visual Studio 솔루션을 사용 하 여 만들어집니다.

## <a name="prerequisites"></a>전제 조건

이 절차를 시작 하기 전에 이러한 구성 요소를 설치 합니다.

- Visual Studio
- Visual Studio SDK (의 일부로 설치 합니다 **Visual Studio 확장 개발** 작업)
- Modeling SDK (Visual Studio 구성 요소로 설치)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="creating-a-domain-specific-language-solution"></a>도메인별 언어 솔루션 만들기

1. 새 DSL 마법사 시작 **도메인별 언어 디자이너** 프로젝트입니다.

   > [!NOTE]
   > 프로젝트에 대해 선택한 이름은 올바른 시각적 개체 이름 이어야 합니다 가급적 C# 식별자 코드 생성에 사용할 수 있으므로 합니다.

   ::: moniker range="vs-2017"

   ![DSL 만들기 대화 상자](../modeling/media/create_dsldialog.png)

   ::: moniker-end

2. DSL 템플릿을 선택 합니다.

    에 **도메인별 언어 옵션 선택** 페이지와 같은 솔루션 템플릿 중 하나를 선택 합니다 **최소 언어**합니다. 만들려는 DSL 비슷한 템플릿을 선택 합니다.

    솔루션 템플릿에 대 한 자세한 내용은 참조 하십시오 [도메인별 언어 솔루션 템플릿 선택](../modeling/choosing-a-domain-specific-language-solution-template.md)합니다.

3. 파일 이름 확장명을 입력 합니다 **파일 확장명** 페이지입니다. 컴퓨터에서 고유 해야 하 고 DSL을 설치 하려는 모든 컴퓨터에서. 메시지가 나타납니다 **응용 프로그램이 나 Visual Studio 편집기는이 확장을 사용할**합니다.

   - 완전히 설치 되지 않은 이전 실험적 Dsl의 파일 이름 확장명을 사용한 경우 지울 수는 있습니다 축소를 사용 하 여 합니다 **실험적 인스턴스 재설정** 도구 [Visual Studio SDK] 메뉴에서 찾을 수 있습니다.

   - 이 파일 확장명을 사용 하는 다른 Visual Studio 확장 컴퓨터에 완전히 설치 된 경우에 제거 하는 것이 좋습니다. 에 **도구** 메뉴에서 클릭 **확장 관리자**합니다.

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

- Visual Studio 실험적 인스턴스를 다시 설정 합니다. 이전에 만든 Dsl의 모든 등록을 취소 합니다. 에 **시작** 메뉴에서 클릭 **모든 프로그램**, **Microsoft Visual Studio 2010 SDK**, **도구**를 차례로 **다시 설정 합니다 Microsoft Visual Studio 2010 실험적 인스턴스**합니다. 다시 사용 하려는 다른 모든 Dsl을 다시 작성할 수 있습니다.

     \- 또는 -

- Visual Studio Extension이 파일 확장명을 사용 하는 컴퓨터에 완전히 설치 된 경우이 제거 합니다. 에 **도구** 메뉴에서 클릭 **확장 관리자**합니다.

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
 **강력한 이름 키 파일을 만드는** DSL 어셈블리에 서명할 새 키를 만드는 기본 옵션입니다.

 **기존의 강력한 이름 키를 사용 하 여** 다른 어셈블리를 사용 하 여 DSL을 통합 하려는 경우이 옵션을 사용 합니다.

 강력한 이름 지정에 대 한 자세한 내용은 참조 하세요. [강력한 어셈블리 만들기 및 사용](http://go.microsoft.com/fwlink/?LinkId=186073)합니다.

## <a name="see-also"></a>참고자료

- [도메인별 언어 정의 방법](../modeling/how-to-define-a-domain-specific-language.md)
- [도메인 특정 언어 도구 용어집](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
