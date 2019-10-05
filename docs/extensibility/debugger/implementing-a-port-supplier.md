---
title: 포트 공급자 구현 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], implementing port suppliers
- port suppliers, implementing
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dd5ba2a96b94cce65dc901a523232b1c3e0a45b9
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66349980"
---
# <a name="implement-a-port-supplier"></a>포트 공급자 구현
포트 공급자 세션 디버그 관리자 (SDM)에 대 한 요청 포트를 제공합니다. 포트 공급자를 비 DCOM 컴퓨터 또는 새 장치를 지원 해야 하는 경우에 디버그할 때 구현 되어야 합니다. 예를 들어 휴대 전화에 디버깅을 제공 하려면 (아마도 통해 IR 또는 셀 연결) 들의 휴대 전화에 연결 및 프로세스와 휴대폰에서 실행 중인 프로그램을 열거 하는 포트를 제공 하는 포트 공급자를 설정할 수 있습니다.

 (원격 디버깅 포함)는 Windows 기반 컴퓨터에서 디버깅 프로그램에 대 한 Visual Studio는 이러한 경우 고유한 포트 공급자를 설정 하지 않아도 되므로 네이티브 및 공용 언어 런타임 (CLR) 프로세스에 대 한 포트 공급자를 제공 합니다.

## <a name="in-this-section"></a>단원 내용
 [구현 하 고 포트 공급자 등록](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md) SDM 포트 공급자 및 해당 포트와 상호 작용 하는 방법에 대해 설명 합니다.

 [필요한 포트 공급자 인터페이스](../../extensibility/debugger/required-port-supplier-interfaces.md) 포트 공급자를 가져오기 위해 구현 해야 하는 인터페이스에 설명 합니다.

## <a name="related-sections"></a>관련 단원
 [디버거 개념](../../extensibility/debugger/debugger-concepts.md) 디버깅 주요 아키텍처 개념을 설명 합니다.

## <a name="see-also"></a>참고자료
 [Visual Studio 디버거 확장성](../../extensibility/debugger/visual-studio-debugger-extensibility.md)