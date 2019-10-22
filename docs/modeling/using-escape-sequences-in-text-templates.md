---
title: 텍스트 템플릿에서 이스케이프 시퀀스 사용
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, escape sequences
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4e03f5eafc00b8431725ed06da10371a93692fb5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662926"
---
# <a name="use-escape-sequences-in-text-templates"></a>텍스트 템플릿에서 이스케이프 시퀀스 사용

텍스트 템플릿에서 이스케이프 시퀀스를 사용 하 여 텍스트 템플릿 태그를 생성 하 고 ( C# 코드만) 제어 문자 및 따옴표를 이스케이프할 수 있습니다.

표준 코드 블록의 여는 태그와 닫는 태그를 출력 파일에 인쇄 하려면 다음과 같이 태그를 이스케이프 합니다.

```
\<# ... \#>
```

다른 텍스트 템플릿 지시문 및 코드 블록 태그를 사용 하 여 동일한 작업을 수행할 수 있습니다.

텍스트 블록에 텍스트 템플릿 태그를 이스케이프 하는 데 사용 되는 문자열이 포함 된 경우 다음 이스케이프 시퀀스를 사용할 수 있습니다.

- 텍스트 템플릿 태그 앞에 짝수 개의 이스케이프 문자 (\\)가 오면 템플릿 파서는 이스케이프 문자의 절반을 포함 하 고 시퀀스를 텍스트 템플릿 태그로 포함 합니다. 예를 들어 텍스트 템플릿에 이스케이프 문자가 4 개 있는 경우 생성 된 파일에는 두 개의 "\\" 문자가 있습니다.

- 텍스트 템플릿 태그 앞에 홀수 개의 이스케이프 문자 (\\)가 오면 템플릿 파서는 "\\" 문자와 태그 자체 (\< # 또는 # >)의 절반을 포함 합니다. 태그는 텍스트 템플릿 태그로 간주 되지 않습니다.

- 이스케이프 (\\) 문자가 제어 문자나 따옴표를 이스케이프 하는 위치 이외의 다른 위치에 있는 경우 (의 경우에 C# 만) 문자는 직접 출력 됩니다.

## <a name="see-also"></a>참조

- [방법: 이스케이프 시퀀스를 사용하여 템플릿에서 템플릿 생성](../modeling/how-to-generate-templates-from-templates-by-using-escape-sequences.md)