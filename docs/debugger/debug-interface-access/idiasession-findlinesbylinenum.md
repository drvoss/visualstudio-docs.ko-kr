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
ms.openlocfilehash: f5d64e9484b9450f5211e271df3b154ebab0fa75
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742098"
---
# <a name="idiasessionfindlinesbylinenum"></a>IDiaSession::findLinesByLinenum
소스 파일의 지정 된 줄 번호가 또는 거의 compiland 줄 번호를 결정 합니다.

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

진행 줄 번호를 검색할 compiland를 나타내는 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 개체입니다. 이 매개 변수를 `NULL` 수 없습니다.

`file`

진행 검색할 소스 파일을 나타내는 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) 개체입니다. 이 매개 변수를 `NULL` 수 없습니다.

`linenum`

진행 1부터 줄 번호를 지정 합니다.

> [!NOTE]
> 모든 줄을 지정 하는 데 0을 사용할 수 없습니다. [IDiaSession:: findlines](../../debugger/debug-interface-access/idiasession-findlines.md) 메서드를 사용 하 여 모든 줄을 찾습니다.

`column`

진행 열 번호를 지정 합니다. 모든 열을 지정 하려면 0을 사용 합니다. 열은 선으로의 바이트 오프셋입니다.

`ppResult`

제한이 검색 된 줄 번호의 목록이 포함 된 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) objta를 반환 합니다.

## <a name="return-value"></a>반환 값
성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="example"></a>예제
다음 예제에서는 소스 파일을 열고,이 파일에서 제공 하는 compilands을 열거 하 고, 각 compiland 시작 되는 소스 파일에서 줄 번호를 찾는 방법을 보여 줍니다.

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

## <a name="see-also"></a>참조
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSession::findLinesByAddr](../../debugger/debug-interface-access/idiasession-findlinesbyaddr.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
