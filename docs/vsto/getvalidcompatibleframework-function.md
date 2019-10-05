---
title: GetValidCompatibleFramework 함수
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
ms.openlocfilehash: b975a4b4b2c1b4ae3f6ef0f1d6d23769bb4c77c7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62788698"
---
# <a name="getvalidcompatibleframework-function"></a>GetValidCompatibleFramework 함수
  이 API는 Office 인프라를 지원 하며 코드에서 직접 사용할 수 없습니다.

## <a name="syntax"></a>구문

```csharp
HRESULT WINAPI GetValidCompatibleFramework(
    LPCWSTR lpwszCompatibleFrameworksXML,
    BSTR* pbstrValidFrameworkTag
);
```

### <a name="parameters"></a>매개 변수

|매개 변수|설명|
|---------------|-----------------|
|*lpwszCompatibleFrameworksXML*|사용 하지 마세요.|
|*pbstrValidFrameworkTag*|사용 하지 마세요.|

## <a name="return-value"></a>반환 값
 함수가 성공 하는 경우 반환 **S_OK**합니다. 함수가 실패할 경우 오류 코드를 반환 합니다.
