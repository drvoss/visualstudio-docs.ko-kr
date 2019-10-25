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
ms.openlocfilehash: 75a81ae23db90b06915e7090a9f2918be3ff18ae
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743400"
---
# <a name="idiaimagedata"></a>IDiaImageData
모듈 또는 이미지의 기본 위치 및 메모리 오프셋에 대 한 세부 정보를 표시 합니다.

## <a name="syntax"></a>구문

```
IDiaImageData : IUnknown
```

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
다음 표에서는 `IDiaImageData`의 메서드를 보여 줍니다.

|메서드|설명|
|------------|-----------------|
|[IDiaImageData::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiaimagedata-get-relativevirtualaddress.md)|응용 프로그램을 기준으로 모듈의 가상 메모리에서 위치를 검색 합니다.|
|[IDiaImageData::get_virtualAddress](../../debugger/debug-interface-access/idiaimagedata-get-virtualaddress.md)|이미지의 가상 메모리에서 위치를 검색 합니다.|
|[IDiaImageData::get_imageBase](../../debugger/debug-interface-access/idiaimagedata-get-imagebase.md)|이미지를 기반으로 하는 메모리 위치를 검색 합니다.|

## <a name="remarks"></a>주의
일부 디버그 스트림 (.XDATA, .PDATA)은 이미지에도 저장 된 데이터의 복사본을 포함 합니다. 이러한 스트림 데이터 개체는 `IDiaImageData` 인터페이스에 대해 쿼리할 수 있습니다. 자세한 내용은이 항목의 "호출자 참고 사항" 섹션을 참조 하세요.

## <a name="notes-for-callers"></a>호출자 참고 사항
[IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md) 개체에서 `QueryInterface`를 호출 하 여이 인터페이스를 가져옵니다. 모든 디버그 스트림이 `IDiaImageData` 인터페이스를 지 원하는 것은 아닙니다. 예를 들어 현재 .XDATA 및 .PDATA 스트림도 `IDiaImageData` 인터페이스를 지원 합니다.

## <a name="example"></a>예제
이 예제에서는 `IDiaImageData` 인터페이스를 지 원하는 모든 스트림에 대해 모든 디버그 스트림을 검색 합니다. 이러한 스트림을 찾으면 해당 스트림에 대 한 일부 정보가 표시 됩니다.

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
헤더: Dia2

라이브러리: diaguids

DLL: msdia80

## <a name="see-also"></a>참조
- [인터페이스(디버그 인터페이스 액세스 SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)
