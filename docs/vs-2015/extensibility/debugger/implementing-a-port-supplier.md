---
title: 포트 공급자 구현 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], implementing port suppliers
- port suppliers, implementing
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ffa6daa20c08bd236657c88e762b2f453554cb74
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68152681"
---
# <a name="implementing-a-port-supplier"></a>포트 공급자 구현
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

포트 공급자 세션 디버그 관리자 (SDM)에 대 한 요청 포트를 제공합니다. 포트 공급자 때나 새 장치를 지원 해야 합니다. DCOM이 아닌 컴퓨터에 디버그할 때 구현 해야 합니다. 예를 들어 휴대 전화에 디버깅을 제공 하려면 (아마도 통해 IR 또는 셀 연결) 들의 휴대 전화에 연결 및 프로세스와 휴대폰에서 실행 중인 프로그램을 열거 하는 포트를 제공 하는 포트 공급자를 구현할 수 있습니다.  
  
 (원격 디버깅 포함)는 Windows 기반 컴퓨터에서 디버깅 프로그램에 대 한 Visual Studio는 이러한 경우 고유한 포트 공급자 구현 하지 않아도 되므로 네이티브 및 공용 언어 런타임 (CLR) 프로세스에 대 한 포트 공급자를 제공 합니다.  
  
## <a name="in-this-section"></a>섹션 내용  
 [포트 공급자 구현 및 등록](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md)  
 SDM 포트 공급자 및 해당 포트와 상호 작용 하는 방법에 대해 설명 합니다.  
  
 [필요한 포트 공급자 인터페이스](../../extensibility/debugger/required-port-supplier-interfaces.md)  
 포트 공급자를 가져오려면 구현 해야 하는 인터페이스를 설명 합니다.  
  
## <a name="related-sections"></a>관련 단원  
 [디버거 개념](../../extensibility/debugger/debugger-concepts.md)  
 기본 디버깅 아키텍처 개념을 설명합니다.  
  
## <a name="see-also"></a>참고 항목  
 [Visual Studio 디버거 확장성](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
