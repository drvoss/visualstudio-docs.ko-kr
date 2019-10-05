---
title: 패키지를 디버그 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], packages
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fb1af813fabb1245d85fe18629d77a45f6acca3f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66345901"
---
# <a name="debug-package"></a>패키지를 디버그 합니다.
디버그 패키지는 Visual Studio shell에서 실행 하 고 전체 UI를 처리 합니다. Visual Studio 디버깅 인터페이스를 사용 하 고 세션 디버그 관리자 SDM ()를 사용 하 여 통신 합니다.

 SDM을 통해 전송 되는 중단 이벤트 실행된 모드에서 디버거가 중단 모드 체인이 끊어진 프로그램에 포커스를 전환 합니다. 디버그 패키지가 이벤트에 의해 전송 되는 정보에서 스택 프레임 및 스레드를 추적 합니다.

 디버그 패키지에 언어 또는 런타임 환경 종속성 없습니다. 구현 하거나 디버그 패키지를 수정할 필요는 없습니다.

 디버그 패키지에 의해 구현 됩니다 *vsdebug.dll*합니다.

## <a name="see-also"></a>참고자료
- [세션 디버그 관리자](../../extensibility/debugger/session-debug-manager.md)
- [스택 프레임](../../extensibility/debugger/stack-frames.md)
- [스레드](../../extensibility/debugger/threads.md)
- [디버거 구성 요소](../../extensibility/debugger/debugger-components.md)