---
title: POPDIRLISTFUNC | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- POPLISTFUNC
helpviewer_keywords:
- POPDIRLISTFUNC callback function
ms.assetid: 0ee90fd2-5467-4154-ab4c-7eb02ac3a14c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0fef3ab783c736fd2573e8d9df1a513e25d37020
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66326128"
---
# <a name="popdirlistfunc"></a>POPDIRLISTFUNC
이에 지정 된 콜백 함수는 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) 디렉터리 및 (선택 사항)는 소스 제어 중인 파일 이름 컬렉션을 업데이트 하는 함수입니다.

 `POPDIRLISTFUNC` 콜백 해당 디렉터리 및 파일 이름에 대해서만 호출 해야 (에 지정 된 목록에는 `SccPopulateDirList` 함수) 소스 제어에서 실제로 합니다.

## <a name="signature"></a>서명

```cpp
typedef BOOL (*POPDIRLISTFUNC)(
   LPVOID pvCallerData,
   BOOL bFolder,
   LPCSTR lpDirectoryOrFileName
);
```

## <a name="parameters"></a>매개 변수
 pvCallerData

[in] 에 제공 된 사용자 값 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)합니다.

 bFolder

[in] `TRUE` 경우에서 이름을 `lpDirectoryOrFileName` ; 디렉터리가 파일 이름을 이름은 그렇지 않은 경우.

 lpDirectoryOrFileName

[in] 소스 코드 제어에서 관리 되는 디렉터리 또는 파일 이름에 전체 로컬 경로입니다.

## <a name="return-value"></a>반환 값
 IDE에는 적절 한 오류 코드를 반환합니다.

|값|설명|
|-----------|-----------------|
|SCC_OK|계속 처리 합니다.|
|SCC_I_OPERATIONCANCELED|처리를 중지 합니다.|
|SCC_E_xxx|적절 한 원본 제어 오류 처리를 중지 해야 합니다.|

## <a name="remarks"></a>설명
 경우는 `fOptions` 의 매개 변수를 `SccPopulateDirList` 함수에 포함 되어는 `SCC_PDL_INCLUDEFILES` 플래그, 디렉터리 이름 뿐만 아니라 파일 이름에 가능한 목록 포함 됩니다.

## <a name="see-also"></a>참고자료
- [IDE에 의해 구현 된 콜백 함수](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)
- [오류 코드](../extensibility/error-codes.md)