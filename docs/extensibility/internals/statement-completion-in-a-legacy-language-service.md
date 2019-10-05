---
title: 레거시 언어 서비스에서 문 완성 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- statement completion
- language services, statement completion
ms.assetid: 617439dc-3f0e-4e5f-b346-3e4e7fcf3c1b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5c6e157505b146b9c1ca37f508311c9e80958be6
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322445"
---
# <a name="statement-completion-in-a-legacy-language-service"></a>레거시 언어 서비스의 명령문 완성
문 완성 하는 언어 서비스는 언어 키워드 또는 핵심 편집기에 입력 시작 하는 요소를 완료 하는 사용자를 사용 하면 프로세스. 이 항목에는 문 완성 작동 원리 및 언어 서비스에서 구현 하는 방법을 설명 합니다.

 레거시 언어 서비스는 VSPackage의 일부로 구현 됩니다 있지만 MEF 확장을 사용 하는 언어 서비스 기능을 구현 하는 최신 방법입니다. 문 완성 기능을 구현 하는 새로운 방법에 대 한 자세한 참조 [연습: 문 완성 표시](../../extensibility/walkthrough-displaying-statement-completion.md)합니다.

> [!NOTE]
> 편집기를 사용 하 여 새 API 최대한 빨리 시작 하는 것이 좋습니다. 언어 서비스의 성능이 향상 되 고 새 편집기 기능을 활용할 수 있습니다.

## <a name="implementing-statement-completion"></a>문 완성 구현
 문 완성 코어 편집기에서 대화형으로 사용 하면 더 쉽게 하 고 신속 하 게 코드를 작성 하는 특별 한 UI를 활성화 합니다. 문 완성 표시 하 여 관련 개체 또는 클래스는 필요할 때 특정 요소를 기억할 필요가 도움말 참조 항목에서 조회 하거나이 방지 하는 기능입니다.

 문 완성 기능을 구현 하려면 언어 문을 완료 트리거를 구문 분석할 수 있어야 합니다. 예를 들어 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 점 (.) 연산자를 사용 하는 동안 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 화살표를 사용 하 여 (->) 연산자. 언어 서비스를 둘 이상의 트리거를 사용 하 여 문 완성을 시작할 수 있습니다. 이러한 트리거 명령 필터에서 프로그래밍 됩니다.

## <a name="command-filters-and-triggers"></a>명령 필터 및 트리거
 명령을 필터 일치를 트리거 또는 트리거를 가로챕니다. 명령 필터에 뷰를 추가 하려면 구현 합니다 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 인터페이스를 호출 하 여 보기에 연결 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> 메서드. 동일한 명령 필터를 사용할 수 있습니다 (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>) 문 완성, 오류 표식 및 메서드 팁 같은 언어 서비스의 모든 측면에 대 한 합니다. 자세한 내용은 [레거시 언어 서비스 명령 가로채기](../../extensibility/internals/intercepting-legacy-language-service-commands.md)합니다.

 트리거를 편집기에 입력 되는 경우-텍스트 버퍼 특히-언어 서비스가 다음 호출을 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> 메서드. 이렇게 하면 편집기에는에서 문 완성 후보 사용자가 선택할 수 있도록 UI를 표시 합니다. 이 메서드를 구현 해야 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> 하며 <xref:Microsoft.VisualStudio.TextManager.Interop.UpdateCompletionFlags> 매개 변수로 플래그입니다. 완성 항목 목록을 스크롤 목록 상자에 나타납니다. 사용자가 입력을 계속, 목록 상자에서 선택한 가장 가까운 최신 자로 입력을 반영 하도록 업데이트 됩니다. 핵심 편집기의 문 완성, UI를 구현 하지만 언어 서비스를 구현 해야 합니다는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> 문에 대 한 후보 완성 항목의 집합을 정의 하는 인터페이스입니다.

## <a name="see-also"></a>참고 항목
- [레거시 언어 서비스 명령 가로채기](../../extensibility/internals/intercepting-legacy-language-service-commands.md)