---
title: 문자 모양 제어 (소스 제어 VSPackage) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- glyphs, source control packages
- source control packages, glyphs
ms.assetid: b9413b08-b3c3-4fc3-a6e0-3dc0db3652d7
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b0960209b67c8d2f111296840119807d95bb2e2d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62538423"
---
# <a name="glyph-control-source-control-vspackage"></a>문자 모양 제어(소스 제어 VSPackage)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

전체 통합 소스 제어 Vspackage를 사용할 수 있는 부분은 원본 제어에서 항목의 상태를 나타내는 고유한 문자 모양을 표시 하는 기능입니다.  
  
## <a name="levels-of-glyph-control"></a>수준의 문자 모양 제어  
 상태 문자 모양을 예제에 표시 하는 경우 항목의 현재 상태를 나타내는 아이콘이 **솔루션 탐색기** 나 **클래스 뷰**합니다. 소스 제어 VSPackage 두 가지 수준의 문자 모양 컨트롤을 발휘할 수 있습니다. 제공 하는 문자 집합을 미리 정의 된 문자 모양 선택을 제한할 수 있습니다는 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE 또는 표시할 문자 모양 사용자 지정 집합을 정의할 수 있습니다.  
  
### <a name="default-set-of-glyphs"></a>기본 문자 집합  
 구조의 항목과 연결 된 상태 문자 모양을 결정할 **솔루션 탐색기**, 프로젝트를 사용 하 여 소스 제어에서 상태 문자 모양 요청는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.GetSccGlyph%2A>합니다. 소스 제어 VSPackage는 IDE에서 제공 하는 미리 정의 된 문자 모양으로 제한 하는 문자 모양 선택 계속 하도록 결정할 수 있습니다. 이 경우 VSPackage vsshell.idl에서 정의한 문자 모양 열거형을 나타내는 값의 배열을 다시 전달 합니다. 자세한 내용은 참조 하세요. <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon> 합니다. "체크 인" 문자 및 문자 모양 "체크 아웃"으로 확인란에 대 한 자물쇠와 같은 IDE에 의해 설정 되는 모양의 미리 정의 된 집합입니다.  
  
### <a name="custom-set-of-glyphs"></a>사용자 지정 문자 모양 집합  
 소스 제어 VSPackage 설치 될 때 고유한 "모양과 느낌을"에 대 한 고유한 문자 모양을 사용할 수 있습니다. 새 소스 제어 VSPackage 활성화 되 면 고유한 문자 모양 이전 소스 제어 VSPackage 하는 경우에 여전히 로드를 사용 하 여 시작할 수 있지만 비활성 해야 합니다. 이 모드에서는 소스 제어 VSPackage 여전히 아이콘을 사용할 수는 기존 참조와 일치 유지 하기 위해 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 을 선택 하는 경우.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> 서비스 인터페이스를 지 원하는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>, 있으며 VSPackage를 선택적으로 구현할 수는 IDE에 의해 요청 수는 있습니다. IDE를 요청 하면 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 현재 등록 된 소스 제어 VSPackage에서에서이 인터페이스를 가져오려면 다시 시도 합니다. 인터페이스를 등록된 하는 VSPackage에 있는 경우 사용자 지정 문자 모양에 대 한 IDE의 요청이 성공 합니다. 이 고, 그렇지는 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE 모양의 해당 기본 집합을 사용 합니다.  
  
 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs.GetCustomGlyphList%2A> 메서드를 사용 하 여 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 상태를 다양 한 소스 제어를 보여 주는 이미지 목록을 가져옵니다. 소스 제어 VSPackage는 사용자 지정 문자 모양에 대 한 이미지 목록에 대 한 핸들을 IDE에 반환합니다. 이미지 목록의 복사본을 시점에서 표시할 문자 모양이 선택 나중에 사용 하는 IDE. 새 인터페이스를 지원 하지 않는 경우 또는 `IVsSccGlyphs::GetCustomGlyphList` 메서드 E_NOTIMPL을 반환 하는 IDE에서 제공 되는 모양의 기본 목록에서 해당 문자 모양을 가져옵니다 합니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]합니다.  
  
## <a name="see-also"></a>참고 항목  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>   
 <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>
