---
title: 사용자 지정 T4 텍스트 템플릿 지시문 프로세서 만들기
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, custom directive processors
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3f9d514178e4b899ca727e17ead260719697b562
ms.sourcegitcommit: 6a19c5ece38a70731496a38f2ef20676ff18f8a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65476644"
---
# <a name="create-custom-t4-text-template-directive-processors"></a>사용자 지정 T4 텍스트 템플릿 지시문 프로세서 만들기

*텍스트 템플릿 변형 프로세스* 사용을 *텍스트 템플릿* 파일을 입력 하 고 텍스트 파일을 출력으로 생성 합니다. 합니다 *텍스트 템플릿 변환 엔진* 프로세스 엔진과 상호 작용 하는 텍스트 템플릿 변형 호스트와 하나 이상의 텍스트 템플릿 컨트롤 *지시문 프로세서* 완료 하는 프로세스입니다. 자세한 내용은 [은 텍스트 템플릿 변형 프로세스](../modeling/the-text-template-transformation-process.md)합니다.

사용자 지정 지시문 프로세서를 만들려면 <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> 또는 <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>에서 상속하는 클래스를 만듭니다.

이 두 가지 차이점은 <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> 사용자 로부터 매개 변수를 가져오기 하 고 템플릿 출력 파일을 생성 하는 코드를 생성 하는 데 필요한 최소 인터페이스를 구현 합니다. <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> 구현 하는 디자인 패턴 필요/제공 합니다. <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> 두 개의 특수 매개 변수를 처리 `requires` 고 `provides`입니다.  예를 들어, 사용자 지정 지시문 프로세서를 수 있습니다 열고 사용자 로부터 파일 이름을 허용 및 파일을 읽고 저장 하는 파일의 텍스트 라는 변수에 `fileText`합니다. 서브 클래스를 <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> 클래스의 값으로 사용자의 파일 이름에 걸릴 수 있습니다 합니다 `requires` 값으로 텍스트를 저장 하려는 변수의 이름과 매개 변수를는 `provides` 매개 변수. 이 프로세서는 파일을 읽을 열고 텍스트 파일의 지정 된 변수에 저장 합니다.

텍스트 템플릿에서 Visual Studio에서 사용자 지정 지시문 프로세서를 호출 하기 전에 등록 해야 합니다.

레지스트리 키를 추가 하는 방법에 대 한 자세한 내용은 참조 하세요. [사용자 지정 지시문 프로세서 배포](../modeling/deploying-a-custom-directive-processor.md)합니다.

## <a name="custom-directives"></a>사용자 지정 지시문

사용자 지정 지시문은 다음과 같습니다.

`<#@ MyDirective Processor="MyDirectiveProcessor" parameter1="value1" ... #>`

텍스트 템플릿에서 외부 데이터 나 리소스에 액세스 하려는 경우 사용자 지정 지시문 프로세서를 사용할 수 있습니다.

다양 한 텍스트 템플릿 지시문 프로세서 다시 사용할 수 있도록 요소 코드 하는 방법을 제공 하므로 단일 지시문 프로세서를 제공 하는 기능을 공유할 수 있습니다. 기본 제공 `include` 지시문 이므로 마찬가지로 코드를 팩터링 하 고 다양 한 텍스트 템플릿 간에 공유를 사용할 수 있습니다. 차이 모든 기능을는 `include` 지시문 제공 고정 되어 있고 매개 변수를 허용 하지 않습니다. 텍스트 템플릿에 대 한 공통 기능을 제공 하 고 템플릿 매개 변수를 전달할 수 있도록 하려는 경우에 사용자 지정 지시문 프로세서를 만들어야 합니다.

사용자 지정 지시문 프로세서의 몇 가지 예는 다음과 같습니다.

- 사용자 이름 및 암호를 매개 변수로 허용 하는 데이터베이스에서 데이터를 반환 하는 지시문 프로세서.

- 매개 변수로 파일 이름을 허용 하는 파일을 열고 지시문 프로세서입니다.

### <a name="principal-parts-of-a-custom-directive-processor"></a>사용자 지정 지시문 프로세서의 주요 부분

클래스에서 상속 되는 지시문 프로세서를 개발 하려면 만들어야 <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> 또는 <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>합니다.

가장 중요 한 `DirectiveProcessor` 구현 해야 하는 메서드는 다음과 같습니다.

- `bool IsDirectiveSupported(string directiveName)` -반환 `true` 경우 지시문 프로세서가 명명된 된 지시문을 사용 하 여 처리할 수 있습니다.

- `void ProcessDirective (string directiveName, IDictionary<string, string> arguments)` -템플릿 엔진 템플릿에서 지시문의 각 항목에 대 한이 메서드를 호출합니다. 프로세서는 결과 저장 해야 합니다.

ProcessDirective()에 대 한 모든 호출 후 템플릿 엔진은 이러한 메서드를 호출 합니다.

- `string[] GetReferencesForProcessingRun()` -템플릿 코드에 필요한 어셈블리의 이름을 반환 합니다.

- `string[] GetImportsForProcessingRun()` -템플릿 코드에서 사용할 수 있는 네임 스페이스를 반환 합니다.

- `string GetClassCodeForProcessingRun()` -메서드, 속성 및 템플릿 코드를 사용할 수 있는 다른 선언의 코드를 반환 합니다. 이 작업을 수행 하는 가장 쉬운 방법은 C# 또는 Visual Basic 코드를 포함 하는 문자열을 작성 하는 경우 지시문 프로세서를 CLR 언어를 사용 하는 서식 파일에서 호출 될 수 있도록 하려면 문을 CodeDom 트리를 생성할 수 있으며 다음 템플릿에 의해 사용 되는 언어에서 트리를 직렬화 하는 작업의 결과 반환 수 있습니다.

- 자세한 내용은 [연습: 사용자 지정 지시문 프로세서 만들기](../modeling/walkthrough-creating-a-custom-directive-processor.md)합니다.

## <a name="see-also"></a>참고자료

- [사용자 지정 지시문 프로세서 배포](../modeling/deploying-a-custom-directive-processor.md) 사용자 지정 지시문 프로세서를 등록 하는 방법에 설명 합니다.
- [연습: 사용자 지정 지시문 프로세서 만들기](../modeling/walkthrough-creating-a-custom-directive-processor.md) 사용자 지정 지시문 프로세서를 만드는 방법, 등록 하 고 지시문 프로세서를 테스트 하는 방법 및 HTML로 출력 파일의 형식을 지정 하는 방법에 설명 합니다.