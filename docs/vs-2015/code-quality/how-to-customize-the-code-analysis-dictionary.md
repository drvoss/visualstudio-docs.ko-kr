---
title: '방법: 코드 분석 사전 사용자 지정 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis dictionary
- custom dictionary, code analysis
- dictionary, code analysis
ms.assetid: 667e3b4e-beff-48be-b3d1-376e1716a895
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 26a9d65ed21eed00820a7968617c610e4b11c153
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68201353"
---
# <a name="how-to-customize-the-code-analysis-dictionary"></a>방법: 코드 분석 사전 사용자 지정
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

코드 분석의 다른 명명 규칙, 맞춤법 및 문법의 경우에는 오류에 대 한 코드의 식별자를 확인 하는 기본 제공 사전을 사용 하 여 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 지침입니다. 사용자 지정 사전을 Xml 파일을 추가, 제거 또는 수정 용어, 약어 및 기본 제공 사전에 머리 글자어를 만들 수 있습니다.  
  
 예를 들어, 코드 라는 클래스를 포함 **DoorKnokker**합니다. 코드 분석으로 두 단어의 복합 이름을 식별 합니다. **도어** 하 고 **knokker**합니다. 경고가 발생 한 다음 해당 하는 **knokker** 맞춤법이 잘못 되었다는 합니다. 철자를 인식 하도록 코드 분석을 적용할 용어를 추가할 수 있습니다 **knokker** 사용자 지정 사전입니다.  
  
## <a name="to-create-a-custom-dictionary"></a>사용자 지정 사전을 만드는  
 라는 파일을 만듭니다 **CustomDictionary.xml**합니다.  
  
 다음 XML 구조를 사용 하 여 사용자 지정 단어를 정의 합니다.  
  
```  
<Dictionary>  
      <Words>  
         <Unrecognized>  
            <Word>knokker</Word>  
         </Unrecognized>  
         <Recognized>  
            <Word></Word>  
         </Recognized>  
         <Deprecated>  
            <Term PreferredAlternate=""></Term>  
         </Deprecated>  
         <Compound>  
            <Term CompoundAlternate=""></Term>  
         </Compound>  
         <DiscreteExceptions>  
            <Term></Term>  
         </DiscreteExceptions>  
      </Words>  
      <Acronyms>  
         <CasingExceptions>  
            <Acronym></Acronym>  
         </CasingExceptions>  
      </Acronyms>  
   </Dictionary>  
```  
  
## <a name="custom-dictionary-elements"></a>사용자 지정 사전 요소  
 사용자 지정 사전의 다음 요소의 내부 텍스트와 용어를 추가 하 여 코드 분석 사전의 동작을 수정할 수 있습니다.  
  
- [사전 및 단어/인식/단어](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsRecognizedWord)  
  
- [사전 및 단어/인식할 수 없는/단어](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsUnrecognizedWord)  
  
- [사전/단어/사용 되지 않음/용어 [@PreferredAlternate]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDeprecatedTermPreferredAlternate)  
  
- [사전/단어/복합/용어 [@CompoundAlternate]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsCompoundTermCompoundAlternate)  
  
- [Dictionary/Words/DiscreteExceptions/Term](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDiscreteExceptionsTerm)  
  
- [Dictionary/Acronyms/CasingExceptions/Acronym](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryAcronymsCasingExceptionsAcronym)  
  
### <a name="BKMK_DictionaryWordsRecognizedWord"></a> 사전 및 단어/인식/단어  
 용어와 철자가 코드 분석을 식별 하는 용어 목록에 포함 하려면 사전 및 단어/인식/단어 요소의 내부 텍스트와 용어를 추가 합니다. 사전 및 단어/인식/단어 요소에서 대/소문자 구분 없는 합니다.  
  
 **예제**  
  
```  
<Dictionary>  
      <Words>  
         <Recognized>  
            <Word>knokker</Word>  
            ...  
         </Recognized>  
         ...  
      </Words>  
      ...  
</Dictionary>  
  
```  
  
 사전/단어/인식 노드에서 용어는 다음 코드 분석 규칙에 적용 됩니다.  
  
- [CA1701: 리소스 문자열 복합 단어에는 올바르게 표기를 사용 해야](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
- [CA1702: 복합 단어에는 올바르게 표기를 사용 해야](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
- [CA1703: 리소스 문자열에는 정확한 철자를 사용 해야](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
- [CA1704: 식별자에는 정확한 철자를 사용 해야](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
- [CA1709: 식별자에는 올바르게 표기를 사용 해야](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
- [CA1726: 기본 설정된 용어를 사용 합니다.](../code-quality/ca1726-use-preferred-terms.md)  
  
- [CA2204: 리터럴 철자가 맞아야 합니다.](../code-quality/ca2204-literals-should-be-spelled-correctly.md)  
  
### <a name="BKMK_DictionaryWordsUnrecognizedWord"></a> 사전 및 단어/인식할 수 없는/단어  
 코드 분석으로 올바르게 식별 하는 조건의 목록에서 용어를 제외 하려면 철자, 사전 및 단어/인식할 수 없음/단어 요소의 내부 텍스트와 제외 용어를 추가 합니다. 사전 및 단어/인식할 수 없음/단어 요소에서 대/소문자 구분 없는 합니다.  
  
 **예제**  
  
```  
<Dictionary>  
      <Words>  
         <Unrecognized>  
            <Word>meth</Word>  
            ...  
         </Unrecognized>  
         ...  
      </Words>  
      ...  
</Dictionary>  
  
```  
  
 인식할 수 없음 사전/단어/노드에서 용어는 다음 코드 분석 규칙에 적용 됩니다.  
  
- [CA1701: 리소스 문자열 복합 단어에는 올바르게 표기를 사용 해야](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
- [CA1702: 복합 단어에는 올바르게 표기를 사용 해야](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
- [CA1703: 리소스 문자열에는 정확한 철자를 사용 해야](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
- [CA1704: 식별자에는 정확한 철자를 사용 해야](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
- [CA1709: 식별자에는 올바르게 표기를 사용 해야](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
- [CA1726: 기본 설정된 용어를 사용 합니다.](../code-quality/ca1726-use-preferred-terms.md)  
  
- [CA2204: 리터럴 철자가 맞아야 합니다.](../code-quality/ca2204-literals-should-be-spelled-correctly.md)  
  
### <a name="BKMK_DictionaryWordsDeprecatedTermPreferredAlternate"></a> 사전/단어/사용 되지 않음/용어 [@PreferredAlternate]  
 코드 분석에 더 이상 사용 되지 식별 하는 용어 목록에 용어를 포함 하려면 사전/단어/사용 되지 않음/용어 요소의 내부 텍스트와 용어를 추가 합니다. 사용 되지 않는 용어는 철자가 하지만 사용 하지 않아야 하는 단어입니다.  
  
 경고에서 제안된 된 대체 용어를 포함 하려면 대체 용어 요소의 PreferredAlternate 특성에 지정 합니다. 대체를 제안 하지 않으려는 경우 특성 값을를 비워 둘 수 있습니다.  
  
- 사전/단어의 사용 되지 않는 용어 사용 되지 않음/용어 요소는 대/소문자 구분 하지 않습니다.  
  
- PreferredAlternate 특성 값은 대/소문자 구분입니다. 복합 대체에 대 한 파스칼식 대 / 소문자를 사용 합니다.  
  
  **예제**  
  
```  
<Dictionary>  
      <Words>  
         <Deprecated>  
            <Term PreferredAlternate="LogOn">login</Term>  
            ...  
         </Deprecated>  
         ...  
      </Words>  
      ...  
</Dictionary>  
  
```  
  
 용어 사전/단어/사용 되지 않는 노드는 다음 코드 분석 규칙에 적용 됩니다.  
  
- [CA1701: 리소스 문자열 복합 단어에는 올바르게 표기를 사용 해야](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
- [CA1702: 복합 단어에는 올바르게 표기를 사용 해야](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
- [CA1703: 리소스 문자열에는 정확한 철자를 사용 해야](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
- [CA1704: 식별자에는 정확한 철자를 사용 해야](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
- [CA1726: 기본 설정된 용어를 사용 합니다.](../code-quality/ca1726-use-preferred-terms.md)  
  
### <a name="BKMK_DictionaryWordsCompoundTermCompoundAlternate"></a> 사전/단어/복합/용어 [@CompoundAlternate]  
 기본 제공 사전 복합 용어 보다는 단일, discrete 조건으로 몇 가지 용어를 식별합니다. 코드 분석 복합 단어를 식별 하는 단어 목록에서 용어를 포함 하 고 조건의 올바른 대/소문자를 지정할 사전/단어/복합/용어 요소의 내부 텍스트와 용어를 추가 합니다. 용어 요소의 CompoundAlternate 특성에 (파스칼식 대 / 소문자)는 개별 단어의 첫 글자를 활용 하 여 복합 용어를 구성 하는 개별 단어를 지정 합니다. Note 내부 텍스트에 지정 된 용어 사전/단어/DiscreteExceptions 목록에 자동으로 추가 됩니다.  
  
- 사전/단어의 사용 되지 않는 용어 사용 되지 않음/용어 요소는 대/소문자 구분 하지 않습니다.  
  
- PreferredAlternate 특성 값은 대/소문자 구분입니다. 복합 대체에 대 한 파스칼식 대 / 소문자를 사용 합니다.  
  
  **예제**  
  
```  
<Dictionary>  
      <Words>  
         <Compound>  
            <Term CompoundAlternate="CheckBox">checkbox</Term>  
            ...  
         </Compound>  
         ...  
      </Words>  
      ...  
</Dictionary>  
  
```  
  
 사전/단어/복합 노드에서 용어는 다음 코드 분석 규칙에 적용 됩니다.  
  
- [CA1701: 리소스 문자열 복합 단어에는 올바르게 표기를 사용 해야](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
- [CA1702: 복합 단어에는 올바르게 표기를 사용 해야](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
- [CA1703: 리소스 문자열에는 정확한 철자를 사용 해야](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
- [CA1704: 식별자에는 정확한 철자를 사용 해야](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
### <a name="BKMK_DictionaryWordsDiscreteExceptionsTerm"></a> 사전/단어/DiscreteExceptions/용어  
 코드 분석을 단일 하 게 식별 하는 조건 목록에서 용어를 제외 하려면 용어 복합 단어에 대 한 대/소문자 구분 규칙에 의해 선택 될 때 개별 단어는 사전/단어/DiscreteExceptions/용어 요소의 내부 텍스트와 용어를 추가 합니다. 사전/단어/DiscreteExceptions/용어 요소의 기간은 대/소문자 구분입니다.  
  
 **예제**  
  
```  
<Dictionary>  
      <Words>  
         <DiscreteExceptions>  
            <Term>checkbox</Term>  
            ...  
         </DiscreteExceptions>  
         ...  
      </Words>  
      ...  
</Dictionary>  
  
```  
  
 사전/단어/DiscreteExceptions 노드에서 용어는 다음 코드 분석 규칙에 적용 됩니다.  
  
- [CA1701: 리소스 문자열 복합 단어에는 올바르게 표기를 사용 해야](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
- [CA1702: 복합 단어에는 올바르게 표기를 사용 해야](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
### <a name="BKMK_DictionaryAcronymsCasingExceptionsAcronym"></a> 사전/머리 글자어/CasingExceptions/머리글자어  
 머리글자어 코드 분석 철자가으로 식별 하는 용어 목록에 포함할 및 머리글자어 대/소문자를 구분 하 여 기간을 선택 하면 복합 단어에 대 한 규칙 방법을 나타내기 위해 용어 사전/머리 글자어/CasingExceptions의 내부 텍스트를 추가 / 머리글자어 요소입니다. 사전/머리 글자어/CasingExceptions/머리글자어 요소의 라는 머리글자어는 대/소문자 구분입니다.  
  
 **예제**  
  
```  
<Dictionary>  
      <Acronyms>  
         <CasingExceptions>  
            <Acronym>NESW</Acronym>   <!-- North East South West -->  
            ...  
         </CasingExceptions>  
         ...  
      </Acronyms>  
      ...  
</Dictionary>  
  
```  
  
 사전/머리 글자어/CasingExceptions 노드에서 용어는 다음 코드 분석 규칙에 적용 됩니다.  
  
- [CA1709: 식별자에는 올바르게 표기를 사용 해야](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
## <a name="BKMK_ToApplyACustomDictionaryToAProject"></a> 사용자 지정 사전을 프로젝트에 적용 하려면  
  
1. **솔루션 탐색기**, 다음 절차 중 하나를 사용 합니다.  
  
2. 사전에 단일 프로젝트를 추가 하려면 프로젝트 이름을 마우스 오른쪽 단추로 클릭 하 고 클릭 **기존 항목 추가**합니다. 파일을 지정 합니다 **기존 항목 추가** 대화 상자.  
  
3. 두 개 이상의 프로젝트 간에 공유 되는 사전에 추가 하려면 공유에서 파일을 찾습니다 합니다 **기존 항목 추가** 대화 상자에서 아래쪽 화살표를 클릭 합니다 **추가** 단추를 클릭 한 다음 **링크로 추가** .  
  
4. **솔루션 탐색기**를 마우스 오른쪽 단추로 클릭 합니다 **CustomDictionary.xml** 파일 이름 및 클릭 **속성**합니다.  
  
5. **빌드 작업** 목록에서 **CodeAnalysisDictionary**합니다.  
  
6. **출력 디렉터리로 복사** 목록에서 **복사 하지 않으려면**합니다.
