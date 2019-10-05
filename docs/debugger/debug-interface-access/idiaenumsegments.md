---
title: IDiaEnumSegments | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments interface
ms.assetid: 0c9edd5e-b9ce-43e1-a791-cd4c5d16d923
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 255c55dff0dab0c7b36f5029de9e688db949a1fe
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62833430"
---
# <a name="idiaenumsegments"></a>IDiaEnumSegments
데이터 원본에 포함 된 다양 한 세그먼트를 열거 합니다.

## <a name="syntax"></a>구문

```
IDiaEnumSegments : IUnknown
```

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
다음 표에서의 메서드를 보여 줍니다. `IDiaEnumSegments`합니다.

|메서드|설명|
|------------|-----------------|
|[IDiaEnumSegments::get__NewEnum](../../debugger/debug-interface-access/idiaenumsegments-get-newenum.md)|검색 된 [IEnumVARIANT 인터페이스](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ienumvariant) 이 열거자의 버전입니다.|
|[IDiaEnumSegments::get_Count](../../debugger/debug-interface-access/idiaenumsegments-get-count.md)|세그먼트의 수를 검색합니다.|
|[IDiaEnumSegments::Item](../../debugger/debug-interface-access/idiaenumsegments-item.md)|인덱스를 사용 하 여 세그먼트를 검색합니다.|
|[IDiaEnumSegments::Next](../../debugger/debug-interface-access/idiaenumsegments-next.md)|열거형 시퀀스에서 세그먼트의 지정된 된 수를 검색 합니다.|
|[IDiaEnumSegments::Skip](../../debugger/debug-interface-access/idiaenumsegments-skip.md)|열거형 시퀀스에서 세그먼트의 지정 된 수를 건너뜁니다.|
|[IDiaEnumSegments::Reset](../../debugger/debug-interface-access/idiaenumsegments-reset.md)|열거형 시퀀스를 처음으로 다시 설정합니다.|
|[IDiaEnumSegments::Clone](../../debugger/debug-interface-access/idiaenumsegments-clone.md)|현재 열거자와 열거 상태가 같은 포함 하는 열거자를 만듭니다.|

## <a name="remarks"></a>설명

## <a name="notes-for-callers"></a>호출자에 대 한 정보
호출 하 여이 인터페이스를 가져올는 `QueryInterface` 메서드는 [IDiaTable](../../debugger/debug-interface-access/idiatable.md) 개체입니다. 세부 정보에 대 한 예제를 참조 하세요.

## <a name="example"></a>예제
가져오는 방법을 보여 주는이 예제는 `IDiaEnumSections` 테이블에서 인터페이스입니다. 세그먼트를 사용 하 여 자세한 예제를 참조 하세요. 합니다 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) 인터페이스입니다.

```C++
void ShowSegments(IDiaTable *pTable, IDiaSession *pSession)
{
    CComPtr<IDiaEnumSegments> pSegments;
    if ( SUCCEEDED( pTable->QueryInterface(
                                __uuidof( IDiaEnumSegments ),
                                (void**)&pSegments )
                  )
       )
    {
        // Do something with this enumeration
    }
}
```

## <a name="requirements"></a>요구 사항
헤더: Dia2.h

라이브러리: diaguids.lib

DLL: msdia80.dll

## <a name="see-also"></a>참고 항목
- [인터페이스(디버그 인터페이스 액세스 SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaTable](../../debugger/debug-interface-access/idiatable.md)
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)
