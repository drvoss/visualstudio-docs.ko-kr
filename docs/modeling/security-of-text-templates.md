---
title: 텍스트 템플릿 보안
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, security
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 66159516c6b1360203130dedb56c0e6c192a118a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62824022"
---
# <a name="security-of-text-templates"></a>텍스트 템플릿 보안
텍스트 템플릿 모두 다음 보안 고려 사항:

- 텍스트 템플릿은 임의의 코드 삽입에 취약 합니다.

- 호스트 된 지시문 프로세서를 찾는 데 사용 하는 메커니즘에 보안이 설정 되지 않으면 악성 지시문 프로세서를 실행할 수 있습니다.

## <a name="arbitrary-code"></a>임의의 코드
 서식 파일을 작성 하는 경우 내 코드를 넣을 수 있습니다는 \<# # > 태그입니다. 이렇게 하면 임의의 코드를 텍스트 템플릿 내에서 실행할 수 있습니다.

 신뢰할 수 있는 출처에서 템플릿을 가져올 해야 합니다. 신뢰할 수 있는 출처에서 제공 되지 않은 템플릿을 실행 하지 않도록 응용 프로그램의 최종 사용자에 게 경고 해야 합니다.

## <a name="malicious-directive-processor"></a>악의적인 지시문 프로세서
 텍스트 템플릿 엔진 템플릿 텍스트를 출력 파일로 변환할 변환 호스트와 하나 이상의 지시문 프로세서를 사용 하 여 상호 작용 합니다. 자세한 내용은 [은 텍스트 템플릿 변형 프로세스](../modeling/the-text-template-transformation-process.md)합니다.

 호스트 된 지시문 프로세서를 찾는 데 사용 하는 메커니즘에 보안이 설정 되지 않으면 악성 지시문 프로세서를 실행 하는 위험이 실행 됩니다. 악의적인 지시문 프로세서에서 실행 되는 코드를 제공할 수 `FullTrust` 템플릿이 실행 될 때의 모드입니다. 사용자 지정 텍스트 템플릿 변형 호스트를 만드는 경우 지시문 프로세서를 찾으려고 엔진에 대 한 레지스트리와 같은 보안 메커니즘을 사용 해야 합니다.