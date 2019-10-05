---
title: FxCopCmd 오류 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- FxCopCmd errors
ms.assetid: bb614ed0-1b7c-4b56-99ae-da50ef6cfef9
caps.latest.revision: 12
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3e0770654f564c57cf576666dcd9575f47d9ce1c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63432287"
---
# <a name="fxcopcmd-errors"></a>FxCopCmd 오류
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
  
 심각한 오류에 대 한 분석 오류가 반환 됩니다. 분석을 완료할 수 없습니다 나타냅니다. 해당 하는 경우 오류 코드는 또한 치명적인 오류의 근본 원인을 포함 합니다. 다음과 같은 오류를 생성합니다.  
  
- 분석 부족 하 여 입력에 의해 발생 수행할 수 없습니다.  
  
- 분석에 FxCopCmd에서 처리 되지 않은 예외가 발생 합니다.  
  
- 지정한 프로젝트 파일을 찾을 수 없습니다 또는 손상 되었습니다.  
  
- 출력 옵션 지정 되지 않았거나 파일을 쓸 수 없습니다.  
  
    > [!NOTE]
    > FxCopCmd "어셈블리 참조 오류" 코드 반환 0x200 자체는 오류가 아닌 경고 합니다. 이 반환 코드에는 누락 된 간접 참조를 찾을 수 있지만 FxCopCmd 처리할 수 있음을 나타냅니다. 이 분석 결과 일부 손상 되었을 수 있을 수 있다는 경고입니다. 다른 모든 반환 코드와 결합 된 경우를 오류로 반환 코드 "어셈블리는 오류를 참조 하는 데 사용"을 고려해 보세요.  
  
## <a name="see-also"></a>참고 항목  
 [코드 분석 애플리케이션 오류](../code-quality/code-analysis-application-errors.md)