---
title: IDiaSegment | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSegment interface
ms.assetid: 384ae0e1-077e-4d4f-98de-ac43c32c882f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 855b40f3d35d884a366e8fdc36ed1ec4f2bef85a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742332"
---
# <a name="idiasegment"></a>IDiaSegment
섹션 번호의 데이터를 주소 공간의 세그먼트로 매핑합니다.

## <a name="syntax"></a>구문

```
IDiaSegment : IUnknown
```

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
다음 표에서는 `IDiaSegment`의 메서드를 보여 줍니다.

|메서드|설명|
|------------|-----------------|
|[IDiaSegment::get_frame](../../debugger/debug-interface-access/idiasegment-get-frame.md)|세그먼트 번호를 검색 합니다.|
|[IDiaSegment::get_offset](../../debugger/debug-interface-access/idiasegment-get-offset.md)|섹션을 시작 하는 세그먼트의 오프셋을 검색 합니다.|
|[IDiaSegment::get_length](../../debugger/debug-interface-access/idiasegment-get-length.md)|세그먼트의 바이트 수를 검색 합니다.|
|[IDiaSegment::get_read](../../debugger/debug-interface-access/idiasegment-get-read.md)|세그먼트를 읽을 수 있는지 여부를 나타내는 플래그를 검색 합니다.|
|[IDiaSegment::get_write](../../debugger/debug-interface-access/idiasegment-get-write.md)|세그먼트를 수정할 수 있는지 여부를 나타내는 플래그를 검색 합니다.|
|[IDiaSegment::get_execute](../../debugger/debug-interface-access/idiasegment-get-execute.md)|세그먼트가 실행 가능한 지 여부를 나타내는 플래그를 검색 합니다.|
|[IDiaSegment::get_addressSection](../../debugger/debug-interface-access/idiasegment-get-addresssection.md)|이 세그먼트에 매핑되는 섹션 번호를 검색 합니다.|
|[IDiaSegment::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasegment-get-relativevirtualaddress.md)|섹션 시작의 RVA (상대 가상 주소)를 검색 합니다.|
|[IDiaSegment::get_virtualAddress](../../debugger/debug-interface-access/idiasegment-get-virtualaddress.md)|섹션 시작 부분의 VA (가상 주소)를 검색 합니다.|

## <a name="remarks"></a>주의
DIA SDK는 이미 상대 가상 주소로 섹션 오프셋에서 번역을 수행 하기 때문에 대부분의 응용 프로그램은 세그먼트 맵의 정보를 사용 하지 않습니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
[IDiaEnumSegments:: Item](../../debugger/debug-interface-access/idiaenumsegments-item.md) 또는 [IDiaEnumSegments:: Next](../../debugger/debug-interface-access/idiaenumsegments-next.md) 메서드를 호출 하 여이 인터페이스를 가져옵니다. 자세한 내용은 예제를 참조 하세요.

## <a name="example"></a>예제
이 함수는 테이블의 모든 세그먼트 주소와 가장 가까운 기호를 표시 합니다.

```C++
void ShowSegments(IDiaTable *pTable, IDiaSession *pSession)
{
    CComPtr<IDiaEnumSegments> pSegments;
    if ( SUCCEEDED( pTable->QueryInterface(
                                _uuidof( IDiaEnumSegments ),
                               (void**)&pSegments )
                  )
       )
    {
        CComPtr<IDiaSegment> pSegment;
        while ( SUCCEEDED( hr = pSegments->Next( 1, &pSegment, &celt ) ) &&
                celt == 1 )
        {
            DWORD rva;
            DWORD seg;

            pSegment->get_addressSection( &seg );
            if ( pSegment->get_relativeVirtualAddress( &rva ) == S_OK )
            {
                printf( "Segment %i addr: 0x%.8X\n", seg, rva );
                pSegment = NULL;

                CComPtr<IDiaSymbol> pSym;
                if ( psession->findSymbolByRVA( rva, SymTagNull, &pSym ) == S_OK )
                {
                    CDiaBSTR name;
                    DWORD    tag;

                    pSym->get_symTag( &tag );
                    pSym->get_name( &name );
                    printf( "\tClosest symbol: %ws (%ws)\n",
                            name != NULL ? name : L"",
                            szTags[ tag ] );
                }
            }
        }
    }
}
```

## <a name="requirements"></a>요구 사항
헤더: Dia2

라이브러리: diaguids

DLL: msdia80

## <a name="see-also"></a>참조
- [인터페이스(디버그 인터페이스 액세스 SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumSegments::Item](../../debugger/debug-interface-access/idiaenumsegments-item.md)
- [IDiaEnumSegments::Next](../../debugger/debug-interface-access/idiaenumsegments-next.md)
