---
title: '방법: 기본 제공 색 항목 사용 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- colorable items
- language services, built-in colorable items
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a86361f28eb4c73a65093fc5c80ef15ddf791a77
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436139"
---
# <a name="how-to-use-built-in-colorable-items"></a>방법: 기본 제공 색 항목 사용
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

기본 제공 색 항목을 사용 하면 먼저 알려야 통합된 개발 환경 (IDE)이 경우에 고유한 사용자 지정 색 항목을 제공 하지 않는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> 개체입니다. 언어 서비스에 대 한 레지스트리 항목을 설정 하 여이 작업을 수행 합니다.  
  
### <a name="to-use-built-in-colorable-items"></a>기본 제공 색 항목을 사용 하려면  
  
1. 아래 HKEY_LOCAL_MACHINE\VisualStudio\\*X.Y*\Languages\Language 서비스\\*언어 이름*여기서 *X.Y* 버전이[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 하 고 *언어 이름* 이름인 언어를 만들기 이라는 DWORD 레지스트리 항목 값을 `RequestStockColors`입니다.  
  
2. 설정 된 `RequestStockColors` 레지스트리 항목 값을 1로 합니다.  
  
     레지스트리 항목에 colorizer의를 만든 후 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> 메서드는 멤버를 사용할 수는 <xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS> 편집기 사용에 대 한 색 특성 배열을 작성 하는 열거형입니다.  
  
    > [!NOTE]
    > 사용자 지정 색 항목을 제공 하는 경우에이 레지스트리 항목을 설정 하지 마십시오. 자세한 내용은 [사용자 지정 색 항목](../../extensibility/internals/custom-colorable-items.md)합니다.  
  
## <a name="see-also"></a>참고 항목  
 [사용자 지정 편집기의 구문 색 지정](../../extensibility/syntax-coloring-in-custom-editors.md)   
 [레거시 언어 서비스의 구문 색 지정](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [구문 색 지정 구현](../../extensibility/internals/implementing-syntax-coloring.md)   
 [사용자 지정 색 항목](../../extensibility/internals/custom-colorable-items.md)   
 [레거시 언어 서비스 등록](../../extensibility/internals/registering-a-legacy-language-service2.md)
