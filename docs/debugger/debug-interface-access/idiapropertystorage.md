---
title: IDiaPropertyStorage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage interface
ms.assetid: d3197a38-5973-4e56-873e-4f1b84c3f674
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2de57f0d3bd44e4d46f19ee74484380bf0e6f2ae
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742836"
---
# <a name="idiapropertystorage"></a>IDiaPropertyStorage
DIA 속성 집합의 영구적 속성을 읽을 수 있습니다.

## <a name="syntax"></a>구문

```
IDiaPropertyStorage : IUnknown
```

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
다음 표에서는 `IDiaPropertyStorage`의 메서드를 보여 줍니다.

|메서드|설명|
|------------|-----------------|
|[IDiaPropertyStorage::Enum](../../debugger/debug-interface-access/idiapropertystorage-enum.md)|이 집합 내에 있는 속성의 열거자에 대 한 포인터를 가져옵니다.|
|[IDiaPropertyStorage::ReadBOOL](../../debugger/debug-interface-access/idiapropertystorage-readbool.md)|속성 집합에서 `BOOL` 값을 읽습니다.|
|[IDiaPropertyStorage::ReadBSTR](../../debugger/debug-interface-access/idiapropertystorage-readbstr.md)|속성 집합에서 `BSTR` 값을 읽습니다.|
|[IDiaPropertyStorage::ReadDWORD](../../debugger/debug-interface-access/idiapropertystorage-readdword.md)|속성 집합에서 `DWORD` 값을 읽습니다.|
|[IDiaPropertyStorage::ReadLONG](../../debugger/debug-interface-access/idiapropertystorage-readlong.md)|속성 집합에서 `LONG` 값을 읽습니다.|
|[IDiaPropertyStorage::ReadMultiple](../../debugger/debug-interface-access/idiapropertystorage-readmultiple.md)|속성 집합의 속성 값을 읽습니다.|
|[IDiaPropertyStorage::ReadPropertyNames](../../debugger/debug-interface-access/idiapropertystorage-readpropertynames.md)|지정 된 속성 식별자에 해당 하는 문자열 이름을 가져옵니다.|
|[IDiaPropertyStorage::ReadULONGLONG](../../debugger/debug-interface-access/idiapropertystorage-readulonglong.md)|속성 집합에서 `ULONGLONG` 값을 읽습니다.|

## <a name="remarks"></a>주의
속성 집합 내의 각 속성은 해당 집합에 고유한 4 바이트 `ULONG` 값인 속성 식별자 (ID)로 식별 됩니다. @No__t_0 인터페이스를 통해 노출 되는 속성은 부모 인터페이스에서 사용할 수 있는 속성에 해당 합니다. 예를 들어 `IDiaPropertyStorage` 인터페이스를 통해 이름으로 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 인터페이스의 속성에 액세스할 수 있습니다. 그러나 속성에 액세스할 수 있는 경우에도 속성이 특정 `IDiaSymbol` 개체에 대해 유효한 지는 것을 의미 하지는 않습니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
다른 인터페이스에서 `QueryInterface` 메서드를 호출 하 여이 인터페이스를 가져옵니다. @No__t_0 인터페이스에 대해 쿼리할 수 있는 인터페이스는 다음과 같습니다.

- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)

- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)

- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)

- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)

- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)

- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)

- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)

## <a name="example"></a>예제
이 예제에서는 `IDiaPropertyStorage` 개체에서 노출 하는 모든 속성을 표시 하는 함수를 보여 줍니다. [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) 인터페이스에서 `IDiaPropertyStorage` 인터페이스를 가져오는 방법에 대 한 예제는 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) 인터페이스를 참조 하세요.

```C++
void PrintPropertyStorage(IDiaPropertyStorage* pPropertyStorage)
{
    IEnumSTATPROPSTG* pEnumProps;
    STATPROPSTG       prop;
    DWORD             celt = 1;

    if (pPropertyStorage->Enum(&pEnumProps) == S_OK)
    {
        while (pEnumProps->Next(celt, &prop, &celt) == S_OK)
        {
            PROPSPEC pspec = { PRSPEC_PROPID, prop.propid };
            PROPVARIANT vt = { VT_EMPTY };

            if (pPropertyStorage->ReadMultiple( 1, &pspec, &vt) == S_OK)
            {
                switch( vt.vt ){
                    case VT_BOOL:
                        wprintf( L"%32s:\t %s\n", prop.lpwstrName, vt.bVal ? L"true" : L"false" );
                        break;
                    case VT_I2:
                        wprintf( L"%32s:\t %d\n", prop.lpwstrName, vt.iVal );
                        break;
                    case VT_UI2:
                        wprintf( L"%32s:\t %d\n", prop.lpwstrName, vt.uiVal );
                        break;
                    case VT_I4:
                        wprintf( L"%32s:\t %d\n", prop.lpwstrName, vt.intVal );
                        break;
                    case VT_UI4:
                        wprintf( L"%32s:\t 0x%0x\n", prop.lpwstrName, vt.uintVal );
                        break;
                    case VT_UI8:
                        wprintf( L"%32s:\t 0x%x\n", prop.lpwstrName, vt.uhVal.QuadPart );
                        break;
                    case VT_BSTR:
                        wprintf( L"%32s:\t %s\n", prop.lpwstrName, vt.bstrVal );
                        break;
                    case VT_UNKNOWN:
                        wprintf( L"%32s:\t %p\n", prop.lpwstrName, vt.punkVal );
                        break;
                    case VT_SAFEARRAY:
                        break;
                    default:
                       break;
                }
                VariantClear((VARIANTARG*) &vt);
            }
        }
        pEnumProps->Release();
    }
}
```

## <a name="requirements"></a>요구 사항
헤더: Dia2

라이브러리: diaguids

DLL: msdia80

## <a name="see-also"></a>참조
- [인터페이스(디버그 인터페이스 액세스 SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)
