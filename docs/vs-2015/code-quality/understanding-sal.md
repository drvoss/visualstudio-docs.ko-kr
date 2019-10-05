---
title: SAL 이해 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: a94d6907-55f2-4874-9571-51d52d6edcfd
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: jillfra
ms.openlocfilehash: 0a898096c282a22201d60995693144cc0e187812
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435392"
---
# <a name="understanding-sal"></a>SAL 이해
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Microsoft 소스 코드 주석 언어 (SAL) 함수에서 해당 매개 변수에 가정 및 완료 될 때 수행 하는 보장을 사용 하는 방법을 설명 하는 데 사용할 수 있는 주석의 집합을 제공 합니다. 주석 헤더 파일에 정의 된 `<sal.h>`합니다. Visual Studio 코드 분석에 대 한 C++ SAL 주석을 사용 하 여 함수에 대 한 분석 내용을 수정 합니다. Windows 드라이버 개발에 대 한 SAL 2.0에 대 한 자세한 내용은 참조 [Windows 드라이버에 대 한 SAL 2.0 주석](http://go.microsoft.com/fwlink/?LinkId=250979)합니다.  
  
 기본적으로, C 및 C++ 개발자가 일관 되 게 의도 및 불변성을 표현 하는 데만 제한적된으로 제공 합니다. SAL 주석을 사용 하 여 하를 사용 하는 개발자 사용 하는 방법을 보다 잘 이해할 수 있도록 자세히 함수를 설명할 수 있습니다.  
  
## <a name="what-is-sal-and-why-should-you-use-it"></a>SAL의 정의 및 이를 사용해야 하는 이유  
 간단히 말해서 SAL는 코드를 확인 하 고 컴파일러에 저렴 한 방법입니다.  
  
### <a name="sal-makes-code-more-valuable"></a>코드의 품질을 높이는 SAL  
 코드 디자인 더 이해할 수 있도록, 사용자와 코드 분석 도구에 대 한 SAL 수 있습니다. C 런타임 함수를 보여 주는이 예제를 살펴보세요. `memcpy`:  
  
```cpp  
  
void * memcpy(  
   void *dest,   
   const void *src,   
   size_t count  
);  
  
```  
  
 이 함수가 수행 하는 새로운 알 수 있습니까? 함수를 호출 또는 구현 된 경우 프로그램 정확성을 유지 하려면 특정 속성을 유지 되어야 합니다. 예와에서 같은 선언을 확인 하 여 무엇 인지 모르는 경우 SAL 주석 없이 문서 또는 코드 주석에 의존 해야 합니다. 다음에 대 한 MSDN 설명서를은 `memcpy` 표시 됩니다.  
  
> "복사본 src 대상의 바이트를 계산 하는 데 사용 합니다. 소스와 대상이 겹치는 경우 memcpy의 동작은 정의 되지 않습니다. Memmove를 사용 하 여 겹치는 영역을 처리 합니다.   
> **보안 정보:** 대상 버퍼의 크기가 소스 버퍼의 크기보다 크거나 같아야 합니다. 자세한 내용은 참조 버퍼 오버런 방지 합니다. "  
  
 설명서에는 두 프로그램 정확성을 유지 하려면 특정 속성을 유지 하기 위해 코드에 제안 하는 정보의 비트:  
  
- `memcpy` 복사본을 `count` 소스 버퍼의 바이트를 대상 버퍼입니다.  
  
- 대상 버퍼가 소스 버퍼 이상이 여야 합니다.  
  
  그러나 컴파일러는 비공식적인 의견을 설명서를 읽을 수 없습니다. 두 부분 문자열 간의 관계 임을 알 수 없는 및 `count`, 것도 없습니다 효과적으로 중요 한 관계에 대 한 합니다. 다음과 같이 SAL 속성 및 함수를 구현 하는 방법에 대 한 보다 명확한을 제공할 수 있습니다.  
  
```cpp  
  
void * memcpy(  
   _Out_writes_bytes_all_(count) void *dest,   
   _In_reads_bytes_(count) const void *src,   
   size_t count  
);  
```  
  
 이러한 주석을 유사 MSDN 문서의 정보를 하지만 보다 간결 하 게 되며 의미 체계는 패턴을 따르는 확인 합니다. 이 코드를 읽을 때이 함수의 속성 및 버퍼 오버런 보안 문제를 방지 하는 방법을 신속 하 게 이해할 수 있습니다. 게다가 SAL 제공 하는 의미 체계 패턴 효율성 및 잠재적인 버그의 초기 검색에 대 한 자동화 된 코드 분석 도구의 효율성을 개선할 수 있습니다. 누군가가이 버그가 있는 구현의 쓰도록 imagine `wmemcpy`:  
  
```cpp  
  
wchar_t * wmemcpy(  
   _Out_writes_all_(count) wchar_t *dest,   
   _In_reads_(count) const wchar_t *src,   
   size_t count)  
{  
   size_t i;  
   for (i = 0; i <= count; i++) { // BUG: off-by-one error  
      dest[i] = src[i];  
   }  
   return dest;  
}  
  
```  
  
 이 구현은 일반적인 해제-하나씩 오류를 포함합니다. 코드 작성자 SAL 버퍼 크기 주석을 포함 하는 다행 스럽게도-코드 분석 도구만이 함수를 분석 하 여 버그를 catch 할 수 있습니다.  
  
### <a name="sal-basics"></a>SAL 기본  
 SAL 네 가지 기본 유형의 사용 패턴에 의해 분류 되는 매개 변수를 정의 합니다.  
  
|범주|매개 변수 주석이|설명|  
|--------------|--------------------------|-----------------|  
|**입력 함수를 호출합니다.**|`_In_`|데이터 호출된 된 함수에 전달 되 고 읽기 전용으로 처리 됩니다.|  
|**입력 함수를 호출 하 고 호출자에 게 출력**|`_Inout_`|사용 가능한 데이터 함수에 전달 되 고 잠재적으로 수정 됩니다.|  
|**호출자에 게 출력**|`_Out_`|호출자는만 쓸 호출된 된 함수에 대 한 공간을 제공 합니다. 호출된 된 함수는 해당 공간으로 데이터를 씁니다.|  
|**호출자에 대 한 포인터의 출력**|`_Outptr_`|와 같은 **호출자에 게 출력**합니다. 호출된 된 함수에서 반환 되는 값에는 포인터입니다.|  
  
 이러한 네 가지 기본 주석은 가능 보다 명시적인 다양 한 방법으로 합니다. 기본적으로 주석이 추가 된 포인터 매개 변수는 필요한 것으로 간주 됩니다-NULL이 아닌 해야만 성공 하는 함수에 대 한 합니다. 기본 주석의 가장 자주 사용 되는 변형 포인터 매개 변수가 옵션 임을 나타냅니다-NULL 인 경우 함수 작업 과정에서 계속 성공할 수 있습니다.  
  
 이 테이블에는 필수 및 선택적 매개 변수를 구분 하는 방법을 보여 줍니다.  
  
||매개 변수는 필수|매개 변수는 선택 사항|  
|-|-----------------------------|-----------------------------|  
|**입력 함수를 호출합니다.**|`_In_`|`_In_opt_`|  
|**입력 함수를 호출 하 고 호출자에 게 출력**|`_Inout_`|`_Inout_opt_`|  
|**호출자에 게 출력**|`_Out_`|`_Out_opt_`|  
|**호출자에 대 한 포인터의 출력**|`_Outptr_`|`_Outptr_opt_`|  
  
 이러한 주석은 가능한 초기화 되지 않은 값을 식별할 및 잘못 된 null 포인터 형식 및 정확한 방식으로 사용 합니다. 충돌이 발생 한 않을 필수 매개 변수를 NULL이 전달 하거나 반환할 "실패" 오류 코드를 발생할 수 있습니다. 어느 함수는 해당 작업에 성공할 수 없습니다.  
  
## <a name="sal-examples"></a>SAL 예제  
 이 섹션에서는 기본 SAL 주석에 대 한 코드 예제를 보여 줍니다.  
  
### <a name="using-the-visual-studio-code-analysis-tool-to-find-defects"></a>Visual Studio 코드 분석 도구를 사용하여 오류 찾기  
 예제에서는 Visual Studio 코드 분석 도구는 코드 오류를 찾으려면 SAL 주석과 함께 사용 됩니다. 작업을 수행 하는 방법은 다음과 같습니다.  
  
##### <a name="to-use-visual-studio-code-analysis-tools-and-sal"></a>Visual Studio 코드 분석 도구 및 SAL을 사용하려면  
  
1. Visual Studio에서 엽니다는 C++ SAL 주석을 포함 하는 프로젝트입니다.  
  
2. 메뉴 모음에서 **빌드**하십시오 **솔루션에서 코드 분석 실행**합니다.  
  
    고려 합니다 \_에서\_ 이 섹션의 예제. 코드 분석을 실행 하는 경우이 경고가 표시 됩니다.  
  
   > **C6387 잘못 된 매개 변수 값**   
   > '고정'는 '0' 일 수 있습니다:이 'InCallee' 함수에 대 한 사양을 따르지 않습니다.  
  
### <a name="example-the-in-annotation"></a>예제: 합니다 \_에서\_ 주석  
 `_In_` 주석이 나타냅니다.  
  
- 매개 변수는 유효 해야 하며 수정 되지 않습니다.  
  
- 함수는 단일 요소 버퍼에서 읽을 수만.  
  
- 호출자는 버퍼를 제공 하 고 초기화 해야 합니다.  
  
- `_In_` "읽기 전용"를 지정합니다. 일반적인 실수를 적용할 `_In_` 있어야 하는 매개 변수에 `_Inout_` 주석 대신 합니다.  
  
- `_In_` 포인터가 아닌 스칼라에 분석기에 의해 무시 하지만 허용 됩니다.  
  
```cpp  
void InCallee(_In_ int *pInt)  
{  
   int i = *pInt;  
}  
  
void GoodInCaller()  
{  
   int *pInt = new int;  
   *pInt = 5;  
  
   InCallee(pInt);  
   delete pInt;     
}  
  
void BadInCaller()  
{  
   int *pInt = NULL;  
   InCallee(pInt); // pInt should not be NULL  
}  
  
```  
  
 이 예제에서 Visual Studio Code 분석을 사용 하는 경우 호출자에 대 한 초기화 버퍼에 Null이 아닌 포인터를 전달 하는 검사 `pInt`합니다. 이 경우 `pInt` 포인터는 NULL 일 수 없습니다.  
  
### <a name="example-the-inopt-annotation"></a>예제: 합니다 \_In_opt\_ 주석  
 `_In_opt_` 동일 `_In_`있다는 점을 제외 하면 입력된 매개 변수는 NULL 일 수를이 함수를 확인 해야 하므로, 합니다.  
  
```cpp  
  
void GoodInOptCallee(_In_opt_ int *pInt)  
{  
   if(pInt != NULL) {  
      int i = *pInt;  
   }  
}  
  
void BadInOptCallee(_In_opt_ int *pInt)  
{  
   int i = *pInt; // Dereferencing NULL pointer ‘pInt’  
}  
  
void InOptCaller()  
{  
   int *pInt = NULL;  
   GoodInOptCallee(pInt);  
   BadInOptCallee(pInt);  
}  
  
```  
  
 Visual Studio Code Analysis 함수 NULL에 대 한 버퍼에 액세스 하기 전에 확인 하는 유효성을 검사 합니다.  
  
### <a name="example-the-out-annotation"></a>예제: 합니다 \_Out\_ 주석  
 `_Out_` 일반적인 시나리오는 요소 버퍼를 가리키는 NULL이 아닌 포인터를 전달 하 고 요소를 초기화 하는 함수를 지원 합니다. 호출자는 호출 전에 버퍼를 초기화 하지 않아도 호출된 된 함수가 반환 하기 전에 초기화 하는 데 약속 합니다.  
  
```cpp  
  
void GoodOutCallee(_Out_ int *pInt)  
{  
   *pInt = 5;  
}  
  
void BadOutCallee(_Out_ int *pInt)  
{  
   // Did not initialize pInt buffer before returning!  
}  
  
void OutCaller()  
{  
   int *pInt = new int;  
   GoodOutCallee(pInt);  
   BadOutCallee(pInt);  
   delete pInt;  
}  
  
```  
  
 Visual Studio Code 분석 도구에 대 한 버퍼에 NULL이 아닌 포인터를 전달 하 호출자가 유효성을 검사 `pInt` 버퍼를 반환 하기 전에 함수에 의해 초기화 되 고 있습니다.  
  
### <a name="example-the-outopt-annotation"></a>예제: 합니다 \_Out_opt\_ 주석  
 `_Out_opt_` 동일 `_Out_`단, 매개 변수는 NULL 일 수를이 함수를 따라서 확인 해야 합니다.  
  
```cpp  
  
void GoodOutOptCallee(_Out_opt_ int *pInt)  
{  
   if (pInt != NULL) {  
      *pInt = 5;  
   }  
}  
  
void BadOutOptCallee(_Out_opt_ int *pInt)  
{  
   *pInt = 5; // Dereferencing NULL pointer ‘pInt’  
}  
  
void OutOptCaller()  
{  
   int *pInt = NULL;  
   GoodOutOptCallee(pInt);  
   BadOutOptCallee(pInt);  
}  
  
```  
  
 Visual Studio 코드 분석 하기 전에 NULL 확인이 함수는 유효성을 검사 `pInt` 역참조가 경우에 `pInt` 반환 하기 전에 함수에서 버퍼가 초기화 되는 NULL이 아닙니다.  
  
### <a name="example-the-inout-annotation"></a>예제: 합니다 \_Inout\_ 주석  
 `_Inout_` 포인터 매개 변수는 함수에 의해 변경 될 수 있는 주석을 추가 하는 데 사용 됩니다. 포인터를 호출 하기 전에 올바른 초기화 데이터를 가리켜야 하 고 변경 될 경우에 여전히 있어야 올바른 값을 반환 합니다. 주석이 함수에서 읽기 및 요소가 하나인 버퍼에 쓰기를 자유롭게 수를 지정 합니다. 호출자는 버퍼를 제공 하 고 초기화 해야 합니다.  
  
> [!NOTE]
> 와 같은 `_Out_`, `_Inout_` 수정 가능한 값에 적용 해야 합니다.  
  
```cpp  
  
void InOutCallee(_Inout_ int *pInt)  
{  
   int i = *pInt;  
   *pInt = 6;  
}  
  
void InOutCaller()  
{  
   int *pInt = new int;  
   *pInt = 5;  
   InOutCallee(pInt);  
   delete pInt;  
}  
  
void BadInOutCaller()  
{  
   int *pInt = NULL;  
   InOutCallee(pInt); // ‘pInt’ should not be NULL  
}  
  
```  
  
 호출자에 대 한 초기화 버퍼에 NULL이 아닌 포인터를 전달 하는 visual Studio 코드 분석의 유효성을 검사 `pInt`, 하 고, 반환 하기 전에 `pInt` 여전히 NULL이 아닌 버퍼가 초기화 되 고 있습니다.  
  
### <a name="example-the-inoutopt-annotation"></a>예제: 합니다 \_Inout_opt\_ 주석  
 `_Inout_opt_` 동일 `_Inout_`있다는 점을 제외 하면 입력된 매개 변수는 NULL 일 수를이 함수를 확인 해야 하므로, 합니다.  
  
```cpp  
  
void GoodInOutOptCallee(_Inout_opt_ int *pInt)  
{  
   if(pInt != NULL) {  
      int i = *pInt;  
      *pInt = 6;  
   }  
}  
  
void BadInOutOptCallee(_Inout_opt_ int *pInt)  
{  
   int i = *pInt; // Dereferencing NULL pointer ‘pInt’  
   *pInt = 6;  
}  
  
void InOutOptCaller()  
{  
   int *pInt = NULL;  
   GoodInOutOptCallee(pInt);  
   BadInOutOptCallee(pInt);  
}  
  
```  
  
 이 함수 NULL에 대 한 버퍼에 액세스 하기 전에 확인 하는 visual Studio 코드 분석의 유효성을 검사 `pInt` 반환 하기 전에 함수에서 버퍼가 초기화 되는 NULL이 아닙니다.  
  
### <a name="example-the-outptr-annotation"></a>예제: 합니다 \_Outptr\_ 주석  
 `_Outptr_` 에 대 한 포인터를 반환 하기 위한 옵션에 매개 변수를 주석을 추가 하는 데 사용 됩니다.  매개 변수 자체에 NULL이를 사용 해야 합니다. 호출된 된 함수에 대 한 NULL이 아닌 포인터를 반환 하 고 포인터 초기화 데이터를 가리킵니다.  
  
```cpp  
  
void GoodOutPtrCallee(_Outptr_ int **pInt)  
{  
   int *pInt2 = new int;  
   *pInt2 = 5;  
  
   *pInt = pInt2;  
}  
  
void BadOutPtrCallee(_Outptr_ int **pInt)  
{  
   int *pInt2 = new int;  
   // Did not initialize pInt buffer before returning!  
   *pInt = pInt2;  
}  
  
void OutPtrCaller()  
{  
   int *pInt = NULL;  
   GoodOutPtrCallee(&pInt);  
   BadOutPtrCallee(&pInt);  
}  
  
```  
  
 Visual Studio 코드 분석의 호출자에 대 한 NULL이 아닌 포인터를 전달 하는 유효성을 검사 `*pInt`, 버퍼를 반환 하기 전에 함수에 의해 초기화 되 고 있습니다.  
  
### <a name="example-the-outptropt-annotation"></a>예제: 합니다 \_Outptr_opt\_ 주석  
 `_Outptr_opt_` 동일 `_Outptr_`한다는 점을 제외 하는 매개 변수는 선택 사항-매개 변수에 대해 NULL 포인터에서 호출자에 게 전달할 수 있습니다.  
  
```cpp  
  
void GoodOutPtrOptCallee(_Outptr_opt_ int **pInt)  
{  
   int *pInt2 = new int;  
   *pInt2 = 6;  
  
   if(pInt != NULL) {  
      *pInt = pInt2;  
   }  
}  
  
void BadOutPtrOptCallee(_Outptr_opt_ int **pInt)  
{  
   int *pInt2 = new int;  
   *pInt2 = 6;  
   *pInt = pInt2; // Dereferencing NULL pointer ‘pInt’  
}  
  
void OutPtrOptCaller()  
{  
   int **ppInt = NULL;  
   GoodOutPtrOptCallee(ppInt);  
   BadOutPtrOptCallee(ppInt);  
}  
  
```  
  
 Visual Studio 코드 분석 하기 전에 NULL 확인이 함수는 유효성을 검사 `*pInt` 역참조가 버퍼를 반환 하기 전에 함수에 의해 초기화 되 고 있습니다.  
  
### <a name="example-the-success-annotation-in-combination-with-out"></a>예제: 합니다 \_성공\_ 조합 하 여 주석 \_아웃\_  
 대부분의 개체에 주석은 적용할 수 있습니다.  특히 전체 함수에 주석을 달 수 있습니다.  함수의 가장 확실 한 특징 중 하나에 성공 또는 실패 수는입니다. 하지만 버퍼와 해당 크기에 C 간의 연결을 같은 /C++ 함수 성공 또는 실패를 표현할 수 없습니다. 사용 하 여는 `_Success_` 주석을 함수의 성공을 같습니다 말할 수 있습니다.  매개 변수는 `_Success_` 주석 식이면 방금 것은 사실 나타내는 함수 성공 했다는 것입니다. 식 주석 파서에서 처리할 수 있는 아무 이름이 나 가능 합니다. 함수가 성공 하는 경우에 함수가 반환 되 면 주석의 효과 적용 됩니다. 이 예제에서는 어떻게 `_Success_` 상호 작용 `_Out_` 오른쪽 작업을 수행. 키워드를 사용할 수 있습니다 `return` 를 나타내는 값을 반환 합니다.  
  
```cpp  
  
_Success_(return != false) // Can also be stated as _Success_(return)  
bool GetValue(_Out_ int *pInt, bool flag)  
{  
   if(flag) {  
      *pInt = 5;  
      return true;  
   } else {  
      return false;  
   }  
}  
  
```  
  
 `_Out_` 주석 하면 유효성을 검사 하려면 Visual Studio Code Analysis 호출자에 대 한 버퍼에 NULL이 아닌 포인터를 전달 하 `pInt`, 버퍼를 반환 하기 전에 함수에 의해 초기화 되 고 있습니다.  
  
## <a name="sal-best-practice"></a>SAL 유용한 정보  
  
### <a name="adding-annotations-to-existing-code"></a>기존 코드에 주석 추가  
 SAL는 보안 및 코드의 안정성을 향상 하는 데 도움이 되는 강력한 기술입니다. SAL을 파악 한 후 새 기술 일상 업무에 적용할 수 있습니다. 새 코드에서 SAL 기반 사양; 전체 디자인 하 여 사용할 수 있습니다. 이전 코드에서 증분 방식으로 주석을 추가 업데이트할 때마다 혜택을 향상 시킵니다.  
  
 Microsoft 공용 헤더에 주석을 다는 이미 있습니다. 따라서는 프로젝트에서 처음에 주석을 지정 리프 노드 함수와 가장 유용 하 게 하는 Win32 Api를 호출 하는 것이 좋습니다.  
  
### <a name="when-do-i-annotate"></a>주석을 달아야 하는 경우  
 다음은 몇 가지 지침입니다.  
  
- 모든 포인터 매개 변수에 주석을 추가 합니다.  
  
- 코드 분석에서 버퍼 및 포인터 안전 되도록 주석을 값 범위에 주석을 답니다.  
  
- 잠금 규칙 및 잠금 부작용에 주석을 추가 합니다. 자세한 내용은 [잠금 동작에 주석 지정](../code-quality/annotating-locking-behavior.md)합니다.  
  
- 드라이버 속성 및 기타 도메인 특정 속성에 주석을 추가 합니다.  
  
  또는 전체에 의도 선택을 취소를 확인 하는 데 쉽게 주석을 완료 되었는지 확인 하려면 모든 매개 변수에 주석을 달 수 있습니다.  
  
## <a name="related-resources"></a>관련 참고 자료  
 [코드 분석 팀 블로그](http://go.microsoft.com/fwlink/p/?LinkId=251197)  
  
## <a name="see-also"></a>참고 항목  
 [SAL 주석은 C를 줄이기 위해 사용 하 여 /C++ 오류 코드](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [함수 매개 변수 및 반환 값에 주석 지정](../code-quality/annotating-function-parameters-and-return-values.md)   
 [함수 동작에 주석 지정](../code-quality/annotating-function-behavior.md)   
 [구조체 및 클래스에 주석 지정](../code-quality/annotating-structs-and-classes.md)   
 [잠금 동작에 주석 지정](../code-quality/annotating-locking-behavior.md)   
 [주석 적용 시기 및 위치 지정](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [모범 사례 및 예제](../code-quality/best-practices-and-examples-sal.md)
