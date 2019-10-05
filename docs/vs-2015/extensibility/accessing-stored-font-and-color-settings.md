---
title: 저장 된 글꼴 및 색 설정에 액세스 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- fonts, accessing stored settings
- font and color control [Visual Studio SDK], persistence
- colors, accessing stored settings
ms.assetid: beba7174-e787-45c2-b6ff-a60f67ad4998
caps.latest.revision: 27
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fbb2f118d903eae2124e705f14c7aa7b51bf9c4d
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67821840"
---
# <a name="accessing-stored-font-and-color-settings"></a>저장된 글꼴 및 색 설정에 액세스
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 통합된 개발 환경 (IDE) 글꼴에 대 한 수정 된 설정을 저장 하 고 레지스트리에 색입니다. 사용할 수는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> 이러한 설정에 액세스 하는 인터페이스입니다.  
  
## <a name="to-initiate-state-persistence-of-fonts-and-colors"></a>글꼴 및 색의 상태 지 속성을 시작 하려면  
 글꼴 및 색 정보는 다음 레지스트리 위치에는 범주별으로 저장 됩니다. [HKCU\SOFTWARE\Microsoft \Visual Studio\\ *\<Visual Studio 버전 >* \FontAndColors\\  *\<CategoryGUID >* ] 여기서  *\<CategoryGUID >* 범주 GUID입니다.  
  
 따라서에 지 속성을 시작 하려면 VSPackage 수행 해야 합니다.  
  
- 가져올는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> 인터페이스를 호출 하 여 `QueryService` 전역 서비스 공급자에 대 한 합니다.  
  
     `QueryService` 서비스 ID 인수를 사용 하 여 호출 해야 합니다 `SID_SVsFontAndColorStorage` 와의 인터페이스 ID 인수 `IID_IVsFontAndColorStorage`합니다.  
  
- 사용 하 여는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> 메서드 인수로 범주의 GUID 및 모드 플래그를 사용 하 여 지속할 범주를 열려고 합니다.  
  
  지정 된 모드를는 `fFlags` 인수를 값에서 생성 되는 <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> 열거형입니다. 이 모드를 제어합니다.  

  - 통해 액세스할 수 있는 설정의 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> 인터페이스입니다.  

  - 모든 설정 또는 경우에 사용자를 수정 하는 이며이 통해 검색할 수는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> 인터페이스입니다.  

  - 사용자 설정 변경 내용을 전파 방식입니다.  

  - 사용 되는 색 값의 형식입니다.  

## <a name="to-use-state-persistence-of-fonts-and-colors"></a>글꼴 및 색의 상태 지 속성을 사용 하려면  
 유지 글꼴 및 색에 포함 됩니다.  
  
- IDE 설정 레지스트리에 저장 된 설정을 사용 하 여 동기화 합니다.  
  
- 레지스트리 수정 정보를 전파 합니다.  
  
- 설정 하 고 설정을 레지스트리에 저장 된 검색 됩니다.  
  
  IDE 설정을 사용 하 여 저장소 설정을 동기화 하는 것은 대부분 투명 합니다. 기본 IDE에 대 한 업데이트 된 설정을 자동으로 작성 **표시 항목** 범주의 레지스트리 항목에 있습니다.  
  
  VSPackage 이벤트는 생성 해야 여러 Vspackage 특정 범주를 공유 하는 경우 때의 메서드는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> 인터페이스는 저장된 레지스트리 설정을 수정 하는 데 사용 됩니다.  
  
  이벤트 생성은 기본적으로 사용 되지 않습니다. 이벤트 생성을 사용 하려면 범주를 사용 하 여 열려 있어야 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>합니다. 이렇게 하면 적절 한 호출을 IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> VSPackage 구현 하는 메서드입니다.  
  
> [!NOTE]
> 통해 수정 합니다 **글꼴 및 색** 의 독립 이벤트를 생성 하는 속성 페이지 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>합니다. 사용할 수는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> 인터페이스의 메서드를 호출 하기 전에 캐시 된 글꼴 및 색 설정의 업데이트가 필요한 지 여부를 결정 하는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> 클래스입니다.  
  
### <a name="storing-and-retrieving-information"></a>저장 하 고 정보를 검색 합니다.  
 Vspackage 호출 얻거나 열기는 범주에는 명명 된 표시 항목에 대 한 사용자가 수정할 수 있는 정보를 구성 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> 및 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetItem%2A> 메서드.  
  
 글꼴에 대 한 정보를 사용 하 여 가져온 특정 범주에 대 한 특성을 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> 고 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetFont%2A> 메서드.  
  
> [!NOTE]
> `fFlags` 에 전달 되는 인수를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> 메서드는 범주 열렸을 때의 동작을 정의 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> 및 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> 메서드. 기본적으로 이러한 메서드 정보를만 반환 aboutdisplay itemsthat 변경 되었습니다. 그러나 범주를 사용 하 여 열면 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> 플래그를 모두 업데이트 하 고 변경 되지 않고 표시 항목으로 액세스할 수 있습니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> 및 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A>합니다.  
  
 기본적으로 변경할 **표시 항목** 레지스트리에 보관 됩니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> 인터페이스를 사용 하 여 글꼴 및 색에 대 한 모든 설정을 검색할 수 없습니다.  
  
> [!NOTE]
> 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> 하며 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> 메서드는 변경에 대 한 REGDB_E_KEYMISSING, 사용 정보를 검색 하는 경우 (0x80040152L)를 반환 합니다. **표시 항목**합니다.  
  
 모든 설정 **표시 항목** 특정에서 **범주** 의 메서드를 사용 하 여 얻을 수 있습니다는 `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults` 인터페이스입니다.  
  
## <a name="see-also"></a>참고 항목  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>   
 [사용자 지정 범주 및 표시 항목 구현](../extensibility/implementing-custom-categories-and-display-items.md)
