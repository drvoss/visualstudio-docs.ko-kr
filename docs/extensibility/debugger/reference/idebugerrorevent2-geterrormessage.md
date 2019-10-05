---
title: IDebugErrorEvent2::GetErrorMessage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugErrorEvent2::GetErrorMessage
helpviewer_keywords:
- IDebugErrorEvent2::GetErrorMessage
ms.assetid: 9e3b0d74-a2dd-4eaa-bd95-21b2f9c79409
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 049f7a78a414df8202d64c1f25eaba854818c88d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66327722"
---
# <a name="idebugerrorevent2geterrormessage"></a>IDebugErrorEvent2::GetErrorMessage
사람이 읽을 수 있는 오류 메시지의 생성을 허용 하는 정보를 반환 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetErrorMessage(
   MESSAGETYPE* pMessageType,
   BSTR*        pbstrErrorFormat,
   HRESULT*     hrErrorReason,
   DWORD*       pdwType,
   BSTR*        pbstrHelpFileName,
   DWORD*       pdwHelpId
);
```

```csharp
int GetErrorMessage(
   out enum_MESSAGETYPE   pMessageType,
   out string             pbstrErrorFormat,
   out int                phrErrorReason,
   out uint               pdwType,
   out string             pbstrHelpFileName,
   out uint               pdwHelpId
);
```

## <a name="parameters"></a>매개 변수
`pMessageType`\
[out] 값을 반환 합니다 [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md) 메시지의 형식을 설명 하는 열거형입니다.

`pbstrErrorFormat`\
[out] 사용자에 게 최종 메시지의 형식 ("설명" 세부 정보에 대 한 참조).

`hrErrorReason`\
[out] 오류 코드는 메시지에 대 한 경우

`pdwType`\
[out] 오류의 심각도입니다 (의 MB_XXX 상수를 사용 하 여 `MessageBox`; 예를 들어 `MB_EXCLAMATION` 또는 `MB_WARNING`).

`pbstrHelpFileName`\
[out] 도움말 파일 (도움말 파일이 없는 경우 null 값으로 설정) 경로입니다.

`pdwHelpId`\
[out] (도움말 항목이 없는 경우 0으로 설정 됨)를 표시할 도움말 항목의 ID입니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 오류 메시지의 서식을 지정할 `"What I was doing.  %1"`합니다. 합니다 `"%1"` 는 다음 오류 코드에서 파생 된 오류 메시지를 사용 하 여 호출자에 의해 대체 됩니다 (반환 되는 `hrErrorReason`). `pMessageType` 매개 변수는 마지막 오류 메시지를 표시 하는 방법을 호출자에 게 지시 합니다.

## <a name="see-also"></a>참고자료
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
- [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)