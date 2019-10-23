---
title: 관리 되는 개체의 사용자 지정 뷰 만들기 | Microsoft Docs
ms.date: 01/08/2019
ms.topic: conceptual
f1_keywords:
- vs.debug.data.elements
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- data types, custom
- custom data types
- managed code, custom data types
- autoexp.dat file
- mcee_cs.dat file
- debugger, expanding data types
- mcee_mc.dat file
ms.assetid: 9969e9b2-9008-4729-8a14-0d6deaa61576
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 196ba13b95245b8c42e6d946572665792f71346d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745633"
---
# <a name="create-custom-views-of-managed-objects-c-visual-basic-f-ccli"></a>관리 되는 개체의 사용자 지정C#뷰 만들기 ( F#, C++Visual Basic,,/cli)
Visual Studio에서 디버거 변수 창에 데이터 형식이 표시되는 방식을 사용자 지정할 수 있습니다.

## <a name="attributes"></a>특성

에서 C#, F#, 및 C++ Visual Basic (C++/cli 코드만 해당) <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, <xref:System.Diagnostics.DebuggerDisplayAttribute> 및 <xref:System.Diagnostics.DebuggerBrowsableAttribute>을 사용 하 여 사용자 지정 데이터에 대 한 확장을 추가할 수 있습니다.

.NET Framework 2.0 코드에서 Visual Basic는 DebuggerBrowsable 특성을 지원 하지 않습니다. 최신 버전의 .NET에서는 이러한 제한 사항이 제거 되었습니다.

## <a name="visualizers"></a>시각화 도우미

시각화 도우미를 작성하여 관리되는 데이터 형식을 표시할 수 있습니다. 자세한 내용은 [방법: 시각화 도우미 작성](/visualstudio/debugger/create-custom-visualizers-of-data)을 참조 하세요.

> [!NOTE]
> 코드의 경우 [디버거에서 개체의 C++ 사용자 지정 뷰 만들기](/visualstudio/debugger/create-custom-views-of-native-objects)에 설명 된 대로 Natvis 프레임 워크를 사용 하 여 사용자 지정 데이터 형식 확장을 추가할 수 있습니다. C++

## <a name="see-also"></a>참조

- [DebuggerDisplay 특성을 사용 하 여 표시할 내용을 디버거에 알립니다.](../debugger/using-the-debuggerdisplay-attribute.md)
- [DebuggerTypeProxy 특성을 사용 하 여 표시할 형식을 디버거에 알립니다.](../debugger/using-debuggertypeproxy-attribute.md)
- [조사식 및 간략한 조사식 창](../debugger/watch-and-quickwatch-windows.md)
- [디버거 표시 특성을 사용하여 디버깅 향상](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)
