---
title: FxCopCmd 오류
ms.date: 10/19/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
helpviewer_keywords:
- FxCopCmd errors
ms.author: gewarren
author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4d723065e224058b7e269299aad2900f97a1425d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62936649"
---
# <a name="fxcopcmd-tool-errors"></a>FxCopCmd 도구 오류

FxCopCmd 심각한 되도록 모든 오류를 고려 하지 않습니다. FxCopCmd 부분 분석을 수행 하는 데 충분 한 정보가 있으면 발생 하는 분석 및 보고서 오류 수행 합니다. 32 비트 정수 오류 코드, 오류에 해당 하는 숫자 값의 비트 조합을 포함 합니다.

다음 표에서 FxCopCmd 반환한 오류 코드를 보여 줍니다.

|Error|숫자 값|
|-----------|-------------------|
|오류 없이|0x0|
|분석 오류|0x1|
|규칙 예외|0x2|
|프로젝트 로드 오류|0x4|
|어셈블리 로드 오류|0x8|
|규칙 라이브러리 로드 오류|0x10|
|보고서 가져오기 로드 오류|0x20|
|출력 오류|0x40|
|명령줄 스위치 오류|0x80|
|초기화 오류|0x100|
|어셈블리 참조 오류|0x200|
|BuildBreakingMessage|0x400|
|알 수 없는 오류|0x1000000|

**분석 오류** 오류가 반환 됩니다. 분석을 완료할 수 없습니다 나타냅니다. 해당 하는 경우 오류 코드는 또한 치명적인 오류의 근본 원인을 포함 합니다. 다음과 같은 오류를 생성합니다.

- 부족 한 입력으로 인해 분석을 수행할 수 없습니다.

- 분석에 FxCopCmd에서 처리 되지 않은 예외가 발생 합니다.

- 지정한 프로젝트 파일을 찾을 수 없습니다 또는 손상 되었습니다.

- 출력 옵션 지정 되지 않았거나 파일을 쓸 수 없습니다.

> [!NOTE]
> FxCopCmd 반환 코드 **어셈블리 참조 오류** 0x200 자체는 오류가 아닌 경고 합니다. 이 반환 코드 FxCopCmd에서 처리할 수 없는 누락 대 한 간접 참조를 나타냅니다. 경고는 분석 결과 일부 손상 되었을 수 가능성이 있는 것을 의미 합니다. 처리 **어셈블리 참조 오류** 으로 다른 모든 반환 코드와 결합 된 경우 오류가 발생 합니다.

## <a name="see-also"></a>참고자료

- [코드 분석 애플리케이션 오류](../code-quality/code-analysis-application-errors.md)