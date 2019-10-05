---
title: 설명서 경고
ms.date: 09/16/2019
ms.topic: reference
f1_keywords:
- vs.codeanalysis.documentationrules
helpviewer_keywords:
- documentation warnings
- managed code analysis warnings, documentation warnings
- warnings, documentation
author: mavasani
ms.author: mavasani
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 00b42dc20b228e30a9b2632a0525a1ec8a9ddbb1
ms.sourcegitcommit: 541a0556958201ad6626bc8638406ad02640f764
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2019
ms.locfileid: "71079212"
---
# <a name="documentation-warnings"></a>설명서 경고

설명서 경고는 외부에서 볼 수 있는 Api에 대 한 [XML 문서 주석을](https://docs.microsoft.com/dotnet/csharp/codedoc) 올바르게 사용 하 여 잘 문서화 된 라이브러리를 작성할 수 있도록 지원 합니다.

## <a name="in-this-section"></a>단원 내용

| 규칙 | 설명 |
| - | - |
| [CA1200: 접두사를 사용 하 여 cref 태그 사용 방지](../code-quality/ca1200.md) | XML 문서 태그의 [cref](https://docs.microsoft.com/dotnet/csharp/programming-guide/xmldoc/cref-attribute) 특성은 "코드 참조"를 의미 합니다. 태그의 내부 텍스트를 형식, 메서드, 속성 등의 코드 요소로 지정합니다. 컴파일러가 참조 `cref` 를 확인 하는 것을 방지 하므로 접두사와 함께 태그를 사용 하지 마십시오. 또한 Visual Studio IDE (통합 개발 환경)에서 리팩터링 중에 이러한 기호 참조를 찾아 업데이트할 수 없습니다. |

## <a name="see-also"></a>참고자료

- [코드 분석 경고](../code-quality/code-analysis-for-managed-code-warnings.md)
