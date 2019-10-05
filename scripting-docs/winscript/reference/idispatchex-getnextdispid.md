---
title: IDispatchEx::GetNextDispID | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.GetNextDispID
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetNextDispID method
ms.assetid: 8263d441-85ee-47f4-bdba-fbf2ad07e85f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4d964a8744f1f0a28704dd0a1d5e0fd2e67aab1c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62997337"
---
# <a name="idispatchexgetnextdispid"></a>IDispatchEx::GetNextDispID

개체의 멤버를 열거합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetNextDispID(
   DWORD grfdex,
   DISPID id,
   DISPID *pid
);
```

## <a name="parameters"></a>매개 변수

`grfdex`\
열거할 항목의 집합 결정 합니다. 다음 값의 조합 수 있습니다.

|값|의미|
|-----------|-------------|
|fdexEnumDefault|요청 개체는 기본 요소를 열거 합니다. 개체 요소 집합을 열거할 수 있습니다.|
|fdexEnumAll|개체의 모든 요소를 열거 하는 요청입니다. 개체 요소 집합을 열거할 수 있습니다.|

`id`\
현재 멤버를 식별합니다. GetNextDispID이 열거형의 항목을 검색합니다. 이 식별자를 가져오려면 GetDispID 또는 GetNextDispID에 대 한 이전 호출을 사용 합니다. 첫 번째 항목의 첫 번째 식별자를 가져오는 DISPID_STARTENUM 값을 사용 합니다.

`pid`\
열거형의 다음 항목의 식별자를 수신 하는 DISPID 변수의 주소입니다.

멤버에서 삭제 되 면 `DeleteMemberByName` 또는 `DeleteMemberByDispID`의 `DISPID` 에 대 한 유효한 상태를 유지 해야 하는 경우 `GetNextDispID`합니다.

## <a name="return-value"></a>반환 값

다음 값 중 하나를 반환합니다.

|||
|-|-|
|`S_OK`|명령 실행 성공|
|`S_FALSE`|열거형이 수행 됩니다.|

## <a name="example"></a>예제

```cpp
   HRESULT hr;
   BSTR bstrName;
   DISPID dispid;
   IDispatchEx *pdex;

   // Assign to pdex
   hr = pdex->GetNextDispID(fdexEnumAll, DISPID_STARTENUM, &dispid);
   while (hr == NOERROR)
   {
      hr = pdex->GetMemberName(dispid, &bstrName);
      if (!wcscmp(bstrName, OLESTR("Bar")))
      {
         SysFreeString(bstrName);
         return TRUE;
      }
      SysFreeString(bstrName);
      hr = pdex->GetNextDispID(fdexEnumAll, dispid, &dispid);
   }
```

## <a name="see-also"></a>참고자료

- [IDispatchEx 인터페이스](../../winscript/reference/idispatchex-interface.md)
- [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)
- [IDispatchEx::DeleteMemberByName](../../winscript/reference/idispatchex-deletememberbyname.md)
- [IDispatchEx::DeleteMemberByDispID](../../winscript/reference/idispatchex-deletememberbydispid.md)