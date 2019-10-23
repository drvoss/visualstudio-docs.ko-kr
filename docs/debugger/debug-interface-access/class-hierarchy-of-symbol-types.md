---
title: 기호 형식의 클래스 계층 구조 Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK], class hierarchies
ms.assetid: 0ccd6990-4654-44cd-a6f3-bdd82fe90f6c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3c42ea4bb2d5c2ad91538bec8b31774a5a41aa4d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745451"
---
# <a name="class-hierarchy-of-symbol-types"></a>기호 형식의 클래스 계층 구조
다음 표에서는 클래스 계층 구조의 기호 형식에 대해 설명 합니다.

## <a name="symbol-types"></a>기호 형식

|기호 형식|설명|
|-----------------|-----------------|
|[UDT](../../debugger/debug-interface-access/udt.md)|각 클래스, 구조체 및 공용 구조체를 나타내는 데 사용 되는 기호입니다.|
|[열거형(디버그 인터페이스 액세스 SDK)](../../debugger/debug-interface-access/enum-debug-interface-access-sdk.md)|열거 형식에 대 한 기호입니다.|
|[PointerType](../../debugger/debug-interface-access/pointertype.md)|포인터 형식의 기호입니다.|
|[ArrayType](../../debugger/debug-interface-access/arraytype.md)|배열 형식에 대 한 기호입니다.|
|[BaseType](../../debugger/debug-interface-access/basetype.md)|기본 형식에 대 한 기호|
|[Typedef(디버그 인터페이스 액세스 SDK)](../../debugger/debug-interface-access/typedef-debug-interface-access-sdk.md)|다른 형식의 이름을 도입 하는 기호입니다.|
|[BaseClass](../../debugger/debug-interface-access/baseclass.md)|UDT (사용자 정의 형식)의 각 기본 클래스에 사용 되는 기호입니다.|
|[Friend(디버그 인터페이스 액세스 SDK)](../../debugger/debug-interface-access/friend-debug-interface-access-sdk.md)|Friend 클래스 및 friend 함수에 대 한 기호입니다.|
|[FunctionType](../../debugger/debug-interface-access/functiontype.md)|각 고유 함수 시그니처의 기호입니다.|
|[FunctionArgType](../../debugger/debug-interface-access/functionargtype.md)|함수의 각 매개 변수에 대 한 기호입니다.|
|[VTableShape](../../debugger/debug-interface-access/vtableshape.md)|가상 테이블 크기에 대 한 기호입니다.|
|[VTable](../../debugger/debug-interface-access/vtable.md)|가상 테이블에 대 한 기호입니다.|
|[CustomType](../../debugger/debug-interface-access/customtype.md)|공급 업체 정의 형식에 대 한 기호입니다.|
|[ManagedType](../../debugger/debug-interface-access/managedtype.md)|메타 데이터에 정의 된 형식에 대 한 기호입니다.|
|[크기](../../debugger/debug-interface-access/dimension.md)|배열 차원에 대 한 기호입니다.|

> [!NOTE]
> 각 기호에는 기호에 대 한 정보 및 다른 기호에 대 한 참조를 포함 하는 속성이 있을 수 있습니다. 이러한 속성은 개별 기호 항목에 나열 됩니다.

## <a name="see-also"></a>참조
- [CV_access_e 열거형](../../debugger/debug-interface-access/cv-access-e.md)
- [기호 형식의 어휘 계층 구조](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
- [기호 및 기호 태그](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)