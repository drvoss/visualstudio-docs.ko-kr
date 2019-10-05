---
title: 쿼리 합니다. Pdb 파일 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- PDB files
- .pdb files, querying
ms.assetid: 8da07d1c-2712-45f9-8fbf-f34040408a8a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3a67dc121790acff1f5e39a82a1711317616fc2d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62855047"
---
# <a name="querying-the-pdb-file"></a>.Pdb 파일 쿼리
프로그램 데이터베이스 파일 (확장 확장자는.pdb) 이진 파일 형식 및 컴파일 및 연결 프로젝트 과정에서 수집 된 기호 디버깅 정보를 포함 하는 경우 C를 컴파일할 때 PDB 파일을 만들 /C++ 사용 하 여 프로그래밍 **/ZI** 또는 **/Zi** 또는 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]를 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], 또는 [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] 사용 하 여 프로그래밍 합니다 **디버그**옵션입니다. 개체 파일에는 디버깅 정보에 대 한.pdb 파일에 대 한 참조를 포함 합니다. Pdb 파일에 대 한 자세한 내용은 참조 하세요. [PDB 파일](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/yd4f8bd1(v=vs.100))합니다. DIA 응용 프로그램을 다음과 같은 일반적인 단계를 사용 하 여 다양 한 기호, 개체 및 실행 가능 이미지 내의 데이터 요소에 대 한 자세한 정보를 얻을 수 있습니다.

### <a name="to-query-the-pdb-file"></a>.Pdb 파일 쿼리

1. 데이터 원본을 만들어 가져올는 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md) 인터페이스입니다.

    ```C++
    CComPtr<IDiaDataSource> pSource;
    hr = CoCreateInstance( CLSID_DiaSource,
                           NULL,
                           CLSCTX_INPROC_SERVER,
                           __uuidof( IDiaDataSource ),
                          (void **) &pSource);

    if (FAILED(hr))
    {
        Fatal("Could not CoCreate CLSID_DiaSource. Register msdia80.dll." );
    }
    ```

2. 호출 [idiadatasource:: Loaddatafrompdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) 하거나 [idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) 디버깅 정보를 로드 합니다.

    ```C++
    wchar_t wszFilename[ _MAX_PATH ];
    mbstowcs( wszFilename, szFilename, sizeof( wszFilename )/sizeof( wszFilename[0] ) );
    if ( FAILED( pSource->loadDataFromPdb( wszFilename ) ) )
    {
        if ( FAILED( pSource->loadDataForExe( wszFilename, NULL, NULL ) ) )
        {
            Fatal( "loadDataFromPdb/Exe" );
        }
    }
    ```

3. 호출 [idiadatasource:: Opensession](../../debugger/debug-interface-access/idiadatasource-opensession.md) 여는 [IDiaSession](../../debugger/debug-interface-access/idiasession.md) 디버깅 정보에 액세스할 수 있습니다.

    ```C++
    CComPtr<IDiaSession> psession;
    if ( FAILED( pSource->openSession( &psession ) ) )
    {
        Fatal( "openSession" );
    }
    ```

4. 메서드를 사용 하 여 `IDiaSession` 데이터 소스의 기호에 대 한 쿼리 합니다.

    ```C++
    CComPtr<IDiaSymbol> pglobal;
    if ( FAILED( psession->get_globalScope( &pglobal) ) )
    {
        Fatal( "get_globalScope" );
    }
    ```

5. 사용 된 `IDiaEnum*` 디버그 정보를 열거 하 고 기호 또는 기타 요소를 검색할 인터페이스입니다.

    ```C++
    CComPtr<IDiaEnumTables> pTables;
    if ( FAILED( psession->getEnumTables( &pTables ) ) )
    {
        Fatal( "getEnumTables" );
    }
    CComPtr< IDiaTable > pTable;
    while ( SUCCEEDED( hr = pTables->Next( 1, &pTable, &celt ) ) && celt == 1 )
    {
        // Do something with each IDiaTable.
    }
    ```

## <a name="see-also"></a>참고 항목
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
