---
title: 사용자 인터페이스 업데이트 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, updating
- commands, updating UI
ms.assetid: 376e2f56-e7bf-4e62-89f5-3dada84a404b
caps.latest.revision: 42
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: db5be965119d1564f2a4bf8a15892af7142663e0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68186351"
---
# <a name="updating-the-user-interface"></a>사용자 인터페이스 업데이트
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

명령을 구현한 후에 새 명령의 상태를 사용 하 여 사용자 인터페이스를 업데이트 하는 코드를 추가할 수 있습니다.  
  
 일반적인 Win32 응용 프로그램을 명령 집합을 지속적으로 폴링할 수 있습니다 하 고 해당 사용자를 볼 경우에 개별 명령의 상태를 조정할 수 있습니다. 그러나 때문에 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 셸 Vspackage의 무제한을 호스트할 수 있습니다, 광범위 한 폴링 응답성, 특히 관리 코드와 COM. interop 어셈블리에서 폴링 저하 될 수 있습니다  
  
### <a name="to-update-the-ui"></a>UI를 업데이트 하려면  
  
1. 다음 단계 중 하나를 수행합니다.  
  
    - <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> 메서드를 호출합니다.  
  
         <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> 인터페이스에서 가져올 수 있습니다는 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> 서비스를 다음과 같이 합니다.  
  
        ```csharp  
        void UpdateUI(Microsoft.VisualStudio.Shell.ServiceProvider sp)  
        {  
            IVsUIShell vsShell = (IVsUIShell)sp.GetService(typeof(IVsUIShell));  
            if (vsShell != null)  
            {  
                int hr = vsShell.UpdateCommandUI(0);  
                Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(hr);  
            }  
        }  
  
        ```  
  
         하는 경우의 매개 변수를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> 0이 아닌 (`TRUE`)를 동기적으로 한 즉시 업데이트가 수행 됩니다. 0을 전달 하는 것이 좋습니다 (`FALSE`) 좋은 성능을 유지 하기 위해이 매개 변수에 대 한 합니다. 캐시 하지 않도록 하려는 경우 적용 된 `DontCache` .vsct 파일에서 명령을 만들 때 플래그입니다. 그럼에도 불구 하 고 플래그를 신중 하 게 사용 또는 성능 저하 될 수 있습니다. 명령 플래그에 대 한 자세한 내용은 참조는 [Command Flag 요소](../extensibility/command-flag-element.md) 설명서.  
  
    - 창에서 바로 활성화 모델을 사용 하 여 ActiveX 컨트롤을 호스트 하는 vspackage에서 더 편리할 수 있습니다 사용 하 여 <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> 메서드. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> 의 메서드를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> 인터페이스 및 <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> 에서 메서드를 <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> 인터페이스는 기능적으로 동일 합니다. 모두 다시 모든 명령의 상태를 쿼리하려면 환경을 발생 합니다. 일반적으로 업데이트를 즉시 수행 되지 않습니다. 대신, 업데이트 하는 유휴 시간까지 지연 됩니다. 셸 좋은 성능을 유지 하기 위해 명령 상태를 캐시 합니다. 캐시 하지 않도록 하려는 경우 적용 된 `DontCache` .vsct 파일에서 명령을 만들 때 플래그입니다. 그럼에도 불구 하 고 사용 하 여 플래그를 신중 하 게 성능 저하 될 수 있습니다.  
  
         통지를 가져올 수 있습니다는 <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> 인터페이스를 호출 하 여는 `QueryInterface` 메서드는 <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager> 개체 또는에서 인터페이스를 가져오는 <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> 서비스.  
  
## <a name="see-also"></a>관련 항목  
 [Vspackage에서 사용자 인터페이스 요소를 추가 하는 방법](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [구현](../extensibility/internals/command-implementation.md)
