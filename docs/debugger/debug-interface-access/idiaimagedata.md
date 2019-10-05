---
title: IDiaImageData | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaImageData interface
ms.assetid: b696f350-fc08-4352-9287-a15e87512c1e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b1e3dd8c395c59bc3255c1c9ee55837466c1cef7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62828517"
---
# <a name="idiaimagedata"></a>IDiaImageData
모듈 또는 이미지의 기본 위치와 메모리 오프셋의 세부 정보를 표시합니다.

## <a name="syntax"></a>구문

```
IDiaImageData : IUnknown
```

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
다음 표에서의 메서드를 보여 줍니다. `IDiaImageData`합니다.

|메서드|설명|
|------------|-----------------|
|[IDiaImageData::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiaimagedata-get-relativevirtualaddress.md)|응용 프로그램에 상대적인 모듈의 가상 메모리의 위치를 검색합니다.|
|[IDiaImageData::get_virtualAddress](../../debugger/debug-interface-access/idiaimagedata-get-virtualaddress.md)|이미지의 가상 메모리의 위치를 검색합니다.|
|[IDiaImageData::get_imageBase](../../debugger/debug-interface-access/idiaimagedata-get-imagebase.md)|여기서 이미지를 기반으로 하는 메모리 위치를 검색 합니다.|

## <a name="remarks"></a>설명
일부 디버그 스트림 (XDATA, PDATA) 이미지에도 저장 된 데이터의 복사본을 포함 합니다. 이 스트림 개체를 쿼리할 수 데이터는 `IDiaImageData` 인터페이스입니다. 자세한 내용은이 항목의 "호출자에 대 한 참고 사항" 섹션을 참조 합니다.

## <a name="notes-for-callers"></a>호출자에 대 한 정보
호출 하 여이 인터페이스를 가져올 `QueryInterface` 에 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md) 개체입니다. 모든 디버그는 스트림 지원은 `IDiaImageData` 인터페이스입니다. 예를 들어 현재 XDATA 및 PDATA 스트림을 지원 합니다 `IDiaImageData` 인터페이스입니다.

## <a name="example"></a>예제
이 예에서는 검색을 지 원하는 모든 스트림에 대 한 디버그 스트림의 모든는 `IDiaImageData` 인터페이스입니다. 이러한 스트림이 있으면 해당 스트림에 대 한 일부 정보가 표시 됩니다.

```C++
void ShowImageData(IDiaSession *pSession)
{
    if (pSession != NULL)
    {
        CComPtr<IDiaEnumDebugStreams> pStreamsList;
        HRESULT hr;

        hr = pSession->getEnumDebugStreams(&pStreamsList);
        if (SUCCEEDED(hr))
        {
            LONG numStreams = 0;
            hr = pStreamsList->get_Count(&numStreams);
            if (SUCCEEDED(hr))
            {
                ULONG fetched = 0;
                for (LONG i = 0; i < numStreams; i++)
                {
                    CComPtr<IDiaEnumDebugStreamData> pStream;
                    hr = pStreamsList->Next(1,&pStream,&fetched);
                    if (fetched == 1)
                    {
                        CComPtr<IDiaImageData> pImageData;
                        hr = pStream->QueryInterface(__uuidof(IDiaImageData),
                                                     (void **)&pImageData);
                        if (SUCCEEDED(hr))
                        {
                            CComBSTR name;
                            hr = pStream->get_name(&name);
                            if (SUCCEEDED(hr))
                            {
                                wprintf(L"Stream %s:\n",(BSTR)name);
                            }
                            else
                            {
                                wprintf(L"Failed to get name of stream\n");
                            }

                            ULONGLONG imageBase = 0;
                            if (pImageData->get_imageBase(&imageBase) == S_OK)
                            {
                                wprintf(L"  image base = 0x%0I64x\n",imageBase);
                            }

                            DWORD relVA = 0;
                            if (pImageData->get_relativeVirtualAddress(&relVA) == S_OK)
                            {
                                wprintf(L"  relative virtual address = 0x%08lx\n",relVA);
                            }

                            ULONGLONG va = 0;
                            if (pImageData->get_virtualAddress(&va) == S_OK)
                            {
                                wprintf(L"  virtual address = 0x%0I64x\n", va);
                            }
                        }
                    }
                }
            }
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
- [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)
