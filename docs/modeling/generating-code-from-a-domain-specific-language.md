---
title: 도메인별 언어에서 코드 생성
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 37c60ed42e7d4a7604dc3d99f7e0311c7000b99c
ms.sourcegitcommit: 6a19c5ece38a70731496a38f2ef20676ff18f8a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65476517"
---
# <a name="generating-code-from-a-domain-specific-language"></a>도메인별 언어에서 코드 생성

Microsoft [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] 모델에 표현 된 데이터에서 코드, 문서, 구성 파일 및 기타 아티팩트를 생성 하는 강력한 방법을 제공 합니다. 사용 하 여 [!INCLUDE[dsl](../modeling/includes/dsl_md.md)], 데이터를 나타내는 클래스의 집합을 만들 수 있습니다 및 이름이 클래스에서 텍스트 템플릿을 작성할 수 있습니다 및 해당 데이터를 반영 하는 속성입니다.

예를 들어, Fabrikam 고객 이름 및 전자 메일 주소 XML 파일을 있습니다. 개발자는 고객은 클래스, 속성 이름 및 전자 메일을 사용 하 여 모델을 만듭니다. HTML 페이지의 일부로 모든 고객의 테이블을 생성 하는이 부분을 포함 하 여 데이터를 처리 하는 데 여러 텍스트 템플릿을 작성 합니다.

```
<table>
<# foreach (Customer c in ContactList) {  #>
  <tr><td> <#= c.FullName #> </td>
      <td> <#= c.EmailAddress #> </td> </tr>
<# } #>  </table>
```

고객 데이터베이스를 처리할 때 XML 파일 모델 저장소로 읽힙니다. A *지시문 프로세서*사용 하 여 만든 [!INCLUDE[dsl](../modeling/includes/dsl_md.md)], 텍스트 템플릿에서 Customer 클래스를 코드에 사용할 수 있도록 합니다. 많은 텍스트 템플릿은 동일한 저장소에 대해 실행할 수 있습니다.

텍스트 템플릿에 필수적인 [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]합니다. VSPackage 및 Visual Studio를 사용 하 여 도구를 통합 하는 데 사용 되는 컨트롤도 도메인 모델의 요소에 대 한 소스 코드 생성 사용 됩니다.

이 섹션에서는 만들기, 수정 및 사용 하는 텍스트 템플릿을 디버그 하는 방법 중 일부를 설명 [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]합니다.

## <a name="in-this-section"></a>섹션 내용

[텍스트 템플릿에서 모델에 액세스](../modeling/accessing-models-from-text-templates.md)\
텍스트 템플릿에서 도메인 특정 언어를 참조 하는 방법에 대 한 기본 정보를 제공 합니다.

[연습: 모델에 액세스 하는 텍스트 템플릿 디버그](../modeling/walkthrough-debugging-a-text-template-that-accesses-a-model.md)\
문제 해결 및 도메인 특정 언어를 가리키는 텍스트 템플릿 디버깅을 수행 하는 방법을 설명 합니다.

[연습: 생성된 된 지시문 프로세서에 호스트 연결](../modeling/walkthrough-connecting-a-host-to-a-generated-directive-processor.md)\
생성된 된 지시문 프로세서에 사용자 지정 호스트를 연결 하는 방법에 설명 합니다.

[DslTextTransform 명령](../modeling/the-dsltexttransform-command.md)\
도메인 특정 언어를 참조 하는 텍스트 템플릿에 대 한 명령줄에서 TextTransform 실행 파일을 실행 하는 명령 파일을 설명 합니다.

## <a name="reference"></a>참조

[T4 텍스트 템플릿 쓰기](../modeling/writing-a-t4-text-template.md)\
텍스트 템플릿 지시문 및 제어 블록의 구문을 제공합니다.

## <a name="related-sections"></a>관련 단원

[T4 텍스트 템플릿을 사용하여 디자인 타임 코드 생성](../modeling/design-time-code-generation-by-using-t4-text-templates.md)\
텍스트 템플릿 변형 프로세스에 설명합니다.

[빌드 프로세스에서 코드 생성](../modeling/code-generation-in-a-build-process.md)\
빌드 서버에서 DSL에서 파일을 생성 하는 경우이 항목을 읽습니다.