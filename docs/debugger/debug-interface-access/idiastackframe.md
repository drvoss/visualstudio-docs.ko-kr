---
title: IDiaStackFrame | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame interface
ms.assetid: 486d25b8-a590-41c1-bdb5-faff3ae35632
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3252d15ebfb06fa840bfad6bf74dc3b8748776ef
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62838095"
---
# <a name="idiastackframe"></a>IDiaStackFrame
스택 프레임의 속성을 표시 합니다.

## <a name="syntax"></a>구문

```
IDiaStackFrame : IUnknown
```

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
다음은이 인터페이스에서 지원 되는 방법입니다.

|메서드|설명|
|------------|-----------------|
|[IDiaStackFrame::get_allocatesBasePointer](../../debugger/debug-interface-access/idiastackframe-get-allocatesbasepointer.md)|이 주소 범위에서 코드에 대 한 기본 포인터 할당 되는 나타내는 플래그를 검색 합니다. 이 메서드는 사용 되지 않습니다.|
|[IDiaStackFrame::get_base](../../debugger/debug-interface-access/idiastackframe-get-base.md)|프레임의 주소 자료를 검색합니다.|
|[IDiaStackFrame::get_cplusplusExceptionHandling](../../debugger/debug-interface-access/idiastackframe-get-cplusplusexceptionhandling.md)|나타내는 플래그를 검색 C++ 예외 처리에 적용 됩니다.|
|[IDiaStackFrame::get_functionStart](../../debugger/debug-interface-access/idiastackframe-get-functionstart.md)|블록에 함수의 진입점이 포함 되어 있음을 나타내는 플래그를 검색 합니다.|
|[IDiaStackFrame::get_lengthLocals](../../debugger/debug-interface-access/idiastackframe-get-lengthlocals.md)|스택에 있는 지역 변수의 바이트 수를 검색 합니다.|
|[IDiaStackFrame::get_lengthParams](../../debugger/debug-interface-access/idiastackframe-get-lengthparams.md)|스택에 푸시된 매개 변수는 바이트 수를 검색 합니다.|
|[IDiaStackFrame::get_lengthProlog](../../debugger/debug-interface-access/idiastackframe-get-lengthprolog.md)|블록에서 프롤로그 코드의 바이트 수를 검색합니다.|
|[IDiaStackFrame::get_lengthSavedRegisters](../../debugger/debug-interface-access/idiastackframe-get-lengthsavedregisters.md)|스택에 저장 된 레지스터의 바이트 수를 검색 합니다.|
|[IDiaStackFrame::get_localsBase](../../debugger/debug-interface-access/idiastackframe-get-localsbase.md)|로컬의 주소 자료를 검색합니다.|
|[IDiaStackFrame::get_maxStack](../../debugger/debug-interface-access/idiastackframe-get-maxstack.md)|프레임의 스택에 바이트의 최대 수를 검색 합니다.|
|[IDiaStackFrame::get_rawLVarInstanceValue](../../debugger/debug-interface-access/idiastackframe-get-rawlvarinstancevalue.md)|원시 바이트로 지정 된 로컬 변수의 값을 검색합니다.|
|[IDiaStackFrame::get_registerValue](../../debugger/debug-interface-access/idiastackframe-get-registervalue.md)|지정 된 레지스터의 값을 검색합니다.|
|[IDiaStackFrame::get_returnAddress](../../debugger/debug-interface-access/idiastackframe-get-returnaddress.md)|프레임의 반환 주소를 검색합니다.|
|[IDiaStackFrame::get_size](../../debugger/debug-interface-access/idiastackframe-get-size.md)|바이트 단위로 프레임의 크기를 검색합니다.|
|[IDiaStackFrame::get_systemExceptionHandling](../../debugger/debug-interface-access/idiastackframe-get-systemexceptionhandling.md)|시스템 예외 처리 적용 중임을 나타내는 플래그를 검색 합니다.|
|[IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)|프레임 유형을 검색합니다.|

## <a name="remarks"></a>설명
스택 프레임에는 해당 실행 하는 동안 함수 호출의 추상화입니다.

## <a name="notes-for-callers"></a>호출자에 대 한 정보
이 인터페이스를 호출 하 여 가져올는 [idiaenumstackframes:: Next](../../debugger/debug-interface-access/idiaenumstackframes-next.md) 메서드. 참조를 [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md) 얻는 방법에 예제에 대 한 인터페이스를 `IDiaStackFrame` 인터페이스입니다.

## <a name="example"></a>예제
이 예제는 스택 프레임의 다양 한 특성을 표시합니다.

```C++
void PrintStackFrame(IDiaStackFrame* pFrame)
{
    if (pFrame != NULL)
    {
        ULONGLONG bottom = 0;
        ULONGLONG top    = 0;

        if (pFrame->get_base(&bottom) == S_OK &&
            pFrame->get_registerValue( CV_REG_ESP, &top ) == S_OK )
        {
            printf("range = 0x%08I64x - 0x%08I64x\n", bottom, top);
        }

        ULONGLONG returnAddress = 0;
        if (pFrame->get_returnAddress(&returnAddress) == S_OK)
        {
            printf("return address = 0x%08I64x\n", returnAddress);
        }

        DWORD lengthFrame     = 0;
        DWORD lengthLocals    = 0;
        DWORD lengthParams    = 0;
        DWORD lengthProlog    = 0;
        DWORD lengthSavedRegs = 0;
        if (pFrame->get_size(&lengthFrame) == S_OK &&
            pFrame->get_lengthLocals(&lengthLocals) == S_OK &&
            pFrame->get_lengthParams(&lengthParams) == S_OK &&
            pFrame->get_lengthProlog(&lengthProlog) == S_OK &&
            pFrame->get_lengthSavedRegisters(&lengthSavedRegs) == S_OK)
        {
            printf("stack frame size          = 0x%08lx bytes\n", lengthFrame);
            printf("length of locals          = 0x%08lx bytes\n", lengthLocals);
            printf("length of parameters      = 0x%08lx bytes\n", lengthParams);
            printf("length of prolog          = 0x%08lx bytes\n", lengthProlog);
            printf("length of saved registers = 0x%08lx bytes\n", lengthSavedRegs);
        }
    }
}
```

## <a name="requirements"></a>요구 사항
헤더: Dia2.h

라이브러리: diaguids.lib

DLL: msdia80.dll

## <a name="see-also"></a>참고 항목
- [인터페이스(디버그 인터페이스 액세스 SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)
- [IDiaEnumStackFrames::Next](../../debugger/debug-interface-access/idiaenumstackframes-next.md)
- [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)
