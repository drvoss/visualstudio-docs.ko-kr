---
title: 'CA1806: 메서드 결과 무시 하지 마십시오 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1806
- DoNotIgnoreMethodResults
helpviewer_keywords:
- CA1806
- DoNotIgnoreMethodResults
ms.assetid: fd805687-0817-481e-804e-b62cfb3b1076
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 117e26fca367c8cf00604bebe01a00f4df58a0ee
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63437393"
---
# <a name="ca1806-do-not-ignore-method-results"></a>CA1806: 메서드 결과를 무시하지 마세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotIgnoreMethodResults|  
|CheckId|CA1806|  
|범주|Microsoft.Usage|  
|변경 수준|주요 변경 아님|  
  
## <a name="cause"></a>원인  
 이 경고에 대 한 몇 가지 가능한 이유는  
  
- 새 개체가 만들어지지만 사용 되지 않습니다.  
  
- 만들고 새 문자열을 반환 하는 메서드를 호출 하 고 새 문자열을 사용 되지 않습니다.  
  
- COM 또는 P/Invoke 메서드는 HRESULT 또는 오류 코드를 반환 하는 사용 되지 않습니다. 규칙 설명  
  
  불필요 한 개체 생성 및 사용 되지 않는 개체의 연결 된 가비지 수집에는 성능이 저하 됩니다.  
  
  문자열을 변경할 수 없는 및 String.ToUpper 등 호출 메서드에 있는 문자열의 인스턴스를 수정 하는 대신 문자열의 새 인스턴스를 반환 합니다.  
  
  HRESULT 또는 오류 코드를 무시 하면 리소스가 부족 하거나 오류 조건에서 예기치 않은 동작이 발생할 수 있습니다.  
  
## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법  
 메서드는 사용 되지 않는 B 개체의 새 인스턴스를 만드는 경우 인스턴스를 다른 메서드에 인수로 전달 하거나 인스턴스가 변수에 할당 합니다. 개체 생성이 필요한 경우 제거 합니다.-또는-  
  
 메서드는 B 메서드를 호출 되지만 B 메서드가 반환 하는 새 문자열 인스턴스를 사용 하지 않습니다. 인스턴스를 다른 메서드에 인수로 전달, 인스턴스를 변수에 할당 합니다. 또는 필요 없는 경우 호출을 제거 합니다.  
  
 또는  
  
 또는 오류 코드를 메서드는 메서드 B를 호출 하지만 HRESULT를 사용 하지 않는 경우에 메서드를 반환 합니다. 조건문에서 결과 사용 하 여, 결과 변수에 할당 또는 다른 메서드에 인수로 전달 합니다.  
  
## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우  
 개체를 만드는 작업에 몇 가지 용도로 사용 하지 않는 한이 규칙에서 경고를 표시 하지 마십시오.  
  
## <a name="example"></a>예제  
 다음 예제에서는 호출 String.Trim의 결과 무시 하는 클래스를 보여 줍니다.  
  
<!-- TODO: review snippet reference  [!CODE [FxCop.Usage.DoNotIgnoreMethodResults#1](FxCop.Usage.DoNotIgnoreMethodResults#1)]  -->  
  
## <a name="example"></a>예제  
 다음 예제에서는 호출 된 변수에 다시 String.Trim의 결과 할당 하 여 위반을 해결 합니다.  
  
<!-- TODO: review snippet reference  [!CODE [FxCop.Usage.DoNotIgnoreMethodResults2#1](FxCop.Usage.DoNotIgnoreMethodResults2#1)]  -->  
  
## <a name="example"></a>예제  
 다음 예제에서는 생성 된 개체를 사용 하지 않는 메서드를 보여 줍니다.  
  
> [!NOTE]
> Visual Basic에서이 위반을 재현할 수 없는 합니다.  
  
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults3/cpp/FxCop.Usage.DoNotIgnoreMethodResults3.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults3/cs/FxCop.Usage.DoNotIgnoreMethodResults3.cs#1)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults3#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults3/vb/FxCop.Usage.DoNotIgnoreMethodResults3.vb#1)]  
  
## <a name="example"></a>예제  
 다음 예제에서는 불필요 한 개체 생성을 제거 하 여 위반을 해결 합니다.  
  
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults4/cpp/FxCop.Usage.DoNotIgnoreMethodResults4.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults4/cs/FxCop.Usage.DoNotIgnoreMethodResults4.cs#1)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults4#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults4/vb/FxCop.Usage.DoNotIgnoreMethodResults4.vb#1)]  
  
## <a name="example"></a>예제  
 다음 예제에서는 GetShortPathName 네이티브 메서드에서 반환 하는 오류 코드를 무시 하는 메서드를 보여 줍니다.  
  
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults5/cpp/FxCop.Usage.DoNotIgnoreMethodResults5.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults5/cs/FxCop.Usage.DoNotIgnoreMethodResults5.cs#1)]  
  
## <a name="example"></a>예제  
 다음 예제에서는 오류 코드를 확인 하 고 호출에 실패 하면 예외를 throw 하 여 위반을 해결 합니다.  
  
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults6/cpp/FxCop.Usage.DoNotIgnoreMethodResults6.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults6/cs/FxCop.Usage.DoNotIgnoreMethodResults6.cs#1)]