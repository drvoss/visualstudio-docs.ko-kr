---
title: GetAutoInsertExtensions 메서드
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fb767ec7301a1d4e0f29003971b017339228fc9f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62972280"
---
# <a name="getautoinsertextensions-method"></a>GetAutoInsertExtensions 메서드
  디버깅 하는 동안 자동으로 삽입 하는 Office 용 앱에 대 한 정보를 가져옵니다.

 @FSHO2@이 메서드는 나중에 사용할 수 있도록 예약되어 있습니다.

## <a name="syntax"></a>구문

```csharp
HRESULT GetAutoInsertExtensions(
    [out, retval] SAFEARRAY(BSTR)* psaExtensionNames
);
```

### <a name="parameters"></a>매개 변수

|매개 변수|설명|
|---------------|-----------------|
|*psaExtensionNames*|Office 용 앱의 확장 이름입니다.|

## <a name="return-value"></a>반환 값
 메서드가 성공적으로 완료되었는지 여부를 나타내는 HRESULT 값입니다.

## <a name="remarks"></a>설명
 삽입할 Office에 대 한 각 앱 아래에 있는 값에 해당 하는 Office 응용 프로그램 확장 이름으로 반환 됩니다 **HKEY_CURRENT_USER\Software\Microsoft\Office\WEF\Developer**합니다. 호스트는 레지스트리에 이러한 값을 조회 하 고 확장을 자동으로 삽입 해야 합니다.
