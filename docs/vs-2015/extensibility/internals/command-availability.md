---
title: 명령 가용성 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, context
- menu items, visibility contexts
ms.assetid: c74e3ccf-d771-48c8-a2f9-df323b166784
caps.latest.revision: 35
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f060f6c49fc02c75b3fe9f792133c9ee88c6d56c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63441597"
---
# <a name="command-availability"></a>명령 가용성
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio 컨텍스트에 사용할 수 있는 명령을 결정 합니다. 컨텍스트는 현재 프로젝트, 현재 편집기, 로드 되는 Vspackage 및 통합된 개발 환경 (IDE)의 다른 측면에 따라 변경할 수 있습니다.  
  
## <a name="command-contexts"></a>명령이 컨텍스트  
 다음 명령은 컨텍스트는 가장 일반적입니다.  
  
- **IDE** IDE에 의해 제공 되는 명령은 항상 사용할 수 있습니다.  
  
- **VSPackage** Vspackage 명령을 표시 하거나 숨길 때 정의할 수 있습니다.  
  
- **프로젝트** 프로젝트 명령 현재 선택한 프로젝트에만 표시 합니다.  
  
- **편집기** 하나만 편집기 한 번에 활성화 될 수 있습니다. 활성 편집기에서 명령을 사용할 수 있습니다. 편집기는 언어 서비스와 긴밀 하 게 작동합니다. 언어 서비스에 연결된 된 편집기의 컨텍스트에서 해당 명령을 처리 해야 합니다.  
  
- **파일 형식** 편집기에는 둘 이상의 파일 형식을 로드할 수 있습니다. 사용 가능한 명령 파일 형식에 따라 변경할 수 있습니다.  
  
- **활성 창** 마지막 활성 문서 창이 키 바인딩에 대 한 사용자 인터페이스 (UI) 컨텍스트를 설정 합니다. 그러나 내부 웹 브라우저를 유사한 키 바인딩 테이블이 있는 도구 창 UI 컨텍스트를 설정할 수도 없습니다. HTML 편집기와 같은 다중 탭 문서 창에 대 한 모든 탭에는 다른 명령을 컨텍스트가 GUID입니다. 도구 창을 등록 되 면 항상 사용할 수 있기에 **보기** 메뉴.  
  
- **UI 컨텍스트의** UI 컨텍스트 변수의 값으로 식별 됩니다 합니다 <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> 클래스, 예를 들어 <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid> 솔루션을 빌드할 때 또는 <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid> 디버거가 활성 상태일 때. 여러 UI 컨텍스트는 동시에 활성화할 수 있습니다.  
  
## <a name="defining-custom-context-guids"></a>사용자 지정 컨텍스트 Guid를 정의합니다.  
 경우 GUID는 아직 정의 되지 않은 적절 한 명령 컨텍스트를 VSPackage의 하나를 정의 하 고 프로그램을 작성 하 게 활성 또는 비활성 명령의 표시 유형을 제어 하려면 필요에 따라 수입니다.  
  
1. 컨텍스트 Guid를 호출 하 여 등록 된 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> 메서드.  
  
2. 호출 하 여 GUID 컨텍스트의 상태를 가져오기는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> 메서드.  
  
3. 호출 하 여 상황에 맞는 Guid 설정 및 해제를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> 메서드.  
  
    > [!CAUTION]
    > VSPackage 영향을 주지 않습니다 모든 기존 컨텍스트 Guid에 따라 달라질 수 있습니다 다른 Vspackage 때문에 있는지 확인 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [선택 컨텍스트 개체](../../extensibility/internals/selection-context-objects.md)   
 [VSPackage에서 사용자 인터페이스 요소를 추가하는 방법](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
