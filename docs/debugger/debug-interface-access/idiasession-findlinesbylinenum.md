---
title: IDiaSession::findLinesByLinenum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findLinesByLinenum method
ms.assetid: 76d5622d-9a91-4c2a-a98f-263af5d1daef
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9d5999febf6e926ef8e9beb365728a3b150e1a38
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62839269"
---
# <a name="idiasessionfindlinesbylinenum"></a>IDiaSession::findLinesByLinenum
컴파일 대상에 있는 소스 파일에서 지정 된 줄 번호 또는 근처의 줄 번호를 확인 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT findLinesByLinenum ( 
    IDiaSymbol*           compiland,
    IDiaSourceFile*       file,
    DWORD                 linenum,
    DWORD                 column,
    IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>매개 변수
`compiland`

[in] [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 컴파일 대상 줄 번호에 대 한 검색을 나타내는 개체입니다. 이 매개 변수 수 없습니다 `NULL`합니다.

`file`

[in] [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) 소스 파일에서 검색을 나타내는 개체입니다. 이 매개 변수 수 없습니다 `NULL`합니다.

`linenum`

[in] 1부터 시작 줄 번호를 지정합니다.

> [!NOTE]
> 모든 선을 지정 하려면 0을 사용할 수 없습니다 (사용 된 [idiasession:: Findlines](../../debugger/debug-interface-access/idiasession-findlines.md) 모든 줄 찾기 방법).

`column`

[in] 열 번호를 지정합니다. 모든 열을 지정 하려면 0을 사용 합니다. 열이 줄에 대 한 바이트 오프셋입니다.

`ppResult`

[out] 반환 된 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) objta 줄 번호의 목록을 포함 하는 검색 합니다.

## <a name="return-value"></a>반환 값
성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="example"></a>예제
다음 예제에서는 소스 파일을 열고이 파일에 제공한 컴파일 대상 열거, 각 컴파일 대상 시작 되는 소스 파일의 줄 번호를 찾으려면 하는 방법을 보여 줍니다.

```C++
void ShowLinesInCompilands(IDiaSession *pSession, LPCOLESTR filename)
{
    IDiaEnumSourceFiles* pEnum;
    IDiaSourceFile*      pFile;
    DWORD                celt;

    pSession->findFile ( NULL, filename, nsFNameExt, &pEnum );
    while ( pEnum->Next ( 1, &pFile, &celt ) == S_OK ) // for each file
    {
        IDiaEnumSymbols* pEnumCompilands;
        IDiaSymbol* pCompiland;

        pFile->get_compilands ( &pEnumCompilands );
        // for each compiland
        while ( pEnumCompilands->Next ( 1, &pCompiland, &celt ) == S_OK )
        {
            IDiaEnumLineNumbers* pEnum;
            // Find first compiland closest to line 1 of the file.
            if (pSession->findLinesByLinenum( pCompiland, pFile, 1, 0, &pEnum ) == S_OK)
            {
                IDiaLineNumber *pLineNumber;
                DWORD lineCount;
                while ( pEnum->Next(1,&pLineNumber,&lineCount) == S_OK)
                {
                    DWORD lineNum;
                    if (pLineNumber->get_line(&lineNum) == S_OK)
                    {
                        printf("compiland starts in source at line number = %lu\n",lineNum);
                    }
                }
            }
        }
    }
}
```

## <a name="see-also"></a>참고 항목
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSession::findLinesByAddr](../../debugger/debug-interface-access/idiasession-findlinesbyaddr.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
