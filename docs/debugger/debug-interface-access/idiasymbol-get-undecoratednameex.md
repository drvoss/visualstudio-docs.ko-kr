---
title: IDiaSymbol::get_undecoratedNameEx | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_undecoratedNameEx method
ms.assetid: 579aed0b-c57d-41a1-a94a-3bf665fd4a9d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 48efbc249d076853e12bc54d2e8a8d438570e740
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738989"
---
# <a name="idiasymbolget_undecoratednameex"></a>IDiaSymbol::get_undecoratedNameEx
C++ 데코레이팅된 (링크) 이름에 대 한 데코레이팅되지 않은 이름의 일부 또는 전체를 검색 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT get_undecoratedNameEx( 
   DWORD undecorateOptions,
   BSTR* pRetval
);
```

#### <a name="parameters"></a>매개 변수
 `undecoratedOptions`

진행 반환 되는 항목을 제어 하는 플래그의 조합을 지정 합니다. 특정 값 및 수행 하는 작업에 대해서는 설명 부분을 참조 하세요.

 `pRetVal`

제한이 C++ 데코레이팅된 이름에 대해 데코레이팅되지 않은 이름을 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 `S_FALSE` 또는 오류 코드를 반환 합니다.

> [!NOTE]
> @No__t_0의 반환 값은 해당 기호에 대해 속성을 사용할 수 없음을 의미 합니다.

## <a name="remarks"></a>주의
 @No__t_0는 다음 플래그를 조합 하 여 사용할 수 있습니다.

> [!NOTE]
> 플래그 이름이 DIA SDK에 정의 되어 있지 않으므로 코드에 선언을 추가 하거나 원시 값을 사용 해야 합니다.

|플래그|값|설명|
|----------|-----------|-----------------|
|UNDNAME_COMPLETE|0x0000|전체 장식을 사용 합니다.|
|UNDNAME_NO_LEADING_UNDERSCORES|0x0001|Microsoft 확장 키워드에서 선행 밑줄을 제거 합니다.|
|UNDNAME_NO_MS_KEYWORDS|0x0002|Microsoft 확장 키워드의 확장을 사용 하지 않도록 설정 합니다.|
|UNDNAME_NO_FUNCTION_RETURNS|0x0004|기본 선언의 반환 형식 확장을 사용 하지 않도록 설정 합니다.|
|UNDNAME_NO_ALLOCATION_MODEL|0x0008|선언 모델의 확장을 사용 하지 않도록 설정 합니다.|
|UNDNAME_NO_ALLOCATION_LANGUAGE|0x0010|선언 언어 지정자의 확장을 사용 하지 않도록 설정 합니다.|
|UNDNAME_RESERVED1|0x0020|예약됨.|
|UNDNAME_RESERVED2|0x0040|예약됨.|
|UNDNAME_NO_THISTYPE|0x0060|@No__t_0 형식에 대 한 모든 한정자를 사용 하지 않도록 설정 합니다.|
|UNDNAME_NO_ACCESS_SPECIFIERS|0x0080|멤버에 대 한 액세스 지정자 확장을 사용 하지 않습니다.|
|UNDNAME_NO_THROW_SIGNATURES|0x0100|함수 및 함수에 대 한 포인터의 "throw 서명" 확장을 사용 하지 않도록 설정 합니다.|
|UNDNAME_NO_MEMBER_TYPE|0x0200|@No__t_0 또는 `virtual` 멤버의 확장을 사용 하지 않도록 설정 합니다.|
|UNDNAME_NO_RETURN_UDT_MODEL|0x0400|UDT의 Microsoft 모델 반환을 사용 하지 않도록 설정 합니다.|
|UNDNAME_32_BIT_DECODE|0x0800|32 비트 데코 레이트 되지 않은 이름을 데코 레이트 합니다.|
|UNDNAME_NAME_ONLY|0x1000|기본 선언의 이름만 가져옵니다. [scope::] 이름만 반환 합니다.  템플릿 매개 변수를 확장 합니다.|
|UNDNAME_TYPE_ONLY|0x2000|입력은 단지 형식 인코딩입니다. 추상 선언 자를 작성 합니다.|
|UNDNAME_HAVE_PARAMETERS|0x4000|실제 템플릿 매개 변수를 사용할 수 있습니다.|
|UNDNAME_NO_ECSU|0x8000|Enum/클래스/구조체/공용 구조체를 표시 하지 않습니다.|
|UNDNAME_NO_IDENT_CHAR_CHECK|0x10000|유효한 식별자 문자를 확인 하지 않습니다.|
|UNDNAME_NO_PTR64|0x20000|출력에 ptr64를 포함 하지 않습니다.|

## <a name="see-also"></a>참조
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)