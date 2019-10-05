---
title: IDebugEnumField::GetValueFromStringCaseInsensitive | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetValueFromStringCaseInsensitive
helpviewer_keywords:
- IDebugEnumField::GetValueFromStringCaseInsensitive method
ms.assetid: ef95b38e-d9b2-4fb5-a166-7c2e14641dc7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 72e6f79616c8c8099b938a29bc1d1809adb152a3
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350060"
---
# <a name="idebugenumfieldgetvaluefromstringcaseinsensitive"></a>IDebugEnumField::GetValueFromStringCaseInsensitive
이 메서드가 열거형 상수의 이름과 연관 된 값을 반환 하는 대/소문자 구분 검색을 사용 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetValueFromStringCaseInsensitive(
   LPCOLESTR  pszValue,
   ULONGLONG* pvalue
);
```

```csharp
int GetValueFromStringCaseInsensitive(
   string    pszValue,
   out ulong pValue
);
```

## <a name="parameters"></a>매개 변수
`pszValue`\
[in] 값을 검색할 원본에 대 한 이름을 지정 하는 문자열입니다. 에 대 한는 C++, 와이드 문자 문자열입니다.

`pValue`\
[out] 연결된 된 숫자 값을 반환합니다.

## <a name="return-value"></a>반환 값
 에 성공 하면 반환 `S_OK`이 고, 그렇지 않으면 반환 `S_FALSE`이면 이름, 열거형 또는 오류 코드의 일부가 아닙니다.

## <a name="remarks"></a>설명
 이 메서드는 대/소문자 구분 합니다. 대/소문자 구분 검색을 필요한 경우 (예를 들어 같은 언어에서에서 C++ 이름은 대/소문자 구분)를 사용 하 여 [GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)합니다.

## <a name="see-also"></a>참고자료
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
- [GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)