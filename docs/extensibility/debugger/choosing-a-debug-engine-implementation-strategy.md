---
title: 디버그 엔진 구현 전략 선택 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementation strategies
ms.assetid: 90458fdd-2d34-4f10-82dc-6d8f31b66d8b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 930908b66b5d2234b8c62585b10ddf751c96f61c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66324502"
---
# <a name="choose-a-debug-engine-implementation-strategy"></a>디버그 엔진 구현 전략 선택
런타임 아키텍처를 사용 하 여 디버그 엔진 (DE) 구현 전략을 결정 합니다. 디버그 엔진 in-process 디버깅할 프로그램을 만들 수 있습니다. 디버그 엔진 in-process Visual Studio 세션 디버그 관리자 SDM ()를 만듭니다. 또는 디버그 엔진-out-of-process 둘 다에 만듭니다. 다음 지침은 이러한 세 가지 전략 중에서 선택 하는 데 도움이 됩니다.

## <a name="guidelines"></a>지침
 de-out-of-process를 할 수 있지만 SDM와 디버깅 중인 프로그램에 일반적으로 이유는 없습니다 이렇게 하려면. 프로세스 경계를 넘어 호출 속도가 비교적 느립니다.

 디버그 엔진은 공용 언어 런타임 환경 및 Win32 기본 런타임 환경에 대 한 이미 제공 됩니다. 환경 중 하나에 대 한 장치를 교체 해야 할 경우 SDM을 사용 하 여는 DE-프로세스를 만들어야 합니다.

 이 고, 그렇지 DE in-process SDM 만들거나 수 또는 디버그 중인 프로그램에는 프로세스에서. 식 계산기는 DE의 프로그램 기호 저장소에 자주 액세스 해야 하는 경우 고려해 야 할 해야 합니다. 아니면, 기호 저장소 빠른 액세스를 위해 메모리에 로드할 수 있습니다. 또한 다음 방법 중 하나를 고려 합니다.

- 식 계산기 및 기호 저장소 간의 호출 수 없는 경우, SDM 메모리 공간에 기호 저장소를 읽을 수 있으면 DE in-process SDM 만듭니다. 프로그램에 연결할 때 SDM을 디버그 엔진의 CLSID를 반환 해야 합니다. SDM이이 CLSID를 사용 하 여는 DE의 in process 인스턴스를 만듭니다.

- DE 기호 저장소에 액세스 하는 프로그램을 호출 해야 프로그램과 DE-프로세스를 만듭니다. 이 경우 프로그램은 DE의 인스턴스를 만듭니다.

## <a name="see-also"></a>참고자료
- [Visual Studio 디버거 확장성](../../extensibility/debugger/visual-studio-debugger-extensibility.md)