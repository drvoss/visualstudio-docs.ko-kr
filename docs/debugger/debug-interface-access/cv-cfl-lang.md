---
title: CV_CFL_LANG | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CV_CFL_LANG enumeration
ms.assetid: 4e8e0613-ad02-4de9-9f46-e4753c5b0251
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0fb684d0ff68e5ede6b0847ef9aeba1821ecafcc
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745343"
---
# <a name="cv_cfl_lang"></a>CV_CFL_LANG
응용 프로그램 또는 연결 된 모듈의 소스 코드 언어를 지정 합니다.

## <a name="syntax"></a>구문

```C++
typedef enum CV_CFL_LANG {
    CV_CFL_C       = 0x00,
    CV_CFL_CXX     = 0x01,
    CV_CFL_FORTRAN = 0x02,
    CV_CFL_MASM    = 0x03,
    CV_CFL_PASCAL  = 0x04,
    CV_CFL_BASIC   = 0x05,
    CV_CFL_COBOL   = 0x06,
    CV_CFL_LINK    = 0x07,
    CV_CFL_CVTRES  = 0x08,
    CV_CFL_CVTPGD  = 0x09,
    CV_CFL_CSHARP  = 0x0A,
    CV_CFL_VB      = 0x0B,
    CV_CFL_ILASM   = 0x0C,
    CV_CFL_JAVA    = 0x0D,
    CV_CFL_JSCRIPT = 0x0E,
    CV_CFL_MSIL    = 0x0F,
    CV_CFL_HLSL    = 0x10
} CV_CFL_LANG;
```

## <a name="elements"></a>요소
CV_CFL_C 응용 프로그램 언어는 C입니다.

CV_CFL_CXX 응용 프로그램 언어 C++는입니다.

CV_CFL_FORTRAN 응용 프로그램 언어는 포트란입니다.

CV_CFL_MASM 응용 프로그램 언어는 Microsoft 매크로 어셈블러입니다.

CV_CFL_PASCAL 응용 프로그램 언어는 파스칼식입니다.

CV_CFL_BASIC 응용 프로그램 언어는 기본입니다.

CV_CFL_COBOL 응용 프로그램 언어가 COBOL입니다.

CV_CFL_LINK 응용 프로그램은 링커에서 생성 된 모듈입니다.

CV_CFL_CVTRES 응용 프로그램은 CVTRES 도구로 변환 된 리소스 모듈입니다.

CV_CFL_CVTPGD 응용 프로그램은 CVTPGD 도구를 사용 하 여 생성 된 POGO 최적화 된 모듈입니다.

CV_CFL_CSHARP 응용 프로그램 언어 C#는입니다.

CV_CFL_VB 응용 프로그램 언어가 Visual Basic 되었습니다.

CV_CFL_ILASM 응용 프로그램 언어는 중간 언어 어셈블리 (CLR (공용 언어 런타임) 어셈블리)입니다.

CV_CFL_JAVA 응용 프로그램 언어가 Java입니다.

CV_CFL_JSCRIPT 응용 프로그램 언어가 Jscript입니다.

CV_CFL_MSIL 응용 프로그램 언어가 알 수 없는 MSIL (Microsoft 중간 언어)입니다. [/ltcg (링크 타임 코드 생성)](/cpp/build/reference/ltcg-link-time-code-generation) 스위치를 사용 했을 수 있습니다.

CV_CFL_HLSL 응용 프로그램 언어는 높은 수준의 셰이더 언어입니다.

## <a name="remarks"></a>주의
이 열거형의 값은 [IDiaSymbol:: get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md) 메서드를 호출 하 여 반환 됩니다.

## <a name="requirements"></a>요구 사항
헤더: cvconst

## <a name="see-also"></a>참조
- [열거형 및 구조체](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)
