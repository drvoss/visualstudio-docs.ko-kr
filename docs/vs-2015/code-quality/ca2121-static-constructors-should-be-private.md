---
title: 'CA2121: 정적 생성자는 private 이어야 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2121
- StaticConstructorsShouldBePrivate
helpviewer_keywords:
- CA2121
- StaticConstructorsShouldBePrivate
ms.assetid: ee93c620-8fc1-4e47-866c-d389c3ca9f2e
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: d7894b4ec0039b28a579239605c22c2397c300f3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68154339"
---
# <a name="ca2121-static-constructors-should-be-private"></a>CA2121: 정적 생성자는 private이어야 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|StaticConstructorsShouldBePrivate|
|CheckId|CA2121|
|범주|Microsoft.Security|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 한 형식은 개인 아닌 정적 생성자에 설명 합니다.

## <a name="rule-description"></a>규칙 설명
 정적 생성자는 클래스 생성자 라고도 형식을 초기화 됩니다. 시스템에서는 형식의 첫 번째 인스턴스가 만들어지거나 static 멤버가 참조되기 전에 static 생성자를 호출합니다. 사용자가 정적 생성자가 호출 하는 경우 제어 하지 않습니다. static 생성자가 private이 아니면 시스템 이외의 코드에서 이를 호출할 수 있습니다. 이렇게 되면 생성자에서 수행하는 작업에 따라 예기치 않은 동작이 발생할 수 있습니다.

 이 규칙은 C# 및 Visual Basic.NET 컴파일러에서 적용 됩니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 위반은 일반적으로 다음 작업 중 하나에 의해 발생 됩니다.

- 유형에 대 한 정적 생성자를 정의 하 고 이루어지지 않았다는 개인입니다.

- 프로그래밍 언어 컴파일러는 형식에는 기본 정적 생성자를 추가 하 고 이루어지지 않았다는 개인.

  위반의 첫 번째 종류를 해결 하려면 정적 생성자를 비공개로 설정 합니다. 두 번째 종류를 해결 하려면 형식에는 개인 정적 생성자를 추가 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이러한 위반은 표시 하지 마십시오. 정적 생성자를 명시적으로 호출 해야 하는 소프트웨어 디자인에 호스팅되고 디자인 심각한 결함을 포함 하 고 검토 해야 합니다.
