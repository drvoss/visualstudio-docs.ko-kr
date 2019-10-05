---
title: 레거시 언어 서비스 인터페이스 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IVsLanguageInfo interface
- language services, objects
ms.assetid: 03b2d507-f463-417e-bc22-bdac68eeda52
caps.latest.revision: 25
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 02f63cd5e3f0599723aee12f7aed2c56b74c3249
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68196102"
---
# <a name="legacy-language-service-interfaces"></a>레거시 언어 서비스 인터페이스
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

모든 특정 프로그래밍 언어에 대해 한 번에 언어 서비스의 인스턴스가 하나만 수 있습니다. 그러나 단일 언어 서비스는 둘 이상의 편집기를 사용할 수 있습니다.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 특정 편집기와 언어 서비스를 연결 하지 않습니다. 따라서 언어 서비스 작업을 요청 하는 경우 적절 한 편집기를 매개 변수로 식별 해야 합니다.  
  
## <a name="common-interfaces-associated-with-language-services"></a>언어 서비스와 관련 된 일반적인 인터페이스  
 편집기를 호출 하 여 언어 서비스를 가져옵니다 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> 적절 한 VSPackage에서. ID (SID)이이 호출에서 전달 하는 서비스는 요청 된 언어 서비스를 식별 합니다.  
  
 임의 개수의 별도 클래스에서 핵심 언어 서비스 인터페이스를 구현할 수 있습니다. 그러나 일반적인 방법은 다음과 같습니다. 단일 클래스에 다음 인터페이스를 구현 합니다.  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageBlock> (선택 사항)  
  
  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> 모든 언어 서비스 인터페이스를 구현 해야 합니다. 것 colorizer를 검색 하는 언어 서비스와 연결 된 파일 이름 확장명을 언어의 지역화 된 이름과 같은 언어 서비스에 대 한 정보를 제공 합니다.  
  
## <a name="additional-language-service-interfaces"></a>추가 언어 서비스 인터페이스  
 언어 서비스를 사용 하 여 다른 인터페이스를 제공할 수 있습니다. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 텍스트 버퍼의 각 인스턴스에 대해 이러한 인터페이스의 개별 인스턴스를 요청합니다. 따라서 구현 해야 이러한 각 인터페이스의 자체 개체입니다. 다음 표에서 텍스트 버퍼 인스턴스 당 하나의 인스턴스를 필요로 하는 인터페이스를 보여 줍니다.  
  
|인터페이스|Description|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|코드 창의 기본 드롭다운 표시줄 등을 관리합니다. 사용 하 여이 인터페이스를 가져올 수 있습니다는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> 메서드. 하나의 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> 코드 창 마다.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>|언어 키워드와 구분 기호 색을 지정 합니다. 사용 하 여이 인터페이스를 가져올 수 있습니다는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> 메서드. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> 그리기 시간에 호출 됩니다. 내에서 계산 집약적인 작업을 피할 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> 또는 성능 저하 될 수 있습니다.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>|IntelliSense 매개 변수 도구 설명을 제공 합니다. 언어 서비스 인식 하면 해당 메서드 데이터를 표시 하는 문자가 여는 괄호와 같이 표시 호출을 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> 메서드 알림 텍스트를 확인 하는 언어 서비스는 매개 변수 정보 도구 설명을 표시할 준비가 합니다. 텍스트 뷰 다시 호출 하 여 언어 서비스의 메서드를 사용 하는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> 를 도구 설명 표시 하는 데 필요한 정보를 가져오는 인터페이스입니다.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>|IntelliSense 문 완성을 제공합니다. 언어 서비스가 완성 목록을 표시 하려면 준비 되 면 호출 하는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> 텍스트 뷰의 메서드. 텍스트 뷰 다시 호출 하 여 언어 서비스에서 메서드를 사용 하 여 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> 개체.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>|명령 처리기를 사용 하 여 텍스트 뷰를 수정할 수 있습니다. 클래스를 구현 하는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> 인터페이스 구현 해야 합니다는 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 인터페이스입니다. 텍스트 뷰를 검색 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> 쿼리하여 개체를 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 에 전달 되는 개체는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> 메서드. 하나의 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> 각 보기에 대 한 개체입니다.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|사용자의 코드 창에 입력 하는 명령을 차단 합니다. 출력을 모니터링 하면 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 구현을 사용자 지정 완료 정보를 제공 하 고 수정 확인<br /><br /> 전달 하 여 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 텍스트 뷰를 호출 하는 개체 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>합니다.|  
  
## <a name="see-also"></a>참고 항목  
 [레거시 언어 서비스 개발](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [검사 목록: 레거시 언어 서비스 만들기](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)
