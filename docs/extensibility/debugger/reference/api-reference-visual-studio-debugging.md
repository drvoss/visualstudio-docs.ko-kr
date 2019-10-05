---
title: API 참조 (Visual Studio 디버깅) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], API reference
ms.assetid: e4e429da-3667-41f7-9158-a8207d13e91a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7f880596854eb376d386bc6a96d789c54767f39d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351856"
---
# <a name="api-reference-visual-studio-debugging"></a>API 참조(Visual Studio 디버깅)
참조 섹션 구문 및 모든 API 요소에 대 한 사용법을 보여 주는 가이드 API에 대 한 개념적인 개요 및 다양 한 코드 예제를 포함 합니다. 모든 참조는 범주별으로 사전순으로 나열 됩니다.

 다음 표에서 일반적인 `HRESULT` 메서드에서 반환 되는 값입니다.

|이름|설명|값|
|----------|-----------------|-----------|
|S_OK|명령 실행 성공|0x00000000|
|E_UNEXPECTED|예기치 않은 오류가 발생 했습니다.|0x8000FFFF|
|E_NOTIMPL|구현되지 않았습니다.|0x80004001|
|E_OUTOFMEMORY|작업을 완료 하는 메모리가 부족 합니다.|0x8007000E|
|E_INVALIDARG|하나 이상의 인수가 잘못 되었습니다.|0x80070057|
|E_NOINTERFACE|없는 해당 인터페이스를 지원 합니다.|0x80004002|
|E_POINTER|잘못 된 포인터입니다.|0x80004003|
|E_HANDLE|잘못 된 핸들입니다.|0x80070006|
|E_ABORT|작업이 중단 되었습니다.|0x80004004|
|E_FAIL|예기치 않은 오류가 발생 했습니다.|0x80004005|
|E_ACCESSDENIED|일반 액세스 거부 오류가 발생 합니다.|0x80070005|

> [!NOTE]
> 경우는 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 반환 메서드를 디버깅 `S_OK`를 매개 변수에 대 한 포인터는 유효한 모든, 즉, 유효성을 검사 하지 out 매개 변수가 포인터에서 수행 되는 가정 때 `S_OK` 반환 됩니다.
>
> [!NOTE]
> 잘못 된 또는 `NULL` [out] 매개 변수 IDE에서 충돌이 발생할 수 있습니다.

## <a name="see-also"></a>참고자료
- [인터페이스](../../../extensibility/debugger/reference/interfaces-visual-studio-debugging.md)
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [클래스 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)
- [디버깅을 위한 SDK 도우미](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [Visual Studio 디버거 확장성](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)