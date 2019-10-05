---
title: 'CA1400: P / Invoke 진입점이 있어야 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1400
- PInvokeEntryPointsShouldExist
helpviewer_keywords:
- PInvokeEntryPointsShouldExist
- CA1400
ms.assetid: 1d64e470-7b2f-4cca-8fb0-ac92829e6332
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 0e5696689d0aa40f4af2e11970c81b47737a3d80
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68200380"
---
# <a name="ca1400-pinvoke-entry-points-should-exist"></a>CA1400: P/Invoke 진입점이 있어야 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|PInvokeEntryPointsShouldExist|
|CheckId|CA1400|
|범주|Microsoft.Interoperability|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 Public 또는 protected 메서드를 사용 하 여 표시할지를 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>입니다. 관리되지 않는 라이브러리를 찾을 수 없거나 해당 메서드와 라이브러리의 함수가 일치하지 않습니다. 규칙을 찾지 못하면 메서드 이름을 지정 된 대로 정확 하 게 찾습니다 ANSI 또는 메서드의 와이드 문자 버전을 'A' 또는 'W'를 사용 하 여 메서드 이름에 접미사로 붙여. 일치 하는 항목이 __stdcall 이름 형식을 사용 하 여 함수를 찾으려고 시도 (_MyMethod@12, 여기서 12는 인수의 길이 나타냄). 일치 항목이 없으면, 메서드 이름 '#'으로 시작 하는 경우 규칙 함수 이름 대신 서 수 참조로 검색 합니다.

## <a name="rule-description"></a>규칙 설명
 컴파일 타임 검사 안 함 확인 수로 표시 된 메서드 <xref:System.Runtime.InteropServices.DllImportAttribute> 참조 된 관리 되지 않는 DLL에 있습니다. 라이브러리에서 지정 된 이름이 없는 함수는 메서드에 대 한 인수는 함수 인수와 일치 하지 않습니다, 경우 공용 언어 런타임 예외를 throw 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 있는 메서드를 수정 합니다 <xref:System.Runtime.InteropServices.DllImportAttribute> 특성입니다. 관리 되지 않는 라이브러리 존재 하 고 메서드를 포함 하는 어셈블리와 동일한 디렉터리에 있는지 확인 합니다. 라이브러리 있고 올바르게 참조 인 경우 메서드 이름, 반환 형식 및 인수 서명 라이브러리 함수를 일치 하는지 확인 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 관리 되지 않는 라이브러리를 참조 하는 관리 되는 어셈블리와 동일한 디렉터리에 경우에이 규칙에서 경고를 표시 하지 마십시오. 안전 하 게 관리 되지 않는 라이브러리를 찾을 수 없는 경우에는이 규칙에서 경고를 표시 하지 않을 수 있습니다.

## <a name="example"></a>예제
 다음 예제에서는 규칙을 위반 하는 형식을 보여 줍니다. 라고 하는 함수가 `DoSomethingUnmanaged` kernel32.dll에서 발생 합니다.

 [!code-csharp[FxCop.Interoperability.DLLExists#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DLLExists/cs/FxCop.Interoperability.DLLExists.cs#1)]

## <a name="see-also"></a>관련 항목
 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>
