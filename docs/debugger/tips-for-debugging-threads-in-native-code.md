---
title: 네이티브 코드의 스레드 디버깅 팁 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- debugging [Visual Studio], threads
ms.assetid: 0374c8c6-57a3-4cfe-8047-2effef5ff5dc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 8ee1f1f2f2029325e3d3b87ca44d05d800a62c07
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62901877"
---
# <a name="tips-for-debugging-threads-in-native-code"></a>네이티브 코드의 스레드 디버깅 팁
다음은 네이티브 코드에서 스레드를 디버깅할 때 사용할 수 있는 몇 가지 팁입니다.

- **조사식** 창이나 **간략한 조사식** 대화 상자에 `@TIB`를 입력하면 스레드 정보 블록의 내용이 표시됩니다.

- **조사식** 창이나 **간략한 조사식** 대화 상자에 `@Err`을 입력하면 현재 스레드의 마지막 오류 코드가 표시됩니다.

- CRT(C Run-Time Libraries) 함수는 다중 스레드 애플리케이션을 디버깅하는 데 유용합니다. 자세한 내용은 [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg)를 참조하세요.

## <a name="see-also"></a>참고 항목
- [다중 스레드 애플리케이션 디버그](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [네이티브 코드 디버그](../debugger/debugging-native-code.md)