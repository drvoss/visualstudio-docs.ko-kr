---
title: 함수 매개 변수 및 반환 값에 주석 지정 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- _Outptr_opt_result_bytebuffer_to_
- _Inout_updates_all_opt_
- _Post_equal_to_
- _Outptr_opt_result_maybenull_
- _Out_writes_bytes_all_
- _Out_writes_all_opt_
- _In_opt_
- _Outptr_
- _Outptr_result_maybenull_
- _Outref_result_bytebuffer_all_maybenull_
- _Inout_updates_opt_z_
- _Inout_updates_z_
- _Out_writes_
- _Out_writes_to_ptr_opt_z_
- _In_reads_to_ptr_opt_
- _Ret_writes_to_maybenull_
- _Outref_result_maybenull_
- _Ret_writes_bytes_
- _Outptr_result_bytebuffer_
- _Out_writes_opt_
- _Inout_updates_bytes_opt_
- _In_z_
- _Inout_updates_to_
- _Ret_maybenull_
- _Ret_writes_bytes_to_
- _Ret_z_
- _COM_Outptr_
- _Ret_maybenull_z_
- _Out_opt_
- _In_reads_opt_z_
- _Outptr_result_bytebuffer_to_
- _Ret_notnull_
- _COM_Outptr_opt_result_maybenull_
- _Inout_updates_to_opt_
- _Inout_updates_
- _Outptr_opt_result_buffer_
- _Outptr_result_buffer_to_
- _Out_writes_to_ptr_opt_
- _Out_writes_bytes_all_opt_
- _Inout_updates_all_
- _Deref_inout_range_
- _Ret_writes_
- _Out_writes_z_
- _Ret_writes_to_
- _Out_writes_to_ptr_z_
- _Out_writes_bytes_to_opt_
- _In_reads_or_z_
- _Inout_updates_bytes_to_
- _In_reads_z_
- _In_opt_z_
- _Outref_result_buffer_maybenull_
- _Ret_range_
- _COM_Outptr_opt_
- _Ouptr_opt_result_maybenull_z_
- _In_reads_opt_
- _Inout_
- _Field_range_
- _Ret_writes_z_
- _Out_writes_to_
- _Out_writes_to_ptr_
- _Inout_opt_z_
- _Outref_
- _Deref_out_range_
- _Outref_result_buffer_
- _Outref_result_buffer_to_
- _Outref_result_bytebuffer_to_maybenull_
- _In_reads_bytes_
- _Outptr_opt_result_buffer_to_
- _Outref_result_buffer_all_
- _Out_writes_bytes_to_
- _Result_zeroonfailure_
- _In_reads_bytes_opt_
- _Outref_result_buffer_to_maybenull_
- _Outref_result_bytebuffer_all_
- _Outref_result_buffer_all_maybenull_
- _Ret_writes_maybenull_z_
- _In_range_
- _Inout_updates_bytes_all_opt_
- _Outref_result_bytebuffer_to_
- _Inout_updates_bytes_to_opt_
- _Pre_equal_to_
- _Ret_writes_bytes_maybenull_
- _COM_Outptr_result_maybenull_
- _Ret_writes_maybenull_
- _Out_writes_bytes_
- _Outptr_opt_
- _Out_writes_opt_z_
- _Outref_result_nullonfailure_
- _Outptr_opt_result_z_
- _Inout_opt_
- _Deref_in_range_
- _Outptr_result_z_
- _In_reads_to_ptr_opt_z_
- _Struct_size_bytes_
- _Outptr_result_nullonfailure_
- _In_
- _Inout_updates_bytes_
- _In_reads_to_ptr_z_
- _Ret_writes_bytes_to_maybenull
- _Outptr_opt_result_nullonfailure_
- _In_reads_to_ptr_
- _Outptr_result_buffer_
- _Out_
- _Outref_result_bytebuffer_maybenull_
- _Outptr_result_maybenull_z_
- _In_reads_
- _Inout_updates_opt_
- _Out_writes_to_opt_
- _Outptr_opt_result_bytebuffer_
- _Out_writes_all_
- _Out_range_
- _Inout_updates_bytes_all_
- _Inout_z_
- _Outref_result_bytebuffer_
- _Result_nullonfailure_
- _Ret_null_
ms.assetid: 82826a3d-0c81-421c-8ffe-4072555dca3a
caps.latest.revision: 17
author: mikeblome
ms.author: mblome
manager: jillfra
ms.openlocfilehash: b6d36b01ca84558d0d3d45251884e5598becfa1b
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63429190"
---
# <a name="annotating-function-parameters-and-return-values"></a>함수 매개 변수 및 반환 값에 주석 지정
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 문서에서는 간단한 함수 매개 변수에 대 한 주석의 일반적인 용도 설명 합니다.-스칼라 및 구조체와 클래스에 대 한 포인터-버퍼의 대부분의 종류입니다.  이 문서는 또한 주석에 대 한 일반적인 사용 패턴을 보여줍니다. 함수에 관련 된 추가 주석을 참조 하세요. [함수 동작에 주석 지정](../code-quality/annotating-function-behavior.md)  
  
## <a name="pointer-parameters"></a>포인터 매개 변수  
 다음 테이블에 대 한 주석에 대 한 포인터 매개 변수 주석이 지정 되는 분석기 오류가 null 포인터 이면 보고 합니다.  포인터를 가리키는 데이터 항목에 적용 됩니다.  
  
 **주석 및 설명**  
  
- `_In_`  
  
     입력된 매개 변수는 스칼라, 구조, 구조에 대 한 포인터 및 like를 주석을 지정 합니다.  명시적으로 간단한 스칼라에 사용할 수 있습니다.  매개 변수 사전 상태에서 유효 해야 하며 수정 되지 않습니다.  
  
- `_Out_`  
  
     출력 매개 변수는 스칼라, 구조, 구조에 대 한 포인터 및 like는 주석을 지정 합니다.  값을 반환할 수 있는 개체에 적용 되지 않습니다-스칼라 값으로 전달 되는 예를 들어 있습니다.  매개 변수 사전 상태에서 유효 하지 않아도 되지만 사후 상태에서 유효 해야 합니다.  
  
- `_Inout_`  
  
     주석을 함수에 의해 변경 되는 매개 변수를 지정 합니다.  이 사전 상태 및 사후 상태에서 유효 해야 하지만 호출 전후 서로 다른 값으로 간주 됩니다. 수정 가능한 값에 적용 해야 합니다.  
  
- `_In_z_`  
  
     입력으로 사용 되는 null로 끝나는 문자열에 대 한 포인터입니다.  문자열 사전 상태에서 유효 해야 합니다.  변형의 `PSTR`에 이미 올바른 주석이는 것이 좋습니다.  
  
- `_Inout_z_`  
  
     수정할 수는 null로 끝나는 문자 배열에 대 한 포인터입니다.  호출 후 및 하기 전에 유효 해야 하지만 값이 변경 된 것으로 간주 됩니다.  Null 종결자를 이동할 수 있습니다 하지만 원래 null 종결자 최대 요소만 액세스할 수 있습니다.  
  
- `_In_reads_(s)`  
  
     `_In_reads_bytes_(s)`  
  
     함수에서 읽어오는 배열에 대 한 포인터입니다.  배열 크기는 `s` 요소를 모두 사용할 수 있어야 합니다.  
  
     `_bytes_` variant는 요소 대신 바이트 크기를 제공 합니다. 크기 요소로 표현할 수 없는 경우에 사용 합니다.  예를 들어 `char` 문자열 사용 합니다 `_bytes_` 변형 하는 유사한 작동 하는 경우에 사용 하 여 `wchar_t` 는 합니다.  
  
- `_In_reads_z_(s)`  
  
     크기는 잘 알려져 있고가 null로 끝나는 배열에 대 한 포인터입니다. Null 종결자 까지의 요소-또는 `s` 있습니다 null 종결자가 없는 경우-사전 상태에서 유효 해야 합니다.  크기 (바이트)에서 알 수 있으면 확장 `s` 요소 크기에 따라 합니다.  
  
- `_In_reads_or_z_(s)`  
  
     가 null로 끝나는 또는 알려진된 크기 중 하나 또는 둘 다에 배열에 대 한 포인터입니다. Null 종결자 까지의 요소-또는 `s` 있습니다 null 종결자가 없는 경우-사전 상태에서 유효 해야 합니다.  크기 (바이트)에서 알 수 있으면 확장 `s` 요소 크기에 따라 합니다.  (사용 된 `strn` 제품군입니다.)  
  
- `_Out_writes_(s)`  
  
     `_Out_writes_bytes_(s)`  
  
     배열에 대 한 포인터 `s` 함수에 의해 기록 되는 요소 (깜박이고 바이트)입니다.  배열 요소를 사전 상태에서 유효 하지 않아도 및 사후 상태에서 잘못 된 요소 수가 지정 되지 않았습니다.  매개 변수 형식에 대 한 주석 경우 사후 상태에서 적용 됩니다. 예를 들어, 다음과 같은 코드를 생각해 볼 수 있습니다.  
  
     `typedef _Null_terminated_ wchar_t *PWSTR; void MyStringCopy(_Out_writes_ (size) PWSTR p1,    _In_ size_t size,    _In_ PWSTR p2);`  
  
     이 예제에서는 호출자의 버퍼를 제공 `size` 요소에 대 한 `p1`합니다.  `MyStringCopy` 결과 유효한 해당 요소의 일부입니다. 무엇 보다도 합니다 `_Null_terminated_` 주석이 `PWSTR` 즉 `p1` 사후 상태에서 null로 종결 됩니다.  이러한 방식으로 유효한 요소 수는 계속 잘 정의 되어 있지만 특정 요소 수가 필요는 없습니다.  
  
     `_bytes_` variant는 요소 대신 바이트 크기를 제공 합니다. 크기 요소로 표현할 수 없는 경우에 사용 합니다.  예를 들어 `char` 문자열 사용 합니다 `_bytes_` 변형 하는 유사한 작동 하는 경우에 사용 하 여 `wchar_t` 는 합니다.  
  
- `_Out_writes_z_(s)`  
  
     배열에 대 한 포인터 `s` 요소입니다.  요소를 사전 상태에서 유효 하지 않아도 됩니다.  Null 종결자를 통해 구성 요소를 사후 상태에서-나타나는-유효 해야 합니다.  크기 (바이트)에서 알 수 있으면 확장 `s` 요소 크기에 따라 합니다.  
  
- `_Inout_updates_(s)`  
  
     `_Inout_updates_bytes_(s)`  
  
     읽기 및 함수를 작성 하는 배열에 대 한 포인터입니다.  크기는 `s` 요소 및 사전 상태 및 사후 상태에서 유효 합니다.  
  
     `_bytes_` variant는 요소 대신 바이트 크기를 제공 합니다. 크기 요소로 표현할 수 없는 경우에 사용 합니다.  예를 들어 `char` 문자열 사용 합니다 `_bytes_` 변형 하는 유사한 작동 하는 경우에 사용 하 여 `wchar_t` 는 합니다.  
  
- `_Inout_updates_z_(s)`  
  
     크기는 잘 알려져 있고가 null로 끝나는 배열에 대 한 포인터입니다. Null 종결자를 통해 구성 요소-나타나는-사전 상태와 사후 상태에서 유효 해야 합니다.  사후 상태에서 값을 사전 상태에서 값과 다른 것으로 간주 되며 null 종결자의 위치를 포함 합니다. 크기 (바이트)에서 알 수 있으면 확장 `s` 요소 크기에 따라 합니다.  
  
- `_Out_writes_to_(s,c)`  
  
     `_Out_writes_bytes_to_(s,c)`  
  
     `_Out_writes_all_(s)`  
  
     `_Out_writes_bytes_all_(s)`  
  
     배열에 대 한 포인터 `s` 요소입니다.  요소를 사전 상태에서 유효 하지 않아도 됩니다.  최대 사후 상태에서는 `c`번째 요소가 유효 해야 합니다.  크기 (바이트)에서 알 수 있으면 확장 `s` 하 고 `c` 요소 크기를 사용 하 여는 `_bytes_` 로 정의 되는 변형:  
  
     `_Out_writes_to_(_Old_(s), _Old_(s))    _Out_writes_bytes_to_(_Old_(s), _Old_(s))`  
  
     최대 버퍼에 있는 모든 요소 즉, `s` 사전 상태에서 유효한 후 상태입니다.  예를 들어:  
  
     `void *memcpy(_Out_writes_bytes_all_(s) char *p1,    _In_reads_bytes_(s) char *p2,    _In_ int s); void * wordcpy(_Out_writes_all_(s) DWORD *p1,     _In_reads_(s) DWORD *p2,    _In_ int s);`  
  
- `_Inout_updates_to_(s,c)`  
  
     `_Inout_updates_bytes_to_(s,c)`  
  
     읽기 및 함수에 의해 작성 하는 배열에 대 한 포인터입니다.  크기의 것 `s` 요소를 모두 유효 해야 사전 상태에서 및 `c` 사후 상태에서 요소는 유효 해야 합니다.  
  
     `_bytes_` variant는 요소 대신 바이트 크기를 제공 합니다. 크기 요소로 표현할 수 없는 경우에 사용 합니다.  예를 들어 `char` 문자열 사용 합니다 `_bytes_` 변형 하는 유사한 작동 하는 경우에 사용 하 여 `wchar_t` 는 합니다.  
  
- `_Inout_updates_z_(s)`  
  
     크기는 잘 알려져 있고가 null로 끝나는 배열에 대 한 포인터입니다. Null 종결자를 통해 구성 요소-나타나는-사전 상태와 사후 상태에서 유효 해야 합니다.  사후 상태에서 값을 사전 상태에서 값과 다른 것으로 간주 되며 null 종결자의 위치를 포함 합니다. 크기 (바이트)에서 알 수 있으면 확장 `s` 요소 크기에 따라 합니다.  
  
- `_Out_writes_to_(s,c)`  
  
     `_Out_writes_bytes_to_(s,c)`  
  
     `_Out_writes_all_(s)`  
  
     `_Out_writes_bytes_all_(s)`  
  
     배열에 대 한 포인터 `s` 요소입니다.  요소를 사전 상태에서 유효 하지 않아도 됩니다.  최대 사후 상태에서는 `c`번째 요소가 유효 해야 합니다.  크기 (바이트)에서 알 수 있으면 확장 `s` 하 고 `c` 요소 크기를 사용 하 여는 `_bytes_` 로 정의 되는 변형:  
  
     `_Out_writes_to_(_Old_(s), _Old_(s))    _Out_writes_bytes_to_(_Old_(s), _Old_(s))`  
  
     최대 버퍼에 있는 모든 요소 즉, `s` 사전 상태에서 유효한 후 상태입니다.  예를 들어:  
  
     `void *memcpy(_Out_writes_bytes_all_(s) char *p1,    _In_reads_bytes_(s) char *p2,    _In_ int s); void * wordcpy(_Out_writes_all_(s) DWORD *p1,     _In_reads_(s) DWORD *p2,    _In_ int s);`  
  
- `_Inout_updates_to_(s,c)`  
  
     `_Inout_updates_bytes_to_(s,c)`  
  
     읽기 및 함수에 의해 작성 하는 배열에 대 한 포인터입니다.  크기의 것 `s` 요소를 모두 유효 해야 사전 상태에서 및 `c` 사후 상태에서 요소는 유효 해야 합니다.  
  
     `_bytes_` variant는 요소 대신 바이트 크기를 제공 합니다. 크기 요소로 표현할 수 없는 경우에 사용 합니다.  예를 들어 `char` 문자열 사용 합니다 `_bytes_` 변형 하는 유사한 작동 하는 경우에 사용 하 여 `wchar_t` 는 합니다.  
  
- `_Inout_updates_all_(s)`  
  
     `_Inout_updates_bytes_all_(s)`  
  
     읽기 및 크기의 함수에 의해 작성 하는 배열에 대 한 포인터 `s` 요소입니다. 동일한 것으로 정의 합니다.  
  
     `_Inout_updates_to_(_Old_(s), _Old_(s))    _Inout_updates_bytes_to_(_Old_(s), _Old_(s))`  
  
     최대 버퍼에 있는 모든 요소 즉, `s` 사전 상태에서 유효 사후 상태에서 사전 상태입니다.  
  
     `_bytes_` variant는 요소 대신 바이트 크기를 제공 합니다. 크기 요소로 표현할 수 없는 경우에 사용 합니다.  예를 들어 `char` 문자열 사용 합니다 `_bytes_` 변형 하는 유사한 작동 하는 경우에 사용 하 여 `wchar_t` 는 합니다.  
  
- `_In_reads_to_ptr_(p)`  
  
     배열에 대 한 포인터 식이 `p` – `_Curr_` (즉, `p` 빼기 `_Curr_`) 표준 적절 한 언어에서 정의 됩니다.  요소를 이전 `p` 사전 상태에서 유효 해야 합니다.  
  
- `_In_reads_to_ptr_z_(p)`  
  
     null로 끝나는 배열에 대 한 포인터 식이 `p` – `_Curr_` (즉, `p` 빼기 `_Curr_`) 표준 적절 한 언어에서 정의 됩니다.  요소를 이전 `p` 사전 상태에서 유효 해야 합니다.  
  
- `_Out_writes_to_ptr_(p)`  
  
     배열에 대 한 포인터 식이 `p` – `_Curr_` (즉, `p` 빼기 `_Curr_`) 표준 적절 한 언어에서 정의 됩니다.  요소를 이전 `p` 사전 상태에서 유효 하지 않아도 되 고 사후 상태에서 유효 해야 합니다.  
  
- `_Out_writes_to_ptr_z_(p)`  
  
     null로 끝나는 배열에 대 한 포인터 식이 `p` – `_Curr_` (즉, `p` 빼기 `_Curr_`) 표준 적절 한 언어에서 정의 됩니다.  요소를 이전 `p` 사전 상태에서 유효 하지 않아도 되 고 사후 상태에서 유효 해야 합니다.  
  
## <a name="optional-pointer-parameters"></a>선택적 포인터 매개 변수  
 포인터 매개 변수 주석이 포함 된 경우 `_opt_`를 나타냅니다. 매개 변수는 null 일 수 있습니다. 그렇지 않으면 주석이 수행 포함 되지 않은 버전과 동일 `_opt_`합니다. 목록은 다음과 같습니다는 `_opt_` 포인터 매개 변수 주석에 변형:  
  
||||  
|-|-|-|  
|`_In_opt_`<br /><br /> `_Out_opt_`<br /><br /> `_Inout_opt_`<br /><br /> `_In_opt_z_`<br /><br /> `_Inout_opt_z_`<br /><br /> `_In_reads_opt_`<br /><br /> `_In_reads_bytes_opt_`<br /><br /> `_In_reads_opt_z_`|`_Out_writes_opt_`<br /><br /> `_Out_writes_opt_z_`<br /><br /> `_Inout_updates_opt_`<br /><br /> `_Inout_updates_bytes_opt_`<br /><br /> `_Inout_updates_opt_z_`<br /><br /> `_Out_writes_to_opt_`<br /><br /> `_Out_writes_bytes_to_opt_`<br /><br /> `_Out_writes_all_opt_`<br /><br /> `_Out_writes_bytes_all_opt_`|`_Inout_updates_to_opt_`<br /><br /> `_Inout_updates_bytes_to_opt_`<br /><br /> `_Inout_updates_all_opt_`<br /><br /> `_Inout_updates_bytes_all_opt_`<br /><br /> `_In_reads_to_ptr_opt_`<br /><br /> `_In_reads_to_ptr_opt_z_`<br /><br /> `_Out_writes_to_ptr_opt_`<br /><br /> `_Out_writes_to_ptr_opt_z_`|  
  
## <a name="output-pointer-parameters"></a>포인터 매개 변수 출력  
 출력 포인터 매개 변수는 매개 변수가 가리키는 위치에 null 특성을 명확 하 게 특수 표기법을 필요 합니다.  
  
 **주석 및 설명**  
  
- `_Outptr_`  
  
   매개 변수는 null 일 수 및 사후 상태에서 가리키는 위치 null 일 수 없으며 유효 해야 합니다.  
  
- `_Outptr_opt_`  
  
   매개 변수는 null 일 수 있지만 사후 상태에서 가리키는 위치 null 일 수 없으며 유효 해야 합니다.  
  
- `_Outptr_result_maybenull_`  
  
   매개 변수는 null 일 수 및 사후 상태에서 가리키는 위치 null 일 수 있습니다.  
  
- `_Outptr_opt_result_maybenull_`  
  
   매개 변수는 null 일 수 및 사후 상태에서 가리키는 위치 null 일 수 있습니다.  
  
  다음 표에 추가 부분 문자열은 추가로 주석의 의미를 한 정하는 데 주석 이름에 삽입 됩니다.  다양 한 부분 문자열은 `_z`, `_COM_`를 `_buffer_`합니다 `_bytebuffer_`, 및 `_to_`합니다.  
  
> [!IMPORTANT]
> 주석을 다는 인터페이스를 COM에 경우에 이러한 주석의 COM 형식을 사용 합니다. 다른 형식의 인터페이스를 사용 하 여 COM 주석을 사용 하지 마세요.  
  
 **주석 및 설명**  
  
- `_Outptr_result_z_`  
  
   `_Outptr_opt_result_z_`  
  
   `_Outptr_result_maybenull_z_`  
  
   `_Ouptr_opt_result_maybenull_z_`  
  
   반환 된 포인터에는 `_Null_terminated_` 주석입니다.  
  
- `_COM_Outptr_`  
  
   `_COM_Outptr_opt_`  
  
   `_COM_Outptr_result_maybenull_`  
  
   `_COM_Outptr_opt_result_maybenull_`  
  
   반환된 된 포인터 COM 의미 체계 및 전달 하므로 `_On_failure_` 후 반환된 된 포인터는 null을 조건입니다.  
  
- `_Outptr_result_buffer_(s)`  
  
   `_Outptr_result_bytebuffer_(s)`  
  
   `_Outptr_opt_result_buffer_(s)`  
  
   `_Outptr_opt_result_bytebuffer_(s)`  
  
   반환된 된 포인터 크기의 유효한 버퍼를 가리키는 `s` 요소나 바이트입니다.  
  
- `_Outptr_result_buffer_to_(s, c)`  
  
   `_Outptr_result_bytebuffer_to_(s, c)`  
  
   `_Outptr_opt_result_buffer_to_(s,c)`  
  
   `_Outptr_opt_result_bytebuffer_to_(s,c)`  
  
   반환된 된 포인터 크기의 버퍼를 가리키는 `s` 요소나 (바이트)는 첫 번째 `c` 유효 합니다.  
  
  특정 인터페이스 규칙 실패 시 출력 매개 변수는 무효화를 가정 합니다.  다음 표에서 양식이 명시적으로 COM 코드를 제외 하 고 기본 설정 됩니다.  COM 코드 등 코드에 대 한 이전 섹션에 나와 있는 해당 COM 폼을 사용 합니다.  
  
  **주석 및 설명**  
  
- `_Result_nullonfailure_`  
  
   다른 주석을 수정합니다. 결과는 함수가 실패 한 경우 null로 설정 됩니다.  
  
- `_Result_zeroonfailure_`  
  
   다른 주석을 수정합니다. 함수가 실패 한 경우 결과 0으로 설정 됩니다.  
  
- `_Outptr_result_nullonfailure_`  
  
   함수가 실패 하면 함수가 성공 하면 유효한 버퍼 또는 null로 반환 된 포인터가 가리킵니다. 이 주석은 필수 매개 변수입니다.  
  
- `_Outptr_opt_result_nullonfailure_`  
  
   함수가 실패 하면 함수가 성공 하면 유효한 버퍼 또는 null로 반환 된 포인터가 가리킵니다. 이 주석은 선택적 매개 변수입니다.  
  
- `_Outref_result_nullonfailure_`  
  
   함수가 실패 하면 함수가 성공 하면 유효한 버퍼 또는 null로 반환 된 포인터가 가리킵니다. 이 주석은 참조 매개 변수입니다.  
  
## <a name="output-reference-parameters"></a>참조 매개 변수 출력  
 참조 매개 변수의 일반적인 용도 출력 매개 변수입니다.  간단한 출력 참조 매개 변수-예를 들어 `int&`-`_Out_` 올바른 의미 체계를 제공 합니다.  그러나 출력 값에 대 한 포인터는-예를 들어 `int *&`-해당 포인터 주석을 같은 `_Outptr_ int **` 올바른 의미 체계를 제공 하지 않습니다.  포인터 형식에 대 한 출력 참조 매개 변수의 의미 체계를 간결 하 게 express 복합 이러한 주석을 사용 합니다.  
  
 **주석 및 설명**  
  
- `_Outref_`  
  
     결과 사후 상태에서 유효 해야 하며 null 일 수 없습니다.  
  
- `_Outref_result_maybenull_`  
  
     결과 사후 상태에서 유효 해야 하지만 사후 상태에서 null 일 수 있습니다.  
  
- `_Outref_result_buffer_(s)`  
  
     결과 사후 상태에서 유효 해야 하며 null 일 수 없습니다. 크기의 유효한 버퍼를 가리키는 `s` 요소입니다.  
  
- `_Outref_result_bytebuffer_(s)`  
  
     결과 사후 상태에서 유효 해야 하며 null 일 수 없습니다. 크기의 유효한 버퍼를 가리키는 `s` 바이트입니다.  
  
- `_Outref_result_buffer_to_(s, c)`  
  
     결과 사후 상태에서 유효 해야 하며 null 일 수 없습니다. 버퍼를 가리키는 `s` 요소는 첫 번째 `c` 유효 합니다.  
  
- `_Outref_result_bytebuffer_to_(s, c)`  
  
     결과 사후 상태에서 유효 해야 하며 null 일 수 없습니다. 버퍼를 가리키는 `s` 바이트는 첫 번째 `c` 유효 합니다.  
  
- `_Outref_result_buffer_all_(s)`  
  
     결과 사후 상태에서 유효 해야 하며 null 일 수 없습니다. 크기의 유효한 버퍼를 가리키는 `s` 유효한 요소입니다.  
  
- `_Outref_result_bytebuffer_all_(s)`  
  
     결과 사후 상태에서 유효 해야 하며 null 일 수 없습니다. 유효한 버퍼를 가리키는 `s` 바이트 유효한 요소입니다.  
  
- `_Outref_result_buffer_maybenull_(s)`  
  
     결과 사후 상태에서 유효 해야 하지만 사후 상태에서 null 일 수 있습니다. 크기의 유효한 버퍼를 가리키는 `s` 요소입니다.  
  
- `_Outref_result_bytebuffer_maybenull_(s)`  
  
     결과 사후 상태에서 유효 해야 하지만 사후 상태에서 null 일 수 있습니다. 크기의 유효한 버퍼를 가리키는 `s` 바이트입니다.  
  
- `_Outref_result_buffer_to_maybenull_(s, c)`  
  
     결과 사후 상태에서 유효 해야 하지만 사후 상태에서 null 일 수 있습니다. 버퍼를 가리키는 `s` 요소는 첫 번째 `c` 유효 합니다.  
  
- `_Outref_result_bytebuffer_to_maybenull_(s,c)`  
  
     결과 사후 상태에서 유효 해야 하지만 사후 상태에서 null 일 수 있습니다. 버퍼를 가리키는 `s` 바이트는 첫 번째 `c` 유효 합니다.  
  
- `_Outref_result_buffer_all_maybenull_(s)`  
  
     결과 사후 상태에서 유효 해야 하지만 사후 상태에서 null 일 수 있습니다. 크기의 유효한 버퍼를 가리키는 `s` 유효한 요소입니다.  
  
- `_Outref_result_bytebuffer_all_maybenull_(s)`  
  
     결과 사후 상태에서 유효 해야 하지만 사후 상태에서 null 일 수 있습니다. 유효한 버퍼를 가리키는 `s` 바이트 유효한 요소입니다.  
  
## <a name="return-values"></a>반환 값  
 함수의 반환 값 비슷합니다는 `_Out_` de-reference, 서로 다른 수준의 비슷하나 매개 변수 및 결과에 대 한 포인터의 개념을 고려해 야 할 필요가 없습니다.  다음 주석을 반환 값은 주석이 추가 된 개체-스칼라, 구조체에 대 한 포인터 또는 버퍼에 대 한 포인터입니다. 이러한 주석은 해당 동일한 의미 체계를 가집니다 `_Out_` 주석입니다.  
  
|||  
|-|-|  
|`_Ret_z_`<br /><br /> `_Ret_writes_(s)`<br /><br /> `_Ret_writes_bytes_(s)`<br /><br /> `_Ret_writes_z_(s)`<br /><br /> `_Ret_writes_to_(s,c)`<br /><br /> `_Ret_writes_maybenull_(s)`<br /><br /> `_Ret_writes_to_maybenull_(s)`<br /><br /> `_Ret_writes_maybenull_z_(s)`|`_Ret_maybenull_`<br /><br /> `_Ret_maybenull_z_`<br /><br /> `_Ret_null_`<br /><br /> `_Ret_notnull_`<br /><br /> `_Ret_writes_bytes_to_`<br /><br /> `_Ret_writes_bytes_maybenull_`<br /><br /> `_Ret_writes_bytes_to_maybenull_`|  
  
## <a name="other-common-annotations"></a>기타 일반 주석  
 **주석 및 설명**  
  
- `_In_range_(low, hi)`  
  
     `_Out_range_(low, hi)`  
  
     `_Ret_range_(low, hi)`  
  
     `_Deref_in_range_(low, hi)`  
  
     `_Deref_out_range_(low, hi)`  
  
     `_Deref_inout_range_(low, hi)`  
  
     `_Field_range_(low, hi)`  
  
     매개 변수, 필드 또는 결과 (포함)에서 범위에 `low` 에 `hi`입니다.  같음 `_Satisfies_(_Curr_ >= low && _Curr_ <= hi)` 적절 한 사전 상태 또는 사후 상태 조건 함께 주석이 달린된 개체에 적용 되는 합니다.  
  
    > [!IMPORTANT]
    > "In" 및 "out"의 의미 체계 이름을 포함 하지만 `_In_` 하 고 `_Out_` 수행 **하지** 이러한 주석을 적용할 합니다.  
  
- `_Pre_equal_to_(expr)`  
  
     `_Post_equal_to_(expr)`  
  
     주석이 추가 된 값이 정확 하 게 `expr`합니다.  같음 `_Satisfies_(_Curr_ == expr)` 적절 한 사전 상태 또는 사후 상태 조건 함께 주석이 달린된 개체에 적용 되는 합니다.  
  
- `_Struct_size_bytes_(size)`  
  
     구조체 또는 클래스 선언에 적용 됩니다.  지정 된 바이트 수를 사용 하 여 해당 형식의 유효한 개체를 선언된 된 형식 보다 클 수 있습니다 나타냅니다 `size`합니다.  예를 들어:  
  
     `typedef _Struct_size_bytes_(nSize) struct MyStruct {    size_t nSize;    ... };`  
  
     버퍼 크기 매개 변수는 바이트 `pM` 형식의 `MyStruct *` 되도록 이동 됩니다.  
  
     `min(pM->nSize, sizeof(MyStruct))`  
  
## <a name="related-resources"></a>관련 참고 자료  
 [코드 분석 팀 블로그](http://go.microsoft.com/fwlink/?LinkId=251197)  
  
## <a name="see-also"></a>참고 항목  
 [SAL 주석은 C를 줄이기 위해 사용 하 여 /C++ 오류 코드](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [SAL 이해](../code-quality/understanding-sal.md)   
 [함수 동작에 주석 지정](../code-quality/annotating-function-behavior.md)   
 [구조체 및 클래스에 주석 지정](../code-quality/annotating-structs-and-classes.md)   
 [잠금 동작에 주석 지정](../code-quality/annotating-locking-behavior.md)   
 [주석 적용 시기 및 위치 지정](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [내장 함수](../code-quality/intrinsic-functions.md)   
 [모범 사례 및 예제](../code-quality/best-practices-and-examples-sal.md)
