---
title: '방법: 레거시 언어 서비스의 개요 표시 지원 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], collapse to definitions command
- language services, supporting Collapse to Definitions command
- hidden text, Collapse to Definitions command
ms.assetid: bb6e74c3-93e4-4ef7-afc7-1c9b342f083b
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d92baa824dbb70dd591cadef99775f943c651aef
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436152"
---
# <a name="how-to-support-outlining-in-a-legacy-language-service"></a>방법: 레거시 언어 서비스의 개요 표시 지원
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

개요 확장 또는 축소 텍스트의 서로 다른 지역에 사용 됩니다. 사용 되는 방식으로 개요 다른 언어에서 다르게 정의할 수 있습니다. 자세한 내용은 [개요](../../ide/outlining.md)를 참조하세요.  
  
 레거시 언어 서비스는 VSPackage의 일부로 구현 됩니다 있지만 MEF 확장을 사용 하는 언어 서비스 기능을 구현 하는 최신 방법입니다. 개요를 구현 하는 새로운 방법에 대 한 자세한 참조 [연습: 개요](../../extensibility/walkthrough-outlining.md)를 참조하세요.  
  
> [!NOTE]
> 편집기를 사용 하 여 새 API 최대한 빨리 시작 하는 것이 좋습니다. 언어 서비스의 성능이 향상 되 고 새 편집기 기능을 활용할 수 있습니다.  
  
 다음이 명령 언어 서비스에 대 한 지원 방법에 설명 합니다.  
  
### <a name="to-support-outlining"></a>개요 표시 지원 하려면  
  
1. 구현 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage> 언어 서비스 개체입니다.  
  
2. 호출 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> 새 개요 영역을 추가 하려면 현재 개요 세션 개체에 있습니다.  
  
## <a name="robust-programming"></a>강력한 프로그래밍  
 사용자가 선택 하면 **정의로 축소** 에 **개요** 메뉴, IDE 호출 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage.CollapseToDefinitions%2A> 언어 서비스에서.  
  
 IDE에서 전달이 메서드를 호출 하는 경우는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> 포인터 (텍스트 버퍼에 대 한 포인터) 및 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession> (현재 개요 세션에 포인터).  
  
 호출할 수 있습니다는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> 의 이러한 영역을 지정 하 여 여러 개의 개요 영역에 대 한 메서드는 `rgOutlnReg` 매개 변수입니다. 합니다 `rgOutlnReg` 매개 변수는 한 <xref:Microsoft.VisualStudio.TextManager.Interop.NewOutlineRegion> 구조입니다. 이 프로세스에는 숨겨진된 영역, 특정 지역을 확장 하거나 축소 하는 여부 등의 다른 특성을 지정할 수 있습니다.  
  
> [!NOTE]
> 줄 바꿈 문자를 숨기는 방법에 대 한 주의 해야 합니다. 숨겨진된 텍스트 확장 해야 첫 번째 줄의 시작 부분에서 마지막 마지막 줄 바꿈 문자에 표시 된 채로 섹션에서 마지막 줄의 문자입니다.  
  
## <a name="see-also"></a>참고 항목  
 [방법: 레거시 언어 서비스의 숨겨진된 텍스트 지원 제공](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)   
 [방법: 레거시 언어 서비스에서 확장 개요 표시 지원 제공](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)
