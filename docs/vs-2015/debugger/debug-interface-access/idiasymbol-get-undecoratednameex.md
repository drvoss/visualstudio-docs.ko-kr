---
title: IDiaSymbol::get_undecoratedNameEx | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_undecoratedNameEx method
ms.assetid: 579aed0b-c57d-41a1-a94a-3bf665fd4a9d
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f9c50f5d352d8a52b0eb8b125992b2c325e48234
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/12/2019
ms.locfileid: "64811868"
---
# <a name="idiasymbolgetundecoratednameex"></a>IDiaSymbol::get_undecoratedNameEx
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

검색에 대 한 데코 레이트 되지 않은 이름의 전체 또는 일부를 C++ 데코 레이트 된 이름 (링크).  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT get_undecoratedNameEx(   
   DWORD undecorateOptions,  
   BSTR* pRetval  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `undecoratedOptions`  
 [in] 플래그의 조합을 반환 되는 해당 컨트롤을 지정 합니다. 특정 값 및 용도 대 한 설명 섹션을 참조 합니다.  
  
 `pRetVal`  
 [out] 데코 레이트 되지 않은 이름을 반환 하는 C++ 데코 레이트 된 이름입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 반환 `S_OK`이 고, 그렇지 않으면 반환 `S_FALSE` 또는 오류 코드입니다.  
  
> [!NOTE]
> 반환 값이 `S_FALSE` 속성 기호를 사용할 수 없는 것을 의미 합니다.  
  
## <a name="remarks"></a>설명  
 `undecorateOptions` 플래그의 조합일 수 있습니다.  
  
> [!NOTE]
> 플래그 이름은 선언 코드를 추가 하거나 원시 값을 사용 해야 하므로 DIA SDK, 정의 되지 않습니다.  
  
|Flag|값|설명|  
|----------|-----------|-----------------|  
|UNDNAME_COMPLETE|0x0000|전체 undecoration 사용 하도록 설정 합니다.|  
|UNDNAME_NO_LEADING_UNDERSCORES|0x0001|Microsoft 확장 키워드 앞에 밑줄을 제거 합니다.|  
|UNDNAME_NO_MS_KEYWORDS|0x0002|Microsoft 확장 키워드의 확장을 사용 하지 않도록 설정 합니다.|  
|UNDNAME_NO_FUNCTION_RETURNS|0x0004|기본 선언에 대 한 반환 형식의 확장을 사용 하지 않도록 설정 합니다.|  
|UNDNAME_NO_ALLOCATION_MODEL|0x0008|선언 모델의 확장을 사용 하지 않도록 설정 합니다.|  
|UNDNAME_NO_ALLOCATION_LANGUAGE|0x0010|선언 언어 지정자의 확장을 사용 하지 않도록 설정 합니다.|  
|UNDNAME_RESERVED1|0x0020|예약됨.|  
|UNDNAME_RESERVED2|0x0040|예약됨.|  
|UNDNAME_NO_THISTYPE|0x0060|모든 한정자를 사용 하지 않도록 설정 된 `this` 형식입니다.|  
|UNDNAME_NO_ACCESS_SPECIFIERS|0x0080|확장 멤버에 대 한 액세스 지정자를 사용 하지 않도록 설정 합니다.|  
|UNDNAME_NO_THROW_SIGNATURES|0x0100|"Throw 서명" 함수 및 함수에 대 한 포인터에 대 한 확장을 사용 하지 않도록 설정 합니다.|  
|UNDNAME_NO_MEMBER_TYPE|0x0200|확장을 사용 하지 않도록 설정 `static` 또는 `virtual` 멤버입니다.|  
|UNDNAME_NO_RETURN_UDT_MODEL|0x0400|UDT 반환에 대 한 Microsoft 모델의 확장을 사용 하지 않도록 설정 합니다.|  
|UNDNAME_32_BIT_DECODE|0x0800|32 비트 트 데코 레이 된 이름이 undecorates 합니다.|  
|UNDNAME_NAME_ONLY|0x1000|기본 선언의; 이름만을 가져옵니다. 만 반환 [범위::] 이름입니다.  템플릿 매개 변수를 확장합니다.|  
|UNDNAME_TYPE_ONLY|0x2000|입력은 인코딩; 일종 추상 선언 자를 작성합니다.|  
|UNDNAME_HAVE_PARAMETERS|0x4000|실제 템플릿 매개 변수를 사용할 수 있습니다.|  
|UNDNAME_NO_ECSU|0x8000|열거형/클래스/구조체/공용 구조체를 표시 하지 않습니다.|  
|UNDNAME_NO_IDENT_CHAR_CHECK|0x10000|유효한 식별자 문자에 대 한 검사를 표시 하지 않습니다.|  
|UNDNAME_NO_PTR64|0x20000|Ptr64 출력에 포함 되지 않습니다.|  
  
## <a name="see-also"></a>참고 항목  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
