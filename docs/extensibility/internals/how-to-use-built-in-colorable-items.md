---
title: '방법: 기본 제공 색 항목 사용 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- colorable items
- language services, built-in colorable items
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ae1c327c14ed2b349ee02566c5cdfd38b9a07859
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66311960"
---
# <a name="how-to-use-built-in-colorable-items"></a>방법: 기본 제공 색 항목 사용
기본 제공 색 항목을 사용 하면 먼저 알려야 통합된 개발 환경 (IDE)이 경우에 고유한 사용자 지정 색 항목을 제공 하지 않는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> 개체입니다. 언어 서비스에 대 한 레지스트리 항목을 설정 하 여이 작업을 수행 합니다.

## <a name="to-use-built-in-colorable-items"></a>기본 제공 색 항목을 사용 하려면

1. 아래 **HKEY_LOCAL_MACHINE\VisualStudio\\< X.Y > \Languages\Language Services\\< 언어 이름을\>** 여기서 \<X.Y >의 버전이 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 및 \<언어 이름 > 이름인 언어를 이라는 DWORD 레지스트리 항목 값을 만들 **RequestStockColors**합니다.

2. 설정 된 **RequestStockColors** 레지스트리 항목 값을 *1*합니다.

    레지스트리 항목에 colorizer의를 만든 후 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> 메서드는 멤버를 사용할 수는 <xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS> 편집기 사용에 대 한 색 특성 배열을 작성 하는 열거형입니다.

   > [!NOTE]
   > 사용자 지정 색 항목을 제공 하는 경우에이 레지스트리 항목을 설정 하지 마십시오. 자세한 내용은 [사용자 지정 색 항목](../../extensibility/internals/custom-colorable-items.md)합니다.

## <a name="see-also"></a>참고자료
- [사용자 지정 편집기의 구문 색 지정](../../extensibility/syntax-coloring-in-custom-editors.md)
- [레거시 언어 서비스의 구문 색 지정](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [구문 색 지정 구현](../../extensibility/internals/implementing-syntax-coloring.md)
- [사용자 지정 색 항목](../../extensibility/internals/custom-colorable-items.md)
- [레거시 언어 서비스 등록](../../extensibility/internals/registering-a-legacy-language-service2.md)