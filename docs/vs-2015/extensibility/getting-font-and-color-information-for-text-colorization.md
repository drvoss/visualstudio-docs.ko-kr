---
title: 글꼴 및 텍스트 색 지정에 대 한 색 정보를 가져오는 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- text, coloring
- font and color control [Visual Studio SDK], coloring
ms.assetid: d1f985bd-743e-40b7-9458-d9af53647c91
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8724c31accb26e478c2726dfe791256994fc95ca
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65696851"
---
# <a name="getting-font-and-color-information-for-text-colorization"></a>글꼴 및 텍스트 색 지정에 대 한 색 정보 가져오기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

렌더링 또는 사용자 인터페이스 (UI) 요소에 컬러로 텍스트를 표시 하는 프로세스는 프로젝트, 기술 및 개발자 환경 설정의 유형에 따라 달라 집니다. 합니다 **글꼴 및 색** 속성 페이지 설정을 저장 합니다.  
  
 컬러로 텍스트를 표시 하는 대부분의 구현 해야 합니다 `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults` 디스플레이 설정 표시, 검색 및 텍스트를 저장에 대 한 인터페이스를 연결 합니다.  
  
> [!NOTE]
> 핵심 편집기 사용자 지정 하는 경우 (지 원하는 합니다 **텍스트 EditorCategory**), 언어 서비스의 색 지정 기술을 사용 하는 것이 좋습니다. 자세한 내용은 [글꼴 및 색 개요](../extensibility/font-and-color-overview.md)합니다.  
  
## <a name="getting-default-font-and-color-information"></a>기본 글꼴 및 색 정보를 가져오는  
 모든 합니다 **글꼴 및 색** 텍스트를 표시 하는 모든 창의 설정으로 지정 해야 합니다 **표시 항목** 하나의 **범주**합니다. 자세한 내용은 [글꼴 및 색, 환경, 옵션 대화 상자](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)합니다.  
  
 색을 지정 하는 VSPackage 현재 가져와야 **글꼴 및 색** 설정 합니다. VSPackage는 다음과 같은 방법으로 요구 사항에 따라이 수행할 수 있습니다.:  
  
- 저장 또는 현재 상태를 검색 하는 글꼴 및 색 지 속성 메커니즘을 사용 합니다. 자세한 내용은 [에 액세스 하는 저장 된 글꼴 및 색 설정](../extensibility/accessing-stored-font-and-color-settings.md)합니다.  
  
- 사용 된 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> 글꼴 및 색 데이터의 인스턴스를 제공 하는 서비스의 인터페이스 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>경우 VSPackage 에서도 글꼴 및 색 공급자가 아닙니다.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> 인터페이스를 구현합니다.  
  
  되었는지 확인 하려면 폴링을 통해 얻은 결과 최대 날짜는 데 유용할 수 있습니다 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> 업데이트의 검색 메서드를 호출 하기 전에 필요한 경우를 결정 하는 인터페이스를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> 인터페이스입니다.  
  
  한 후 정보를 얻은 글꼴 및 색, 색 지정을 요구 하는 요소를 식별 하 게 표시 될 텍스트를 구문 분석 및 적절 한 글꼴 및 색을 사용 하는 창에 텍스트를 표시 합니다.  
  
## <a name="see-also"></a>참고 항목  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>   
 [글꼴 및 텍스트 사용](https://msdn.microsoft.com/library/d43640f3-da94-4df2-a29d-a9d021a1c069)   
 [색 작업](https://msdn.microsoft.com/library/d34ff96f-241d-494f-abdd-13811ada8cd3)   
 [GDI (그래픽 장치 인터페이스)](https://msdn.microsoft.com/7e1d4540-bb2e-4257-8eee-eee376acba83)
