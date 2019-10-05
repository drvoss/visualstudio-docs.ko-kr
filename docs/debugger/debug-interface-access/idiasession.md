---
title: IDiaSession | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession interface
ms.assetid: 69dab9bf-2c68-4f70-9678-3b50fba3e6fa
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c69383eacfdb39a65cd9a791185d6793e9e6f681
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62832309"
---
# <a name="idiasession"></a>IDiaSession
디버그 기호에 대 한 쿼리 컨텍스트를 제공 합니다.

## <a name="syntax"></a>구문

```
IDiaSession : IUnknown
```

## <a name="methods"></a>메서드
다음 표에서의 메서드를 보여 줍니다. `IDiaSession`합니다.

|메서드|설명|
|------------|-----------------|
|[IDiaSession::get_loadAddress](../../debugger/debug-interface-access/idiasession-get-loadaddress.md)|이 기호 저장소의 기호에 해당 하는 실행 파일의 로드 주소를 검색 합니다. 이 전달 된 값과 동일 합니다 `put_loadAddress` 메서드.|
|[IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)|이 기호 저장소에 기호에 해당 하는 실행 파일의 로드 주소를 설정 합니다. **참고:**  가져올 때이 메서드를 호출 해야는 `IDiaSession` 개체 및 개체를 사용 하 여을 시작 하기 전에 합니다.|
|[IDiaSession::get_globalScope](../../debugger/debug-interface-access/idiasession-get-globalscope.md)|전역 범위에 대 한 참조를 검색합니다.|
|[IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)|기호 저장소에 포함 된 모든 테이블에 대 한 열거자를 검색 합니다.|
|[IDiaSession::getSymbolsByAddr](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md)|정적 위치에 있는 모든 명명 된 기호에 대 한 열거자를 검색합니다.|
|[IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)|지정한 부모 식별자의 이름 및 기호 형식과 일치 하는 모든 자식을 검색 합니다.|
|[IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)|포함 된 단어나 가장 가까운 지정된 된 주소에 지정 된 기호 형식을 검색 합니다.|
|[IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)|포함 된 단어나 가장 가까운 지정 된 상대 가상 주소 (RVA)에 지정 된 기호 형식을 검색 합니다.|
|[IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)|포함 된 단어나 가장 가까운 지정된 된 가상 주소 (VA)에 지정 된 기호 형식을 검색 합니다.|
|[IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)|지정 된 메타 데이터 토큰을 포함 하는 기호를 검색 합니다.|
|[IDiaSession::symsAreEquiv](../../debugger/debug-interface-access/idiasession-symsareequiv.md)|두 기호에 해당 하는 경우를 확인 합니다.|
|[IDiaSession::symbolById](../../debugger/debug-interface-access/idiasession-symbolbyid.md)|해당 고유 식별자로 기호를 검색합니다.|
|[IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)|포함 된 단어나 가장 가까운 지정 된 상대 가상 주소 및 오프셋에 지정 된 기호 형식을 검색 합니다.|
|[IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)|포함 된 단어나 가장 가까운 지정 된 가상 주소와 오프셋을 지정 된 기호 형식을 검색 합니다.|
|[IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)|컴파일 대상 이름으로 소스 파일을 검색합니다.|
|[IDiaSession::findFileById](../../debugger/debug-interface-access/idiasession-findfilebyid.md)|원본 파일 식별자에서 소스 파일을 검색합니다.|
|[IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md)|지정 된 컴파일 대상 및 소스 파일 식별자 내의 줄 번호를 검색합니다.|
|[IDiaSession::findLinesByAddr](../../debugger/debug-interface-access/idiasession-findlinesbyaddr.md)|지정된 된 주소를 포함 하는 지정 된 compiland에서 줄을 검색 합니다.|
|[IDiaSession::findLinesByRVA](../../debugger/debug-interface-access/idiasession-findlinesbyrva.md)|지정된 된 상대 가상 주소를 포함 하는 지정 된 compiland에서 줄을 검색 합니다.|
|[IDiaSession::findLinesByVA](../../debugger/debug-interface-access/idiasession-findlinesbyva.md)|줄 번호 정보를 지정 된 주소 범위에 포함 된 줄을 찾습니다.|
|[IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)|소스 파일 및 줄 번호로 지정된 compiland에서 줄을 검색합니다.|
|[IDiaSession::findInjectedSource](../../debugger/debug-interface-access/idiasession-findinjectedsource.md)|컴파일 프로세스의 다른 구성 요소 또는 특성 공급자에 의해 기호 저장소에 배치 된 소스를 검색 합니다.|
|[IDiaSession::getEnumDebugStreams](../../debugger/debug-interface-access/idiasession-getenumdebugstreams.md)|디버그 데이터 스트림의 열거 순서를 검색합니다.|
|[IDiaSession::findInlineFramesByAddr](../../debugger/debug-interface-access/idiasession-findinlineframesbyaddr.md)|주어진된 주소에 있는 인라인 프레임의 모든 반복에 대 한 클라이언트를 허용 하는 열거자를 검색 합니다.|
|[IDiaSession::findInlineFramesByRVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyrva.md)|클라이언트가 지정 된 상대 가상 주소 (RVA)에 있는 인라인 프레임의 모든 반복 하는 데 사용 하는 열거형을 검색 합니다.|
|[IDiaSession::findInlineFramesByVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyva.md)|클라이언트가 지정된 된 가상 주소 (VA)에 있는 인라인 프레임의 모든 반복 하는 데 사용 하는 열거형을 검색 합니다.|
|[IDiaSession::findInlineeLines](../../debugger/debug-interface-access/idiasession-findinlineelines.md)|클라이언트가 모든 없는 함수를 인라인을 직접 또는 간접적으로 지정 된 부모 기호는 줄 번호 정보를 반복 하는 데 사용 하는 열거형을 검색 합니다.|
|[IDiaSession::findInlineeLinesByAddr](../../debugger/debug-interface-access/idiasession-findinlineelinesbyaddr.md)|클라이언트가 모든 없는 함수를 인라인을 직접 또는 간접적으로 지정 된 부모 기호는 줄 번호 정보를 반복 하는 데 사용 하는 지정 된 주소 범위 내에 포함 된 열거자를 검색 합니다.|
|[IDiaSession::findInlineeLinesByRVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyrva.md)|클라이언트가 모든 없는 함수를 인라인을 직접 또는 간접적으로 지정 된 부모 기호는 줄 번호 정보를 반복 하는 데 사용 하는 지정 된 가상 RVA (상대 주소) 내에 포함 된 열거자를 검색 합니다.|
|[IDiaSession::findInlineeLinesByVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyva.md)|클라이언트가 모든 없는 함수를 인라인을 직접 또는 간접적으로 지정 된 부모 기호는 줄 번호 정보를 반복 하는 데 사용 하는 지정 된 가상 주소 (VA) 내에 포함 된 열거자를 검색 합니다.|
|[IDiaSession::findInlineeLinesByLinenum](../../debugger/debug-interface-access/idiasession-findinlineelinesbylinenum.md)|클라이언트가 모든 함수에에서 있지 않은 인라인을 직접 또는 간접적으로 지정 된 소스 파일과 줄 번호의 줄 번호 정보를 반복 하는 데 사용 하는 열거형을 검색 합니다.|
|[IDiaSession::findInlineesByName](../../debugger/debug-interface-access/idiasession-findinlineesbyname.md)|클라이언트가 지정 된 이름과 일치 하는 모든 인라인 함수의 줄 번호 정보를 반복 하는 데 사용 하는 열거형을 검색 합니다.|
|[IDiaSession::findSymbolsForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsforacceleratorpointertag.md)|부모 Accelerator 스텁 함수에서에서 지정 된 태그 값에 해당 하는 변수에 대 한 기호의 열거형을 반환 합니다.|
|[IDiaSession::findSymbolsByRVAForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsbyrvaforacceleratorpointertag.md)|이 메서드 해당 태그 값을 지정 합니다 지정된 된 상대 가상 주소에서 지정 된 부모 가속기 스텁 함수에 포함 된 기호의 열거형을 반환 합니다.|
|[IDiaSession::findAcceleratorInlineesByName](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbyname.md)|지정 된 인라인 함수 이름에 해당 하는 인라인 프레임에 대 한 기호의 열거형을 반환 합니다.|
|[IDiaSession::findAcceleratorInlineesByLinenum](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbylinenum.md)|지정한 원본 위치에 해당 하는 인라인 프레임에 대 한 기호의 열거형을 반환 합니다.|

## <a name="remarks"></a>설명
호출 해야 합니다 [idiasession:: Put_loadaddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) 메서드를 만든 후를 `IDiaSession` 개체-및 전달 되는 값을 `put_loadAddress` 메서드는 0이 아닌 값 이어야 합니다.-기호 수의 가상 주소 (VA) 속성에 대 한 액세스할 수 있습니다. 원하는 프로그램 로드 디버깅 중인 실행 파일의 로드 주소 제공 됩니다. 예를 들어 Win32 함수를 호출할 수 있습니다 `GetModuleInformation` 검색할 실행 파일의 로드 주소 실행 파일에 대 한 핸들을 지정 합니다.

## <a name="example"></a>예제
가져오는 방법을 보여 주는이 예제는 `IDiaSession` DIA sdk 일반 초기화의 일부로 인터페이스입니다.

```C++
CComPtr<IDiaDataSource> pSource;
ComPtr<IDiaSession> psession;

void InitializeDIA(const char *szFilename)
{
    HRESULT hr = CoCreateInstance( CLSID_DiaSource,
                                   NULL,
                                   CLSCTX_INPROC_SERVER,
                                   __uuidof( IDiaDataSource ),
                                  (void **) &pSource);
    if (FAILED(hr))
    {
        Fatal("Could not CoCreate CLSID_DiaSource. Register msdia80.dll." );
    }
    wchar_t wszFilename[ _MAX_PATH ];
    mbstowcs( wszFilename,
              szFilename,
              sizeof( wszFilename )/sizeof( wszFilename[0] ) );
    if ( FAILED( pSource->loadDataFromPdb( wszFilename ) ) )
    {
        if ( FAILED( pSource->loadDataForExe( wszFilename, NULL, NULL ) ) )
        {
            Fatal( "loadDataFromPdb/Exe" );
        }
    }
    if ( FAILED( pSource->openSession( &psession ) ) )
    {
        Fatal( "openSession" );
    }
}
```

## <a name="requirements"></a>요구 사항
헤더: Dia2.h

라이브러리: diaguids.lib

DLL: msdia80.dll

## <a name="see-also"></a>참고 항목
- [인터페이스(디버그 인터페이스 액세스 SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [개요](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)
- [Exe](../../debugger/debug-interface-access/exe.md)
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
- [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)
- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
- [.Pdb 파일 쿼리](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)
