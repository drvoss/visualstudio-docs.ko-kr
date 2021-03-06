---
title: CV_CFL_LANG | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- CV_CFL_LANG enumeration
ms.assetid: 4e8e0613-ad02-4de9-9f46-e4753c5b0251
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f6e2aa402d3f882d83525b180707653b97533e32
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51724797"
---
# <a name="cvcfllang"></a>CV_CFL_LANG
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

응용 프로그램 또는 연결 된 모듈의 소스 코드 언어를 지정합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
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
 CV_CFL_C  
 응용 프로그램 언어는 C입니다.  
  
 CV_CFL_CXX  
 응용 프로그램 언어는 c + +입니다.  
  
 CV_CFL_FORTRAN  
 응용 프로그램 언어가 FORTRAN 합니다.  
  
 CV_CFL_MASM  
 응용 프로그램 언어는 Microsoft Macro Assembler입니다.  
  
 CV_CFL_PASCAL  
 응용 프로그램 언어는 파스칼식입니다.  
  
 CV_CFL_BASIC  
 응용 프로그램 언어는 BASIC입니다.  
  
 CV_CFL_COBOL  
 응용 프로그램 언어는 COBOL입니다.  
  
 CV_CFL_LINK  
 응용 프로그램에는 링커 생성 모듈입니다.  
  
 CV_CFL_CVTRES  
 응용 프로그램은 CVTRES 도구를 사용 하 여 변환 하는 리소스 모듈입니다.  
  
 CV_CFL_CVTPGD  
 응용 프로그램은 CVTPGD 도구를 사용 하 여 생성 된 POGO 액세스에 최적화 된 모듈입니다.  
  
 CV_CFL_CSHARP  
 응용 프로그램 언어는 C#입니다.  
  
 CV_CFL_VB  
 응용 프로그램 언어는 Visual Basic입니다.  
  
 CV_CFL_ILASM  
 응용 프로그램 언어는 중간 언어 어셈블리 (즉, 공용 언어 런타임 (CLR) 어셈블리)입니다.  
  
 CV_CFL_JAVA  
 응용 프로그램 언어가 Java 합니다.  
  
 CV_CFL_JSCRIPT  
 응용 프로그램 언어는 Jscript입니다.  
  
 CV_CFL_MSIL  
 응용 프로그램 언어가 알 수 없는 언어 MSIL (Microsoft Intermediate)를 사용 하 여 결과 수를 [/LTCG (링크 타임 코드 생성)](http://msdn.microsoft.com/library/788c6f52-fdb8-40c2-90af-4026ea2cf2e2) 전환 합니다.  
  
 CV_CFL_HLSL  
 응용 프로그램 언어는 High Level Shader Language입니다.  
  
## <a name="remarks"></a>설명  
 이 열거형의 값에는 호출에서 반환 되는 [idiasymbol:: Get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md) 메서드.  
  
## <a name="requirements"></a>요구 사항  
 헤더: cvconst.h  
  
## <a name="see-also"></a>참고 항목  
 [열거형 및 구조체](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)



